# Data Capture and Architecture for a Cloud-Based Real-Time ... 253

![](bbox=[0.139, 0.096, 0.861, 0.375])

Figure 4.2. Overview of program structure for Android Application.

The Android Application, Monitor_App use of three Java classes, named MainActivity.java, Prediction.java and Download.java whose methods are in Table 4.1.

# Table 4.1. Complete program structure for Monitor_App

| MainActivity.java | Prediction.java | Download.java |
| :--- | :--- | :--- |
| Uses activity.main.xml as its layout and performs monitoring and data pushing processes. | Uses prediction.xml as its layout and performs the analysis function, i.e., making connections to either the hosted server or the local server. | Uses csvdownload.xml as its layout and downloads parameters based on user's choice of the cloud or the local server, as displays them on an area. |
| onCreate | | Sets the components into the display, uses the initial parameters and starts the monitoring process through the clicking of on-buttons. Contains button calls to stop the process as well as navigate to prediction. |
| getNumberOfItems(Thread) | Retrieves the last index of records stored on the Cloud database before pushing them they can be entered in an orderly fashion. Uses the CloudClient and Database objects. | |
| getTotalSpeeds() | | Gets the total download and upload speeds with the TrafficStats class, thus filling the parameters. |
| getMobileSpeeds() | | Gets the mobile and upload speeds, i.e., for LTE only using the TrafficStats class. |
| getPackets() | | Gets the number of received and sent packets per second. |
| getWiFiStrength() | | Gets the Wi-Fi strength in db using the WiFiManager. |
| mRunnable(Thread) | The main thread calls the retrieve method and updates the line graph as well as each entry. Also pushes values to the local server and the Cloudababase. |
| addEntry() | | Adds a value to the live monitor using a LineData object. |
| setData() | | Sets the printing options and colours of the graph with a LineDataSet object. |
| onItemSelected() | | Displays a toast upon selecting a specific value on the graph. |