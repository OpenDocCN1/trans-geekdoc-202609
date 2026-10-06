# Appendix C: Alternatives to MySQL

# ODBC

ODBC (Open Database Connectivity API). It isn't a database engine as such, but rather it is an application programming interface (API). It allows an application to talk to a wide variety of database engines, without either the application or the database engine needing knowledge of each other. Communication happens through a driver manager installed on the database server machine. Applications make requests to the driver manager, which passes the request to the database using the appropriate ODBC driver.

ODBC is commonly used to communicate with Microsoft's Access and SQL database engines, as well as IBM's DB2 database. Access is user-friendly, and for simple databases; however, it doesn't scale well, so is not recommended for anything other than small, low-traffic Web applications. SQL Server is a powerful RDBMS comparable to Oracle (though somewhat easier to administer), only available on the Windows platforms. It's a good choice if you're working with Microsoft technologies in general. DB2 is also a RDBMS in a similar vein to Oracle; versions exist for AIX, Windows, Linux, and z/OS (IBM's mainframe operating system).

Microsoft Windows has an ODBC driver manager built in, and open-source versions of ODBC exist for other platforms, including various flavors of UNIX, Linux, and Mac OS.

You can connect to an ODBC database using PHP's PDO. (The ODBC extension is built into the Windows version of PHP; however, if you want to use ODBC with PDO you need to connect the PDO_ODBC extension.) Here's a PDO example that connects to a SQL Server database, adds a product to tables, and retrieves the product for display:

```
<php
$dsn = "odbc:driver={SQL Server};server=localhost;database=mydatabase";
$username = "username";
$password = "password";

// Connection to SQL Server database
try {
$conn = new PDO($dsn, $username, $password);
$conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
echo "Connection failed: " . $e->getMessage();
}

// Add a product
$sql = "INSERT INTO products (id, productname) VALUES (:id, :productname)\*";
$stmt = $conn->prepare($sql);
$stmt->bindValue(":id", 123, PDO::PARAM_INT);
$stmt->bindValue(":productname", "WonderWidget", PDO::PARAM_STR);
$stmt->execute();

// Retrieve the product
```