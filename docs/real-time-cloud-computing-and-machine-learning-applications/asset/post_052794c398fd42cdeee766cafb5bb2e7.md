
# Server and Servlet Architectures for a Cloud-Based Real-Time .

## 5.3.5.2. livegraphAndroid.java servlet

The same principles from the previous section are repeated for the Android live graph through the following steps, while now using the Android databases and filling up seven parameters:

- 1. The global variables are shown in Listing 5.46.

Listing 5.46. Global variables for livegraphAndroid.java

```java
public class livegraphAndroid extends HttpServlet {
    private static final long serialVersionUID = 1L;

    // Object to send the output onto the browser
    private PrintWriter out;

    // Declaring variables for connection to cloud database
    CloudClient client = null;
    Database db;

    double numItems = 0.0; // For predict button and download functions

    // Variables for Regression analytics
    double keys; // Key
    double downspeed; // Wi-Fi download speed
    double upspeed; // Wi-Fi upload speed
    double pacRec; // Number of packets received
    double pacSent; // Number of packets sent
    String timestamp; // Timestamp for each record
    double mobSpeed; // LTE download speed
    double mobUspeed; // LTE upload speed
    double wstrength; // Wi-Fi strength for mobile
```

- 2. The fetchInputValueAndroid() adapted from the fetchRegressionValues() method is shown in Listing 5.47.

Listing 5.47. fetchInputValueAndroid() method

```java
public void fetchInputValueAndroid() {
    // Checking if the localhost is enabled
    if (dataSource.equals("localhost")) {
        // Fetch all values from localhost database for Android
        // Create resultSet object to hold retrieved values
        ResultSet resultSet = null;
        try {
            Class.forName("com.mysql.jdbc.Driver");
            // Creating a connection to the localhost by specifying the database 
            // name, username and password
            Connection m_connection = (Connection) DriverManager
            .getConnection("jdbc:mysql://localhost:3306/root", "");

            // Using the Statement class to make an object for querying
            Statement m = m_connection.createStatement();

            // Creating query object of type String
            String query = "SELECT * FROM androidregression";

            // Executing the query and obtaining the results
            ResultSet resultSet = m.executeQuery(query);
        } catch (ClassNotFoundException | SQLException) {
            System.out.println("SQL EXCEPTION 1");
        }

        // Fetching the set of values by setting the cursor to the last row
        try {
            resultSet.last(); // Moves cursor to the last row
            // Filling arrays with respective values
            keys = Double.parseDouble(resultSet.getString(1));
            downspeed = Double.parseDouble(resultSet.getString(2));
            upspeed = Double.parseDouble(resultSet.getString(3));
            mobSpeed = Double.parseDouble(resultSet.getString(4));
            mobUSpeed = Double.parseDouble(resultSet.getString(5));
            pacRec = Double.parseDouble(resultSet.getString(6));
            pacSent = Double.parseDouble(resultSet.getString(7));
            wstrength = Double.parseDouble(resultSet.getString(8));
            timestamp = resultSet.getString(9);
        } catch (SQLException ex) {
            System.out.println("SQL EXCEPTION 2");
        }

        // Making connection to cloud
        try {
            client = ClientBuilder.newURL("https://8118bf82-4f01-4173-be30-7fe6ff8bee7d-bluemix.cloud.com/")
                .username("apikey-")
                .password("ee77af59384bde695eafad7e2255bfa7d0a98e").build();
            System.out.println("Successful connection made to cloud...");
        } catch (IOException e) {
            System.out.println("Error accessing cloud: " + e);
        }

        // Getting number of items in the database so that arrays can be initialized
        try {
            Database db = client.database("androidcloudparameters", false);
            System.out.println("Trying to read all records from database...");
            String query = "{\"selector\":{\"Key\":0},\"fields\":{\"Key\":1},\"sort\":{\"Key\":\"desc\"}}";
            QueryResultSet-LinkedTreeMap queryResult = db.query(query, (Class)LinkedTreeMap.class);
            LinkedTreeMap result = queryResult.getDocs();
            if (result.size() > 0) {
                numItems = result.get(0).get("Key");
            }
        } catch (Exception e) {
            System.out.println("Problem fetching number of items: " + e.toString());
        }

        // Retrieving data from database
        try {
            Database dbRetrive = client.database("androidcloudparameters", false);
            String query = "{\"selector\":{\"Key\":{\"$gt\":0}},\"fields\":{\"Key\",\"DownloadSpeed\",\"UploadSpeed\",\"MobileDownloadSpeed\",\"MobileUploadSpeed\",\"PacketsReceived\",\"PacketsSent\",\"WiFiStrength\",\"Timestamp\"},\"sort\":{\"Key\":{\"asc\":1}},{\"Key\":1}}}";
            QueryResultSet-LinkedTreeMap queryParameters = dbRetrive.query(query, (Class)LinkedTreeMap.class);
            LinkedTreeMap parameters = queryParameters.getDocs();
            for (int i = 0; i < numItems; i++) {
                keys = (Double)parameters.get(i).get("Key");
                downspeed = (Double.parseDouble((String)parameters.get(i).get("DownloadSpeed")));
                upspeed = (Double.parseDouble((String)parameters.get(i).get("UploadSpeed")));
                pacRec = (Double.parseDouble((String)parameters.get(i).get("PacketsReceived")));
                pacSent = (Double.parseDouble((String)parameters.get(i).get("PacketsSent")));
                mobSpeed = (Double.parseDouble((String)parameters.get(i).get("MobileDownloadSpeed")));
                mobUspeed = (Double.parseDouble((String)parameters.get(i).get("MobileUploadSpeed")));
                wstrength = (Double.parseDouble((String)parameters.get(i).get("WifiStrength")));
                timestamp = (String) parameters.get(i).get("Timestamp");
            }
        } catch (Exception e) {
            System.out.println("Problem filling arrays with fetched items: ");
        }
        System.out.println("Arrays have been filled...");
    }
}
```

- 3. The doGet() method is shown in Listing 5.48.

# Listing 5.48. doGet() method for livegraphAndroid.java

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response)
    throws ServletException, IOException {
    // Allow cross-domain requests (Allow CORS policy)
    response.setHeader("Access-Control-Allow-Origin", "*");

    // Indicating the data source selected by the user from the HTTP request
    Double source = Double.parseDouble(request.getParameter("source"));
    if (source == 1) {
        dataSource = "cloudant";
    }
    if (source == 2) {
        dataSource = "localhost";
    }

    // Fetching the last set of values from the Android database
    fetchlastAndroid();

    // Write back to client in JSON format after obtaining results
    JSONObject jsonn = new JSONObject();
    jsonn.put("downloadSpeed", downspeed);
    jsonn.put("uploadSpeed", upspeed);
    jsonn.put("packetsReceived", pacRec);
    jsonn.put("packetsSent", pacSent);
    jsonn.put("mobiledloadSpeed", mobSpeed);
    jsonn.put("mobileuploadSpeed", mobUspeed);
    jsonn.put("wifiStrength", wstrength);
    // Using a PrintWriter object to write onto the page
    PrintWriter out = response.getWriter();
    response.setContentType("application/json");
    response.setCharacterEncoding("UTF-8");
    // Writing values to the page
    out.print(jsonn.toString());
    out.flush();
}
```
