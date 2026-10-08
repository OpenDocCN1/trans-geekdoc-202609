# string mysql_field_type(integer result, integer field)

Use mysql_field_type to get the type of a particular field in the result set.

# boolean mysql_free_result(integer result)

Use mysql_free_result to free any memory associated with the specified result set. This is not strictly necessary, as this memory is automatically freed when a script finishes executing.

```
<?
// connect to server
$Link = mysql_connect("localhost", "httpd", "");

// select the 'store' database
mysql_select_db("store", $Link);

// get everything from customer table
$Query = "SELECT * FROM customer \;
$Result = mysql_query($Query, $Link);

// free result set
mysql_free_result($Result);
?>
```

# integer mysql_insert_id(integer link)

After inserting into a table with an auto increment field, the mysql_insert_id function returns the id assigned to the inserted row. If the link argument is left out, the most recent connection will be used.

```
<?
// connect to server as freetrader, no password
$dbLink = mysql_connect("localhost", "freetrade", "");

// select the 'freetrade' database
mysql_select_db("freetrade", $dbLink);

// insert a row
$Query = "INSERT INTO user (Login, Password) " . 
"VALUES ('leon', 'secret') ";
$dbResult = mysql_query($Query, $dbLink);

// get id
print("ID is " . mysql_insert_id($dbLink));?>
```