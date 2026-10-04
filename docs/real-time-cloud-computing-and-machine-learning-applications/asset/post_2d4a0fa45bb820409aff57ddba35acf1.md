
# Server and Servlet Architectures for a Cloud-Based Real-Time .

```java
System.out.println("Creating server for edge device on port: " + port);
try {
    // Creating the ServerSocket object
    ServerSocket ss = new ServerSocket(port);
    System.out.println("Waiting for connection...");
    // While connections are made
    while (true) {
        // Accepting connection from client device
        Socket socket = ss.accept();
        // Getting the input stream using the BufferedReader
        // Encapsulating the input in an InputStreamReader
        BufferedReader br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
        // Reading the full message using a String object
        String str = br.readLine();
        // Converting the String object into a JSON object
        JSONObject readings = (new JSONObject(str));
        System.out.println("Fetching request code from edge device...");
        // Extracting values from the JSON Object
        int requestCode = readings.getInt("requestCode");
        System.out.println("Request Code: " + requestCode);
        // PrintWriter to write JSONObject parameters to Edge device
        PrintWriter out = new PrintWriter(socket.getOutputStream());
        // Switch statement to differentiate between requests
        switch (requestCode) {
            // Listings 5.31 and 5.32 are placed here
        }
    }
} catch (IOException ex) {
    System.out.println(ex);
} catch (Exception ex) {
    Logger.getLogger(LocServer.class.getName()).log(Level.SEVERE, null, ex);
}

// Creating a Thread to start the Runnable thread
Thread launchThread = new Thread(localDAServer);
// Start the thread to launch the server
launchThread.start();
```

500 T. P. Fowdur, L. Babooram, M. N-U-Dbn Nazir Rosun and M. Indoonondan

Listing 5.31 and 5.32 make use of the same principles used for the download and analytics functionalities aforementioned, by calling their respective methods based on the received request codes. For the Android device, Listing 5.31 is placed inside the switch statement in Listing 5.30.

# Listing 5.31. Local download and analytics for Android edge device

```java
// Android - Download to csv by N samples:
case 1:
    // Set the fetching for android regression values to true
    fetchRegressionAndroid = true;
    // Fetching all values from the local android database
    fetchRegressionAndroid();
    // Getting the length from the JSONObject from the Android device
    length = readings.getDouble("lengthSamples");
    System.out.println("Length of samples: " + length);
    // Calculating the initial value so that only the N parameters are stored
    int initial = (int) (numbers - length);
    String csvStr = "Timestamp, Download Speed, Upload Speed, Packets Received, Packets Set, Mobile Download Speed, Mobile Upload Speed, Wifi Strength" + "\n";
    // For loop last N parameters until end of database
    for (int i = initial; i < numbers; i++) {
        // Appending values to String
        csvStr = csvStr + String.valueOf(timestamp[i]).replace(",", " ") + ", " +
                 String.valueOf(upspeed[i]) + ", " + ", " +
                 String.valueOf(pacRec[i]) + ", " + ", " +
                 String.valueOf(mobSpeed[i]) + ", " + ", " +
                 String.valueOf(wstrength[i]) + ", " + ", " + "\n";
    }
    System.out.println("Sending following through socket: " + csvStr);
    // Sending the values through the socket connection
    out.println(csvStr);
    // Flushing the stream
    out.flush();
    // Closing the socket connection
    out.close();
    break;
// Android - Download to csv by date:
case 2:
    // Set the fetching for android regression values to true
    fetchRegressionAndroid = true;
    // Fetching the values from the local android database
    fetchRegressionAndroidValues();
}
```

# Server and JSONArchitectures for a Cloud-Based Real-Time . 501

```java
// Getting the date from the JSONObject from the Android device
date = readings.getString("date");
// Conversion of date fetched to yyyy-mm-dd to match format of MySQL
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("MMM d, yyyy", Locale.ENGLISH);
LocalDateConverted = LocalDate.parse(date, formatter);
// Adding header containing 8 variables
csvStr = "Timestamp, Download Speed, Upload Speed, Packets Received, Packets Sent, Mobile Download Speed, Mobile Upload Speed, Wi-Fi Strength" + "\n";
// For loop for all readings
for (int i = 0; i < numitems; i++) {
    // Appending values to the date, to the String object
    if (String.valueOf(timestamp(i)).contains(date.toString())) {
        csvStr = csvStr + String.valueOf(timestamp(i)) + ", " + ","
        + String.valueOf(downspeed(i)) + ", " + String.valueOf(upspeed(i)) + ","
        + String.valueOf(pacRec(i)) + ", " + String.valueOf(pacSent(i)) + ","
        + String.valueOf(mobDownSpeed(i)) + ", " + String.valueOf(mobUpspeed(i)) + ","
        + String.valueOf(wstrength(i)) + ", " + "\n";
    }
}
System.out.println("Sending following through socket: " + csvStr);
// Sending the values through the socket connection
out.println(csvStr);
// Flushing the stream
out.flush();
// Closing the socket connection
out.close();
break;
// Android - Regression analytics
case 3:
// Fetching the parameters for regression from Android device
predictionTime = readings.getInt("predictionTime");
windowSize = readings.getInt("windowSize");
// Set the fetching Booleans for regression values to true
fetchRegressionAndroid = true;
// Fetching the values from the local android database
fetchRegressionValues();
localRegression = true;
Regression();
// Performing MLR Regression
MLPRegression();
System.out.println("Sending following through socket: " + mlrPrediction + "\n"
+ mlpPrediction);
// Sending the values through the socket connection
out.println("Packets received with MLR: " + Math.round(mlrPrediction) + "\n");
```

```java
"Packets received with MLP: " + Math.round(mlpPrediction);\n// Flushing the stream after each set
out.flush();
// Closing the socket connection
out.close();
break;

// Android - Wi-Fi Classification analytics
case 4:
// Fetching the parameters for classification from Android device
dpeed = readings.getDouble("dpeed");
uspeed = readings.getDouble("speed");
prec = readings.getDouble("prec");
psent = readings.getDouble("psent");
// Setting boolean for Android classification to true
fetchClassificationAndroid = true;
// Fetching Android values
fetchClassificationValues();
// Setting the values in a double [] array
values = new double[] {dpeed, uspeed, prec, psent};
// Performing KNN classification
KNNClassification();
// Printing the numerical result with the highest number of nodes and
converting the label back to a String object to be printed
System.out.println("The set belongs to category: " + greatestClass.doubleValue());
if (greatestClass.doubleValue() == 1.0) {
// Sending the values through the socket connection
out.println("Client activity with KNN: idle");
out.flush();
out.close();
}
if (greatestClass.doubleValue() == 2.0) {
// Sending the values through the socket connection
out.println("Client activity with KNN: browsing");
out.flush();
out.close();
}
if (greatestClass.doubleValue() == 3.0) {
// Sending the values through the socket connection
out.println("Client activity with KNN: streaming");
out.flush();
out.close();
}
MLPClassification(); // Performing MLP classification
if (Math.round(classificationMLP) == 1) {
// Sending the values through the socket connection
out.println("Client activity with MLP: idle");
}
```

# Server and Servlet Architectures for a Cloud-Based Real-Time .

```java
out.flush();
out.close();
if (Math.round(classificationMLP) == 2) {
// Sending the values through the socket connection
out.println("Client activity with MLP: browsing");
out.flush();
out.close();
}
if (Math.round(classificationMLP) == 3) {
// Sending the values through the socket connection
out.println("Client activity with MLP: streaming");
out.flush();
out.close();
}
break;
// Android - LTE Classification analytics
case 5: 
// Fetching the parameters for classification from Android device
mdspeed = readings.getDouble("mspeed");
mspeed = readings.getDouble("mspeed");
prec = readings.getDouble("prec");
psent = readings.getDouble("psent");
// Setting boolean for Android classification to true
fetchClassificationLTE = true;
// Fetching Android LTE values
fetchClassificationValuesLTE();
// Setting the values in a double [] array
values = new double[]{mdspeed, mspeed, prec, psent};
KNNClassificationLTE(this); // Performing KNN Classification
// Printing the numerical label with the highest number of votes and
converting the label to a String object to be printed
System.out.println("The set values belongs to category: " + greatestClass.doubleValue());
if (greatestClass.doubleValue() == 1.0) {
// Sending the values through the socket connection
out.println("Client activity with KNN: idle");
out.flush();
out.close();
}
if (greatestClass.doubleValue() == 2.0) {
// Sending the values through the socket connection
out.println("Client activity with KNN: browsing");
out.flush();
out.close();
}
```
