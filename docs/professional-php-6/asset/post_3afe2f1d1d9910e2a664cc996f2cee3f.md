
![](img/a1b732997d9cb194dceec0570dc79710_208_0.png)

Figure 8-3: Output if Horatio clicks the Edit button.

As you can see, Horatio's attempts to edit records are stopped in their tracks, as only David may edit records.

The power of this approach should be making itself clearer now. You have seen security as an example of how easy it is to modify the application, but this approach can apply to any number of new requirements that might arise.

## Pausing for Thought

Many issues must be carefully considered when designing a well-architected, enterprise-level, event-driven application. Improvements to your event-handling methodology could include some sort of handler registration, for example. This would mean that when a user logs onto a site (logging on, in this case, would be an event captured by the application), the application could automatically check which handlers are available to the user. This is achieved through the use of a default handler, which retrieves a list of the user's permissible handlers from a database and returns that information to the presentation layer.

Armed with this information, the presentation layer would know which buttons to render for the user. The administrator would get many buttons, whereas a visitor might have only one View button. If access is restricted to a View button, there is little chance that an untrusted user can maliciously modify anything to which he or she has no access.

A second issue to consider (albeit closely related to the first) before using this method for your next big contract is how to get the dispatcher to include the correct PHP project files in the first place. Because the dispatcher instantiates the event handlers, it must have the correct classes included. In this example, you simply included every handler class that you would need. For larger applications, this approach would be wasteful, because you might be including a hundred classes and only ever use one of them.

One way to rectify this issue is to mark certain handlers as being available by default, with the rest being made available on a per-user basis. Each user stored in the database would have (among other properties) a field containing a list of handlers available to that user. This information could be used to automatically include the relevant handlers in the dispatcher at the same time as the relevant buttons are being added to the user interface.

Finally, your various events may be fired by different entities, so you may want to consider adding functionality to determine what entity is invoking that event, and return an appropriate response based largely on that determination. This may be useful, for example, should you want to return some piece of data either in machine-readable XML format or in human-readable HTML, depending on which entity has invoked the event.

One design pattern that may interest you is the reactor pattern. This deals with multisource, enterprise-level event handling, and is definitely worth a look if you are serious about using events. Remember that a design pattern may exist that fits your requirements. The reactor pattern is very similar to what you have done in this chapter, but has added capabilities that enable your handlers to easily differentiate between event sources. For more information on this, see Pattern-Oriented Software Architecture, Volume 2, Patterns for Concurrent and Networked Objects by Douglas C. Schmidt, Michael Stal, Hans Rohnert, and Frank Buschmann (Wiley, 2000).

## Summary

This chapter has served as an introduction to event-driven programming in PHP. You should now have a good idea of how the event-driven paradigm can be implemented using simple OOP.

Creating an event-driven application is a problem-specific business, and much attention should be paid to the environment in which the intended application will run. Event-driven programming has applications in many areas of computing, but good candidates are often those programs that have graphical user interfaces.

Finally, through the discussion in this chapter, you have seen how the power and elegance inherent in OOP can be effectively complemented by designing applications using an event-driven programming paradigm.

Chapter 9 takes a look at implementing an effective logging and debugging mechanism in your application, to aid you and your development team during both the development and the testing phases of your project.

## Logging and Debugging

In every application you build, robust logging and debugging mechanisms can save you hours of effort trying to track down problems that might occur.

Logs can be used to help you analyze historical usage patterns that can’t be obtained through the Web server log, such as server load, specific SQL statements that were executed, or application-specific messages that wouldn’t otherwise be captured.

A debugging mechanism enables you to examine the values of variables, see which conditional loops are being executed, or otherwise determine the state of the application at run-time, without having to litter your code with `print` statements that need to be deleted before you deploy. After you’ve worked through the code in this chapter, you’ll have a set of classes that should be a part of every project you work on.

## Creating a Logging Mechanism

The primary purpose of logging is to enable you to see what the application was doing, or how it was performing, at some time in the past. A properly written log will enable you to do a historical analysis of system behavior to determine whether changes must be made.

## Simple File Logging

The easiest way to handle logging is to write the information to a file. Usually, the user ID from which your Web server process is running does not have the access needed to write to the file system, except for a temporary directory (/tmp on most UNIX systems), which isn’t necessarily the best location in which to keep important application log files. To allow the Web server user to be able to write to a file, create a dedicated directory in which to store your log files:

Create a folder above the document root of your application called logs and ensure that the Web server user has write permissions to this folder. (Use chmod 744 and chown nobody, or the name of your Apache user, on UNIX systems. Windows users should consult the relevant documentation for your version of Windows).

```
/www
|
+-----.mysite
|
+----htdocs
|     |
|     +----images
|     |
|     +----css
|
+----.logs
```

## Example File System Layout

To write to a file in PHP, use fopen() to get a file handle and specify that you want to open the file for writing. Use fwrite() to write data to the file, and fclose() to close the file. The following code defines and then demonstrates a simple method called logMessage(), which uses these basic methods to write to a predefined log file:

```php
<?php
function logMessage($message) {
    $LOGDIR = '/www/mysite/logs/'; //chmod 744 and chown nobody
    $LogFile = $LOGDIR . 'mysite.log';
    $hFile = fopen($LogFile, 'a+'); //open for appending, create
                                     //the file if it doesn't exist

    if (! is_resource($hFile)) {
        printf("Unable to open %s for writing. Check file permissions.", $LogFile);
        return false;
    }

    fwrite($hFile, $message);
    fclose($hFile);

    return true;
}

logMessage("Hello, log!\n");
?>
```

If you run this code, and you have all the permissions correctly set on the $LOGDIR directory, you should see the message Hello, log! in the mysite.log file. For the most rudimentary needs, this function might be sufficient; but for a real application, you’ll want to track more than just the message. The log should be a “machine-parseable” file, meaning that you should be able to process the log data using a separate application that analyzes the information held within it. The log should include the date and time of each message, some sense of the severity or importance of the message, and some remark about which module of the application generated the message.

## The Logger Class

The class in the following code sample provides an OO mechanism for generating a more detailed log file than that created using the code in the previous section. Create a file called class.Logger.php. This file will contain the Logger class, which enables you to write information in a tab-delimited format to a text file on the server, tracking the timestamp, the log level (which is the severity of the message), the message itself, and an optional module name. The module name can be any string that helps to identify which part of the application generated the message. The code for the Logger class is as follows:

```php
<?php
class Logger {
    private $hLogFile;
    private $logLevel;

    // Log Levels. The higher the number, the less severe the message
    // Gaps are left in the numbering to allow for other levels
    // to be added later
    const DEBUG = 100;
    const INFO = 75;
    const NOTICE = 50;
    const WARNING = 25;
    const ERROR = 10;
    const CRITICAL = 5;

    // Note: private constructor. Class uses the singleton pattern
    private function __construct() {
        // This is pseudo code that fetches a hash of configuration information
        // Implementation of this is left to the reader, but should hopefully
        // be quite straightforward.
        $cfg = Config::getConfig();

        /* If the config establishes a level, use that level,
        otherwise, default to INFO */
        $this->logLevel = isset($cfg['LOGGER_LEVEL']) ?
            $cfg['LOGGER_LEVEL'] :
            Logger::INFO;

        // We must specify a log file in the config
        if (! isset($cfg['LOGGER_FILE']) && strlen($cfg['LOGGER_FILE'])) {
            throw new Exception('No log file path was specified ' .
                'in the system configuration.');
        }
    }
}
?>
```

