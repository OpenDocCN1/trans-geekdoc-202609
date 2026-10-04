# 658 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoondonman

is saved to the database and the connection is shut down. The codes for this operation are shown in List 6.27.

# Listing 6.27. sendData Method

```
public void sendData(JSONObject currentReadings) {
  try {
    /* Send the data to Database.*/
    CloudantClient client = ClientBuilder.URL(new URL(
      ("/ic3ce0434f-ab39-4abf-a854-5532a64d1f89-bluemixcloud.com/"))
    ).username("apikey-ec10b30de78974b57ab57b516f949965093")
    .password("69385274f8ec7098c35f032fbc7ef4606fb").build();\n
    /* Database API implementation to connect to the weather_data database
       create flag - set to false so that the database is not created if it does not exist.*/
    Database database = client.database("weather_data", false);
//String representation of the query to select all data and sort in descending order of idx
    final String query = "{"selector":{\"idx\":{\$gt\ 0}},"sort":{\"idx\":\desc\}}";
    //Execute the query on the selected database "weather_data"
    QueryResult-LinkedTreeMap queryResult = database.query(query, LinkedTreeMap.class);
    //Fetches the list of documents matching the query
    List-LinkedTreeMap resultList = query.getDocs();
    //Fetch the value of idx returns 1 if the database is empty
    double idx = (resultList.size() > 0) ? (double) resultList.get(0).get("idx") : 1;
    //Increment the idx by 1 and add to the JSONObject currentReadings.put("idx", idx + 1);
    //Save the JSONObject to the database
    database.save(currentReadings.toMap());
    //Close the connection to the Cloudant Database
    client.shutdown();
  } catch (MalformedURLException ex) {
    Logger.getLogger("MonitoringFrame").class.getName()).log(Level.SEVERE, null,ex);
  }
}
```