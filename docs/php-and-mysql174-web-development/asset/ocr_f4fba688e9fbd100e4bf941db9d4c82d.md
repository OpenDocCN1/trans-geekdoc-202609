# Chapter 26 Debugging and Logging

and stops executing the script. For nonfatal errors, the same text is output, but execution continues.

This HTML output makes the error stand out but looks poor. The style of the error message is unlikely to fit the rest of the site's. It might also result in some users seeing no output at all if the page's content is displayed within a table and their browser is fussy about HTML. HTML opens does not close table elements, such as

```
<table>
<tr><td>
<br>
<b>Error Type:</b> error message in <b>path/file.php</b>
on line <b>lineNumber:</b><br></td>
```

You do not have PHP's default error handling behavior or even the same settings for all files. To change the error reporting level for the current script, you can call the function error_reporting().

Passing an error reporting constant, or a combination of them, sets the level in the same way that the similar directive in php.ini does. The function returns the previous error reporting level. A common way to use the function is like this:

```
// turn off error reporting
$old_level = error_reporting(0);
```

```
// here, put code that will generate warnings
```

```
// turn error reporting back on
error_reporting($old_level);
```

This code snippet turns off error reporting, allowing you to execute some code that is likely to generate warnings that you do not want to.

Turning off error reporting permanently is a bad idea because it makes finding your coding errors and fixing them more difficult.

# Triggering Your Own Errors

The function trigger_error() can be used to trigger your own errors. Errors created in this way are handled in the same way as regular PHP functions.

The function requires an error message and optionally give an error type. The error type needs to be one of E_USER_ERROR, E_USER_WARNING, or E_USER_NOTICE. If you do not specify a type, the default is E_USER_NOTICE.

You use trigger_error() as follows:

```
trigger_error('This computer will self destruct in 15 seconds', E_USER_WARNING);
```