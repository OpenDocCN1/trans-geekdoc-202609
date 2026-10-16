A common pattern is to use a fixed naming scheme for files containing classes and to put the classes in a defined directory. For instance, the class MyClass resides in the file /classes/MyClass.class.php. In that case, the following autoloading function would load the class on demand:

```
<?php
function myAutoloadFunction($classname) {
    if (preg_match('/^[a-zA-Z_\x7f-\xff][a-zA-Z0-9_\x7f-\xff]*$/', $classname)) {
        //check for valid classname
        require_once
        "/path/to/classes/$classname.class.php";
    }
}

spl_autoload_register('myAutoloadFunction');
?>
```

Autoloading Classes (autoload.php)

So, for instance, the following call

`$c = new UnknownClass();`

would in turn call myAutoloadFunction(), providing UnknownClass as the value for the $classname parameter. If you call spl_autoload_register() multiple times, all autoloading functions are registered, so PHP calls each of them until the desired class is finally defined—or until all such functions have been called.

NOTE: The spl_autoload_register() function was introduced in PHP 5.1.2 as part of the SPL (Standard PHP Library). Formerly, you had to write a function