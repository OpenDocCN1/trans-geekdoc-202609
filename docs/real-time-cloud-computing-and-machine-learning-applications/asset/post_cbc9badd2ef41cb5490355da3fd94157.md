
# 386 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nasir Rosun and M. Indoondonman

```java
// Printing each fetched value onto the JTextarea one after the other
resultArea.append(String.valueOf(timestamp[i]) + ", ");
    + String.valueOf(downspeed[i]) + ", ");
    + String.valueOf(upspeed[i]) + ", ");
    + String.valueOf(pacRec[i]) + ", ");
    + String.valueOf(pacSent[i]) + ",\n");

// Writing the List object to the destination chosen
csvWriter csvWriter = new csvWriter(new FileWriter(filepath));
csvWriter.write(records); // Writing the records
csvWriter.close(); // Closing the stream
csvWriter.flush(); // Flushing the stream

} catch (Exception ex) {
    java.util.logging.Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE, null, ex);
};
// Creating a runnable thread for values from localhost (XAMPP)
Runnable downloadLocalhost = new Runnable() {
    @Override
    public void run() {
        try {
            // Clear the result area upon clicking the button
            resultArea.setText("");
            // Trying to send data to local server, if active
            try {
                // Getting N from GUI
                double length = Double.parseDouble(lastN.getText().toString());
                // Socket connection to server
                host = new InetAddress(getText()).toString();
                socket = new Socket(host, port2);
                // PrintWriter object to write JSONObject parameters to PC
                PrintWriter out = new PrintWriter(socket.getOutputStream());
                try {
                    // Filling the JSONObject to identify localhost download for PC parameters
                    requestCode.put("requestCode", 6);
                    requestCode.put("lengthSamples", length);
                } catch (Exception ex) {
                    System.out.println("Connection error");
```

```
}
  // Sending the values through the socket connection
  out.println(requestCode);
  // Flushing the stream after each set
  out.flush();
  // Receiving the result from the local server
  BufferedReader bufferedReader = new BufferedReader(new
  InputStreamReader(socket.getInputStream()));
  String str;
  StringBuilder sb = new StringBuilder();
  while ((str = bufferedReader.readLine()) != null) {
    sb.append(str + "in");
    resultArea.append(str + "in");
  }
  System.out.println("Message from local server: " + sb.toString());
  try (PrintWriter writer = new PrintWriter(new File(finalpath))) {
    writer.write(sb.toString());
    writer.flush();
    System.out.println("Done writing to csv...");
  } catch (FileNotFoundException e) {
    System.out.println(e.getMessage());
  } catch (Exception e) {
    System.out.println("Connection error");
  } catch (Exception ex) {
    System.out.println("Exception creating CSV");
  }
}
// Starting the above defined threads depending on the radio button selected
on the GUI
if (downloadCloudant.isSelected()) {
  Thread downloadParameters = new Thread(download);
  downloadParameters.start();
}
if (downloadLocal.isSelected()) {
  Thread downloadParameters = new Thread(downloadLocalhost);
  downloadParameters.start();
}
```

# 388 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonon

## 4.4.12.3. Download by Specific Date Button

This performs performs same general functionalities as the previous button, while instead retrieving values by a specific date by the user. The "Cloudant" option is performed by fetching all the parameters from the cloud, as performed by the fetchRegressionValuesPCI method(), followed by comparing the String values contained by the timestamp[] object which bears the respective dates that the values were collected. A for loop encompasses the process and selects values that have the same date as specified by the user on the GUI. As for downloading stored values using the local server, the same principles from the previous section are followed. This process is elaborated through the steps.

- 1. The file name is firstly constructed using a combination of the date that the user enters and the edge device, in this case being "PC." This is followed by creating the String possibilities of the date formats. For e.g., if the entered date is "Dec 18, 2020," the possibilities made for String comparisons with the database, are both "Dec 18, 2020" and "18 Dec 2020." This is because edge devices push the dates to the Cloudant database in slightly different formats for the PC and the Android devices. Thus, the String objects type1 and type2 are the different date formats.

## 4.72. Creating a name for the .csv file for download by date

```java
private void downloadDateButtonActionPerformed(java.awt.event.ActionEvent event) {
    // User first input the date as well as choose the destination

    beforeLoading
    if (path.equals("") || dateFetch.getText().toString().equals("")) {
        System.out.println("Please browse for a destination first and enter
        t number of records.");
    } else {
        // Making an automatic file name based on number of values to be
        printed, as well as the selected device
        filename = dateFetch.getText().toString() + "_" + "PC";
        // Adding the csv extension to the filename
        finalpath = path + "/" + filename + ".csv";
        // Storing the directory path into the finalpath object
        System.out.println("File path: " + finalpath);
        String date = dateFetch.getText();
        String type1 = date;
        String[] splits = date.split(",");
        String[] splits2 = splits[0].split(",");
        String type2 = splits2[1] + " " + splits2[0] + splits[1];
        System.out.println("Date formats are: " + type1 + " and " + type2);
    }
```

# Data Capture Client Architecture for a Cloud-Based Real-Time ... 389

2. The Runnable threads are then implemented just after Listing 4.72.

## Listing 4.73. Threads to download by specific data

```java
// Creating a Runnable thread for values from the servlet/Cloudant database
Runnable download = new Runnable() {
    @Override
    public void run() {
        try {
            // Clear the fetching area upon clicking the button
            resultArea.setText("");
            // Fetch all values from cloud database for PC
            fetchGestionValuesPC();
            // Make the list that contains the String arrays
            List<String> records = new ArrayList<>();
            // Adding header record
            records.add(new String("Timestamp", "Download Speed", "Upload Speed", "Packets Received", "Packets Sent"));
            // Adding headers to GUI
            resultArea.append("Timestamp, " + "Download Speed, " + "Upload " + "Packets Received, " + "Packets Sent " + "\n");
            // For for all parameters
            for (int i = 0; i < numitems; i++) {
                // Comparing the date to individual values in timestamp array
                if (String.valueOf(timestamp[i]).contains(type1) ||
                    String.valueOf(timestamp[i]).contains(type2)) {
                    records.add(new String[
                        String.valueOf(timestamp[i]),
                        String.valueOf(downspeed[i]),
                        String.valueOf(upspeed[i]),
                        String.valueOf(pacRec[i]),
                        String.valueOf(pacSent[i])
                    ]);
                    // Printing each fetched value onto the JTextarea one after the other
                    resultArea.append(String.valueOf(timestamp[i]) + ", ");
                        + String.valueOf(downspeed[i]) + ", ");
                        + String.valueOf(upspeed[i]) + ", ");
                        + String.valueOf(pacRec[i]) + ", ");
                        + String.valueOf(pacSent[i]) + ",\n");
                }
            }
        } catch (Exception ex) {
            java.util.logging.Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE, null, ex);
        }
        // Checking if records exists for the specific date
        if (records.size() == 1) {
            // No records exist
            resultArea.setText("");
            resultArea.append("No records found for this date.");
        } else {
            // Writing the List to the destination if records exist
            CSVWriter csvWriter = new CSVWriter(new FileWriter(finalpath));
            csvWriter.writeAll(records); // Writing the records
            csvWriter.close(); // Closing the stream
            csvWriter.flush(); // Flushing the stream
        }
    }
}
```
