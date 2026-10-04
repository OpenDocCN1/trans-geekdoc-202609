# 4.3.11.9. Fetching Values from Cloudant Database

This method is mentioned in Section 5.1 and simply fetches all the parameters from the Cloudant database, before storing them in double and String arrays, created as global variables.

# Listing 4.50. fetchRegressionValuesAndroid() method

```
// Fetching all values in database for Android
public void fetchRegressionValuesAndroid() {
    // Making connection to the cloud
    try {
        client = ClientBuilder.url(new URL("https://8118bf82-4f01-4173-be30-7fe6ff8e7d-bluemix.cloudant.com"))
            .username("apikey-f41d7e2574b134b8c26dba1b8dc")
            .password("ee7af593849bde695eefad7e2255ffa7d0a98e")
            .build();
        System.out.println("Success connection to cloud...");
    } catch (IOException e) {
        System.out.println("Error accessing cloud: " + e);
    }
    // Getting items from database so that arrays can be initialised
    Database db = client.database("androidcloudparameters", false);
    System.out.println("Trying to read all records from database...");
    String query = "{"selector":{\"Key\":0},\"fields":{\"Key\":""}},"sort":{\"Key\":"desc\"}}";

    QueryResult<LinkedTreeMap> queryResult = (QueryResult<LinkedTreeMap>) (Class) LinkedTreeMap.class);
    List<LinkedTreeMap> resultList = queryResult.getDocs();
    if (resultList.size() > 0) {
        numitems = (double) resultList.get(0).get("Key");
```