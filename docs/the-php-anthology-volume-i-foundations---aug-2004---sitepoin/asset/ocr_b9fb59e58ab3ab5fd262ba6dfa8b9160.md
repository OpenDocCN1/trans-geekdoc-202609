Further information can be found in the PHP manual[26], and in Kevin Yank's article, Write Secure Scripts with PHP 4.2![27] on SitePoint.

# # Magic Quotes

Magic quotes is a feature intended to help prevent security breaches in sites developed by PHP beginners.

It adds escape characters (see Chapter 5 for more information) to incoming URL query strings, form posts, and cookie data automatically, before your script is able to access any of these values. Should you insert the data directly into your database, there's no risk of someone being able to tamper with the database provided magic quotes functionality is switched on.

For beginners, this is certainly a useful way to prevent disasters. However, once you understand what SQL injection attacks are, and have developed the habit of dealing with them in your code, the magic quote functionality can become more of a problem than it's worth.

Magic quotes functionality is controlled by a PHP configuration setting, magic_quotes_gpc, which can be either on or off.

My own preference is to always have magic quotes switched off, and deal with escaping data for SQL statements myself. Unfortunately, this means the code I write won't port well to PHP installations where magic quotes is switched on (I'll end up with backslashes in my content). Thankfully, to deal with this problem, PHP provides the function get_magic_quotes_gpc, which can be used to find out whether magic quotes are switched on. To keep the code in this book portable, we'll use a simple file that strips out magic quotes, should the functionality be enabled:

```
<?php
/**
 * Checks for magic_quotes_gpc = On and strips them from incoming
 * requests if necessary
 */
if (get_magic_quotes_gpc()) {
    $_GET    = array_map('stripslashes', $_GET);
    $_POST   = array_map('stripslashes', $_POST);
}
```

[26] http://www.php.net/registerglobals
[27] http://www.sitepoint.com/article/758