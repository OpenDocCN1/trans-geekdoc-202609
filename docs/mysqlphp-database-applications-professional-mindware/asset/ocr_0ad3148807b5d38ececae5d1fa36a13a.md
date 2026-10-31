This application is going to use the same 401-type authentication used in the previous examples, but here the values for $PHP_AUTH_USER and $PHP_AUTH_PW will also be the values used to log into the database.

![](bbox=[0.15, 0.2, 0.24, 0.26])

> > $PHP_AUTH_USER and $PHP_AUTH_PW are only available if PHP is installed as an Apache module. If you are working on Windows, you will not be able to use this type of authentication.

The header.php file, which is included in every page in the content management system, contains the following code:

```
```php
if ($authentication == "admin")
{
    include "admin_authenticate.php";
}
else
{
    include "authenticate.php";
}
$this_username = $PHP_AUTH_USER;
```
```

This if ... else block determines which authentication script will run. In pages that require administrative access you will see a variable assignment like the following prior to the include of header.php.

```
```php
$authentication = "admin";
```
```

If this does not exist, the authenticate.php will be included. Here are the contents of the authenticate.php file.

```
```php
$realm = "Netsloth Content";
$errmsg = "You must enter a valid name & password to access this function";
if (empty($PHP_AUTH_USER)
    || ( !empty($newuser) && $olduser == $PHP_AUTH_USER )
)
{
    $what = empty($PHP_AUTH_USER) ? "login" :
        "newuser($newuser,$olduser)";
    authenticate($realm,$errmsg. ":".$what);
}
```
```