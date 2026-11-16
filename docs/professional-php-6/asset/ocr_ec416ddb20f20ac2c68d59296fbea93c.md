separate application that analyzes the information held within it. The log should include the date and time of each message, some sense of the severity or importance of the message, and some remark about which module of the application generated the message.

# # The Logger Class

The class in the following code sample provides an OO mechanism for generating a more detailed log file than that created using the code in the previous section. Create a file called class.Logger.php. This file will contain the Logger class, which enables you to write information in a tab-delimited format to a text file on the server, tracking the timestamp, the log level (which is the severity of the message), the message itself, and an optional module name. The module name can be any string that helps to identify which part of the application generated the message. The code for the Logger class is as follows:

```
```php
<?php
class Logger {
    private $hLogFile;
    private $logLevel;

    //Log Levels. The higher the number, the less severe the message
    //Gaps are left in the numbering to allow for other levels
    //to be added later
    const DEBUG = 100;
    const INFO = 75;
    const NOTICE = 50;
    const WARNING = 25;
    const ERROR = 10;
    const CRITICAL = 5;

    //Note: private constructor. Class uses the singleton pattern
    private function __construct() {
        //This is pseudo code that fetches a hash of configuration information
        //Implementation of this is left to the reader, but should hopefully
        //be quite straightforward.
        $cfg = Config::getConfig();

        /* If the config establishes a level, use that level,
        otherwise, default to INFO */
        $this->>logLevel = isset($cfg['LOGGER_LEVEL']) ?
            $cfg['LOGGER_LEVEL'] :
            Logger::INFO;

        //We must specify a log file in the config
        if( ! isset($cfg['LOGGER_FILE']) & strlen($cfg['LOGGER_FILE'])) {
            throw new Exception('No log file path was specified ' .
                'in the system configuration.');
        }
    }
}
```
```