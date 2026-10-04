```
// Variables to hold ptime and window size
int ptime, window;

// Path for csv destination
String path = "";
String filename;
String finalpath;

double numitems = 0.0; // Number of items fetched for csv download function

// Variables for fetching values for csv download
double keys[]; // Key
double downspeed[]; // Wi-Fi download speed
double upspeed[]; // Wi-Fi upload speed
double pacRec[]; // Number of packets received
double pacSent[]; // Number of packets sent
String timestamp[]; // Timestamp for each record
```

# 4.4.6. Creating Live Monitor Layout

With JFreeChart imported, the live monitor can now be integrated into the project. Since it is ideal for the graph to appear upon running the application, the codes for creating the layout of the chart are added into the constructor of the monitor.java class. This is because constructor methods are called when an object of the class is created, i.e., when it runs. This is also the method where GUI objects are practised and automatically inserted onto the JFrame using the initComponents() method. The constructor bears the same name as the class and therefore, the method that creates the graph is added just after the initialisation of the components as shown in Listing 4.53.

# Listing 4.53. Populating the constructor of netmonitor.java

```
public netmonitor() {
    // Initialise all components and set them onto the GUI
    initComponents();
    // Method to programmatically create an area for the graph
    createGraphSpace();
    // Disable the toggle for pushing to cloud temporarily
    cloud.setEnabled(false);
    // Setting the focus on the Start button
    startMonitoring.requestFocus();
}
```