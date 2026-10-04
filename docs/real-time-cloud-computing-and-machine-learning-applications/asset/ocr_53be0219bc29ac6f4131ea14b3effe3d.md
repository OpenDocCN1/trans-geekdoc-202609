# Server and Servlet Architectures for a Cloud-Based Real-Time .

```
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