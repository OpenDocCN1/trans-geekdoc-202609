# Preselecting Multiple Selection Lists

It contains two additional functions that return an array instead of a string.

```
```php
function getFormDataArrayGET($name) {
    if (isset($_GET[$name])) {
        return $_GET[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
    return array();
}
function getFormDataArrayPOST($name) {
    if (isset($_POST[$name])) {
        return $_POST[$name];
    } else {
        $cookiedata = getCookieData();
        if ($cookiedata != null &&
            isset($cookiedata[$name])) {
            return $cookiedata[$name];
        }
    }
    return array();
}
```
```

*Retrieving Form Data from a Cookie (getFormData.inc.php: excerpt)*

These functions return an array for multiple lists that you can use as you did in `select-multiple.php`.

```
```php
<?php
    require_once 'getFormData.inc.php';
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0
```
```