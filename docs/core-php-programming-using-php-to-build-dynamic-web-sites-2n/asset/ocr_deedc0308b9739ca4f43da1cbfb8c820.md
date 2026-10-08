# boolean dbc_free_result(integer result)

Use dbc_free_result to free the memory associated with the result set. This is not strictly necessary, but it's a good idea if you are worried about running out of memory. If autocommit is disabled and you free a result set before calling dbc_commit, the transaction will be rolled back.

```
<<?
// connect to database
$Connection = dbc_connect("store", "guest", "guest");

// execute query
$Query = "SELECT name, price ";
$Query = "FROM catalog";
$Result = dbc_do($Connection, $Query);

// free the result set
dbc_free_result($Result);

dbc_close($Connection);
?>
```

# boolean dbc_longreadlen(integer result, integer length)

Use dbc_longreadlen to set the maximum length for values of any columns of type long. This handles binary columns as longbinary. By default the maximum length is zero, which has the special meaning of causing fetched columns to be echoed to the browser. Any other positive number will cause returned values to be truncated to the specified length.

Note that it is not always perfect that a field is considered to be a long by the ODBC driver. For example a memo column in Microsoft Access is a long. Data appearing in the wrong place are a sign of fetching a long where you didn't expect it. One strategy to avoid these problems is to always dbc_longreadlen.

See dbc_binmode for an example of use.

# integer dbc_num_fields(integer result)

Use dbc_num_fields to find the number of fields in the result set.

```
<<?
// connect to database
$Connection = dbc_connect("store", "guest", "guest");
```