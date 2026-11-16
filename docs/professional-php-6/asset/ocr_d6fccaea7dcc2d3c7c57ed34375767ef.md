```
throw new Exception("The specified backend $name was not " .
    'registered with Logger.');
}

} else {
    //we must be adding
    $backEnds[$name] = $objBack;
}
}
```

```
public static function levelToString($logLevel) {
    switch ($logLevel) {
        case Logger::DEBUG:
            return 'Logger::DEBUG';
            break;
        case Logger::INFO:
            return 'Logger::INFO';
            break;
        case Logger::NOTICE:
            return 'Logger::NOTICE';
            break;
        case Logger::WARNING:
            return 'Logger::WARNING';
            break;
        case Logger::ERROR:
            return 'Logger::ERROR';
            break;
        case Logger::CRITICAL:
            return 'Logger::CRITICAL';
            break;
        default:
            return 'unknown';
    }
}
?>
```

In the preceding code, Logger pulls in the file that defines an abstract class called LoggerBackend, which serves as the base class for the classes that will do the actual work of writing to a given logging mechanism. Logger's constructor is now empty, but is still declared to be private to prevent its instantiation outside the getInstance() method.

The new static method, register(), is responsible for instantiating a LoggingBackend object based on the scheme part of the URL specified in the second parameter. To do so, it makes a call to parse_url() to determine the scheme. If no scheme was present in the URL, register() throws an exception. If the scheme is present, an attempt is made to include_once a file called Logger/class.[scheme]LoggerBackend.php, and the class contained therein is instantiated by passing the $urlData array. If the file isn't found, the code throws an exception. include_once is used here instead of require_once because if you use require_once and the file isn't found, a fatal exception is thrown, and application execution terminates.