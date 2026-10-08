
# Listing 7.1 basic_exception.php—Throwing and Catching an Exception

```php
<?php
try {
    new Exception("A terrible error has occurred", 42);
}
catch (Exception $e) {
    echo "Exception: " . $e->getCode() . ": " . $e->getMessage() . "<br />";
    echo "in " . $e->getFile() . " on line " . $e->getLine() . "<br />";
}
?>
```

In Listing 7.1, you can see that we used a number of methods of the Exception class, which we discuss shortly. The result of running this code is shown in Figure 7.1.

![](img/654520c37415debd4290b9b4aa2c03f2_232_0.png)

In the sample code, you can see that we raise an exception of class Exception. This built-in class has methods you can use in the catch block to report a useful error message.

# The Exception Class

PHP has a built-in class Exception. The constructor takes three optional parameters, as we discussed previously: an error message, an error code, and a previous exception.

In addition to the constructor, this class comes with the following built-in methods:

- getCode()—Returns the code passed to the constructor
- getMessage()—Returns the message passed to the constructor
- getFile()—Returns the full path to the code file where the exception was raised
- getLine()—Returns the line number in the code file where the exception was raised
- getTrace()—Returns an array containing a backtrack where the exception was raised
- getTraceAsString()—Returns the same information as getTrace, formatted as a string
- getPrevious()—Returns the previous exception (from the third parameter to the constructor)
- __toString()—Allows you to echo an Exception object, giving all the information from the above

You can have used the first four of these methods in Listing 7.1. You could obtain the same information (plus the backtrack) by executing
`echo $e;`

A backtrack shows which functions were executing at the time the exception was raised.

# User-Defined Exceptions

Instead of instantiating and passing an instance of the base Exception class, you can pass any other object by you. In most cases, you will extend the Exception class to create your own exception classes.

You can pass any other object with your throw clause. You may occasionally want to do this if you are having problems with one particular object and want to pass it through for debugging purposes.

Most of the time, you will need to extend the base class. The PHP manual provides code that shows the skeleton of the Exception class. This code, taken from http://php.net/manual/en/exceptions.php, is reproduced in Listing 7.2. Note that this is not the only code but represents what you can inherit.

# Listing 7.2 Exception class—This Is What You Can Inherit

```php
<?php
class Exception
{
    protected $message = 'Unknown exception'; // exception message
    private $string; //
    protected $code = 0; // user defined code
    protected $file; // source filename
    protected $line; // source line
    private $trace; // backtrack
    private $previous; // previous exception if nested

    public function __construct($message = null, $code = 0, Exception $previous = null);

    final function __clone(); // Prohibits cloning of exceptions.
    final function getMessage(); // message of exception
    final function getCode(); // code of exception
    final function getFile(); // source filename
    final function getLine(); // source line
    final function getTrace(); // array of backtrack
    final function getPrevious(); // previous exception
    final function getTraceAsString(); // formatted string of trace

    /* Override */
    public function __toString(); // formatted string for display
}
?>
```

The main reason we are looking at this class is to note that most of the public methods are final: that means you cannot override them. You can create your own subclass, but you cannot change the behavior of basic methods. Note that you can override `toString()` so you can change the way the exception is displayed. You can also add your own methods.

An example of a user-defined class is shown in Listing 7.3.

# Listing 7.3 user_defined_exception.php—An Example of a User-Defined Class

```php
<?php

class myException extends Exception
{
    function __toString()
    {
        return "Exception " . $this->getCode() .
        ": " . $this->getMessage() . "<br />"
        ."in " . $this->getFile() . " on line " . $this->getLine() . "<br />";
    }
}

try {
    throw new myException("A terrible error has occurred", 42);
}
catch (myException $m) {
    echo $m;
}
?>
```

In this code, you declare a new exception class, myException, that extends the basic Exception class. The difference between this class and the Exception class is that you override the `toString()` method to provide a "pretty" printing of the exception. The output from executing this code is shown in Figure 7.2. As you can see, it's similar to the previous example.

![](img/654520c37415debd4290b9b4aa2c03f2_235_0.png)

Figure 7.2 The Exception class provides exceptions with "pretty printing"

This example is fairly simple. In the next section, we look at how to create different exceptions to deal with different categories of error.

# Exceptions in Bob’s Auto Parts

Chapter 2, "Storing and Retrieving Data," described how you could store Bob's order data in a flat file. You know that I/O (in fact, any kind of I/O) is one area in programs where errors often occur. This is a good place to apply exception handling.

Looking back at the original code, you can see that three things are likely to go wrong with writing to the file: the file cannot be opened, or a lock cannot be obtained, or the file cannot be written to. We created an exception class for each of these possibilities. The code for each is shown in Listing 7.4.

# Listing 7.4 file_exceptions.php—I/O-Related Exceptions

```php
<?php
class fileOpenException extends Exception
{
    function __toString() {
        return "fileOpenException " . $this->getCode()
        ": " . $this->getMessage() . "<br />" in ""
        . $this->getFile() . " on line " . $this->getLine()
        . "<br />";
    }
}
class fileWriteException extends Exception
{
    function __toString() {
        return "fileWriteException " . $this->getCode()
        ": " . $this->getMessage() . "<br />" in ""
        . $this->getFile() . " on line " . $this->getLine()
        . "<br />";
    }
}
class fileLockException extends Exception
{
    function __toString() {
        return "fileLockException " . $this->getCode()
        ": " . $this->getMessage() . "<br />" in ""
        . $this->getFile() . " on line " . $this->getLine()
        . "<br />";
    }
}
?>
```

These Exception subclasses do not do anything particularly interesting. In fact, for the purpose of this application, you could leave them as empty subclasses or use the provided Exception class. We have provided a `__toString()` method for each of the subclasses that explains what type of exception has occurred.

We rewrote the `processor.php` file from Chapter 2 to incorporate the use of exceptions. The new version is shown in Listing 7.5.

# Listing 7.5 processor.php—Bob's Order-Processing Script with Exception Included

```php
<?php

require_once("file_exceptions.php");

// create short variable names
$tireqty = (int) $_POST['tireqty'];
$oilqty = (int) $_POST['oilqty'];
$sparkqty = (int) $_POST['sparkqty'];
$address = preg_replace('/[tR]/', '', $_POST['address']);
$document_root = $_SERVER['DOCUMENT_ROOT'];
$date = date('H:i, JS F Y');

<!DOCTYPE html>
<html>
<head>
<title>Bob's Auto Parts - Order Results</title>
</head>
<body>
<h1>Bob's Auto Parts</h1>
<h2>Order Results</h2>
<?php
echo "<p>Order processed at " . date('H:i, JS F Y') . "</p>";
echo "<p>Your order is as follows: </p>";

$totalqty = 0;
$totalamount = 0.00;

define('TIREPRICE', 100);
define('OILPRICE', 10);
define('SPARKPRICe', 4);

$totalqty = $tireqty + $oilqty + $sparkqty;
echo "<p>Items ordered: " . $totalqty . "<br> />";

if ($totalqty == 0) {
    echo "You did not order anything on the previous page!<br /> ";
} else {
    if ($tireqty > 0) {
        echo htmlspecialchars($tireqty).' tires<br> />";
    }
    if ($oilqty > 0) {
        echo htmlspecialchars($oilqty).'bottles of oil<br> />";
    }
    if ($sparkqty > 0) {
        echo htmlspecialchars($sparkqty).'spark plugs<br> />";
    }
}
?>
</body>
</html>
```
