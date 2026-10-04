# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 366

XYSeries series; // Sequence of data items in the form (x,y)
JFreeChart chart; // 2D Chart object

// Initialisations for bytes/speeds:
long previousDownload; // Initial number of bytes received
long previousUpload; // Initial number of bytes sent
long currentDownload; // Current number of bytes received
long currentUpload; // Current number of bytes sent
long downloadSpeed; // Download Speed in kbps
long uploadSpeed; // Upload Speed in kbps
long dchange; // Change in number of bytes received in 1 second
long unchanged; // Change in number of bytes sent in 1 second

// Initialisations for packets:
long previousReceived; // Initial number of packets received
long previousSent; // Initial number of packets sent
long currentReceived; // Current number of packets received
long currentSent; // Current number of packets sent
long packetsReceived; // Number of packets received per second
long packetsSent; // Number of packets sent per second
long rchange; // Change in number of packets received in 1 second
long change; // Change in number of packets sent in 1 second

// Count to set first values as 0 since they cannot be obtained at t=0
int count = 0;

// Variables to find the last index in the cloud database
int idx = 0;
double numberOfItems = 0.0;

// Declaring variables for connection to cloud database
CloudantClient client = null;
Database db;

// Declaring the object bearing the parameters for the local server
final JSONObject parameters = new JSONObject();

// Declaring the object bearing the request code for the local server
final JSONObject requestCode = new JSONObject();

// Variables for connection to local server
String host = "";
final int port = 2001; // Port for monitoring
final int port2 = 2002; // Port for download/analytics