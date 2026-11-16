```
<?php
echo($access);
if ($access == 1) {
    echo(" time!");
} else {
    echo(" times!");
}
?>
</html>
```

The following error does not show up if the error messages are turned off, and would be virtually impossible to find in a large script with many cookies being set, sessions started, or other header() calls.

The following output comes from the above error-prone code:

![](bbox=[0.1, 0.34, 0.94, 0.51])

If an error message like this is generated, check to see if any HTML or PHP generated text appears before the setcookie() function call. Also be careful to check for any require() or include() calls that may generate text or send data to the browser.

If these check alright, then locate the php.ini file and look for the auto_prepend directive which will automatically require() PHP data into the beginning of your files.

If we haven't compiled PHP with this option, we will not be able to access our cookies by using the variable referenced to the name of the cookie (that is, $cookieename). In this case we will have to access cookies by using $HTTP_COOKIE_VARS['cookieename']. It is not necessary to rebuild PHP to fix this; it is changeable.

Another common error found in cookie-related code is that the name is set incorrectly. The name for a cookie can only be alphanumeric. Any characters other than a-z, A-Z, 0-9, hyphen (-), and underscore (_) are automatically converted to the underscore character.

This means if we use setcookie("my.initials", "d.h.o."), the cookie name would be changed to my_initials. Consequently, we would call the variable set from the cookie $my_initials, even though it would still hold the value "d.h.o."

However useful cookies are, they should not be required for an application to run. If for some reason, we absolutely require cookies for our application, include code to check for cookies on the user's side and tell them to turn their cookie acceptance on. The following code will perform a simple check to see if cookies are enabled: