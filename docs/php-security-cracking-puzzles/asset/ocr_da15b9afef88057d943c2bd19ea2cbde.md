# 32 Part I: Puzzles

```
// Requesting the list of registered users
$query = "SELECT FROM userslist ORDER BY name";
$usr = mysql_query($query);
if (!$usr) exit("Error - " . mysql_error());
whilewhile($user = mysql_fetch_array($usr))
{
    echo "<a href=user.php?id_user=$user[id]>$user[name]</a><br>";
}
>
```

The user.php page provides information about each visitor. The code of the script contained in the user.php file is presented in Listing I.4.3.

The code of the user.php page and the code shown in Listing I.4.3 can be found in the /scripts/4.4/2 directory in the accompanying CD-ROM.

![](bbox=[0.095, 0.413, 0.158, 0.493])

# Listing I.4.3. The contents of the user.php file

```
<?php
// Setting the connection to the database
require_once("config.php");
// Requesting the list of all users
$query = "SELECT FROM userslist WHERE id_user = $_GET[id_user]";
$usr = mysql_query($query);
if (!$usr) exit("Error - " . mysql_error());
$user = mysql_fetch_array($usr);
echo "User name - $user[name]<br>";
if(!empty($user['email'])) echo "email - $user[email]<br>";
if(!empty($user['url'])) echo "URL - $user[url]<br>";\?>
```

Using the script provided in Listing I.4.3, display the user password in the browser window. Then rewrite the script to eliminate the possibility of hacking it using an SQL injection.