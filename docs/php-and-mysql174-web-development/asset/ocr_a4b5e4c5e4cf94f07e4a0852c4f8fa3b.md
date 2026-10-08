Listing 26.2 contains a script that declares an error handler, sets the error handler using
set_error_handler(), and then generates some errors.

# Listing 26.2 handle.php—This Script Declares a Custom Error Handler
and Generates Different Errors

```
<php
// The error handler function
function myErrorHandler($errno, $errstr, $errfile, $errline) {
    echo "<p><strong>" . $errno . ":<strong>" . $errstr . "</strong><br>/";
    Please try again, or contact us and tell us that the
    error occurred in line \" . $errline . " of file \" . $errfile . ";
    so that we can investigate further.</p>";
}

if (($errno == E_USER_ERROR) || ($errno == E_ERROR)) {
    echo "<p>Fatal error. Program ending.</p>";
    exit;
}

// Set the error handler
set_error_handler('myErrorHandler');

// trigger different levels of error
trigger_error('Trigger function called.', E_USER_NOTICE);open('nofile', 'r');
trigger_error('This computer is beige.', E_USER_WARNING);
include('nofile');
trigger_error('This computer will self destruct in 15 seconds.', E_USER_ERROR);
?>
```

The output from this script is in Figure 26.1.

This custom error handler does not do any more than the default behavior. Because you write
this code, you can make it anything. You have a choice about what to tell your visitors
when something goes wrong and how to present information so that it fits the rest
of site. More importantly, you have the flexibility to decide what happens. Should the
script continue? Should a message be logged or displayed? Should tech support be alerted
automatically?