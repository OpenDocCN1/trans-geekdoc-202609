```
```php
<?php
// Database connection information
$host = 'localhost'; $dbname = 'library'; $username = 'root'; $password = "";

try {
// Create an instance of the PDO class to establish the connection
$connection = new PDO("mysql:host=$host;dbname=$dbname", $username, $password);

// Set PDO to generate exceptions on errors
$connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

echo "Database connection successfully established";
} catch (PDOException $e) {
// Connection error handling
echo "Connection error: " . $e->getMessage();
}
?>
```
```

In this example :

The variables $host, $dbname, $username and $password contain the informations needed to connect to the MySQL database.

Since the "library" application is developed locally, the value of $host is "localhost" and that of $username