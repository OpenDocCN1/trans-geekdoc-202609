# Server and Servlet Architectures for a Cloud-Based Real-Time .

# Listing 5.25. Calling threads for download by last N samples

```
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

+   5. The file name is first created in Listing 5.26. For fetching data from localhost, due to the slight difference in date formats, a corresponding date format is also created from the user-input date. This is performed using the DateTimeFormatter class and specifying the format of the date being input.

# Listing 5.26. Creating an automatic name for download by specific date

```
private void downloadDateButtonActionPerformed(java.awt.event.ActionEvent event) {
  // User should input the date as well chooses the destination before downloading
  if (path.equals("")) || date.getText().toString().equals("")) {
    System.out.println("Please browse for a destination and enter
t number of records.");
  } else {
    // Making an automatic file name based on the number of values to be
    printed, as well as the selected device
    filename = date.getText().toString() + "_" + "PC";
    // Adding the .csv extension to the filename
    finalpath = path + "\" + filename + ".csv";
    // Storing the full directory path into the pathname object
    System.out.println("File path: " + finalpath);
    String date = date.getText();
    String type1 = 1;
    String[] splits = date.split("_");
    String[] splits2 = splits[0].split("_");
    String type2 = splits2[1] + " " + " + splits2[0] + splits1[1];
```