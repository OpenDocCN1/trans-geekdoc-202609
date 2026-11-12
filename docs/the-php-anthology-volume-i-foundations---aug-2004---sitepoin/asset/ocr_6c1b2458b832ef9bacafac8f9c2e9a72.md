```
####START ERROR####
Level: $errLvl
File: $errFile
Line: $errLine
Time: $time

$errMsg
####END ERROR####

EOD;
error_log($error, 3, 'log/errors.log');
switch ($errLvl) {
  case E_USER_ERROR:
    echo 'System is temporarily unavailable. ' .
      'Please try again later';
    break;
  }
}

// Set the custom error handler
set_error_handler('myErrorHandler');

// Trigger an error
if (!@mysql_connect('localhost', 'wronguser', 'wrongpassword')) {
  trigger_error('Error connecting to MySQL Server: ' .
    mysql_error(), E_USER_ERROR);
}
?>
```

The custom error handler now logs errors in a format that’s easy to parse using PHP’s string functions. It logs these errors to the errors.log file, which looks like this:

```
####START ERROR####
Level: 256
File: c:\htdocs\phpanth\errorhandling\8.php
Line: 39
Time: 20031012233727

Error connecting to MySQL Server: Access denied for user:
'wronguser@127.0.0.1' (Using password: YES)
####END ERROR####
```