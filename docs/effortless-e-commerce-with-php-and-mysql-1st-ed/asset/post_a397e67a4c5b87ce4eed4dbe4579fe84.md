
## CONNECTING TO THE DATABASE

Every PHP script in the site will require a connection to the database, so let’s create a separate file in the includes directory for that purpose.

- 1. Create a new PHP script in your text editor or IDE to be named mysql.inc.php.
- See Figures 3.2 and 3.3 for indications of where this file should be placed.

- 2. Define the constants for accessing the database:

```php
<?php
define ('DB_USER', 'username');
define ('DB_PASSWORD', 'password');
define ('DB_HOST', 'localhost');
define ('DB_NAME', 'ecommerce1');
```

You’ll need to replace these values with those that are correct for your server. For my setup, I created a database called ecommerce1 and created a MySQL user with SELECT, INSERT, and UPDATE privileges on that database. You absolutely must use a more secure username and password than these!

- 3. Connect to the database:

```php
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME);
```

The mysqli_connect() function is used to connect to the database. The connection is assigned to the $dbc variable, which will be used by many functions in other scripts.

- 4. Establish the character set:

```php
mysqli_set_charset($dbc, 'utf8');
```

This function indicates what character set should be used for communications between PHP and the database. The database tables, the HTML pages, and the PHP-MySQL connection must all use the same character set.

- 5. Begin defining a function for making data safe to use in queries:

```php
function escape_data ($data) {
global $dbc;
```

> note
> Since the site will be using the UTF-8 character set, your text editor or IDE must be set to encode each page also using UTF-8.

> note
> If your PHP-MySQL setup does not support the MySQL Improved extension, which I’ll be using, you’ll need to use the older MySQL functions, which have slightly different syntax. See the PHP manual for details.

> note
> Any connection errors that occur will be handled by the custom error handler defined in the configuration file (in just a couple of pages).

This function will take a piece of data as its lone argument and make it safe to use in database queries. In other words, this function will prevent SQL Injection attacks from succeeding (see Chapter 2, “Security Fundamentals”). The function does three things:

  - Removes extra slashes if Magic Quotes is enabled
  - Trims extra spaces from the data
  - Runs the data through the mysqli_real_escape_string() function

This last task is the most important, because the mysqli_real_escape_string() function will make a value safe to use in a query, keeping in mind the database's configuration and character set in use. The function needs the database connection, which is made available through the global command.

Magic Quotes as a feature has been deprecated and will disappear from future versions of PHP.

- 6. Strip the extra slashes if Magic Quotes is on:

```php
if (get_magic_quotes_gpc()) $data = stripslashes($data);
```

Magic Quotes was created to provide a blanket level of security on incoming data, but it's not as secure as using mysqli_real_escape_string(). Hopefully, Magic Quotes is disabled on your server; but if Magic Quotes is enabled, then incoming data will already have slashes applied to potentially problematic characters that might break a query. Those slashes would be a problem, because mysqli_real_escape_string() will also apply slashes, thereby creating two slashes when there should be only one. To prevent that from happening, this line of code checks the Magic Quotes setting and calls the stripslashes() function if Magic Quotes is on.

- 7. Return a trimmed, secure version of the data:

```php
return mysqli_real_escape_string(trim($data), $dbc);
```

The difference between mysqli_real_escape_string() and something like Magic Quotes or addslashes() is that mysqli_real_escape_string() identifies what characters could be problematic based upon the database, the character set in use, and so forth.

The mysqli.inc.php file found in the downloadable source code for this book contains additional code discussed in later chapters.

- 8. Complete the escape_data() function:

```php
} // End of the escape_data() function.
```

All included PHP files will omit the closing PHP tag to prevent “headers already sent” errors.

- 9. Save the file.

You may notice that you're not being instructed to include the closing PHP tag here. This is acceptable and, in some situations, actually better. If you were to use the closing tag and then inadvertently leave an extra space or blank line after that tag, the inclusion of this file by other scripts will result in headers being sent to the Web browser. If the including (that is, parent) script later attempts to send a cookie, start a session, or redirect the browser, you'll get a "headers already sent" error message (Figure 3.4). By omitting the closing tag, that cannot happen (at least not when this script is included).

![](img/4f47e47c67bd619ac73250f11c9fc7ce_73_0.png)

Figure 3.4

## THE CONFIG FILE

The next PHP script to be created is a configuration file. Like the mysqli.inc.php script, this one will be used by every script in the site (although some sites will have pages that don't require a database connection, every PHP script in every site should always use the configuration file). The configuration file has four purposes:

- Define systemwide settings so they may be changed easily
- Define useful constants that may be used by multiple scripts
- Start the session
- Establish how errors will be handled

Let's start defining the configuration file now, and in Chapter 4, “User Accounts,” more code will be added to it.

- 1. Create a new PHP script in your text editor or IDE to be named config.inc.php and stored in your includes directory, as in Figures 3.2 and 3.3.
- 2. Define the $live and $contact_email variables:

```php
<?php
$live = false;
$contact_email = 'you@example.com';
```

The $live variable is really the most important variable because it’ll dictate how errors will be handled. Depending upon the payment gateway, this variable could also be used to switch from just testing the payment processing to actually using it. However, PayPal is a bit different, so that won’t be the case in this example.

![](img/4f47e47c67bd619ac73250f11c9fc7ce_73_1.png)

The $contact_email variable is for the email address to which error messages will be sent when the site goes live. It could also be used for contact forms, or you could define different email addresses for different purposes.

- 3. Define the constants:

```php
define ('BASE_URI', '/path/to/Web/parent/folder');
define ('BASE_URL', 'www.example.com/');
define ('MYSQL', '/path/to/mysql.inc.php');
```

These are the first three constants the site will use, and you'll need to change the values accordingly. The first constant should point to the parent of the Web root directory, if your site can use it. So, in Figure 3.2, BASE_URI . pdfs will be where the PDFs are stored and BASE_URI . mysql.inc.php will be the location of the MySQL connection script. If you can't access above the Web root directory, then assign to BASE_URI the Web root directory itself. So, in Figure 3.3, BASE_URI . 'includes/pdfs' will be where the PDFs are stored.

![](img/4f47e47c67bd619ac73250f11c9fc7ce_74_0.png)

> note
> Both the BASE_URI and BASE_URL values end with a slash.

The second constant is the base URL of the site, without the protocol, such as www.example.com/. I've specifically left off the http:// part, because some pages will use https://.

The third constant points to the MySQL connection script just created. You can use BASE_URI to help create this full path.

Constants like these are used for a couple of reasons. First, if you reference certain values in multiple scripts in multiple directories, it can be hard getting the references consistently correct. By using absolute references, they'll always be right. Second, if you change anything big about the site—its domain name or its hosting—just changing these values is all you will need to do.

- 4. Start the session:

```php
session_start();
```

The site will use sessions to track logged-in users. Since every page will require the configuration file, starting the session here will make sure that every page has access to the session data. Plus, if you want to customize the session, like its name or how long it lasts, you can do that in one place.

On the other hand, this also means that sessions will be started in some situations where they're not actually necessary, like when someone views the home page or a content listing page, without going further.
