
is a perfectly valid PHP statement. It contains no syntax errors.

However, this statement might generate a runtime error. If you execute this statement and filename.php does not exist, or the user whom the script runs as is denied read permission, you will get an error resembling this:

```
Fatal error: require(): Failed opening required 'filename.php' (include_path=':../usr/local/php/lib/php') in /var/www/pwmd5e/chapter26/error.php on line 2
```

Although nothing resembling this with the code here, because it relies on a file that might not exist at different times when the code is run, it can generate a runtime error.

The three statements are all valid PHP. Unfortunately, in combination, they attempt to do the impossible—divide by zero:

```
$i = 10;
$j = 0;
$k = $i/$j;
```

This code snippet generates the following:

```
Warning: Division by zero in /var/www/pwmd5e/chapter26/error.php on line 4
```

This makes it very easy to correct. Few people would try to write code that attempted to divide by zero on purpose, neglecting to check user input results in this type of error.

The following code generates the same error but might be much harder to isolate and correct because it happens some of the time:

```
$i = 10;
$k = $i/$_REQUEST['input'];
```

This is one of many runtime errors that you might see while testing your code.

Common causes of runtime errors include the following:

- Calls to functions that do not exist
- Reading or writing files
- Interaction with MySQL or other databases
- Connections to network services
- Failure to check input data

We briefly discuss each of these causes in the following sections:

# Calls to Functions That Do Not Exist

Accidentally calling functions that do not exist is easy. The built-in functions are often inconsistently named. For example, strip_tags() has an underscore, whereas stripsslashes() does not. This sort of mixup is very easy to make.

# Chapter 26 Debugging and Logging

It is also easy to call one of your own functions that does not exist in the current script but might exist elsewhere. If your code contains a call to a nonexistent function, as as

nonexistent_function();

or

mispeled_function();

you will see an error message similar to:

```
Fatal error: Uncaught Error: Call to undefined nonexistent_function() in /var/www/pmd5e/chapter26/error.php:2 Stack trace: #0 [main] thrown in /var/www/pmd5e/chapter26/error.php on line 2
```

Similarly, if you call a function that exists but call with an incorrect number of parameters, you will receive a warning.

The function substr() requires two strings: a haystack to search and a needle to find. instead you can call it using

```
strstr();
```

you will get the following warning:

```
Warning: strstr() expects at least 2 parameters, 0 given in /var/www/pmd5e/chapter26/error.php on line 2
```

That same statement within the following script is equals wrong:

```php
<?php
if($var == 4) {
  strstr();
}
?>
```

Except in the possibly rare case the variable $var has the value 4, the call to strstr() will not occur, and no warning will be issued. The PHP interpreter does not waste time parsing sections of your code that are not needed for execution of the script. You need to be sure that you can test everything!

Calling functions incorrectly is easy to do, but because the resulting error messages identifies the exact line and call that are causing the problem, they equally easy to fix. They are difficult to find if your testing is poor and does not test conditionally executed code. When you test, one of the goals is to execute every line of code at least once. Another goal is to test all the boundary conditions and classes of input.

# Reading or Writing Files

Although anything can go wrong at some point in your program's useful life, problems are more likely than others. Because errors accessing files are likely enough to occur, you need to handle them gracefully. Hard drives fail or fill up, and human error results in directory permissions changing.

Functions as fopen() are likely to fail occasionally generally have a return value to signal that an error occurred. For fopen(), a return value of false indicates failure.

For functions that provide notification, you need to carefully check the return value of every call and act on failures.

# Interaction with MySQL or Other Databases

Connecting to and using MySQL can generate many errors. The function mysqli_connect() can also generate one of the following errors:

- **Warning**: mysqli_connect() [function.mysqli-connect]: Can't connect to MySQL server on 'localhost' (10061)
- **Warning**: mysqli_connect() [function.mysqli-connect]: Unknown MySQL Host 'hostname' (11001)
- **Warning**: mysqli_connect() [function.mysqli-connect]: Access denied for user: 'username@localhost' (Using password: YES)

As you would probably, mysqli_connect() provides a return value of false when an error occurs. This means that you can easily trap and handle these types of common errors.

If do not stop the regular execution of your script and handle these errors, your script will attempt to continue interacting with the database. Trying to run queries and get results without a valid MySQL.
