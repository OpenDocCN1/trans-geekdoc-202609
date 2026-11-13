Returns true on success, false on failure.

# mysql_connect

```
mysql_connect([hostname [:port] [:/path/to/socket] [,username [,password]]])
```

Opens a connection to a MySQL server and returns a connection ID (which evaluates to true) that may be used in other MySQL-related functions. The following default values are assumed if they are not specified:

+   hostname:port = "localhost:3306"
+   username = server process name
+   password = ""

If the connection attempt is unsuccessful, an error message will be displayed by default and the function will return false. To bypass display of the error message (e.g. to display your own by checking the return value), put '@' at the start of the function name (i.e. @mysql_connect(...)).

# mysql_create_db

```
mysql_create_db(db_name [,link_id])
```

Creates a new MySQL database with the specified name, using the default or specified (link_id) MySQL connection. Returns true on success, or false on error. mysql_createdb() may also be used, but is deprecated.

# mysql_data_seek

```
mysql_data_seek(result_id, row_number)
```

Moves the internal result pointer of the result set identified by result_id to row number row_number, so that the next call to a mysql_fetch_* function will retrieve the specified row. Returns true on success, and false on failure. The first row in a result set is number 0.