# Listing II.5.5. The session.php file

```
<?php
// Opening the session
function open($save_path, $session_name)
{
    // Network address of the MySQL server
    $dblocation = "localhost";
    // Database name
    $dbname = "boo";
    // Database user
    $dbuser = "root";
    // User password
    $dbpasswd = "";
    // Establishing the database connection
    $dbcnx = mysql_connect($dblocation, $dbuser, $dbpassword);
    if (!$dbcnx) exit(
        ("Unfortunately, MySQL server is not available: ".mysql_error());
    );
    // Selecting the database
    if (!$mysql_select_db($dbname, $dbcnx))
    exit("Unfortunately, the database is not available: ".mysql_error());

    return true;
}

function close()
{
    // Closing the database connection
    mysql_close();

    return true;
}

function read($id)
{
    // Reading the session value
    $query = "SELECT * FROM session WHERE session = '$id'";
    $ses = mysql_query($query);

```