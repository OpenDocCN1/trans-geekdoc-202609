If the specified LoggerBackend class is properly instantiated, the new instance is passed, along with the canonical name specified in the first parameter to register() to the private function manageBackends(). This function exists because all public methods of Logger are now static. As a result, the class can't use any member variables to store the instantiated back-end objects.
manageBackends() contains a static variable that takes the place of a class member. If the function has two parameters, it stores the LoggerBackend object in the $backEnds array using the $name parameter as a key. If only one parameter is specified (the $name parameter), manageBackends() returns the LoggerBackend object stored in $name (if one exists).

The new getInstance() method no longer returns a Logger object, but instead returns an instantiated LoggerBackend. It does so by calling manageBackends() with only one parameter, the canonical name of the particular log requested. If the named log wasn't previously registered, or was unable to be instantiated during register(), manageBackends() throws an exception that will bubble up to getInstance().

# **The LoggerBackend Class**

The manageBackends(), register(), and getInstance() methods all interact with LoggerBackend objects. This class provides a concrete constructor (a construct that exists and is callable) and an abstract method called logMessage(), which you probably remember from the original Logger class. The latter method is unchanged in number and type of parameters from the code presented previously.
However, in the LoggerBackend class, the logMessage() method is abstract—no actual function body exists, just the declaration of a function that must be implemented by classes that inherit from LoggerBackend. The constructor of the class takes the array output from parse_url() and stores it in a protected member variable. No other methods are defined by the LoggerBackend class.

Save the following as Logger/class.LoggerBackend.php:

```
```php
<?php
abstract class LoggerBackend {
	protected $urlData;

	public function __construct($urlData) {
		$this->urlData = $urlData;
	}

	abstract function logMessage($message, $logLevel = Logger::INFO, $module);
}
?>
```
```

The class itself should be declared abstract because it contains one abstract method and because there is no practical use for an instance of LoggerBackend. Only the subclasses of LoggerBackend will do any real work.

# **Subclassing LoggerBackend**

In order for the new and improved Logger class to be able to do anything, you'll need to create at least one subclass of LoggerBackend. Because you already have some code that will log information to a file, this will be the easiest LoggerBackend subclass to create first.