# Server and Servlet Architectures for a Cloud-Based Real-Time . 497

```
fetchArea.append("Timestamp, " + "Download Speed, " + "Upload
Speed, " + "Packets Received, " + "Packets Sent, " +
"Mobile Download Speed, " + "Mobile Upload Speed, " + "Wifi
Strength, " + "n",");
// For for loop N parameters
while (resultSet != null && resultSet.next()) {
    if(String.valueOf(resultSet.getString(9)).toString().contains(convertedDate.toString())) {
        records.add(new String([
            String.valueOf(resultSet.getString(9) + " " + +
            resultSet.getString(9),
            String.valueOf(resultSet.getString(2)),
            String.valueOf(resultSet.getString(3)),
            String.valueOf(resultSet.getString(4)) + " " + +
            String.valueOf(resultSet.getString(5)) + " " + +
            String.valueOf(resultSet.getString(6)),
            String.valueOf(resultSet.getString(7)),
            String.valueOf(resultSet.getString(8)) + "\n"
        ]));
    }
}
// Updating UI with fetched values
fetchArea.append(String.valueOf(resultSet.getString(9)) + +
" " + String.valueOf(resultSet.getString(2)) + " " + +
String.valueOf(resultSet.getString(3)) + " " + +
String.valueOf(resultSet.getString(4)) + " " + +
String.valueOf(resultSet.getString(5)) + " " + +
String.valueOf(resultSet.getString(6)) + " " + +
String.valueOf(resultSet.getString(7)) + " " + +
String.valueOf(resultSet.getString(8)) + "\n\n}
}
// Writing the List object to the destination chosen
csvWriter = new CSVWriter(new FileWriter(finalpath));
csvWriter.writeAll(records); // Writing the records
csvWriter.close(); // Closing the stream
csvWriter.flush(); // Flushing the stream
}
} catch (Exception ex) {
    java.util.logging.Logger.getLogger(LogServer.class.getName()).log(Level.SEVERE, null,
    ex);
}
};
```