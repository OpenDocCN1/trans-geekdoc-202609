```
```php
<?php
$conn = mysql_connect("localhost", "jon", "secret")
    or die("Could not connect to MySQL.");
echo("Connection successful.");
mysql_close($conn);
?>
```
```

If another call to `mysql_connect()` is made with the same arguments while the original connection is still open, a new connection to the server will not be established. Instead, the second call to `mysql_connect()` will simply return the link identifier of the connection that is already open. The connection will be closed when either `mysql_close()` is called or the PHP script terminates.

# ## mysql_pconnect()

```
```
resource mysql_pconnect([string hostname [:port] [:path/to/socket]
[, string username [, string password]])
```
```

The "p" stands for "persistent". `mysql_pconnect()` is the same function as `mysql_connect()`, except for the fact that the connection created by `mysql_pconnect()` is not closed when `mysql_close()` is called nor when the PHP script ends. The PHP interpreter itself maintains the connection to the database server.

When subsequent calls to `mysql_pconnect()` are made with the same arguments, the PHP interpreter reuses the existing connection instead of establishing a new one. This eliminates the burden of repeatedly opening and closing database connections in applications in which frequent calls are made using the same arguments. This time saving of persistent connections is one of PHP's great advantages over the CGI model. Of course, this only works if PHP is installed as a web server module, and not in CGI mode.

Use persistent connections with care, however. Overusing persistent connections could lead to a large number of idle database connections to your database. The most ideal use of a persistent connection is in those instances where multiple pages will also request the same kind (meaning same connection parameters) of database connection. In this case, persistent connections offer a substantial performance boost.

# ## mysql_close()

```
```
boolean mysql_close([resource link_identifier])
```
```

This function closes non-persistent links to the MySQL server and returns true or false, depending on its success:

```
```php
<?php
$conn = mysql_connect("localhost", "jon", "secret")
    or die("Could not connect to MySQL.");
mysql_close($conn);
?>
```
```

# ## mysql_select_db()

```
```
boolean mysql_select_db(string database_name [, resource link_identifier])
```
```