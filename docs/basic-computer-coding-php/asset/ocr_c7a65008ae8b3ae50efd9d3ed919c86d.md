file bearing that name and a validation can be done by comparing both values.


A session ends when the user loses the browser or after leaving the site, the server will terminate the session after a predetermined period of time, commonly 30 minutes’ duration.

# Remember

# Starting a PHP Session

A PHP session is easily started by making a call to the session_start() function. This function first checks if a session is already started and if none is started then it starts. It is recommended to put the call to session_start() at the beginning of the page.

This must occur before any HTML code is sent to the Web browser. Even a <php will qualify as sending information to the browser, and it will be too late to use session_start.

Session variables are stored in associative array called $_SESSION[]; These variables can be accessed during lifetime of a session.

The following example starts a session then register a variable called counter that is incremented each time the page is visited during the session.

Make use of isset() function to check if session variable is already set or not.

Put this code in a test.php file and load it many times to see the result –

```
<?php
session_start();
```

```
if ( isset($_SESSION['counter'])) {
    $_SESSION['counter'] += 1;
} else {
    $_SESSION['counter'] = 1;
}
```