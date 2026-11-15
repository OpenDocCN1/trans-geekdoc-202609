# # Deleting Records

Deleting rows of data via PHP is a similar process to updating. Chapter 12 showed you how to delete rows from a table using the SQL DELETE keyword:

```
```
mysql> DELETE FROM fruit WHERE id = 2;
Query OK, 1 row affected (0.02 sec)
```
```

To delete rows using PHP, you pass a DELETE statement directly via PDO::query(), or create the statement using PDO::prepare() with placeholders, passing in values (such as the criteria for the WHERE clause) with PDOStatement::bindValue() and running the query with PDOStatement::execute().

The following script deletes the member record with the ID of 8 from the members table:

```
```php
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";

try {
  $conn = new PDO( $dsn, $username, $password );
  $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
  echo "Connection failed: " . $e->getMessage();
}

$id = 8;

$sql = "DELETE FROM members WHERE id = :id";

try {
  $st = $conn->prepare( $sql );
  $st->bindValue( ":id", $id, PDO::PARAM_INT );
  $st->execute();
} catch ( PDOException $e ) {
  echo "Query failed: " . $e->getMessage();
}

?>
```
```

Incidentally, rather than binding the value of a variable to a placeholder with PDOStatement::bindValue(), you can instead use PDOStatement::bindParam() to bind the variable itself. If you then change the value of the variable after the call to bindParam(), the placeholder value is automatically updated to the new value (in other words, the variable is bound by reference rather than by value). This can be useful if you're not sure what value you're going to pass in at the time you prepare the statement. Find out more on bindParam() in the online PHP manual at http://www.php.net/manual/en/pdostatement.bindparam.php.