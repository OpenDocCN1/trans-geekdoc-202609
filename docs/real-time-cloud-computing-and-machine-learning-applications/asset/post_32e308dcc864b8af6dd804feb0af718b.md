
# 376 T. P. Fowdur, L. Babooram, M. N-D-Ibn Naz Rosun and M. Indoondonon

```java
+ "&predictionTime=" + String.valueOf(ptime)
+ "&windowSize=" + String.valueOf(window)
+ "&device=" + 1
+ "&action=" + 2
+ "&source=" + 1);
```

```java
System.out.println("URL IS:" + url.toString());
resultArea.setText("Performing regression analytics. Please wait...");
```

```java
// Open a URL to receive the data sent by servlet
Connection connection = url.openConnection();
// Listening for data
```

```java
try (BufferedReader in = new BufferedReader(new InputStreamReader(connection.getInputStream()))) {
// Preparing incoming data into readable format
String inputLine;
// Object to hold the result
StringBuilder result = new StringBuilder();
// While data is read
while ((inputLine = in.readLine()) != null) {
// Append any character to the String
result.append(inputLine);
}
```

```java
System.out.println("URL IS:" + url.toString());
resultArea.setText("Performing regression analytics. Please wait...");
```

```java
// Open a URL to receive the data sent by servlet
Connection connection = url.openConnection();
// Listening for data
```

```java
try (BufferedReader in = new BufferedReader(new InputStreamReader(connection.getInputStream()))) {
// Preparing incoming data into readable format
String inputLine;
// Object to hold the result
StringBuilder result = new StringBuilder();
// While data is read
while ((inputLine = in.readLine()) != null) {
// Append any character to the String
result.append(inputLine);
}
```

```java
// Getting the result in raw String format
System.out.println("RESULT IS: " + result);
// Converting String into a JSONObject that can be easily read
JSONObject json = new JSONObject(result.toString());
```

# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 377

```java
// Extracting the actual value from the JSONObject
final String predictionMLR = (String) json.get("mlrRegression");
final String predictionMLP = (String) json.get("mlpRegression");

System.out.println("Prediction using MLR: " + predictionMLR);
System.out.println("Prediction using MLP: " + predictionMLP);
// Updating the UI:
System.out.println("Prediction using MLR: " + predictionMLR);
System.out.println("Prediction using MLP: " + predictionMLP);
// Updating the UI:
resultArea.setText("Prediction using MLR: " + predictionMLR
+ " packets received: " + "Prediction using MLP: "
+ predictionMLP + " packets received");

catch (JSONException ignored) {
} catch (IOException ex) {
    Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE, null, ex);
} catch (MalformedURLException ex) {
    Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE, null, ex);
} catch (IOException ex) {
    Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE, null, ex);
}
}

predictThreadLocalhost = new Thread() {
public void run() {
try {
    // Clear the fetching area upon clicking the button
    resultArea.setText("");
    // Trying to send data to local server, active
    try {
    // Making connection to local server running on NetBeans
    host = (ipAddress.getText()).toString();
    Socket socket = new Socket(host,port2);
    // PrintWriter object to write JSONObject parameters
```

# 378 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nasir Rosun and M. Indoondonon

```java
PrintWriter out = new PrintWriter(socket.getOutputStream());
try {
    // Filling the JSONObject to indicate localhost
    requestCode.put("requestCode", 8);
    requestCode.put("predictionTime", ptime);
    requestCode.put("windowSize", window);
} catch (JSONException e) {
    System.out.println("Connection error");
}

// Sending the values through the socket connection
out.println(requestCode);
// Flushing the stream after each set
out.flush();

// Receiving the result from the local server
BufferedReader bufferedReader = new BufferedReader(
InputStreamReader(socket.getInputStream()));
String str;
StringBuilder sb = new StringBuilder();
while ((str = bufferedReader.readLine()) != null) {
    sb.append(str + "\n");
    resultArea.append(str + "\n");
}
System.out.println("Message from local server: " + sb.toString());
} catch (Exception e) {
    System.out.println("Connection error");
}
} catch (Exception ex) {
    System.out.println("Exception");
}

// Starting the above defined thread depending on the radio button selected on the GUI
if (analyticsCloudant.isSelected()) {
    predictThread.start();
}
if (analyticsLocal.isSelected()) {
    predictThreadLocalhost.start();
}
```

# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 379

## 4.4.11.2. Classify Button

The same processes elaborated in Section 4.3.10.2 are repeated for the classification button, except that it makes current network parameters in its query to the servlet. The request codes for the local server are again as per Table 4.7.

Listing 46.7. Populating the classify button

```java
// Classify button
private void classifyButtonActionPerformed(java.awt.event.ActionEvent evt) {
    public void run() {
        try {
            // Creates the corresponding URL to the query servlet
            // Adding dummy values for prediction time and window.
            URL url = new URL("http://networkcloud-eu-gb.bymemix/net.mil?")
                + "&downloadSpeed=" + String.valueOf(downloadSpeed)
                + "&uploadSpeed=" + String.valueOf(uploadSpeed)
                + "&packetsReceived=" + String.valueOf(packetsReceived)
                + "&packetsSent=" + String.valueOf(packetsSent)
                + "&predictionTime=" + 10
                + "&windowSize=" + 20
                + "&device=" + 1
                + "&action=" + 2
                + "&source=" + 1);
            resultArea.setText("Performing classification analytics. Please wait...");
            // ... (rest of logic follows)
        } catch (Exception e) {
            // handle handling
        }
    }
}
```

# 380 T. P. Fowdur, L. Babooram, M. N-D-Ibn Naz Rosun and M. Indoondonon

```java
// Extracting the actual value from the JSONObject
final String classificationKNN = (String) json.get("knnClassification");
final String classificationMLP = (String) json.get("mlpClassification");

System.out.println("Classification using KNN: " + classificationKNN);
System.out.println("Classification using MLP: " + classificationMLP);
// Updating the UI:
resultArea.setText("Client activity using KNN: " + classificationKNN
+ "\n" + "Client activity using MLP: "
+ classificationMLP);

catch (IOException ex) {
    Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE, null, ex);
} catch (MalformedURLException ex) {
    Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE, null, ex);
} catch (IOException ex) {
    Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE, null, ex);
}
```
