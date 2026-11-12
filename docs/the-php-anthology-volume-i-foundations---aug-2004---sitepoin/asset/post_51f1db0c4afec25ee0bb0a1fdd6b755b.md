
ob_end_clean();
// Clean out the main buffer
ob_clean();
// Display an error message
echo '
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Temporary Interruption </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
</head>
<body>
<h2>Temporary Interruption</h2>
The site is currently down for non-scheduled maintenance.<br />
Please try again shortly
</body>
</html>';
// End and flush the main buffer
ob_end_flush();
// Stop execution
exit();
break;
// Handle WARNINGs
case E_USER_WARNING:
// Clean out the main buffer
ob_clean();
// Display an error message
echo '<b>Warning:</b> ' . $errMsg;
break;
// Handle NOTICEs
case E_USER_NOTICE:
// Display an error message
echo '<b>Notice:</b> ' . $errMsg;
break;
}
}
```

This custom error handler is capable of dealing with three error levels, E_USER_ERROR, E_USER_WARNING, and E_USER_NOTICE. You'll notice that the way it handles the output buffer is a little different at each level. An E_USER_ERROR message, which, you'll remember, is a fatal error, results in the handler clearing out both output buffers (there are two, the reason for which will become obvious in a moment), and displaying a message about the site being down; this completely eliminates any HTML that may already have been sent to the buffer. An E_USER_WARNING error will result in the second buffer being wiped and replaced with the error message; as a result, the body of the HTML page is replaced with an error message. The E_USER_NOTICE behavior adds the notice error to the second buffer—it's simply appended to the existing HTML.

Look at the body of the page now:

```
// Set the custom error handler
set_error_handler('myErrorHandler');
// Start an output buffer for ERRORs
ob_start()
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Custom Error Handling with Buffering </title>
<meta http-equiv="Content-Type"
    content="text/html; charset=iso-8859-1" />
</head>
<body>
<h2>Example Errors</h2>
<?php
// Start a second output buffer for NOTICES and WARNINGs
ob_start();
?>
```

Above, after instructing PHP to use our custom error handler, we've nested one output buffer inside another so that the header and footer of the page are in a separate buffer to the body.

```
<a href="?<?php echo $_SERVER['PHP_SELF']; ?>?triggerError=error">
Trigger a Fatal Error</a><br />
<a href="?<?php echo $_SERVER['PHP_SELF']; ?>?triggerError=warning">
Trigger a Warning</a><br />
<a href="?<?php echo $_SERVER['PHP_SELF']; ?>?triggerError=notice">
Trigger a Notice</a><br />

<?php
// Generate sample errors
if (isset($_GET['triggerError'])) {
switch ($_GET['triggerError']) {
```

```
case 'error':
    trigger_error('A fatal error', E_USER_ERROR);
    break;
case 'warning':
    trigger_error('You have been warned!', E_USER_WARNING);
    break;
case 'notice':
    trigger_error('Please take note!', E_USER_NOTICE);
    break;
}
}
// Finish and display the second buffer
ob_end_flush();
?>
</body>
</html>
<?php
// Finish the main buffer
ob_end_flush();
?>
```

In the body of the page, inside the second buffer, we've used trigger_error to demonstrate the handler, using the $_GET variable triggerError.

As you execute the script, you'll notice that a fatal error results in a completely different page being rendered (as defined in the custom error handler for E_USER_ERROR); a warning error replaces the three links with the warning message, and an error notice is added below the three links.

With some care, it's possible to combine custom handlers with output control to handle errors in a manner that's graceful from the point of view of visitors to your site. Be aware, though, that it's best to keep this kind of code down to earth rather than building anything too complex, for the reasons discussed in "How do I implement a custom error handler with PHP?", in the section called "Triggered Errors vs. Conditional Execution".

## Further Reading

- Error Handling in PHP: http://www.devshed.com/Server_Side/PHP/ErrorHandling

This two part series takes an in depth look at PHP's custom error handling features and how they can be combined with output buffering.

- Error Handling: http://www.derickrethans.nl/errorhandling/talk.html

Derick Rethans, one of PHP's leading developers, gives a succinct analysis of error handling techniques from HTTP status pages to debugging and profiling PHP code in this great tutorial.

- PEAR-Error in detail: http://www.php-mag.net/itr/online_artikel/psecom,id,330,nodeid,114.html

Alexander Merz examines PEAR::Error in this freely available article published in PHP Magazine.

## Appendix A: PHP Configuration

This is a quick reference to configuring PHP that covers the most important general settings you need to be aware of, either when running applications in a live environment, or because they impact security or the way you write code.

### Configuration Mechanisms

The primary mechanism for configuring PHP is the php.ini file. As the master file, this provides you with control over all configuration settings. Entries generally take the format:

```
setting = value
```

Be sure to read the comments provided in the file before making changes, though. There are a few tricks, such as include_path using a colon (:) as a separator on Unix, and a semicolon (;) on Windows.

Most Web hosts will not provide you access to your php.ini file unless you have root access to the system (which is typically not the case if you're using a cheap virtual hosting service). Your next alternative is to use .htaccess files to configure PHP (assuming the Web server is Apache).

An .htaccess file is a plain text file that you place in a public Web directory to determine the behavior of Apache when it comes to serving pages from that directory; for instance, you might identify which pages you'll allow public access to. Note that the effect of an .htaccess file is recursive—it applies to subdirectories as well.

To configure PHP with .htaccess files, your hosting provider must have the Apache setting AllowOverride Options or AllowOverride All applied to your Web directory in Apache's main httpd.conf configuration file. Assuming that is done, there are two Apache directives you can use to modify PHP's configuration:

**php_flag**
used for settings that have boolean values (i.e. on/off or 1/0) such as register_globals

**php_value** used to specify a string value for settings, such as you might have with the include_path setting

Here's an example .htaccess file:

```
# Switch off register globals
php_flag register_globals off

# Set the include path
php_value include_path ".:/home/username/pear"
```

The final mechanism controlling PHP's configuration is the group of functions ini_set and ini_alter, which let you modify configuration settings, as well as ini_get, which allows you to check configuration settings, and ini_restore, which resets PHP's configuration to the default value as defined by php.ini and any .htaccess files. Using ini_set, here's an example which allows us to avoid having to define our host, user name and password when connecting to MySQL:

```
ini_set('mysql.default_host', 'localhost');
ini_set('mysql.default_user', 'harryf');
ini_set('mysql.default_password', 'secret');

if (!mysql_connect()) {
 echo mysql_error();
} else {
 echo 'Success';
}
```

Be aware that PHP provides for some settings, such as error_reporting, alternative functions that perform effectively the same job as ini_set. Which you prefer is a matter of taste.

Note that certain settings, such as register_globals, can only be usefully modified by php.ini or .htaccess, because such settings influence PHP's behavior before it begins executing your scripts.

Furthermore, some configuration settings can be changed only in php.ini, such as extension_dir, which tells PHP the directory in which PHP extensions can be found. For a complete reference on controlling settings, refer to the PHP Manual[1].
