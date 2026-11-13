```
mysql_close($conn);
?>
```

**WARNING** – It's very dangerous to delete a database and any table. So before deleting any table or database you should make sure you are doing everything intentionally.

# Deleting a Table

It's again a matter of issuing one SQL command through **mysql_query** function to delete any database table. But be very careful while using this command because by doing so you can delete some important information you have in your table.

# Example

Try the following example to drop a table –

```
<?php
$dbhost = 'localhost:3036';
$dbuser = 'root';
$dbpass = 'rootpassword';
$conn = mysql_connect($dbhost, $dbuser, $dbpass);

if(! $conn ) {
  die('Could not connect: ' . mysql_error());
}

$sql = 'DROP TABLE employee';
$retval = mysql_query( $sql, $conn );

if(! $retval ) {
  die('Could not delete table employee: ' . mysql_error());
}

echo "Table deleted successfully\n";
mysql_close($conn);
?>
```

# Insert Data to MySQL Database

Data can be entered into MySQL tables by executing SQL INSERT statement through PHP function **mysql_query**. Below a simple example to insert a record into **employee** table.