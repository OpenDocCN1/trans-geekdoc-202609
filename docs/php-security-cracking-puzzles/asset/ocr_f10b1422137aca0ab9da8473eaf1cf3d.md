# Chapter I.7: Authorization and Authentication 65

The SID, which is passed using either the GET method (as the command line parameter) or the session's cookies.

In Section I.4.1, it was suggested that you develop a user registration system. The code of the user authorization system based on sessions is presented in Listing I.7.4.

# Listing I.7.4. Authorization system based on sessions

```
<?php
// Initiating a session
session start();
?>
<form method=post>
Name: <input type=text name='name' value='<?php $_SESSION['name']; ?>'><br>
Password: <input type=password name='password' value='<?php $_SESSION['password']; ?>'><br>
<input type=submit value=Submit>
</form>
<?php
// The form handler
if (empty($_POST['name']) && empty($_POST['password'])) {

    // Establishing the database connection
    require_once("config.php");
    // To protect against SQL injection, process
    // the obtained login and password using the
    // mysql_escape_string function;
    if (!get_magic_quotes($gpc)) {

        $_POST['name'] = mysql_escape_string($_POST['name']);
        $_POST['password'] = mysql_escape_string($_POST['password']);
    }
    // Executing the query that returns
    // the number of records matching the login and the password
    $query = "SELECT COUNT(*) FROM userslist\n\n    WHERE name = '$_POST[name]' AND password = '$_POST[password]'";
    $usr = mysql_query($query);
    if (!$usr) exit("Error in authorization block");
    // Obtaining the number of records *
```