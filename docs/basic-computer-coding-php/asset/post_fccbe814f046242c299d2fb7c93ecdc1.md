
You can use isset() function to check if a cookie is set or not.

```php
<html
<head>
<title>Accessing Cookies with PHP</title>
</head>
<body>
<?php
if (isset($_COOKIE["name"]))
echo "Welcome " . $_COOKIE["name"] . "<br />";
else
echo "Sorry... Not recognized" . "<br />";
?>
</body>
</html>
```

# Deleting Cookie with PHP

Officially, to delete a cookie you should call setcookie() with the name argument only but this does not always work well, however, and should not be relied on.

It is safest to set the cookie with a date that has already expired

```php
<?php
setcookie("name", "", time()- 60, "/", "", 0);
setcookie("age", "", time()- 60, "/", "", 0);
?>
```

```html
<head>
<title>Deleting Cookies with PHP</title>
</head>
<body>
<?php echo “Deleted Cookies” ?>
</body>
</html>
```

# 7.2.2 Sessions

An alternative way to make data accessible across the various pages of an entire website is to use a PHP Session.

A session creates a file in a temporary directory on the server where registered session variables and their values are stored. This data will be available to all pages on the site during that visit.

The location of the temporary file is determined by a setting in the php.ini file called session.save_path. Before using any session variable you have setup this path.

When a session is started following happen –

- PHP first creates a unique identifier for particular session which is such as 3c70fj34c3jij973hjkop2fc937e3443.
- A cookie named PHPSESSID is automatically sent to the user's computer to store unique session identification string.
- A file is automatically created on the server in the designated temporary directory and bears the name of the unique identifier prefixed by sess__ie_3c70fj34c3jij973hjkop2fc937e3443.

When a PHP script wants to retrieve the value from a session variable, PHP automatically gets the unique session identifier string from the PHPSESSID cookie and then looks in its temporary directory for the file bearing that name and a validation can be done by comparing both values.

A session ends when the user loses the browser or after leaving the site, the server will terminate the session after a predetermined period of time, commonly 30 minutes’ duration.

# Remember

# Starting a PHP Session

A PHP session is easily started by making a call to the session_start() function. This function first checks if a session is already started and if none is started then it starts. It is recommended to put the call to session_start() at the beginning of the page.

This must occur before any HTML code is sent to the Web browser. Even a <php will qualify as sending information to the browser, and it will be too late to use session_start.

Session variables are stored in associative array called $_SESSION[]; These variables can be accessed during lifetime of a session.

The following example starts a session then register a variable called counter that is incremented each time the page is visited during the session.

Make use of isset() function to check if session variable is already set or not.

Put this code in a test.php file and load it many times to see the result –

```php
<?php
session_start();
```

```php
if ( isset($_SESSION['counter'])) {
    $_SESSION['counter'] += 1;
} else {
    $_SESSION['counter'] = 1;
}
```

# Basic Computer Coding: PHP

```php
$msg = "You have visited this page ". $_SESSION['counter'];
$msg .= "in this session.";
?>
```

```html
<html>
<head>
  <title>Setting up a PHP session</title>
</head>
<body>
  <?php echo ($msg); ?>
</body>
</html>
```

It will produce the following result – You have visited this page 1 in this session.

# Destroying a PHP Session

A PHP session can be destroyed by session_destroy() function. This function does not need any argument and a single call can destroy all the session variables. If you want to destroy a single session variable variable then you can use unset() function to unset a session variable. Here is the example to unset a single variable –

```php
<?php
unset($_SESSION['counter']);
?>
```

Here is the call which will destroy all the session variables –

```php
<?php
  session_destroy();
?>
```

# Turning on Auto Session

You don't need to call start_session() function to start a session when a user visits your site if you can set `session.auto_start` variable 1 in `php.ini`.

# Sessions without cookies

There may be a case when a user does not allow to store cookies on their machine. So there is another method to send session ID to the browser.

Alternatively, you can use the constant SID which is defined if the session started. If the client did not send an appropriate session cookie, if it has the form session_name=session_id. Otherwise, it expands to an empty string. Thus, you can embed it unconditionally into URLs.

The following example demonstrates how to register a variable, and how to click correctly to another page using SID.

```php
<?php
session_start();

if (isset($_SESSION['counter'])) {
    $_SESSION['counter'] = 1;
} else {
    $_SESSION['counter']++;
}

$msg = "You have visited this page ". $_SESSION['counter'];
$msg .= "in this session.";

echo ( $msg );
?>
```

<p>To continue click following link <br /></p>

# Basic Computer Coding: PHP

```html
<a href = "nextpage.php?<?php echo htmlspecialchars($SID); ?>"></a>
```

It will produce the following result -
You have visited this page 1 in in this session.
To continue click following link

The htmlspecialchars() may be used when printing the SID in order to prevent XSS related attacks.

# ROLE MODEL

# Vannevar Bush

Vannevar Bush born on March 11, 1890, in Everett, Massachusetts, in a family of the Universalist minister—the Reverend Richard Perry Bush of Provincetown, MA, and Emma Linwood (Paine).

The Universalist minister—the Reverend Richard Perry Bush of Provincetown, MA, and Emma Linwood (Paine).

The Universalist minister—the Reverend Richard Perry Bush of Provincetown, MA, and Emma Linwood (Paine).

# ROLE MODEL

Vannevar Bush

In 1919, Bush left Tufts and went to the Massachusetts Institute of Technology (MIT) as a professor of electrical power transmission. Starting from 1925, Bush began construction of mechanical devices for performing integration. First was the Product Intergraph, next was the Differential Analyzer, an analog computer that could solve differential equations with many as 18 independent variables. It actually used large gears and other mechanical parts to solve equations. In 1931, he completed the first differential analyzer (see the lower photo). At the same time, Bush and team at MIT develop the “network analyzer”, a system for setting up miniature versions of large and important electrical networks. Later Bush constructed an improved Differential Analyzer, built by electronic tubes, which was used intensively during the WWII.

# Bush and his Differential Analyzer

In 1922, Bush, his college roommate, Laurence Marshall, and a colleague of Bush from the company Amrad (a small company for radio devices, where Vannevar served as a consultant), Charles G. Smith, set up the Metals and Controls Corporation, for producing thermostats and thermionic tubes. Later the company managed to
