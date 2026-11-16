```
if(isset($_GET['fooid'])) {
    //not written to the log - the log level is too high
    $log->logMessage('A fooid is present', Logger::DEBUG);
    //LOG_INFO is the default so this would get printed
    $log->logMessage('The value of fooid is ' . $_GET['fooid']);
} else {
    //This will also be written, and includes a module name
    $log->logMessage('No fooid supplied',
        Logger::CRITICAL,
        "Foo Module");
    throw new Exception('No fooid id!');
}
?>
```

If `$_GET['fooid']` is set, then two calls to `logMessage()` are made, but only one message will actually be written to the file because of the configured logging level. The contents of the log will look something like the following:

```
03/17/04 03:58:42   Logger::INFO   The value of fooid is 25
```

Here you see the timestamp, the logging level of the message, and the message itself.

If `$_GET['fooid']` is not set, then you will see the following log entry:

```
03/19/04 05:30:07   Logger::CRITICAL   No fooid passed from
http://localhost/testLogger.php   Foo Module
```

In this case, the `testLogger.php` page failed to pass `fooid` to the page that invoked the logger, so the `Logger::CRITICAL` error was written to the file.

# Extending the Logger Class

Logging to a text file is an incredibly useful way to store log data. There are literally thousands of utilities you can use to parse and analyze this data—from simple UNIX utilities (such as `sed` and `grep`) to fancy commercial log analysis software packages costing tens of thousands of dollars. Sometimes, however, a text file isn't the most convenient storage medium. You might want to use a relational database or integrate with your platform’s system logger to centralize all your application logs. Additionally, the `Logger` class as developed thus far is capable of writing only to a single file, no matter where in the application it is invoked. There are several circumstances in which you might want to keep separate logs for different sections of an application, or for different tasks performed. In this section, you'll extend the `Logger` class to be able to integrate with any data storage medium and support multiple logs in a single application.