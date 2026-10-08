# Chapter 7 Error and Exception Handling

+   - getFile()—Returns the full path to the code file where the exception was raised
- getLine()—Returns the line number in the code file where the exception was raised
- getTrace()—Returns an array containing a backtrack where the exception was raised
- getTraceAsString()—Returns the same information as getTrace, formatted as a string
- getPrevious()—Returns the previous exception (from the third parameter to the constructor)
- _toString()—Allows you to echo an Exception object, giving all the information from the above

You can have used the first four of these methods in Listing 7.1. You could obtain the same information (plus the backtrack) by executing
echo $e;

A backtrack shows which functions were executing at the time the exception was raised.

# User-Defined Exceptions

Instead of instantiating and passing an instance of the base Exception class, you can pass any other object by you. In most cases, you will extend the Exception class to create your own exception classes.

You can pass any other object with your throw clause. You may occasionally want to do this if you are having problems with one particular object and want to pass it through for debugging purposes.

Most of the time, you will need to extend the base Exception class. The PHP manual provides code that shows the skeleton of the Exception class. This code, taken from http://php.net/manual/en/language.exceptions.extending.php, is reproduced in Listing 7.2. Note that this is not the only code but represents what you can expect to inherit.

Listing 7.2 Exception class—This Is What You Can Expect to Inherit

```
<?php
class Exception
{
    protected $message = 'Unknown exception'; // exception message
    private $string; // __toString cache
    protected $code = 0; // user defined exception code
    protected $file; // source filename of exception
    protected $line; // source line of exception
    private $trace; // backtrack
    private $previous; // previous exception if nested
    exception
```