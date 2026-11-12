# Email Overload

Although error_log is capable of sending emails containing error messages, be careful! You may find a lot more in your inbox than you bargained for. You can control the frequency of error reporting with the php.ini values ignore_repeated_errors and ignore_repeated_source—see Appendix A for details.

Of course, you're not tied to using the error_log function as the only way to create log files. You may decide it's better to write your own classes for logging errors, or consider using PEAR::Log[4], which provides many more options for capturing data from your application.

# How do I display errors gracefully?

Now that you've seen how to define your own custom error handler, I can show you how to use PHP's output buffering (which I'll discuss in detail in Volume II, Chapter 5, and which is described in the PHP Manual[5]) so that your production Website gracefully informs users of “temporary difficulties” without slapping ugly error messages across partially rendered HTML pages. The following example demonstrates the approach and provides a more thorough custom error handler that's capable of dealing with multiple error levels:

```
<?php
/**
 * Custom Error handler
 *
 * @param int error level number
 * @param string error message
 * @param string php script where error occurred
 * @param int line number in script where error was triggered
 * @param array current state of all global variables
 */
function myErrorHandler($errLvl, $errMsg, $errFile, $errLine,
$errContext)
{
    switch ($errLvl) {
        // Handle ERRORs
        case E_USER_ERROR:
            // Stop and clean the second buffer
```

[4] http://pear.php.net/package/Log
[5] http://www.php.net/manual/en/ref.outcontrol.php