issues here, outside sites “hot linking” your images may also eat up your band-
width.

Different solutions have been devised, such as using Apache’s mod_rewrite to
check the referral information the browser provides (which cannot always be relied
upon) to make sure the source is a local Web page. For example:

```
SetEnvIfNoCase Referer "^http://www\.sitepoint\.com/" locally_link
ed=1
SetEnvIfNoCase Referer "^http://sitepoint\.com/" locally_linked=1
SetEnvIfNoCase Referer "^$" locally_linked=1
<FilesMatch "\.(gif|png|jpe?g)$">
    Order Allow,Deny
    Allow from env=locally_linked
</FilesMatch>
```

Another option is to use sessions to establish that the person viewing the image
is a visitor to your site. The trick is to register a session variable that a visitor
must have to be able to view the image, then use a second script to render the
image. For example:

```
<?php
// Start a session
session_start();

// Register a variable in the session
$_SESSION['viewImages'] = TRUE;
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Preventing Hotlinking </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
</head>
<body>
<p> Here is the image:</p>
<img src="11.php?img=php-big.png" />
</body>
</html>
```