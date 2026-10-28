# A utility file that forces a valid admin user (util/valid_admin.php)

```
```php
<?php
    // make sure the user is logged in as a valid administrator
    if (!isset($_SESSION['is_valid_admin'])) {
        header("Location: .");
    }
?>
```
```

# Code that’s included at the top of the login page

```
```php
<?php
    require_once('util/secure_conn.php');    // require a secure connection
?>
```
```

# Code that’s included at the top of the other protected pages

```
```php
<?php
    require_once('util/secure_conn.php');    // require a secure connection
    require_once('util/valid_admin.php');     // require a valid admin user
?>
```
```

# Description

+   - You can use a utility file like the valid_admin.php file to redirect to the controller if the user isn’t logged in as a valid administrator.
+   - The code at the top of the login page should force the page to use a secure connection.
+   - The code at the top of each protected page should force a secure connection. To do that, it can include a utility file that forces the connection like the file in figure 21-5.
+   - The code at the top of each protected page should also force a valid admin user. To do that, it can include a utility file like the valid_admin.php file in this figure.