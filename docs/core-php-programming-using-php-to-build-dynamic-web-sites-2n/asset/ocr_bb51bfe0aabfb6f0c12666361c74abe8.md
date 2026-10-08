# Core PHP Programming

determining the number of rows returned by a server statement. Also, this function is available only when using Client-Library.

```
<?php
//open connection as admin
$Link = sybase_pconnect("dbl1", "sa", "sa");

//use the store database
sybase_select_db("store", $Link);

//take 10% off all items that cost
//more than ten dollars
$Query = "UPDATE item \n$Query .= "SET Price = Price * 0.90 \"
$Query .= "WHERE Price > 10.00; \"
$Result = sybase_query($Query, $Link);

//get number of rows changed
$RowsChanged = sybase_affected_rows($Link);

print("$RowsChanged prices updated.<BR>\n");

//close connection
sybase_close($Link);
?>
```

# boolean sybase_close(integer link)

The sybase_close function closes a connection to a database. Its use is not strictly necessary, as PHP will close connections for you when your script ends. You can leave out the link, and the last one to be opened will be closed.

# integer sybase_connect(string server, string user, string password)

The sybase_connect function returns a connection identified by the server, user and password arguments. The server must be a valid server name as defined in the interfaces file. All the arguments are optional, and if left out, PHP will use sensible defaults. Connections created with sybase_connect will be closed automatically when your script completes. Compare this function with sybase_pconnect.

# boolean sybase_data_seek(integer result, integer row)

The sybase_data_seek function moves the internal row for a result to the specified row. Rows are numbered starting with zero. Use this function with sybase_fetch_array, sybase_fetch_object or sybase_fetch_row to move arbitrarily among the result set.