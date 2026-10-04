
# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 666

```java
String data = br.readLine();
//Convert the String into a JSON Object
JSONObject prediction = new JSONObject(data);
//store the JSON in string format to formatted
String analytics = prediction.toString();
//Display Readings in TextArea
result.setText(formatData(analytics));
```

```java
catch (IOException | NumberFormatException | JSONException e) {
//prints the trace of the error occurred
System.out.println(e);
}
).start();
```

# 6.4.4.9. The requestDataCloud () Method

This method is responsible for downloading either the last N records or data for a specific date from the cloud database. An anonymous Thread is created and the functions carried by the thread are as follows:

- 4. A DataRetriever Object is created from the DataRetriever class.
- 5. The value of the boolean "fetchdate" is checked. If the value is true, it means data for a specific date need to be fetched only the last N records to be fetched. Depending on the value of "fetchdate", the appropriate query is formulated and the data is fetched using the getDatabaseArray () method.
- 6. After getting the data, the user is presented with a JFileChooser to choose the directory in which the CSV file needs to be saved.
- 7. After choosing the directory, the data is converted into a CSV file. (explained in section 6.3.26)
- 8. After creating the file, it is saved to the desired location.

The codes for the function are given in Listing 6.30.

# Listing 6.30. requestDataCloud () method

```java
public void requestDataCloud() {
//Starts anonymous Thread to download data from the cloud
new Thread(() -> {
//Create a DataRetriever Object to fetch data from the cloud
DataRetriever dt = new DataRetriever();
Object[] databaseArray;
```

```java
//check fetchdate to formulate the query
if (fetchdate) {
    //fetch the entered date
    String date = down_date.getText();
    //fetches the last N where N is the value passed in the down-JTextField
    databaseArray = dt.databaseArray(date, 0);
} else {
    //fetch the entered date
    int size = Integer.parseInt(down_n.getText());
    //fetches the last N where N is the value passed in the down-JTextField
    databaseArray = dt.databaseArray("", size);
}

double[] readings = (double[][]) databaseArray[0];
String[] timestamps = (String[]) databaseArray[1];

// Parent component of the dialogue
JFrame parentFrame = new JFrame();
//Create a new JFileChooser object
JFileChooser chooser = new JFileChooser();
//Sets the JFileChooser to allow the user to select directories.
chooser.setSelectionMode(JFileChooser.DIRECTORIES_ONLY);
//sets the title of the window bar
chooser.setTitle("Select a file to save");
//Pops up a "Save File" chooser dialogue.
int userService = chooser.showSaveDialog(parentFrame);
if (userService == JFileChooser.APPROVE_OPTION) {
    try {
        //get the selected directory from the chooser.
        File fileToSave = chooser.getSelectedFile();
        //get the absolute path of the selected file.
        String absolutePath = fileToSave.getAbsolutePath();
        //Create a String equivalent of the current timestamp
        String timestamp = new SimpleDateFormat("yyyyMMddHHmm").format(new Date());
        //Create a new file in the selected directory and
        //the timestamp as a unique identify appended to the filename/
        File file = new File(absolutePath + "/WeatherData_" + timestamp + "_date.CSV");
        //Create a new BufferedWriter from the file object
        try (BufferedWriter br = new BufferedWriter(new FileWriter(file))) {
            //create a new StringBuilder object
            StringBuilder sb = new StringBuilder();
```

662 T. P. Fowdur, L. Babooram, M. N-U-D-ibn Naz Rosun and M. Indoonon

# Data Capture and Client Architecture for a Cloud-Based Real-Time ...

//A string representing the header of the CSV file
String header = "Time,"
+ "Temperature",
+ "Wind Speed",
+ "Wind Direction",
+ "Pressure",
+ "Visibility",
+ "Humidity",
+ "Cloudiness";

//append a new line for each line in the CSV file
sb.append(header).append("\n");
//append each row of the array in a new line
for (int i = 0; i < readings.length; i++) {
//gets the current value of the parameters
String data_time = timestamps[i];
double[] element = readings[i];
sb.append(data_time.replace(",", " ")).append(",");
for (double d : element) {
//separate each value by a comma, ","
sb.append(String.valueOf(d)).append(",");
}
//append new line for each row
sb.append("\n");
}
//write the String to the File
br.write(sb.toString());
//flush any remaining data to the File
br.flush();
//close the BufferedWriter
br.close();
//view the data in the viewarea
data_view.setText(sb.toString());
} catch (IOException ex) {
//log any exception that has occurred.
Logger.getLogger(MonitoringFrame.class.getName()).log(Level.SEVERE, null, ex);
}
}).start();
```

664 T. P. Fowder, L. Babooram, M. N-U-Idbn Nazir Rosun and M. Indoonon

# 6.4.4.10. The requestDataLocal () Method

This method is responsible for downloading the last N records or data for a specific date from the local java server. An anonymous Thread is created to perform the network activities. To connect to the local java server, a socket connection is opened using the IP entered on port 11111.

A JSONObject is created to store the request type and based on the value of "date", either store the date or sample size is stored. The value of the "date" boolean is checked, if it is true, means data for a specific date is being requested. Hence, the date entered is stored in the JSON Object. Otherwise, if the value of the date is false, means data for a sample size is being requested. Therefore, the sample size entered is stored in the JSON Object.

The JSONObject is sent to the server. The server processes the request and returns the CSV file in a JSONObject. The CSV String is extracted from the JSONObject, displayed in the TextView, and saved to the internal storage. After getting the data, the user is presented with a JFileChooser to choose the directory in which the CSV file needs to be saved. After choosing the directory, a file is created in the directory, and the data is saved in the file as a CSV format.

The codes for the function are given in Listing 6.31.

# Listing 6.31. requestDataLocal () Method

```java
public void requestDataLocal() {

    //starts an anonymous thread to request data from the local server
new Thread(() -> {
        try {
            //create a JSON object to store the request parameters
            JSONObject request = new JSONObject();
            //check fetchdate to formulate the query
            if (fetchdate) {
                //fetch the entered date
                String date = down_date.getText();
                //informs the server, we request data for a specific date
                request.put("request", "date");
                //sends the date for which data is needed
                request.put("date", date);
            } else {
                //fetch the entered sample size
                int size = Integer.parseInt(down_n.getText());
                //informs the server, we request a specific number of samples
                request.put("request", "size");
                //sends the number of samples we need to download
                request.put("size", size);
            }
        }
}
```

# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 665

```java
// Opens a socket connection to the local server
socket socket = new Socket(address_f.getText(), 11111);
// Create a PrintWriter from the socket OutputStream
PrintWriter out = new PrintWriter(socket.getOutputStream());
// Sends the request to the local server
out.println(request);
out.flush();
out.flush();

// creates a BufferedReader Object from the socket InputStream
InputStream is = socket.getInputStream();
// Encapsulates it in an InputStreamReader
InputStreamReader isr = new InputStreamReader(is);
// Encapsulates it in a BufferedReader
BufferedReader br = new BufferedReader(isr);
// Read the data from the BufferedReader object.
String data = br.readLine();
// Convert the String into a JSON Object
JSONObject CSV_data = new JSONObject(data);
// store the CSV data obtained from the server
String CSV = CSV_data.getString("CSV");

//Parent component of the dialogue
JFrame parentFrame = new JFrame();
// Create a new JFileChooser
JFileChooser fileChooser = new JFileChooser();
// Sets the JFileChooser to allow the user to select directories.
fileChooser.setSelectionMode(JFileChooser.DIRECTORIES_ONLY);
fileChooser.setTitle("File to save");
// Pops up a "Save" file chooser dialogue.
int selection = fileChooser.showDialog(parentFrame);
// if approve (yes, ok) is chosen.
if (selection == JFileChooser.APPROVE_OPTION) {
// get the selected directory from the JFileChooser.
fileToSave = fileChooser.getSelectedFile();
// get the absolute path of the selected file.
String absolutePath = fileToSave.getAbsolutePath();
```
