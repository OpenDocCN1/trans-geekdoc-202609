+   * The domain is left empty, which means that the cookie is valid for the current domain.
+   * Finally, the **setcookie()** function is used to create the cookie with the specified parameters.
+   * After executing this code, a cookie named "user" with the value "Alice Dupont" will be created, valid for one hour.

# Result:

![](bbox=[0.04, 0.3, 0.95, 0.65])

# Reading Cookies

Created cookies are automatically included in the `$_COOKIE` superglobal. To read a cookie in PHP, you can use the `$_COOKIE` superglobal. Here's how you can read an existing cookie:

```
```php
<?php
// Check if the cookie exists
```
```