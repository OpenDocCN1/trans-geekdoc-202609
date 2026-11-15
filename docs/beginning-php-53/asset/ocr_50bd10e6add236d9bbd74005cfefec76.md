Unlike trigger_error(), calling error_log() does not cause the error to be handled by the PHP error handler (or your own custom error handler, if you’ve created one), nor can it stop the script from running. It merely sends a log message somewhere. If you want to raise an error, use trigger_error() instead of (or as well as) error_log().

error_log() is also useful within custom error handler functions, as you see in a moment.

To use error_log(), call it with the error message you want to log:

```
error_log ( "Houston, we've had a problem." );
```

By default, the message is sent to the PHP logger, which usually adds the message to the system log or the Web server’s error log (see “Controlling Where Error Messages Are Sent” for more details). If you want to specify a different destination for the message, pass an integer as the second parameter.

Passing a value of 1 causes the message to be sent via email. Specify the email address to send to as the third parameter. You can optionally specify additional mail headers in a fourth parameter:

```
error_log ( "Houston, we've had a problem.", 1, "joe@example.com", "Cc: bill@example.com" );
```

Pass a value of 3 to send the message to a custom log file:

```
error_log ( "Houston, we've had a problem.\n", 3, "/home/joe/custom_errors.log" );
```

Notice that error_log() doesn’t automatically add a newline (
) character to the end of the log message, so if you want your messages to appear on separate lines you need to add your own newline.

error_log() returns true if the error was successfully logged, or false if the error couldn’t be logged.

# Letting Your Script Handle Errors

For greater flexibility, you can create your own error handler function to deal with any errors raised when your script runs (whether raised by the PHP engine or by calling trigger_error()). Your error handler can then inspect the error and decide what to do: it might log the error in a file or database; display a message to the user; attempt to fix the problem and carry on; clean up various files and database connections and exit; or ignore the error altogether.

To tell PHP to use your own error handler function, call set_error_handler(), passing in the name of the function:

```
set_error_handler ( "myErrorHandler" );
```

> The following error types cannot be handled by a custom error handler; instead they will always be handled by PHP’s built-in error handler: E_ERROR, E_PARSE, E_CORE_ERROR, E_CORE_WARNING, E_COMPILE_ERROR, and E_COMPILE_WARNING. In addition, most E_STRICT errors will bypass the custom error handler, if they’re raised in the file where set_error_handler() is called.