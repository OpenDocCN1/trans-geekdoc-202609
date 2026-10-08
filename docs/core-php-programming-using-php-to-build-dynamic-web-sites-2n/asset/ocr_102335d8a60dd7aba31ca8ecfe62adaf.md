```
//get each row
while($row = mysql_fetch_row($dbResult))
{
    //print name
    print($row[0]. "<BR>\n");
}
?
```

The mysql_num_fields function returns the number of fields in a result set. See mysql_list_fields for an example of use.

# integer mysql_num_rows(integer result)

The mysql_num_rows function returns the number of rows in a result set. See mysql_result for an example of use.

# integer mysql_pconnect(string host, string user, string password)

The mysql_pconnect function operates like mysql_connect except that the connection will be persistent. That is, it won't be closed when the script ends. The connection will last as long as the server process lasts, so that if a connection is attempted later from the same process, the overhead of opening a new connection will be avoided.

A link identifier is returned. This identifier is used in many of the other functions in this section.

```
?//open persistent connection
$dbLink = mysql_pconnect("localhost", "freetrade", "");
?
```

# integer mysql_query(string query, integer link)

Use mysql_query to execute a query. If the link argument is omitted, the last connection is used. If there has no previous connection, PHP will connect to the local host. If the query performs an insert, delete, or update, a boolean value will be returned. Select queries return a result identifier. See mysql_fetch_object for an example of use.

# string mysql_result(integer result, integer row, string field)