# The default location of the config file for phpMyAdmin

```
`/opt/lampp/phpmyadmin/config.inc.php`
```

# How to configure authentication for phpMyAdmin

+   1. Open a terminal and change to the `/opt/lampp/phpmyadmin` directory.
+   2. Open the `config.inc.php` file for editing by typing the following command:
+      ```bash
+      sudo gedit config.inc.php
+      ```
+   3. Set the ‘blowfish_secret’ option to a random string up to 46 characters. This specifies the encryption key for the cookie.
+   4. Set the ‘auth_type’ option to a value of ‘cookie’.
+   5. Set the ‘user’ and ‘password’ options to empty strings.
+   6. Save your changes.

# The default settings

```
```php
$cfg['blowfish_secret'] = 'xampp'; /* YOU SHOULD CHANGE THIS FOR A MORE
SECURE COOKIE AUTH! */

/* Authentication type and info */
$cfg['Servers'][$i]['auth_type']      = 'config';
$cfg['Servers'][$i]['user']           = 'root';
$cfg['Servers'][$i]['password']       = '';
```
```

# The settings after phpMyAdmin has been configured for authentication

```
```php
$cfg['blowfish_secret'] = 'd2k0vc93ms28si29';

/* Authentication type and info */
$cfg['Servers'][$i]['auth_type']      = 'cookie';
$cfg['Servers'][$i]['user']           = '';
$cfg['Servers'][$i]['password']       = '';
```
```

# How to use phpMyAdmin to test the MySQL server

+   1. Use the XAMPP Control Panel to start the Apache and MySQL servers as described in figure C-3.
+   2. Start Chrome and enter this URL:
+      ```text
+      http://localhost/phpmyadmin/
+      ```
+      This should start phpMyAdmin and prompt you for a username and password. If it doesn’t, click the “Log out” link to get to the log in page.
+   3. Log in as the root user by specifying a username of ‘root’ and the password for the root user. By default, the root user doesn’t have a password, so you don’t need to enter one. When you successfully log in as the root user, phpMyAdmin should display its Home page. At this point, both the MySQL server and phpMyAdmin are working correctly.

Figure C-4    How to configure phpMyAdmin