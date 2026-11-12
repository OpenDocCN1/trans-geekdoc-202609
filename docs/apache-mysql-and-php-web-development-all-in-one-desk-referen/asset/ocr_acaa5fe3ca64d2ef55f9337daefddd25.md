# Listing 6-6: getcookie.php

```
<html><title>Have a cookie! Yum yum!</title>
<body>
This file reads the temporary cookie that was set
in the <a href="setcookie.php">setcookie.php</a>
file.<p>
<pre>
name: dummies1000<br>
The value according to the PHP code is...
<?php
print $_COOKIE['dummies1000'];
?>
</pre>
</body>
```

When you open the setcookie.php page, the cookie is set for the duration of the session, which simply means the cookie is (dare I say it?) eaten (groan) after you shut down the browser. But if you keep the browser open and then visit getcookie.php, you will see that the cookie's value is indeed still set.

![](bbox=[0.12, 0.45, 0.2, 0.54])

When you set a cookie, the cookie's value is not available to the page where you set it. It's true and a bit of a bummer. So if you write a PHP program where you set a cookie value, don't attempt to access the $_COOKIE array inside that same .php file, hoping to access the value. Instead, just hard-code the cookie's value or store it in another variable.

# Storing cookies for the long term

The setcookie() function includes some optional parameters that give you more control over your jar of cookies. (Ahh, so many cookie jokes.) One crunchy and useful parameter is the expiration parameter. This is a date that the cookie is removed from the system. Prior to that date, the cookie lives on the user's system in the cookie cache.

To specify the date, you have to give it in a Unix time, which is the number of seconds since January 1, 1970.

![](bbox=[0.12, 0.735, 0.2, 0.82])

If you want, for example, to see that your cookie rots and expires 60 days from the date the page is loaded, determine the current Unix time and add the number of seconds corresponding to 60 days, which is 60 × 60 × 60 × 24. Thus, to set a cookie that will stay on the user's system for 60 days, use this:

```
<?php
$expiredate = time()+60*60*60*24;
setcookie('dummies1001', 'goodbye', $expiredate);
?>
```