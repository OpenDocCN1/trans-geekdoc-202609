```
<head>
  <title>Beginning PHP, Apache, MySQL Web Development</title>
</head>
<body>
  Invalid Username and/or Password<br>
  Not registered? <a href="register.php">Click here</a>/ to register.<br>
  <form action="user_login.php" method="post">
    <input type="hidden" name="redirect" value="<?php echo $_POST['redirect'] ?? ''; ?>">

    Username: <input type="text" name="username"><br>
    Password: <input type="password" name="password"><br>
    <input type="submit" name="submit" value="Login">
  </form>
</body>

<?php
if ($_SERVER['HTTP_REFERER'] == "*" || $_SERVER['HTTP_REFERER'] == "http://localhost/index.php") {
  $redirect = "/index.php";
} else {
  $redirect = $_GET['redirect'];
}
?>
<html>
<head>
  <title>Beginning PHP, Apache, MySQL Web Development</title>
</head>
<body>
  Login below by supplying your username/password...<br>
  Or <a href="register.php">click here</a> to register.<br>
  <form action="user_login.php" method="post">
    <input type="hidden" name="redirect" value="<?php echo $redirect; ?>">
    Username: <input type="text" name="username"><br>
    Password: <input type="password" name="password"><br>
    <input type="submit" name="submit" value="Login">
  </form>
</body>
</html>
<?php
?>
```

# 3. Create the user_personal.php page with the following code:

```
<?php
session_start();
include "auth_user.inc.php";
include "conn.php";
?>
```