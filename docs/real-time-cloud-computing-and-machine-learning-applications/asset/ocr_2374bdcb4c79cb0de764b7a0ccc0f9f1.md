# 438 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nasir Rosun and M. Indoonondan

```
// Initialising variables for making connection to localhost
static Connection c = null;
static PreparedStatement insertReadings = null;
static String sql = null;

public void localhost(int identifier) {
    // If the identifier equals 1, the PC is being accessed
    if (identifier == 1) {
        // Creating MySQL statement to insert values by specifying table name
        sql = "INSERT INTO regression(DownloadSpeed,UploadSpeed,PacketsReceived,PacketsSent) VALUES (?,?,?,?,?)";
        try {
            Class.forName("com.mysql.jdbc.Driver");
            // Using port 3306 for localhost
            // Opening the table using a Connection object and specified database name, username and password
            c = (Connection) DriverManager.getConnection("jdbc:mysql://localhost:3306/network", "root", "\n            // Using the Statement to insert the readings
            insertReadings = (PreparedStatement)c.prepareStatement(sql);
            System.out.println("OPENED DATABASE SUCCESSFULLY.");
        } catch (ClassNotFoundException | SQLException e) {
            System.out.println("DB ERROR: " + e);
        }
    }

    // If the identifier equals 2, the android is being accessed
    if (identifier == 2) {
        // Creating MySQL statement to insert values into database
        sql = "INSERT INTO androidression(DownloadSpeed,UploadSpeed,MobileDownloadSpeed,MobileUploadSpeed,PacketsReceived,PacketsSent,WifiStrength) VALUES (?,?,?,)";
        try {
            Class.forName("com.mysql.jdbc.Driver");
            // Opening the table using a Connection object and specified database name, username and password
            c = (Connection) DriverManager.getConnection("jdbc:mysql://localhost:3306/network", "root", "");
            // Using the Statement object to insert the readings
            insertReadings = (PreparedStatement)c.prepareStatement(sql);
            System.out.println("OPENED DATABASE SUCCESSFULLY.");
        } catch (ClassNotFoundException | SQLException e) {
            System.out.println("DB ERROR: " + e);
        }
    }
}
```