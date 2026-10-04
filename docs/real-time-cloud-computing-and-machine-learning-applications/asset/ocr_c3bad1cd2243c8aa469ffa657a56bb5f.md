660 T. P. Fowder, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoonon

# 6.4.4.8. The requestAnalyticsLocal() Method

To query the java server for forecast results, the window size and prediction time need to be entered in the respective JTextField. Then, the predict button is pressed and the predictActionPerformed() method is invoked. If the value of "src_local" is set to true, analytics is fetched from the local server else the servlet hosted in the client else is contacted for the results.

To query the Local Java server for forecasting results, a Socket connection is first open to the IP address entered by the user on port 11111. A JSONObject is created to store the request type, window size, and prediction time entered by the user. The JSONObject is sent to the server. The server processes the request and returns the analytics results in a JSONObject. The data is extracted from the JSONObject, formatted into a readable format using the getData() method and displayed in the TextView. The codes for the QueryLocalStorage Class are given in Listing 6.29.

# Listing 6.29. requestAnalyticsLocal method

```
public void requestAnalyticsLocal() {
//Starts anonymous Thread to request analytics from the local server
new Thread(() -> {
try {
//Stores the window size & prediction time in a JSONObject
JSONObject jsonObject = new JSONObject();
jsonObject.put("request", "analytics");
jsonObject.put("window_size", Integer.parseInt(window.getText()));
jsonObject.put("prediction_time", Integer.parseInt(ptime.getText()));

//Opens a socket connection to the Java local server
Socket socket = new Socket(address.getText(), 11111);
//Create a PrintWriter from the socket OutputStream
PrintWriter out = new PrintWriter(socket.getOutputStreamStream());
//Sends the data to the local server
out.println(jsonObject);
out.flush();

//creates a Buffered Object from the socket InputStream
InputStream inputStream = socket.getInputStream();
//Encapsulates it in an InputStreamReader
InputStreamReader isr = new InputStreamReader(inputStream);
//Encapsulates it in a BufferedReader
BufferedReader br = new BufferedReader(isr);
//Read the data from the BufferedReader object.
```