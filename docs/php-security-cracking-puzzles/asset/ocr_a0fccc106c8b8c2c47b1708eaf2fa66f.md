# Chapter II.4: MySQL and SQL Injections

```
//////////////////////////////////////////////////////////////////////
// The block to check whether the name is already in use
//////////////////////////////////////////////////////////////////////
// Connecting to the database
require_once("config.php");
// Checking whether the provided
// name has already been used
$query = "SELECT COUNT(*)\ FROM userslist WHERE name = '" . \$_POST[\[\'name\]] . '\';";
$usr = mysql_query($query);
if(!$usr) exit("Error - " . \$mysql_error()");
$total = mysql_result($usr, 0);
if ($total > 0) {
    exit("The user name has already been used. Select another one.");
}
//////////////////////////////////////////////////////////////////////
// The user registration block
//////////////////////////////////////////////////////////////////////
// Forming and executing a SQL query
// to add a new user
$query = "INSERT INTO userslist
    VALUES (NULL,
    '" . \$_POST[\[\'name\]] . '\',\n    '" . \$_POST[\[\'pass\]] . '\',\n    '" . \$_POST[\[\'email\]] . '\',\n    '" . \$_POST[\[\'url\]] . '\');";
if(mysql_query($query)) {
    // Reloading the page to clear the POST data
    echo "<html><head>
META HTTP-EQUIV = 'Refresh' CONTENT = '0; URL = '" . \$_SERVER[\[\'PHP_SELF\]] . '\</head></html>";
} else exit("Error adding data - " . \$mysql_error()");
>
```

As noted in the preceding listing, quotation marks can be escaped using the mysql_escape_string() function. However, if the magic quotes mode is enabled on the server, calling the function duplicates the server's work. The enabled magic