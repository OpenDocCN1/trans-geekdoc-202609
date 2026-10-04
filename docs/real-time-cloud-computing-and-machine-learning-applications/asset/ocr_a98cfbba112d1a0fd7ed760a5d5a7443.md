```
// Executing the query and obtaining the results
resultSet = m_Statement.executeQuery(query);
} catch (ClassNotFoundException | SQLException ex) {
    System.out.println("SQL EXCEPTION");
}

// Retrieving the last set of values - set cursor to last row
if (resultSet != null) {
    try {
        resultSet.last(); // Moves cursor to the last row
        keys = Double.parseDouble(resultSet.getString(1));
        downspeed = Double.parseDouble(resultSet.getString(3));
        pacRec = Double.parseDouble(resultSet.getString(4));
        pacSent = Double.parseDouble(resultSet.getString(5));
        timestamp = resultSet.getString(6);
    } catch (SQLException ex) {
        System.out.println("SQL EXCEPTION");
    }
} else {
    // Connecting to cloud using credentials
    try {
        client = ClientBuilder.url(new URL("https://8118bf82-40f1-4173-be30-7fe6fb8e6d7-bluenix.cloud.com/"))
            .username("apikey-5c2c3ef26874d4f6cb69a1350c71a5")
            .password("a2ec8f6bd2fd97774e07402f86da6bcf9a")).build();
        System.out.println("Successful connection made to cloud...");
    } catch (IOException e) {
        System.out.println("Error accessing cloud: " + e);
    }
}
// Getting number of items in the database so that arrays are initialisedntry {
    Database db = client.database("laptopcloudparameters", false);
    System.out.println("Trying to read records from database...");
    String query = "{"selector":{\"Key\":{\"$gt:0\}},\"fields\":[{\"Key\":{\"$desc\":"}}]}}";
    QueryResultLinkedMap queryResult = db.query(query, 
        Class<LinkedMap.class>);
    List<LinkedMap> resultSet = queryResult.getDocs();
    if (resultList.size() > 0) {
        numitems = (double) resultSet.get("Key");
    }
```