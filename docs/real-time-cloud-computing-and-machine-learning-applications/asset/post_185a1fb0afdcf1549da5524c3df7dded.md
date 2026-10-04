
```java
// Pushing to cloud directly if the switch is active
if (cloudSwitch.isChecked()) {
    System.out.println("CLOUD SWITCH: ON");
}

// Adding a timestamp to the set of data being pushed
String Time = java.text.DateFormat.dateTimeInstance().format(new Date());

try {
    // Filling the global JSONObject with values to be sent
    parameters.put("Timestamp", Time);
    parameters.put("DownloadSpeed", String.valueOf(downloadSpeed));
    parameters.put("UploadSpeed", String.valueOf(uploadSpeed));
    parameters.put("MobileDownloadSpeed",
        String.valueOf(mobileDownloadSpeed));
    parameters.put("MobileUploadSpeed", String.valueOf(mobileUploadSpeed));
    parameters.put("PacketsReceived", String.valueOf(RXPackets));
    parameters.put("PacketsSent", String.valueOf(TXPackets));
    parameters.put("WifiStrength", String.valueOf(IFI_RSSI));
    parameters.put("Key", idx);
    // Moving to the next one
    idx = idx + 1;
} catch (JSONException e) {
    System.out.println(e.toString());
}

// Making a connection to the Cloud database
try {
    client = ClientBuilder.url(new URL("https://8118bf82-4f01-4173-b30-7fe6fb8e7d7-bluemix.cloud.com/")) // External endpoint
    .username("apikey-f41k2e2574b7134b8c26bdafa1b8dc") // Username
    .password("ee7af593849bde695seefabad72255bfa7d0a98e") // Password
    .build();
} catch (IOException e) {
    System.err.println(e.toString());
}

// Get database instance to send Cloud database:
db = client.database("androidcloudparameters", false);
// Convert JSON to a Map using Gson:
Map map = new Gson().fromJson(parameters.toString(), HashMap.class);
// Save the readings in the database:
db.save(map);
System.out.println("RECORD SENT TO CLOUD");
} else {
    System.out.println("CLOUD SWITCH: OFF");
}
```

# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 297

## 4.3.9. Live Graph Plotting

### 4.3.9.1. Initialising the Chart
With the LineChart object created as a global variable in MainActivity.java, the latter is used to set the colours of the axes and lines for the chart. Several features such as enabling the graph to be zoomed in and as well as spanned upon dragging the screen are also set to true in the onCreate() method. A LineData object is also created to set the colour of the dot added every second, which in this case it is, with the outline of it being specified as black. The purpose of each method called using the LineChart object denoted as chart is included in the comments. The whole block of code, given in Listing 4.32 is included inside the onCreate() method described by its functionalities in Section 4.3.3.

#### Listing 4.32. Initialising chart variables in onCreate()

```java
// Chart settings and options:
chart = findViewById(R.id, chart);
// Enable drag with the finger:
chart.setDragEnabled(true);
// Enable zooming:
chart.setPinchZoom(true);
// Enable zooming in and out by gesture:
chart.setScaleEnabled(true);
// Display grid:
chart.setDrawGridBackground(false);
chart.setHighlightPerTapEnabled(true);
// Enable all gestures and touches on the chart:
chart.setTouchEnabled(true);
// Set a listener to the current activity:
chart.setOnChartValueSelectedListener(this);
// Set background colour to transparent:
chart.setBackgroundColor(Color.TRANSPARENT);

// Create a LineData object to hold the data to be printed:
LineData data = new LineData();
// Setting colour of data to white:
data.setValueTextColor(Color.WHITE);
// Adding new data object to the chart:
chart.setData(data);

// Legend and axis configurations:
Legend D = chart.getLegend();
D.setTextColor(Color.BLUE);
// Setting options for the X-axis
```

```java
XAxis x = chart.getXAxis();
x.setTextColor(Color.BLACK);
x.setDrawGridLines(true);
x.setAvoidFirstClipping(true);
x.setEnabled(true);
```

```java
// Setting options for the Y-axis and enabling the left part
YAxis yL = chart.getXAxisLeft();
yL.setTextColor(Color.BLACK);
yL.setDrawGridLines(true);
// Disabling the axis which would appear on the right
YAxis yR = chart.getXAxisRight();
yR.setEnabled(false);
```

### 4.3.9.2. Creating and Populating the Spinner

1. The Spinner object, used to select the parameter displayed on the live monitor described by the switch statement in Listing 4.29, is paired with an ArrayAdapter object. The ArrayAdapter object is responsible for populating the spinner with a list of choices. These variables have been defined as global variables in MainActivity.java.

2. After allocating the spinner particular spot on the layout and creating its object in the Java class, it needs to be populated with the different statistics that the user will select. This can be created in an XML file which is referred to as a string resource. Usually, in Android development, such files are stored in the "values" folder. A new "Values Resource File" can be found in the Android pane. By right-clicking on the values folder and selecting the option as shown in Figure 4.19.

(img/2b52de0e70e8c2f05a10309c3f8982309_0.png)

Figure 4.19. Creating a value resource. The name of the XML file entered, which in this case is "strings", is created as shown in Figure 20.

3. This is followed by entering the codes for filling the spinner with a list of downs as shown in Listing 4.33. The string array has been given the name "networkparameters" through which it is referenced in the next step.

#### Listing 4.33. Creating resource file for parameter selection

```xml
<resources>
  <string name="app_name">Network-Monitor-App</string>
  <string-array name="networkparameters">
    <item>WiFi Download Speed</item>
    <item>WiFi Upload Speed</item>
    <item>LTE Download Speed</item>
    <item>LTE Upload Speed</item>
    <item>Packets Received</item>
    <item>Packets Sent</item>
    <item>Wifi Signal Strength</item>
  </string-array>
</resources>
```

### 4.3.9.3. Applying the Adapter to the Spinner
Inside onCreate(), the spinner is then initialized by linking its ID to its object using the findViewById() method. The created strings xml file is then allocated to the spinner through the adapter object. This is made possible with the createFromResource() method, by passing arguments firstly, the String array "networkparameters" and secondly, the default spinner layout. The third line of code in this step sets a default white colour to the dropdown when the spinner is clicked on, via the setDropDownResource() method. Finally, the adapter is applied to the spinner using the setAdapter() method as an argument, the ArrayAdapter object.

#### 4.34. Configuring spinner to select one network parameters

```java
// Configure the spinner to select one of the different network parameters
spinner = (Spinner) findViewById(R.id.spinner);
// Using the adapter to select the string array which is "networkparameters" stored
// in strings.xml file
adapter = ArrayAdapter.createFromResource(this, R.array.networkparameters,
android.R.layout.simple_spinner_item);
// Use a default spinner when the spinner is clicked on, plain white
adapter.setDropDownResource(android.R.layout.simple_spinner_dropdown_item);
// Apply the adapter to the spinner
spinner.setAdapter(adapter);
```

### 4.3.9.4. Getting Spinner Value as a String
The functions of the Spinner object are invoked using the setOnItemSelected method, which actively listens for any changes in the parameter that the user wishes to view. Listing 4.35 specifies the interface implementation and changes the netparams object to the String that is currently selected on the spinner.

#### Listing 4.35. Setting listener on spinner

```java
// Specify the interface implementation by calling where the argument is the current activity
spinner.setOnItemSelectedListener(new AdapterView.OnItemSelectedListener()) {
    @Override
    public void onItemSelected(AdapterView<?> parent, View view, int position, long id) {
        // Obtain the name of the parameter
        netparams = parent.getItemAtPosition(position).toString();
        // Clear the graph before monitoring another parameter
        chart.clearValues();
    }

    @Override
    public void onNothingSelected(AdapterView<?> parent) {
    }
};
```
