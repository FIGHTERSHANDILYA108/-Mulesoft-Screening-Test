    /**
     * Get the movies whose actor has appeared more than one time
     * @param count
     */
     
    public void getCountGreaterThan(int count){
               String sql = "SELECT movie "
                          + "FROM movies WHERE count(actor) > 1";

        try (Connection conn = this.connect();
             PreparedStatement pstmt  = conn.prepareStatement(sql)){

            // set the value
            pstmt.setInt(1,count);
            //
            ResultSet rs  = pstmt.executeQuery();

            // loop through the result set
            while (rs.next()) {
                System.out.println(rs.getString("movie"));
            }
        } catch (SQLException e) {
            System.out.println(e.getMessage());
        }
    }
