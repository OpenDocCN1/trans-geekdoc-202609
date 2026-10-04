
# Chapter 11

5. Finally, create the fifth file, testcookie.php:

```php
<html
<head>
  <title>Beginning PHP, Apache, MySQL Web Development</title>
</head>
<body>
  <h1>This is the Test Cookie Page</h1>
  <?php
  if ($_COOKIE['username'] == '' || $_COOKIE['password'] == '') {
    echo "No cookies set.<br>";
    echo "<a href=\"setcookie.php\">Click here</a> to set your cookies.";
  } else {
    echo "setcookie:<br>";
    echo "Username cookie value: <?php echo $_COOKIE['username']; ?><br>";
    echo "Password cookie value: <?php echo $_COOKIE['password']; ?><br><br>";
  }
  ?>
</body>
</html>
```

# How It Works

We ran the previous cookie example to show you how you can keep persistent logins between single browser sessions. As you have noticed, some of the pages are just display or navigation pages. For that reason, we won't explain those. We will instead focus on setcookie_un.php, setcookie_pw.php, and testcookie.php.

The testcookie_un.php does just what the name says: it sets the cookie for the username, which is just hardcoded for the example. It uses a header redirect to send you to the next page.

Next page is setcookie_pw.php, which does the same as setcookie_un.php, except that it is setting the cookie for the password. When you're redirected to a simple display that tells you your cookies have been set.

You can navigate to testcookie.php. This page checks if the cookie values are valid. If they are not, it says, "No cookies set," and you can try to set the cookies again. If you are successful in your login, the screen will look like the one in Figure 11-16.

Should you need to delete or end a cookie, simply run some code (like the code that follows) to end the cookie from the user's browser.

```php
setcookie('username', '', time() - 3600);
```

# Using Logins, Profiles, and Personalization

This is the Test Cookie Page

Your cookies were set:
Username cookie value: jermys
Password cookie value: apache

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_369_0.png)

This sets the username cookie for one hour ago and sets the username value to an empty string, thereby making the username cookie unavailable to the Web site the user is logged into.

Now that you have some cookie knowledge, you can use it in the login system if you want. Although cookies are a good way to keep persistent logins between browser sessions, they can be altered and/or spoof by a user because the cookie is stored on the client machine. That is generally why systems house their main login information with sessions and use cookies as a subfeature only.

Now let's move on the last part of this chapter. We will show you how logged-in admins can change information and delete information based on their access privileges. You may notice similarities between this system and the user login system and you'd be right. Remember that the more you practice, the easier this will be when you are writing systems like this for your clients.

# Chapter 11

# Administration Section

### Try It Out

In this section, administrators are required to log in before they can view the users signed up in our registration database. Once they are logged in, only certain privileged admins are allowed to perform operations. For this example, admins with a privilege level of 1 are allowed to update user accounts and delete user accounts. Admins with a privilege level of 2 are allowed to update user information; they will not be allowed to delete a user's account. This would be useful if some user was, reason unable to log into the site and the administrator needed to reset passwords, change usernames, and so on, you don't want just any administrator to be allowed to do everything administrator.

The code for all pages follows. Keep the files, save them in a folder called admin in your Web directory. We will explain how they work after showing you the code.

- 1. Create the first file, conn.inc.php:

```php
<?php
$conn = mysql_connect('localhost', 'jcstolz', 'r3minyL') or die(mysql_error());
$db = mysql_select_db('registration') or die(mysql_error());
```

- 2. Create the second file, auth_inc.php:

```php
<?php
session_start();
if ($_SESSION['admin_logged'] == "" || $_SESSION['admin_password'] == "**") {
    $redirect = $_SERVER['PHP_SELF'];
    header("Refresh: 5;URL=admin_login.php?redirect=$redirect");
    echo "You are currently not logged in, we are redirecting you, be patient!;<br>";
    echo "(If your browser doesn't support this, <a href=\"login.php?redirect=$redirect\">click here</a>)";
    die();
} else {
n}
?>
```

- 3. Create the third file, saving it as index.php:

```php
<?php
session_start();
if ($_SESSION['admin_logged'] == "" || $_SESSION['admin_password'] == "**") {
    include "unlogged_admin.php";
} else {
    include "logged_admin.php";
}
?>
```

- 4. Create the fourth file, logged_admin.php:

```html
<html>
<head>
  <title>Beginning PHP, Apache, MySQL Web Development</title>
</head>
<body>
  <h1>Welcome to the Admin Area!</h1
You are currently logged in.<br>
  <a href="admin_area.php">Click here</a> to access your administrator tools.
</body>
</html>
```

- 5. Create and save the fifth file as unlogged_admin.php:

```html
<html>
<head>
  <title>Beginning PHP, Apache, MySQL Web Development</title>
</head>
<body>
  <h1>Welcome to the Admin Area!</h1
You are currently not logged in.<br>
Once logged in, you will have access to your administrator tools.<br>
  <a href="admin_login.php">Click here</a> to login.
</body>
</html>
```

- 6. Create the sixth file, admin_login.php:

```php
<?php
session_start();
include 'conn.php';
if (isset($_POST['submit'])) {

$query = "SELECT username, password, admin_level FROM admin WHERE username = '" . $_POST['username'] . "' AND password = '" . $_POST['password'] . "'";
```

```php
else
{
  <html>
<head>
<title>Beginning PHP, Apache, MySQL Web Development</title>
</head>
<body>
Invalid Username and/or Password<br>
<form action="admin_login.php" method="post">
<input type="hidden" name="redirect" value="<?php echo $_POST['redirect']; ?>"?>
  Username: <input type="text" name="username"<br>
Password: <input type="password" name="password"<br>
<input type="submit" name="submit" value="Login">
</form>
?>
<?php
}
else
  if ($_SERVER['HTTP_REFERER'] == "http://localhost/admin/index.php") {
    $redirect = 'admin/index.php';
  }
  else
    $redirect = $_GET['redirect'];
  }
?<html>
<head>
<title>Beginning PHP, Apache, MySQL Web Development</title>
</head>
<body>
Login below supplying your username...<br>
<form action="admin_login.php" method="post">
<input type="hidden" name="redirect" value="<?php echo $redirect; ?>"?>
  Username: <input type="text" name="username"<br>
Password: <input type="password" name="password"<br>
<input type="submit" name="submit" value="Login">
</form>
</body>
</html>
<?php
}
?>
```

- 7. Create the seventh file, save it as admin_area.php:

```php
<?php
session_start();
include "auth_admin.inc.php";
```

```php
include "conn.php";
?>
<html>
<head>
<title>Beginning PHP, Apache, MySQL Web Development</title>
</head>
<body>
<h1>Admin Area</h1>
Below is a list of users and your available administrator privileges.<br><br>
<?php
if ($_SESSION['admin_level'] == "1") {
$query = "SELECT FIRST_name, last_name, id FROM user_info ORDER BY last_name;";
$result = mysql_query($query) or die(mysql_error());

while ($row = mysql_fetch_array($result)) {
echo $row['first_name']; ?> <?php echo $row['last_name']; ?>
&nbsp;&nbsp;<a href="update_user.php?id=<?php echo $row['id']; ?>">Update User</a><br>
<a href="delete_user.php?id=<?php echo $row['id']; ?>">Delete User</a><br>
}
}
else {
$query = "SELECT FIRST_name, last_name, id FROM user_info ORDER BY last_name;";
$result = mysql_query($query) or die(mysql_error());

while ($row = mysql_fetch_array($result)) {
echo $row['first_name']; ?> <?php echo $row['last_name']; ?>
&nbsp;&nbsp;<a href="update_user.php?id=<?php echo $row['id']; ?>">Update User</a><br>
}
}
?>
</body>
</html>
```

- 8. Create the eighth file, update_user.php:

```php
<?php
session_start();
include "auth_admin.inc.php";
include "conn.php";
?>
<html>
<head>
<title>Beginning PHP, Apache, MySQL Web Development</title>
</head>
<body>
<h1>Update User Information</h1>
```
