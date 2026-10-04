# Data Capture]] Client Architecture for a Cloud-Based Real-Time ... 389

2. The Runnable threads are then implemented just after Listing 4.72.

# Listing 4.73. Threads to download by specific data

```
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
            records.add(new String("Timestamp", "Download Speed", "Upload
Speed", "Packets Received", "Packets Sent"));
            // Adding headers to GUI
            resultArea.append("Timestamp, " + "Download Speed, " + "Upload
" " + "Packets Received, " + "Packets Sent " + "\n");
            // For for all parameters
            for (int i = 0; i < numitems; i++) {
                // Comparing the date to individual values in timestamp
                array
                if (String.valueOf(timestamp[i]).contains(type1) ||
                    String.valueOf(timestamp[i]).contains(type2)) {
                    records.add(new String[
                        String.valueOf(timestamp[i]),
                        String.valueOf(downspeed[i]),
                        String.valueOf(upspeed[i]),
                        String.valueOf(pacRec[i]),
                        String.valueOf(pacSent[i])
                    ]);
                    // Printing each fetched value one after the other
                    resultArea.append(String.valueOf(timestamp[i]) + " " + ""
                        + String.valueOf(downspeed[i]) + " " + ""
                        + String.valueOf(upspeed[i]) + " " + ""
                        + String.valueOf(pacRec[i]) + " " + ""
                        + String.valueOf(pacSent[i]) + "\n");
                }
            }
        }
    // Checking if records exists for the specific date
```