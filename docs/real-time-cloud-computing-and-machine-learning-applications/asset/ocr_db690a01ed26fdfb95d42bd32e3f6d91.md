# Server and Servlet Architectures for a Cloud-Based Real-Time .

```
//Getting number of items in the database so that arrays can be initialisedntry {
    Database db = client.database("androidcloudparameters", false);
    System.out.println("Trying to read all records from database...");
    String query = 
    "{"selector":{\"Key\":0},\"fields":{\"Key\":1},"sort":{\"Key\":\"desc\"}}";
    QueryResultSet-LinkedTreeMap queryResult = db.query(query, (Class)LinkedTreeMap.class);
    LinkedTreeMap result = queryResult.getDocs();
    if (result.size() > 0) {
        numbits = result.get(0).get("Key");
    }
} catch (Exception e) {
    System.out.println("Problem fetching number of items: " + e.toString());
}

// Retrieving data from database
try {
    Database dbRetrive = client.database("androidcloudparameters", false);
    String query = "{"selector":{" + 
 +"KeyKey\":{" + 
    "\$gt\":0" + "} + ", + + "fieldsfields":{" + " +nn    "\Key\" + ", " + 
    "\DownloadSpeed\" + ", " + "\UploadSpeed\" + ", " + 
    "\MobileDownloadSpeed\" + ", " + "\MobileUploadSpeed\" + ", " " + 
    "\PacketsReceived\" + ", " + "\PacketsSent\" + ", " " + 
    "\WiFiStrength\" + ", " + "\Timestamp\" + ", " + +"sort":{" + 
    "{" + "\Key\":{" + "\asc\":1} + "},{" + "\Key\":1}}";
    QueryResultSet-LinkedTreeMap queryParameters = dbRetrive.query(query, (Class)LinkedTreeMap.class);
    LinkedTreeMap parameters = queryParameters.getDocs();
    for (int i = 0; i < numbits; i++) {
        keys = (Double)parameters.get(i).get("Key");
        downspeed = (Double.parseDouble((String)
parameters.get(i).get("DownloadSpeed")));
        upspeed = (Double.parseDouble((String)
parameters.get(i).get("UploadSpeed")));
        pacRec = (Double.parseDouble((String)
parameters.get(i).get("PacketsReceived")));
        pacSent = (Double.parseDouble((String)
parameters.get(i).get("PacketsSent")));
        mobDspeed = (Double.parseDouble((String)
parameters.get(i).get("MobileDownloadSpeed")));
        mobUspeed = (Double.parseDouble((String
```