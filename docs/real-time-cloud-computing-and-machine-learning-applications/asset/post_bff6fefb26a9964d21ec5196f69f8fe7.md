
# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 381

```java
PrintWriter(socket.getOutputStream());
try {
    // Filling the JSONObject to indicate localhost
    classification for PC parameters
    requestCode.put("requestCode", 9);
    requestCode.put("dspeed", downloadSpeed);
    requestCode.put("uspeed", uploadSpeed);
    requestCode.put("prec", packetsReceived);
    requestCode.put("psent", packetsSent);
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
System.out.println("Message from local server: " +
sb.toString());
} catch (Exception e) {
    System.out.println("Connection error");
} catch (Exception ex) {
    System.out.println("Exception");
}

// Starting the above defined thread depending on the radio button
selected on the GUI
if (analyticsCloudant.isSelected()) {
    classifyThread.start();
}
if (analyticsLocal.isSelected()) {
    classifyThreadLocal.start();
}
```

382 T. P. Fowdur, L. Babooram, M. U. Nazir Rosun and M.

## 4.4.12. Downloading to .csv

The download operation can be broken down into use of three functionalities as follows:

- **Browse**: Opens the aforementioned dataframe from the JFrame class, which contains a FileChooser, set to take a specific directory input. After obtaining the selection, the path to store the .csv file is obtained in a String object which is displayed on the GUI.
- **Download N samples**: Retrieves the parameters from the cloud and uses OpenCSV library to output specially formatted characters to a .csv file. The retrieval of parameters is performed using `fetchValuesPC()` method detailed in Section 4.4.12.3 to retrieve the last N number of parameters to be saved locally such as databases accessed through the local server.
- **Download by specific date**: For the "Cloud" option, it takes an input with a particular date entered by the user and fetches the parameters using `fetchValuesPC()` method itself. It compares the user-entered date with records bearing the same date and outputs them to both a .csv file and the result component.

### 4.4.12.1. Browse Button

As mentioned before, "Browse" opens the dataframe object. Listing 4.68. Populating the browse button

```java
private void browseButton(java.awt.event.ActionEvent evt) {
    // Open dataframe when button is pressed
    dataframe.setVisible(true);
    // Manually set size of explorer
    dataframe.setSize(700, 400);
}
```

2. To get the path of the directory selected by the user, `actionPerformed` is called as shown in Figure 4.68. Binding the `actionPerformed(event)` event to the file chooser.

![](img/2b52de0e707e8c2f05a10309c3f8982394_0.png)
Figure 4.68. Example of making a dataframe.

1. Next, the path is obtained using the `getSelectedFile()` method and printed on the GUI through Listing 4.69.

### Listing 4.69. Getting the path using the dataframe

```java
private void dataframeActionPerformed(java.awt.event.ActionEvent evt) {
    // If the selection is made
    if (evt.getActionCommand().equals(FileChooser.APPROVE_SELECTION)) {
        // Getting the path of the directory
        File f = dataframe.getSelectedFile();
        path = f.toString();
        System.out.println("The current set path is:");
        System.out.println(path);
        // Closing the explorer
        dataframe.setVisible(false);
        // Setting the path obtained in Path JTextField
        destination.setText(path);
    }
    // If the selection is cancelled, the explorer is closed
    if (evt.getActionCommand().equals(FileChooser.CANCEL_SELECTION)) {
        dataframe.setVisible(false);
    }
}
```

### 4.4.12.2. Download Last N Button

1. With the directory obtained in the path variable, which is a String object, the latter is used to automatically create a proper name for the .csv file. This is the first task performed when clicking the "Download" button.

### Listing 4.70. Creating a name for the .csv file for samples download

```java
private void downloadButtonActionPerformed(java.awt.ActionEvent event) {
    // User should input the number of records as well as choose the
    // destination before downloading
    if (path.equals("") || lastN.getText().toString().equals("")) {
        System.out.println("Please browse for a destination first and enter the number of records.");
    } else {
        // Making an automatic file name based on number of values to be
        // printed, as well as the selected device
        filename = "Last_" + lastN.getText().toString() + "_" + "PC";
        // Adding the .csv extension to the filename
        finalpath = path + "\\" + filename + ".csv";
        // Storing the full directory path into the finalpath
        System.out.println("File path: " + finalpath);
    }
}
```

E.g., the name depicted in Figure 4.69 is constructed by the snippet Listing 4.70 if 20 items are chosen for download. The first path refers to the directory selection made by the user and the file path pertains to its String addition with the built file name.

```
run:
The current set path is:
C:\Users\...Last_20_PC.csv
```

Figure 4.69. Example of making a filename for the .csv file.

The next step is to fetch the values from the cloud and use OpenCSV library to prepare the data to be saved in a .csv file. This is performed when the "Cloud" button is clicked using the Runnable thread.

- **Fetch N from the GUI**
- Fetch all values from cloud database for PC
- Create a list that contains the String arrays
- Add a header record
- Use the List object to store the variables
- for loop for last N parameters
- converting variables of double to String

385 T. P. Fowdur, L. Babooram, M. U. Nazir Rosun and M.

The codes for steps 2 and 3 are shown in Listing 4.71. Likewise, for the “Local” option, the “downloadLocal” Runnable thread is used. The Runnable threads are started depending on the selection of the radio buttons on the GUI.

### Listing 4.71. Threads to download last N of samples

```java
Runnable download = new Runnable() {
    @Override
    public void run() {
        // Clear the fetching area upon clicking the button
        resultArea.setText("");
        // Getting N from GUI
        double length = Double.parseDouble(lastN.getText().toString());
        // Fetch all values from cloud database for PC
        fetchValuesPC();
        // Make the list that contains the String arrays
        List<String> records = new ArrayList<>();
        // Adding header record
        records.add(new String[]{"Timestamp", "Download Speed", "Upload Speed", "Packets Received", "Packets Sent"});
        // Adding headers to area on GUI
        resultArea.append("Timestamp,\ " + "Download Speed,\ " + "Upload Speed,\ " + "Packets Received,\ " + "Packets Sent " + "\n");
        // Calculating the initial value so that only the last N parameters are stored
        int initial = (int) (numitems - length);
        // For loop for last N parameters
        for (int i = initial; i < numitems; i++) {
            // Adding the values to the records object for csv creation
            records.add(new String[]{
                String.valueOf(timestamp[i]),
                String.valueOf(downspeed[i]),
                String.valueOf(upspeed[i]),
                String.valueOf(pacRec[i]),
                String.valueOf(pacSent[i])
            });
        }
    }
};
```
