We'll start by building the login screen (login.php):

```
<html>
<head>
<title>Online Library - Login</title>
</head>
<body bgcolor="#ffffff" text="#000000">
<h2>Online Library - Login</h2>
<form action="login.php" method="POST">
Username: <input name="username" type="text" /><br />
Password: <input name="password" type="password" /><br />
<input type="submit" value="Log in" />
</form>
</body>
</html>
```

This is the HTML foundation for our login system. Of course, it doesn't do much at the moment except display a basic login form. Let's add some database interaction:

```
<?php
// Connect to the database
$conn = mysql_connect('localhost', 'jon', 'secret') or die(mysql_error());
mysql_select_db('Library', $conn) or die(mysql_error());

// Close the connection to the database
mysql_close($conn);
?>
<html>
<head>
<title>Online Library - Login</title>
</head>
<body bgcolor="#ffffff" text="#000000">
<h2>Online Library - Login</h2>
<form action="login.php" method="POST">
Username: <input name="username" type="text" /><br />
Password: <input name="password" type="password" /><br />
<input type="submit" value="Log in" />
</form>
</body>
</html>
```

Now, we connect to the database every time the page is loaded. That's wasteful, because we only want to connect to the database when we're actually trying to authenticate the user. Let's continue by retrieving the form variables and only connecting to the database if they exist. We'll just focus on the PHP section here: