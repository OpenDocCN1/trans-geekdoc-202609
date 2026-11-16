In this example we'll set a value, path, and domain scope for the cookie:

```
```php
setcookie("my_cookie", "value", 0, "/user/index.php", ".site tronics.com");
```
```

Note that there is no 0 for secure. Since it's an optional argument, the above code and:

```
```php
setcookie("my_cookie", "value", 0, "/user/index.php", ".site tronics.com", 0)
```
```

gives the same result.

# # Deleting a Cookie

To delete a cookie, call the setcookie() function and pass the name of the cookie that is to be removed:

```
```php
setcookie("my_cookie");
```
```

Deleting cookies like this will not affect any other cookies that are set already. This method doesn't change $HTTP_COOKIE_VARS either.

The following code will also delete the cookie:

```
```php
setcookie("cookie", , 0, "/user/index.php", ".site tronics.com");
```
```

Deleting cookies can also be done by setting the lifetime of the cookie to the current time minus 24 hours:

```
```php
setcookie("my_cookie", $value, time() - 86400);
```
```

# # Amalgamating Cookie Data

PHP allows the use of arrays to make multiple values accessible through one cookie name. That is, this method sets individual cookies named cookie[0], cookie[1], cookie[2], and so on. The form of these names simply causes PHP to receive them as components of a single array variable, instead of as separate variables.

In the following example, we include both the username and the number of times that user has viewed the site in the cookie. In reality, two cookies are created with names cookie[0] and cookie[1]:

```
```php
<?php
// check to see if the user has submitted username data
if ($Submit) {
    // If first cookie does not exist, we will need to create it
    if (!$my_cookie[0]) {
        setcookie("my_cookie[0]", $username);
    }

    // Increment our counter cookie and set it.
    $my_cookie[1]++;
    setcookie("my_cookie[1]", $cookie[1]);
```
```