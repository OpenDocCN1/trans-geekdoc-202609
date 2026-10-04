
# Server and Servlet Architectures for a Cloud-Based Real-Time .

```java
resultSet.next(); // Moving to next record
// Writing the List object to the destination chosen
CSVWriter csvWriter = new FileWriter(finalPath);
csvWriter.writeAll(records); // Writing the records
csvWriter.close(); // Closing the stream
csvWriter.flush(); // Flushing the stream
}
// If the selected device is the Android device
if (downloadDevice.getSelectedItem().toString().equals("Android")) {
    // Getting N Gui
    double length = Double.parseDouble(lastN.getText().toString());
    // Fetch all values from localhost database for Android
    ResultSet resultSet = null;
    try {
        Class.forName("com.mysql.jdbc.Driver");
        Connection m_Connection = (Connection) DriverManager.getConnection("jdbc:mysql://localhost:3306/network", "root", "");
        Statement m_Statement = new Statement(m_Connection);
        m_Connection.createStatement();
        String query = "SELECT * FROM androidregression";
        resultSet = m_Statement.executeQuery(query);
    } catch (ClassNotFoundException | SQLException ex) {
        Logger.getLogger(LoCServer.class).log(Level.SEVERE, null, ex);
    }
    // Make the list that contains the Array strings
List<String> records = new ArrayList<>();
// Adding header record
records.add(new String[]{
    "Timestamp",
    "Download Speed",
    "Upload Speed",
    "Packets Received",
    "Packets Sent",
    "MobileDownloadSpeed",
    "MobileUloadSpeed"
});
fetchArea.add("Timestamp, " + "Download Speed, " + "Upload Speed, " + "Packets Received, " + "Packets Sent, " + "Mobile Download Speed, " + "Mobile Upload Speed, " + "Wifi Strength, " + "in,");
// Calculating the initial value so that only the last N parameters are stored
int initial = (int) (numitems - length);
resultSet.absolute(initial); // Move cursor to start of last N
```

```java
// For loop list N parameters
for (int i = initial; i < resultSet.getFetchSize(); i++) {
    // Adding values to records object for saving to csv
    records.add(new String[]{
        String.valueOf(resultSet.getString(9)),
        String.valueOf(resultSet.getString(2)),
        String.valueOf(resultSet.getString(3)),
        String.valueOf(resultSet.getString(4)),
        String.valueOf(resultSet.getString(5)),
        String.valueOf(resultSet.getString(6)),
        String.valueOf(resultSet.getString(7)),
        String.valueOf(resultSet.getString(8))
    });
    // Updating UI with fetched values
    fetchArea.append(String.valueOf(resultSet.getString(9)) +
        "" + " + String.valueOf(resultSet.getString(2)) + "" + " + +
        String.valueOf(resultSet.getString(3)) + "" + " + +
        String.valueOf(resultSet.getString(4)) + "" + " + +
        String.valueOf(resultSet.getString(5)) + "" + " + +
        String.valueOf(resultSet.getString(6)) + "" + " + +
        String.valueOf(resultSet.getString(7)) + "" + " + +
        String.valueOf(resultSet.getString(8)) + ""\n");
    resultSet.next(); // Moving to next record
}
// Writing the List to the destination chosen
CSVWriter csvWriter = new CSVWriter(new FileWriter(filepath));
csvWriter.writeAll(records); // Writing the records
csvWriter.close(); // Closing the stream
csvWriter.flush(); // Flushing the stream
}
} catch (Exception ex) {
    java.util.logging.Logger.getLogger(LogServer.class.getName()).log(
        Level.SEVERE, null, ex);
}
}
```

Next, the threads defined by Listings 5.23 and 5.24 are called depending on the selection of the “localhostDownload” toggle, which differentiates between downloading from Cloudant database or localhost. Listing 5.25 is also placed inside the downloadButtonActionPerformed(method).

# Server and Servlet Architectures for a Cloud-Based Real-Time .

# Listing 5.25. Calling threads for download by last N samples

```java
if (localhostDownload.isSelected()) {
  // Starting the thread for values from localhost
  Thread downloadParameters = new Thread(downloadLocal);
  downloadParameters.start();
} else {
  // Starting the thread for values from Cloudant database
  Thread downloadParameters = new Thread(downloadLocal);
  downloadParameters.start();
}
```

# 5.1.13.2. Download by Specific Date Button

The implementation for downloading .csv files from the date entered by the user follows the same principles depicted in Section 4.4.12.3 for the Desktop Application.

- 5. The file name is first created in Listing 5.26. For fetching data from localhost, due to the slight difference in date formats, a corresponding date format is also created from the user-input date. This is performed using the DateTimeFormatter class and specifying the format of the date being input.

# Listing 5.26. Creating an automatic name for download by specific date

```java
private void downloadDateButtonActionPerformed(java.awt.event.ActionEvent event) {
  // User should input the date as well chooses the destination before downloading
  if (path.equals("") || date.toString().equals("")) {
    System.out.println("Please browse for a destination and enter a date.");
  } else {
    // Making an automatic name based on the number of values
    filename = date.toString() + "_" + count;
    // Adding the .csv extension to filename
    finalpath = path + filename + ".csv";
    // Printing the full path
    System.out.println("File path: " + finalpath);
    String[] splits = date.toString().split("_");
    String type1 = splits[0];
    String type2 = splits[1];
    // Conversion to yyyy-mm-dd
    DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd", Locale.ENGLISH);
    LocalDate convertedDate = LocalDate.parse(date, formatter);
    // Variable representing the content
    System.out.println("Date: " + convertedDate);
```

# Listing 5.27. Thread to download by specific date

```java
Runnable download = new Runnable() {
  @Override
public void run() {
    // Clear the area upon clicking the button
    fetchArea.setText("");
    // If the selected device is PC
    if (downloadDevice.getSelectedItem().toString().equals("PC")) {
      fetchRegressionValues();
      // Make the list to Arrays
      List<String[]> records = new ArrayList<>();
      // Adding headers
      records.add(new String[]{"Timestamp", "Download Speed", "Upload Speed", "Packets Received", "Packets Sent"});
      // Appending to area
      fetchArea.append("Timestamp, " + "Download Speed, " + "Upload Speed, " + "Packets Received, " + "Packets Sent" + "\n");
      // For loop all parameters
      for (int i = 0; i < numitems; i++) {
        // Comparing the data to individual values in timestamp
        if (String.valueOf(timestamp[i]).contains(type1) ||
            String.valueOf(timestamp[i]).contains(type2)) {
          records.add(new String[] {
            String.valueOf(timestamp[i]),
            String.valueOf(downspeed[i]),
            String.valueOf(upspeed[i]),
            String.valueOf(pacRec[i]),
            String.valueOf(pacSent[i])
          });
        }
      }
      # Printing each value onto the JTextArea
      resultArea.append(String.valueOf(timestamp[i]) + ", \n" +
        String.valueOf(downspeed[i]) + ", \n" +
        String.valueOf(upspeed[i]) + ", \n" +
        String.valueOf(pacRec[i]) + ", \n" +
        String.valueOf(pacSent[i]) + "\n");
    }
    // Checking if records exist for the specific date
    if (records.size() <= 1) {
      // No records exist
      resultArea.setText("No records found for this date.");
      resultArea.append("No records found for this date.");
    } else {
      // Writing the List to the destination records exist
      CSVWriter csvWriter = new CSVWriter(new FileWriter(filepath));
      csvWriter.writeAll(records); // Writing the records
      csvWriter.close(); // Closing the stream
      csvWriter.flush(); // Flushing the stream
    }
  }
};
```
