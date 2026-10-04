
692 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nasir Rosun and M. Indoondonun

## 7.1.4.3. The MainFrame () Constructor

When the application is first started, the MainFrame () constructor is called which performs the following tasks:

- 1. Initializes the Swing components using the auto-generated code in the initComponents() method.
2. Creates a Chart Panel and adds it to the current JFrame.
3. Creates a Thread called "serverSocket" that performs the following functions:
   - Starts a ServerSocket that Monitors incoming socket connection to the application for new data.
   - Updates the graph with the incoming data from the edge device
   - Sends the data to the Cloudant database.
   - Sends the data to the local database.
4. Creates a Thread called "querySocket" that performs the following functions:
   - Starts a ServerSocket that Monitors socket connections to respond to queries from mobile and desktop users for analytics or CSV file download.
   - Accepts request from a user in form of JSONObject which contains the request type and other values needed to evaluate the request. Table 7.6 shows the request type and their definitions.

- If the user requested weather data, the getCSVData () method is invoked to fetch the required data.
- If the user requested analytics, the analytics () method is invoked to perform the analytics. The JSONObject returned by the method is then formatted using the formatData () method.
- The formatted String is returned to the client via the socket connection.

- 5. Creates a Thread called "downloadThread" that performs the following functions:
  - Checks the value of db_src to verify the source of the data, either local or from the cloud.
  - Checks whether data for a specific date need to be fetched or only the last N samples are needed.
  - Fetches the required data from the chosen source using the getCSVData () method.
  - Prompts the user to choose a directory to save the CSV file.
  - Converts the fetched data into a CSV file and saves it into the chosen directory.

The codes for the constructor are given in Listing 7.3.

## Table 7.6. Request Type & their Definition

| Request Type | Definition |
|---|---|
| date | The user has requested weather data for a specific date. |
| size | The user has requested the last N rows of weather data. |
| analytics | The user has requested analytics for the next time |

## Listing 7.3. MainFrame Constructor

```java
public MainFrame() {
    //initialize the GUI with the auto-generated code
    initComponents();
    /* Dynamically adding the JFreeChart to the JFrame*/
    /*creates a new chart XYLineChart(String title, String xAxisLabel, String yAxisLabel, XYDataset
    //represents a collection of XYSeries objects that can be used as a dataset
    XYSeriesCollection dataset = new XYSeriesCollection(xy_series);
    chart = ChartFactory.createXYLineChart("Current Weather Readings", Time
(seconds),"Temperature", dataset dataset);
    //A Swing component for a JFreeChart object.
    final ChartPanel chartPanel = new ChartPanel(chart);
    //Sets the preferred size of the component.
    chartPanel.setPreferredSize(new Dimension(575, 400));
    //Enables mouse support for the panel.
    chartPanel.setMouseEnabled(true);
    //Create a new JPanel as the parent for the ChartPanel
    JPanel graphPanel = new JPanel();
    //Sets the bound of the JPanel on the JFrame
    graphPanel.setBounds(225, 40, 563, 550);
    //add the chart panel to the JPanels
    graphPanel.add(chartPanel);
    //add the JPanel to the JFrame
    add(graphPanel);
    //update the JFrame with the added JPanel
    revalidate();
} 

server_Thread = new Thread(() -> {
    try {
        //connect to the local database to obtain data
        myConnector = new SQLConnector();
        //starts a ServerSocket on port 6000
        serverSocket = new ServerSocket(6000);
        //infinite loop to accept socket connections
    } ...
```

```java
while (true) {
//Listens for a connection to be made to this socket and accepts it.
//The method blocks until a connection is made.
try (Socket socket = serverSocket.accept()) {
//creates a BufferedReader Object from the socket InputStream
InputStream inputStream = socket.getInputStream();
InputStreamReader isr = new InputStreamReader(isr);
BufferedReader br = new BufferedReader(isr);
//Read the data from the BufferedReader object.
String data = br.readLine();
//Convert the String to a JSON Object
JSONObject currentReadings = new JSONObject(data);
//Get the value of the variable being displayed.
double a = currentReadings.getDouble(parameter);
//add the value to the XYSeries and increment the counter by 1
xy_series.add(x++, a);
//invoke the sendData method to send data to Cloudant
sendData(currentReadings);
//invoke the insertIntoDatabase method to send data to the local database
myConnection.insertIntoDatabase(currentReadings);
}
} catch (IOException ex) {
//print any exceptions caught
System.out.println(ex);
}
};

querySocket = new Thread(() -> {
try {
//starts a ServerSocket on port 11111
serverSocket = new ServerSocket(11111);
//infinite loop to accept socket connections
System.out.println("Server:" + serverSocket.toString());
while (true) {
//List for a connection to be made to this socket and accepts it.
//The method blocks until a connection is made.
try (Socket socket = serverSocket.accept()) {
System.out.println("accepted:" + socket.toString());
//creates a BufferedReader Object from the socket InputStream
InputStream inputStream = socket.getInputStream();
InputStreamReader isr = new InputStreamReader(isr);
BufferedReader br = new BufferedReader(isr);
//Read the data from the BufferedReader object.
String data = br.readLine();
```

```java
//Convert the request into a JSON Object
JSONObject request = new JSONObject(data);
//Get the request type
String type = request.getString("request");
//Create a JSONObject to store the response
JSONObject response = new JSONObject();
//Gets the type of request from the User request
switch (type) {
    //responds the query for data for a specific date
    case "date":
        //set fetchdata to true
        fetchdata = true;
        //Extract the data for which is requested
        String date = request.getString("date");
        //get the required data and put in JSON response
        response.put("CSV", getCSVData(date));
        break;
    //responds the query for data for sample size
    case "size":
        fetchdata = false;
        //extract the number of observations needed
        int size = request.getInt("size");
        //get the required data and put in JSON response
        response.put("CSV", getCSVData("", size));
        break;
    //responds the query for analytics results
    case "analytics":
        //extract the prediction time from the JSONObject
        int p_time = request.getInt("prediction_time");
        //performs analytics using the window and prediction time
        JSONObject values = analytics(window, p_time);
        response.put("analytics", formatData(values.toString()));
        break;
}
//Create a PrintWriter from the socket OutputStream
PrintWriter out = new PrintWriter(socket.getOutputStream());
//Sends the data to the local server
out.println(response);
//flush the data
out.flush();
```

```java
//close printwriter connection
out.close();
//close socket connection
socket.close();
}
} catch (IOException object) {
//print any exceptions caught
System.out.println(ex);
}

downloadThread = new Thread(() -> {
//fetch the entered date
String date = down_date.getText();
//fetch the entered n
int size = Integer.parseInt(down_n.getText());
//fetches the data from either local database or cloudant
String sb = getCSVData(data, size);
//Parent component of the dialogue
JFrame parentFrame = new JFrame();
//Create a new JFileChooser object
JFileChooser chooser = new JFileChooser();
//Sets the JFileChooser to allow the user to select directories.
fileChooser.setSelectionMode(JFileChooser.DIRECTORIES_ONLY);
//sets the title of the window bar
fileChooser.setDialogTitle("Specify a file to save");
//Pops up a "Save" file chooser dialogue.
int userSelection = chooser.showSaveDialog(parentFrame);
//if approve, ok is chosen.
if (userSelection == JFileChooser.APPROVE_OPTION) {
try {
//get the selected directory from the FileChooser.
File fileToSave = chooser.getSelectedFile();
//get the absolute path of the selected file.
String absolutePath = fileToSave.getAbsolutePath();
//Create a String equivalent of the current timestamp
String timestamp = new SimpleDateFormat("yyyyMMddHHmm").format(new Date());
//Create a new file saved in the selected directory and
//the timestamp as a unique identify appended to the filename
File file = new File(absolutePath + "/WeatherData_" + timestamp + "_dateT.CSV");
//Create a new BufferedWriter for the file object
```
