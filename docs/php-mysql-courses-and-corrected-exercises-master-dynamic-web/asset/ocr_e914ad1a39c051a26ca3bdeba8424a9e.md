```
```php
$database = new Database();
$database->connect();
echo "<br>";
$database->disconnect();
```
```

```
```
?>
```
```

This code begins by including the Database.php file, which contains the definition of the Database class we've just seen. Next, an instance of the Database class is created using the default constructor. Finally, the connect() and disconnect() methods of this instance are called successively.

This means that the connection to the database is established by calling the connect() method, which displays a message indicating that the connection has been established. Next, the disconnect() method is called to close the connection, which displays a message indicating that the connection has been closed. When you run this code, you will get a result similar to the following outcome: