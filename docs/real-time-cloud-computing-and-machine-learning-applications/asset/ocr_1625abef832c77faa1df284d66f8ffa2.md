# Server and Servlet Architectures for a Cloud-Based Real-Time . 433

```
System.out.println("Pushing Android record to localhost");
}
count = count + 1;
}
catch (IOException ex) {
System.out.println(ex);
}
}
```

# 5.1.8.3. Server Thread for PC Values

The same process is repeated for accommodating incoming values for PC. The switch-case scenario is however modified such that an “Unavailable for PC” message is displayed as the title of the graph whenever a parameter is not monitored on PC is chosen with the parameterSelection JComboBox. The username, password and database name of the Cloudant database are changed accordingly. The full codes are shown in Listing 5.7 and are placed in the launchMonitorActionPerformed method.

# Listing 5.7. Thread to incoming values from PC

```
localServerPC = new Runnable() {
@Override
public void run() {
// Defining the variables to the incoming values
// These values are changed every second
double totalupload = 0;
double totalownload = 0;
double packetsreceived = 0;
double packetsent = 0;
// Count to add values to the graph with respect to time
count = 0;

String time; // Timestamp for the database
final int port = 2001; // Port on which server is created
System.out.println("Creating server for PC on port: " + port);
try {
  ServerSocket ss = new ServerSocket(port);
  System.out.println("Waiting for connection...");
  while (true) {
    Socket socket = ss.accept();
    //Accepting connection from client device
    BufferedReader br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
    String str = br.readLine());n
```