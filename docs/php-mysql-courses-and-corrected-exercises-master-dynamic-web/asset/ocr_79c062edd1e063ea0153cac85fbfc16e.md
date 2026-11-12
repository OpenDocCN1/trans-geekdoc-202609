```
```html
<!DOCTYPE html>
<html>
<head>
<title>Connection</title>
</head>
<body>
<form action="connexion.php" method="post">
<label for="email">Email:</label>
<input type="text" id="email" name="email"><br><br>
<label for="password">Password:</label>
<input type="password" id="password" name="password"><br>
<button type="submit">Log in</button>
</form>
</body>
</html>
```
```

Here is an example of the code in the connection.php file that handles the connection request:

```
```php
<?php
// Database connection
$connection = new PDO("mysql:host=localhost;dbname=library", "root", "");

// Retrieve user data
```
```