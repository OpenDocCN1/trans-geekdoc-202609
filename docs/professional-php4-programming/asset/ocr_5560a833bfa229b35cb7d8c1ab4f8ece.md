```
<?php
// check for cookies with the algorithm:
// 1 - Send a cookie
// 2 - Reload the page
// 3 - Check to see if the cookie exists
// 4 - Perform desired action based on the results

if (!$cookie) {
    // Send a redirect header to the page proving that
    // we've attempted to set the cookie.
    header("Location: $PHP_SELF?cookie=1");

    // Set a test cookie.
    setcookie("test", "1");
} else {
    // Test to see if the cookie hasn't been set
    if (!$test) {
    // The cookie doesn't exist
    echo ("Please enable cookies in your browser.");
    } else {
    // The cookie exists, send them to a page with cookie support.
    header("Location: http://yourserver.com/next.php");
    }
}
?>
```

# # Some More Session Functions

We have most of the useful session functions in the above examples. There are some others too:

```
string session_save_path([string path])
```

Returns the current path in which session files are stored. If the path is specified, it sets the path in which session files are stored:

```
boolean session_is_registered(string name)
```

Returns true if the name passed to the function is a registered session variable, and false if it is not:

```
array session_get_cookie_params()
```

Returns an array of items relating to the session cookie. These items are lifetime (the cookie's expiration), path (path on the server of files that can access the cookie), domain (the domain setting the cookie), and secure (whether or not the cookie can be accessed outside of a secure connection):

```
void session_set_cookie_params(int lifetime [, string path
[, string domain]])
```