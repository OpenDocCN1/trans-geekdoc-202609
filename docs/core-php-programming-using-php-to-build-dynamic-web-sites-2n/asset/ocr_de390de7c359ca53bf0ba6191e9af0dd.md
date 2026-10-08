# boolean mysql_create_db(string database, integer link)

Use mysql_create_db to create a new database. Note that you must open a connection with an account that has permission to create databases. If you leave out the link argument, the last-opened connection will be used.

```
<?php
// open connection
$dbLink = mysql_connect("localhost", "admin", "secret");

//create database
mysql_create_db("garbage", $dbLink);
?>
```

# boolean mysql_data_seek(integer result, integer row)

The mysql_data_seek function moves the internal row pointer of a result set to the specified row. Use this function with mysql_fetch_row to jump to a specific row. The result argument must have been returned from mysql_query or a similar function.

```
<?php
//connect to server freetrade user, no password
$dbLink = mysql_pconnect("localhost", "freetrade", "");

//select the 'freetrade' database
mysql_select_db("freetrade", $dbLink);

//get states from tax table
$Query = "SELECT State " FROM tax ";
$dbResult = mysql_query($Query, $dbLink);

//jump to fifth row
mysql_data_seek($dbResult, 4);

//get row
$row = mysql_fetch_row($dbResult);

//print state name
print($row[0]);
?>
```

# integer mysql_db_query(string database, string query, integer link)