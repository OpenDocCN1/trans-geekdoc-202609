# 380 T. P. Fowdur, L. Babooram, M. N-U-Dbn Nazir Rosun and M. Indoondonon

```
result.append(inputLine);
}
//Getting the result in raw String format
System.out.println("RESULT IS: " + result);
// Converting that result into a JSONObject that can be String
easy read
JSONObject json = new JSONObject(result.toString());
// Extracting the actual value from the JSONObject
final String classificationKNN = (String)
json.get("knnClassification");
final String classificationMLP = (String)
json.get("mlpClassification");
System.out.println("Classification using KNN: " +
classificationKNN);
System.out.println("Classification using MLP: " +
classificationMLP);
// Updating the UI:
```

```
resultArea.setText("Client activity using KNN: " +
classificationKNN + "\n" + "Client activity using MLP: " +
+ classificationMLP);
catch (JSONException ignored) {
catch (IOException exception) {
Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE, null, ex);
}
catch (MalformedURLException exception) {
Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE,
null, ex);
catch (IOException exception) {
Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE,
null, ex);
}
}
}

```

// Thread to start classification analytics using local server running on
NetBeans

```
classifyThreadLocal = new Thread(){
public void run() {
try {
// Clear the fetching area upon clicking the button
resultArea.setText("");
// Trying to send data to local server, if active
try {
// Making connection to local server running on PC
host = (ipAddress.getText()).toString());
Socket socket = new Socket(host, port2);
// PrintWriter object to write JSONObject parameters to PC
PrintWriter out = new
```