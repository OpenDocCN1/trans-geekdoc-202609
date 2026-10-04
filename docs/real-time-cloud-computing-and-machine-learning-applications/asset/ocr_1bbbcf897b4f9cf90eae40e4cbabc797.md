```
public static double RXPackets = 0; // Number of packets received in 1 second
public static double TXPackets = 0; // Number of packets sent in 1 second
public static double downloadSpeed = 0; // Download Speed in kbps
public static double uploadSpeed = 0; // Upload Speed in kbps
public static double mobiledownloadSpeed = 0; // Mobile Download Speed in kbps
public static double mobileuploadSpeed = 0; // Mobile Upload Speed in kbps
long WIFI_RSSI; // Wi-Fi signal strength in dB
```

```
// Default String that changes upon spinner
String netparams = "Total Download Speed";
```

```
// Variables for connection to the local server
String host = "";
final int port = 2001;
```

```
// Variables to find the last index in the cloud database
int idx = 0;
double numberOfItems = 0.0;
```

```
// Declaring variables for connection to the cloud database
CloudantClient client = null;
Database db;
```

```
// Declaring the bearing parameters for the local server
final JSONObject parameters = new JSONObject();
```

```
// Creating a Handler object
private Handler mHandler = new Handler();
```

```
// Formatting the value to be outputted to 2 decimal places
DecimalFormat precision = new DecimalFormat("0.00");
```

# 4.3.5. Retrieving the Last Index from the Cloud

After pushing data to the cloud directly using the switch, data must be sorted one after the other with respect to time. This is why a "Key" needs to be added to the data being registered, i.e., in a JSONObject, before it is pushed to the cloud. This is however depicted later in the documentation, in Section 4.5.2. Since the Cloudant database might already contain values before the data is pushed, the "Key" value should be retrieved prior to sending the next value to the database. The successive parameters registered be indexed with the successive value of the "Key." To do so, a thread is created in MainActivity.java with the following functions:

+   - Make a connection to the Cloudant database.
- Use a String object to specify a query to the database in MongoDB.
- Retrieve the "Key" values in descending order so that the first result bears the last index which is also the number of items in the database.