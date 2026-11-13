```
```php
<?php
}
?>
</body>
</html>
```
```

# Retrieving Data from MySQL Database

Data can be fetched from MySQL tables by executing SQL SELECT statement through PHP function mysql_query. You have several options to fetch data from MySQL.

The most frequently used option is to use function mysql_fetch_array(). This function returns row as an associative array, a numeric array, or both. This function returns FALSE if there are no more rows.

Following is a simple example to fetch records from employee table.

# Example

Try the following example to display all the records from employee table.

```
```php
<?php
$dbhost = 'localhost:3036';
$dbuser = 'root';
$dbpass = 'rootpassword';

$conn = mysql_connect($dbhost, $dbuser, $dbpass);

if(! $conn ) {
  die('Could not connect: ' . mysql_error());
}

$sql = 'SELECT emp_id, emp_name, emp_salary FROM employee';
mysql_select_db('test_db');
$retval = mysql_query( $sql, $conn );

if(! $retval ) {
  die('Could not get data: ' . mysql_error()));
}

while($row = mysql_fetch_array($retval, MYSQL_ASSOC)) {
```
```