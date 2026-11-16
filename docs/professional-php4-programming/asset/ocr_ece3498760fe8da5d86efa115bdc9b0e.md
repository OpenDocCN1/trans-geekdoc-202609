```
// the error message is logged to the webserver's error log
error_log("File could not be opened", 0);
// the error message is logged as an e-mail
error_log("File could not be opened", 1, "phpuser@php.wrox.com",
    "Reply-To:      phpcoder@somedomain.com");
// send to debug port
error_log("File could not be opened", 2,
    "debugmachine.somedomain.com:333");
// log error message to a file
error_log("File could not be opened", 3,
    "/var/adm/logs/php_errors.log");
}
?>
```

In practice, however, the error reporting need not be based just on these four levels. In fact they are sometimes more useful when used in conjunction with functions that route the error message to the web site's functional maintainers. The code below illustrates this:

```
<?php
//Route_Error.php
function logContentError($msg)
{
    error_log($msg, 0);
    error_log($msg, 1, "content.manager@foowidgets.com",
        "Reply-To: content.manager@foowidgets.com");
}

function logDBError($msg)
{
    error_log($msg, 0);
    error_log($msg, 1, "content.manager@foowidgets.com",
        "Reply-To: content.manager@foowidgets.com");
    error_log($msg, 3, "/tmp/dberrors.log");
}
?>
```

The error reporting functions logContentError() and logDBError() are called when an error related to the content or a database related error occurs, respectively. The functions take care of routing the error message to the maintainer or the appropriate log file.

# Debugging Utilities

Now that we have a fair understanding of the various bugs that can creep into our scripts and also how to handle them, we can take a look at the various tools that we can use to identify bugs and fix them. We shall take a look at tools both commercial and open source, ranging from simple command line utilities to fully-fledged debuggers integrated into IDEs. Some of the common utilities available are:

+   - HTTP debugging utilities
+   - Bug tracers