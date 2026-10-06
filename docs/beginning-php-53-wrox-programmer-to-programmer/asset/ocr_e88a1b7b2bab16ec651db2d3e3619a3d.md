# Chapter 14: Manipulating MySQL Data with PHP

# # Deleting Records

Deleting rows via PHP is a similar process to updating. Chapter 12 showed you how to delete rows from a table using the SQL DELETE keyword:

```
mysql> DELETE FROM fruit WHERE id = 2;
Query OK, 1 row affected (0.02 sec)
```

Deleting rows using PHP, you pass a DELETE statement directly via PDO::query(), or create the statement using PDO::prepare() with placeholders, passing in values (the criteria for the WHERE clause) with PDOStatement::bindValue() and running the query with PDOStatement::execute().

The following script deletes the member record with the ID of 8 from the members table:

```
<php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "myapp";

try {
  $conn = new PDO($dsn, $username, $password, PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
  echo "Connection failed: " . $e->getMessage();
}

$id = 8;
$sql = "DELETE FROM members WHERE id = :id";

try {
  $stmt = $conn->prepare($sql);
  $stmt->bindValue(":id", $id, PDO::PARAM_INT);
  $stmt->execute();
} catch (PDOException $e) {
  echo "Query failed: " . $e->getMessage();
}

?>
```

Incidentally, rather than binding the value of a variable to a placeholder with PDOStatement::bindValue(), you can use PDOStatement::bindParam() to bind the variable itself. If you change the value of the variable after the call to bindParam(), the placeholder value is automatically updated to the new value (in other words, by reference rather than by value). This can be useful if you're not sure what value you're going to pass in the time you prepare the statement. Find out more about bindParam() in the online PHP manual at http://www.php.net/manual/en/pdostatement.bindparam.php.