# Core PHP Programming

```
$Link = mysql_connect("mysql.clearink.com");
mys_select_db("store", $Link);
```

```
$Result = mysql_query("SELECT Name FROM customer", $Link);
```

```
// jump to tenth customer
msql_data_seek($Result, 10);
```

```
$Row = mysql_fetch_row($Result);
```

```
print($Row[0]);
```

```
mysql_close($Link);
?>
```

# integer mysql_db_query(string database, string query, integer link)

The mysql_db_query function is identical to mysql_query except that it specifies a
database rather than using the database selected with mysql_select_db. The query is executed in the specified database and a result is returned.

```
<?
$Link = mysql_connect("mysql.clearink.com");
$Query = "DELETE FROM customer";
$Result = mysql_db_query("store", $Query, $Link);
```

```
$RowsAffected = mysql_affected_rows($Link);
print($RowsAffected . " rows deleted.");
```

```
mysql_close($Link);
?>
```

# boolean mysql_drop_db(string database, integer link)

The mysql_drop_db function removes an entire database from the server. The link
argument is optional and, if omitted, the connection opened will be used.

```
<?
$Link = mysql_connect("mysql.clearink.com");
if(mysql_drop_db("store", $Link)) {
	print("Database deleted!");
} else {
	print("Database not deleted!");
}

```