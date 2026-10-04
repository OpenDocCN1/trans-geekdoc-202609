
292 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoondonman

## 4.3.8.2. Fetching Network Data

Network data are fetched by calling the methods explained in Listings 4.23 as 4.25 as shown in Listing 4.27.

### Listing 4.27. Calling methods to fetch network data

```
// Finding the next value for each parameter after 1 second
getTotalSpeeds();
getMobileSpeeds();
getPackets();
WifiSignalStrength();
```

### 4.3.8.3. Updating UI and Live Monitor

- 1. After obtaining the parameters, the UI is updated by using the layout variables, after which the thread is paused for one second, i.e., 1000 ms, using the postDelayed() method, as shown in Listing 4.28.

### Listing 4.28. Updating UI and live monitoring

```
// Updating the User Interface
RX.setText("WiFi Download Speed: " + downloadSpeed + " kb/s");
TX.setText("WiFi Upload Speed: " + uploadSpeed + " kb/s");
MRX.setText("LTE Download Speed: " + mobiledownloadSpeed + " kb/s");
MTX.setText("LTE Upload Speed: " + mobileuploadSpeed + " kb/s");
RXP.setText("Packets Received: " + RXPackets + " per sec");
TXP.setText("Packets Sent: " + TXPackets + " per sec");
WIFisig.setText("Wifi Signal Strength: " + Long.toString(WiFi_RSSI) + " dBm");
```

```
// Pausing the thread for 1 second
mHandler.postDelayed(mRunnable, 1000);
```

```
// Setting the initial values to the current ones to allow subsequent subtraction
initRXPackets = current_RXPackets;
initTXPackets = current_TXPackets;
initRXBytes = current_RXBytes;
initTXBytes = current_TXBytes;
initMRXBytes = current_MRXBytes;
initMTBytes = current_MTBytes;
```

- 2. A switch-mechanism is implemented in the mRunnable thread after updating the TextViewfield. This work is made using use of a Spinner and a String object, which dynamically changes upon selections on the spinner. This snippet of code works by analysing the netparams object holds and adding an entry to the chart based on what the String was. This object is defined in Listing 4.14, as a default String object that changes upon selection. For e.g., if the netparams object holds "WiFi Download Speed" as a String, the downloadSpeed object, representing the double value of the Wi-Fi download speed in Kbps, is passed as an argument through the addEntry() method, implemented in Listing 4.29.

### Listing 4.29. Switch-case for updating UI

```
// Updating the live monitor graph
switch (netparams) {
  case "WiFi Download Speed":
    addEntry(downloadSpeed);
    break;
  case "WiFi Upload Speed":
    addEntry(uploadSpeed);
    break;
  case "LTE Download Speed":
    addEntry(mobiledownloadSpeed);
    break;
  case "LTE Upload Speed":
    addEntry(mobileuploadSpeed);
    break;
  case "Packets Received":
    addEntry(RXPackets);
    break;
  case "Packets Sent":
    addEntry(TXPackets);
    break;
  case "Wifi Signal Strength":
    addEntry((double) (WIFI_RSSI));
    break;
}
```

## 4.3.8.4. Pushing Values to the Local Server

The values retrieved from the Android phone need to be pushed to a running server on NetBeans IDE, which will in turn perform functions, the first one being the parameter retrieval process and the second being filling up of a cloud database for analytics. This section, therefore, involves the codes related to the Android application sending the parameters to the local server.

Apart from fetching network parameters every second, the application needs to have an ongoing piece of code that carries out the sending process at the same time the parameters are obtained. The best choice in this scenario is another thread, which is placed inside the Runnable thread in Listing 4.30. The steps are described below.

- 1. In this thread, a connection is made to the running server using the Socket class which aims towards providing a pathway for communication between two devices. A previously created String object, is used to fetch the IP address returned by the user in the EditText input on the layout. This is returned through the getText().toString() methods that convert the text into a String object. The obtained IP address and the port number, stored as an integer on which the server is listening are specified as arguments in the Socket class. The connection is made, with a try and catch loop encompassing the snippet to catch any connection errors.

- 2. The program also envisions the storage of time for prediction, a timestamp is created using the newDate() method, followed by a conversion to String. This is also heretofore considered as a variable sent to the local server and subsequently, the cloud database. There are thus variables in total.

- 3. The variables obtained are then passed into JSONObjects so that they can be sent through the connection using a PrintWriter. The variable parameters, is to the JSONObject and can store the eight variables for the local server.

- 4. The println() and flush() methods are used consecutively to push to the local server. The above steps are all illustrated through the code in Listing 4.30.

### Listing 4.30. Thread to push values to the local server

```
// Another thread to transmit the received data
Runnable runnable = new Runnable() {
  @Override
  public void run() {
    // Trying to send data to the local server
    try {
      // Connection to server
      host = ipaddress.getText().toString();
      Socket socket = new Socket(host, port);

      // Adding a timestamp to the set
      String Time = java.text.DateFormat.getDateFormat().format(new Date());

      // PrintWriter object to write to JSONObject
      PrintWriter out = new PrintWriter(socket.getOutputStream());
      try {
        // Filling the JSONObject with specific values
        parameters.put("Timestamp", Time);
        parameters.put("DownloadSpeed", String.valueOf(downloadSpeed));
        parameters.put("UploadSpeed", String.valueOf(uploadSpeed));
        parameters.put("MobileDownloadSpeed", String.valueOf(mobiledownloadSpeed));
        parameters.put("MobileUploadSpeed", String.valueOf(mobileuploadSpeed));
        parameters.put("PacketsReceived", String.valueOf(RXPackets));
        parameters.put("PacketsSent", String.valueOf(TXPackets));
        parameters.put("WifiStrength", String.valueOf(WIFI_RSSI));
      } catch (JSONException e) {
        Log.w("connection error", e);
      }
      // Sending the values through the socket connection
      out.println(parameters);
      // Flushing the stream after each set
      out.flush();
    } catch (Exception e) {
      Log.w("connection error", e);
    }
  }
};
// Creating the local server/cloud thread
Thread task = new Thread(runnable);
task.start();
```

## 4.3.8.5. Pushing Values Directly to the Cloud

Bounded to the toggle that provides the user with the option of directly sending values to the Cloud database, this piece of code is implemented inside the runnable thread. The toggle, which is a switch component, is first checked for activity.

With the CloudantClient and Database variables for cloud connection declared globally in MainActivity.java, the same principles for the local server are followed, for the ClientBuilder class to make a Cloud connection by specifying the endpoint, username and password of the created database on the IBM dashboard. The block of codes shown in Listing 4.31 is placed in the runnable thread just after the local server implementation, as previously indicated in Listing 4.30.

### Listing 4.31. Pushing data to cloud directly if the switch is active

```
// Pushing data to cloud directly if the switch is active
if (cloudSwitch.isChecked()) {
    // Code for cloud pushing goes here
} else {
    // Code for local server pushing goes here
}
```
