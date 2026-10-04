# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 379

# 4.4.11.2. Classify Button

The same processes elaborated in Section 4.3.10.2 are repeated for the classification button, except that it makes of current network parameters in its query to the servlet. The request codes for the local server are again as per Table 4.7.

Listing 46.7. Populating the classify button

```
// Classify button
private void classifyButtonActionPerformed(java.awt.event.ActionEvent evt) {
    public void Thread run() {
        try {
            // Creates the corresponding URL to the query servlet
            // Adding dummy values for prediction time and windowcloud.
            URL url = new URL("http://networkcloud-eu-gb.bymemix/net.mil?")
                + "&downloadSpeed=" + String.valueOf(downloadSpeed)
                + "&uploadSpeed=" + String.valueOf(uploadSpeed)
                + "&packetsReceived=" + +
                String.valueOf(packetsReceived)
                + "&packetsSent=" + String.valueOf(packetsSent)
                + "&predictionTime=" = 10
                + "&windowSize=" = 20
                + "&device=" = 1
                + "&action=" = 1
                + "&source=" = 1);
            result.setText("Performing classification analytics
on: ");
            result.append("\nDownload Speed: " + downloadSpeed);
            result.append("\nUpload Speed: " + uploadSpeed);
            result.append("\nnPackets Received: " + +
            packetsReceived);
            result.append("\nnPackets Sent: " + packetsSent);
            result.append("\nnPlease wait...");
        } 

        // Open a URLConnection to receive the data set by servlet
        URLConnection connection = url.openConnection();
        // Listening for data
        try (BufferedReader in = new BufferedReader(new
            InputStreamReader(connection.getInputStream()))) { 
            // Preparing incoming data into readable format
            String inputLine;
            // Object to hold the result
            StringBuilder result = new StringBuilder();
            // While data is read
            while ((inputLine = in.readLine()) != null) {
                // Append character to the String
```