# Part II: Solutions

The headers will display the form for entering the login and password (Fig. I.7.7). The user name and password will be placed by the browser into the $ \$_SERVER['PHP_AUTH_USER'] and \$_SERVER['PHP_AUTH_FW'] variables, respectively, of the superglobal $_SERVER array.

The $_SERVER['PHP_AUTH_USER'] and $_SERVER['PHP_AUTH_FW'] variables of the superglobal $_SERVER array are available only if PHP is installed as a module and not as a common gateway interface application.

A file, security_mod.php (Listing II.7.20), must be created, which when included into a page with the help of the include statement will require user to be authorized before the page can be viewed.

# II.7.20. The security_mod.php file

```
<?php
// Connecting to the database
require once("config.php");
// If the user is not authorized, starting the authorization procedure
if(isset($_SERVER['PHP_AUTH_USER']))
{
    Header("WW-Authenticate: Basic realm = \"Admin Page\"");
    Header("HTTP/1.0 401 Unauthorized");
    exit();
}
else
{
    // Checking the $_SERVER['PHP_AUTH_USER'] and
    // $_SERVER['PHP_AUTH_FW'] variables to protect
    // against an SQL injection
    if (get_mysql_quotes_gpc())
    {
        $_SERVER['PHP_AUTH_USER'] = =
            mysql_escape_string($_SERVER['PHP_AUTH_USER']);
        $_SERVER['PHP_AUTH_FW'] = =
            mysql_escape_string($_SERVER['PHP_AUTH_FW']);
    }
}
$query = "SELECT pass FROM userslist
    WHERE name = \".$_SERVER['PHP_AUTH_USER'].""";
$lst = @mysql_query($query);
// If the SQL query is wrong, displaying the password entry entry window
if(!$lst)
```