
## Making a Connection

To make a connection to a MySQL database in your PHP script, all you need to do is create a new PDO object. When you create the object, you can provide it in three arguments: the DSN, which describes the connection to connect to; the username of the user you want to connect as; and the user's password. The returned PDO object serves as your script's connection to the database:

```php
$conn = new PDO($dsn, $username, $password);
```

A DSN, or Database Source Name, is a simple string that describes attributes of the connection such as the type of database system, the location of the database, and the database name. For example, the following DSN can be used to connect to a MySQL database called mydatabase running on the same machine as the PHP engine:

```php
$dsn = "mysql:host=localhost;dbname=mydatabase";
```

If host isn't specified, localhost is assumed.

So, putting it all together, you could connect to your MySQL database as follows (replacing mypass with your real root password of course):

```php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";
$conn = new PDO($dsn, $username, $password);
```

When you've finished the connection, you should close it so that it's freed for other scripts to use. Although the PHP engine usually closes connections when a script finishes, it's a good idea to close the connection explicitly on the safe side.

To close the connection, just assign null to your connection variable. This effectively destroys the PDO object, and therefore the connection:

```php
$conn = null;
```

## Handling Errors

Database errors can be notoriously difficult to track down and deal with. One of the nice things about PDO is that you can get it to return MySQL errors in the form of highly descriptive PDO objects. You can use the PHP keywords try and catch to handle these exceptions easily and deal with them appropriately.

Exceptions are covered fully in Chapter 20, so you just learn the basics.

To set PDO to raise exceptions when database errors occur, use the PDO::setAttribute method to set your PDO object's error mode, as follows:

```php
$conn = new PDO($dsn, $username, $password);
$conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```

## Chapter 12: Introducing Databases and SQL

Now you can capture any error that might occur when connecting to the database using a try ... catch block code. If you were writing a sophisticated application, you would probably log the error message to a file, and personally send an email to the Webmaster including the details of the error. For the sake of these examples, though, you'll just display the error message in the Web page:

```php
try {
  $conn = new PDO($dsn, $username, $password);
  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
  echo "Connection failed: " . $e->getMessage();
}
```

PHP runs the code within the try block. If an exception is raised by PDO, the catch block stores the PDOException object in $e, then displays the error message with $e->getMessage().

For example, if the $password variable in the script contains an incorrect password, you would see a message like this when you run the script:

```
Connection failed: SQLSTATE[28000] [1045] Access denied for user 'root'@localhost' (using password: YES)
```

## Reading Data

Now that you've connected to your database in your PHP script, you can read some data from the database using a SELECT statement. To send SQL statements to the MySQL server, you use the query method of the PDO object:

```php
$conn->query($sql);
```

If your SQL statement returns rows of data from a result set, you can capture the data by assigning the result of $conn->query to a variable:

```php
$rows = $conn->query($sql);
```

The result returned by $conn->query is actually another type of object, called a PDOStatement object. You can use this object along with a foreach loop to move through all the rows in the result set. Each row is an associative array containing all the field names and values for that row. For example:

```php
$sql = "SELECT * FROM fruit";
$rows = $conn->query($sql);
foreach ($rows as $row) {
  echo "name = " . $row["name"] . "<br />";
  echo "color = " . $row["color"] . "<br />";
}
```

## Part III: Using PHP Practice

### Try It Out: Read a Database Table with PHP

This simple example shows how you use PDO to connect to a MySQL server and database, read all the rows of a table, and handle any errors that might occur.

First, you need a database and table to work with. This assumes that you've already created the database called mydatabase, and created the popular table fruit, as shown in previous sections. If you haven't, you can easily re-create the database and table by typing the following into the MySQL command-line tool:

```sql
CREATE DATABASE mydatabase;
USE mydatabase;

CREATE TABLE fruit (
  id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
  name VARCHAR(30) NOT NULL,
  color VARCHAR(30) NOT NULL,
  PRIMARY KEY (id)
);

INSERT INTO fruit (name, color)
```

Now save the following script as get_fruit.php in your folder, and run the script in your browser. You should see a result similar to Figure 12-1.

```php
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Fruit</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
<h1>Fruit</h1>
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";

try {
  $conn = new PDO($dsn, $username, $password);
  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
  echo "Connection failed: " . $e->getMessage();
}

$sql = "SELECT * FROM fruit";
echo "<ul>";
try {
  $rows = $conn->query($sql);
  foreach ($rows as $row) {
    echo "<li>A " . $row["name"] . " is " . $row["color"] . "</li>";
  }
} catch (PDOException $e) {
  echo "Query failed: " . $e->getMessage();
}
echo "</ul>";

$conn = null;
?>
</body>
</html>
```
