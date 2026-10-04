# 390 T. P. Fowdur, L. Babooram, M. N-D-Ibn Naz Rosun and M. Indoondonon

```
if (records.size() == 1) {
    // No records exist
    resultArea.setText("");
    resultArea.append("No records found for this date.");\n} else {
    // Writing the List to the destination chosen if records exist
    CSVWriter csvWriter = new CSVWriter(new FileWriter(finalpath));
    csvWriter.writeAll(records); // Writing the records
    csvWriter.close(); // Closing the stream
    csvWriter.flush(); // Flushing the stream
}
 catch (Exception e) {
    java.util.logging.Logger.getLogger(netmonitor.class.getName()).log(Level.SEVERE, null);
}
// Creating a Runnable thread for values from localhost (XAMPP)
Runnable downloadLocalhost = new Runnable() {
    @Override
    public void run() {
        try {
            // Clearing the fetching area upon clicking the button
            resultArea.setText("");
            // Trying to send data to local server, if active
            try {
                // Fetch the data from the GUI:
                String date = dateFetch.getText().toString();
                Socket host = (ipAddress.getHost()).toString();
                Socket socket = new Socket(host,port2);
                // PrintObject to write JSONObject parameters to PC
                PrintWriter out = new PrintWriter(socket.getOutputStream());
                try {
                    // Filling the JSONObject to identify localhost download for PC parameters
                    requestCode.put("requestCode", 7);
                    requestCode.put("date", date);
                } catch (JSONException) {
                    System.out.println("Connection error");
                }
                // Sending the values through the socket connection
                out.println(requestCode);
                // Flushing the stream after each set
                out.flush();
            }
    }
}
```