# The default location of the config file for phpMyAdmin

```
```text
/Applications/XAMPP/xamppfiles/phpmyadmin/config.inc.php
```
```

# How to configure authentication for phpMyAdmin

+   1. Use TextWrangler to open the config.inc.php file shown above.
+   2. Set the ‘blowfish_secret’ option to a random string up to 46 characters. This specifies the encryption key for the cookie.
+   3. Set the ‘auth_type’ option to a value of ‘cookie’.
+   4. Set the ‘user’ and ‘password’ options to empty strings.
+   5. Save your changes. You may need your system password.

# The default settings

```
```php
$cfg['blowfish_secret'] = 'xampp'; /* you SHOULD CHANGE THIS FOR A MORE
SECURE COOKIE AUTH! */

/* Authentication type and info */
$cfg['Servers'][$i]['auth_type']          = 'config';
$cfg['Servers'][$i]['user']               = 'root';
$cfg['Servers'][$i]['password']           = '';
```
```

# The settings after phpMyAdmin has been configured for authentication

```
```php
$cfg['blowfish_secret'] = 'dk20vc93ms28si29';

/* Authentication type and info */
$cfg['Servers'][$i]['auth_type']          = 'cookie';
$cfg['Servers'][$i]['user']               = '';
$cfg['Servers'][$i]['password']           = '';
```
```

# How to use phpMyAdmin to test the MySQL server

+   1. Use the manager-osx application to start the Apache and MySQL servers as described in figure B-2.
+   2. Start Chrome and enter this URL:
+      `http://localhost/phpmyadmin/`
+      This should start phpMyAdmin and prompt you for a username and password. If it doesn’t, click the “Log out” link to get to the log in page.
+   3. Log in as the root user by specifying a username of ‘root’ and the password for the root user. By default, the root user doesn’t have a password, so you don’t need to enter one. When you successfully log in as the root user, phpMyAdmin should display its Home page. At this point, both the MySQL server and phpMyAdmin are working correctly.

# Permissions note

+   - If you don’t have permission to save the config.inc.php file, give yourself the appropriate permissions. To do that, use the Finder to select the config.inc.php file. Then, select the File menu, the Get Info item, and the Sharing and Permissions link. Next, click on the lock icon to allow changes, click on the plus sign (+), and add yourself as a user who has read and write privileges. If necessary, repeat this procedure for the phpmyadmin folder.

![](bbox=[0.046, 0.948, 0.438, 0.966])