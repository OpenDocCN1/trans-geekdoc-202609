```
break;
// Catch all other errors
default:
$error = "<h2>Default Error Message</h2>
<b>Level </b>$errLvl</b> in $errFile on line $errLine<br />
$errMsg";
break;
}
echo $error;
}

// Set the custom error handler
set_error_handler('myErrorHandler');

// Attempt to disable E_WARNING messages (applies to in built
// handler only)
error_reporting(E_ALL ^ E_WARNING);

// Trigger an error
if (!@mysql_connect('localhost','wronguser','wrongpassword')) {
    trigger_error('Error connecting to MySQL Server: ' .
    mysql_error(), E_USER_ERROR);
}
?>
```

Although we've attempted to disable the E_WARNING message—both with the error_reporting function and the error suppression operator—the above example will report both errors.

# Triggered Errors vs. Conditional Execution

PHP's custom error handling mechanism effectively introduces another level of error handling to your applications, this time, at a global level. It is important to understand the ramifications of this approach before we use this mechanism.

Until now, you've probably built error handling into your code at call time. Here's a typical example:

```
<?php
// Some function which updates the database
function updateUserDetails($name, $password, $email)
{
    // If update succeeds...
    return TRUE;
```