```
```php
echo "<p>Cookie Set</p>";
?>
</body>
</html>
```
```

In order to reduce space, we shall show the simple script forms.

# Reading a cookie

Viewing and accessing cookies is easy. We mentioned previously that cookie variables could be accessed using the predefined $_COOKIE array and this is exactly how we shall access them. Remember that cookies do not become visible until the next loading of a page. To test if a cookie was successfully set, we need to check for the cookie on the next load of the page before the cookie expires. The script below illustrates checking for our cookie:

```
```php
<?php
// File: example12-13.php

$strCookieData = $_COOKIE["TestCookie"];

echo "<p>$strCookieData</p>";
?>
```
```

The output from the above script is:

Hello, this is a cookie

# Deleting a cookie

Cookies can be deleted by simply using the setcookie() function with only the name of the cookie, for example:

```
```php
setcookie ("TestCookie");
```
```

# Storing multiple data items in a cookie

One way of storing multiple variable data items within a cookie is to create a string with all preferred information stored within it and pass it as a single value to the cookie. We can then use the explode() function to extract all the information from the cookie. The following script illustrates the creation of the cookie's data:

```
```php
<?php
// File: example12-14.php

$strAddress = $_SERVER['REMOTE_ADDR'];
$strBrowser = $_SERVER['HTTP_USER_AGENT'];
$strOs = $_ENV['OS'];

$strInfo = "$strAddress::$strBrowser::$strOs";
setcookie ("AnotherCookie", $strInfo);
?>
```
```