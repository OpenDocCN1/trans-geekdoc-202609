
![image](images/7b.jpg)
Use File Explorer to navigate to your web server’s `/htdocs` directory and see the file created by the PHP script

![image](images/pg129_2.jpg)

![image](images/8b.jpg)
Open the file to see the text written by the PHP script

![image](images/pg129_3.jpg)

![image](images/snake.jpg)

The folder where a file is to be written must have write permission.

![image](images/hot.jpg)

You can run this example repeatedly and each time it will erase the content then write it again.

## Appending text

![image](images/pg130_1.jpg)

Once a “filestream” object has been created specifying an append mode, a text file can be opened to add text at its end. Text can be appended to the file by specifying the filestream and a file name to the PHP `fwrite()` function. The process is identical to writing a file, except that the file pointer is positioned at the end of existing content before the text is written into the file:

![image](images/1b.jpg)
Begin a PHP script with a statement to assign text, including non-printing characters for formatting

```
<?php
$info \= “\\r\\n\\r\\n\\tThe Ballad of Reading Gaol” ;
$info .= “\\r\\n\\t\\t\\tOscar Wilde 1898” ;
```

![image](images/commonb.jpg)

`append.php`

![image](images/2b.jpg)
Next, assign a name for the file to be written into

```
$filename \= ‘poem.txt’ ;
```

![image](images/3b.jpg)
Attempt to open the plain text file for appending, or exit the script upon failure

```
$filestream \= fopen( $filename , ‘a’ )
or die( ‘Unable to open file!’ ) ;
```

![image](images/4b.jpg)
Write the text and display a confirmation of how many bytes have been appended in total

```
$num \= fwrite( $filestream , $info ) ;
if( $num )
{
echo “$num bytes appended to $filename” ;
}
```

![image](images/5b.jpg)
Now, remember to close the filestream

```
fclose( $filestream ) ;
```

![image](images/6b.jpg)
Save the document in your web server’s `/htdocs` directory as `append.php` then open the page via HTTP to see confirmation that the text has been appended to the file

![image](images/pg130_2.jpg)

![image](images/forget.jpg)

Remember that non-printing characters must be enclosed in double quotes for interpretation.

![image](images/7b.jpg)
Navigate to your web server’s `/htdocs` directory and open the file to see the text appended by the PHP script

![image](images/pg131_1.jpg)

## Overwriting text

It is important to recognize that when you write to an existing file in write mode it will overwrite any existing content:

![image](images/1b.jpg)
Begin a PHP script by attempting to open an existing text file for writing, or exit the script upon failure

```
<?php
$filestream \= fopen( ‘poem.txt’ , ‘w’ )
or die( ‘Unable to open file!’ ) ;
```

![image](images/commonb.jpg)

`overwrite.php`

![image](images/2b.jpg)
Upon success, write new text into the file

```
fwrite( $filestream , ‘Overwritten!’ ) ;
```

![image](images/3b.jpg)
Now, remember to close the filestream

```
fclose( $filestream ) ;
```

![image](images/4b.jpg)
Save the document in your web server’s `/htdocs` directory as `overwrite.php` then open the page via HTTP and reopen the text file to see its contents overwritten

![image](images/pg131_2.jpg)

![image](images/snake.jpg)

Be careful when writing to files as it is easy to accidentally overwrite.

## Handling errors

![image](images/pg132_1.jpg)

You can anticipate possible errors and terminate a running script when they occur using the `die()` function or the `exit()` function. Without this contingency, the default PHP error handler provides a useful but unsightly message when an error occurs. For example, `fopen( ‘nonsuch.txt’ , ‘r’ )` to open a non-existing file:

![image](images/pg132_2.jpg)

![image](images/hot.jpg)

The `die()` and `exit()` functions perform identical operations in PHP, but their terminology can have different appeals. For some, `die()` possibly seems more appropriate to quit when an error is detected, and `exit()` may seem more suitable to quit in other scenarios.

It is not always desirable to terminate a script when an error occurs, but you can create a custom error handler to provide a more user-friendly message than that provided by the default PHP error handler. A custom error handler is simply a function with this syntax:

`function error_handler( $level , $message , $file , $line , $context )`

Only the first two parameters are required, the rest are optional. The first of these is a numerical value, representing a constant, indicating the severity of the error that has occurred:

| **Level** || **Constant** || **Description** |
| --- | --- | --- |
| **2** || `E_WARNING` || Non-fatal runtime error |
| **8** || `E_NOTICE` || Non-fatal possible error |
| **256** || `E_USER_ERROR` || Fatal user-generated error |
| **512** || `E_USER_WARNING` || Non-fatal user-generated error |

![image](images/hot.jpg)

The basic error levels are listed in this table but the PHP manual lists many more (`[php.net/](http://www.php.net/)` manual).

A custom error handler function is nominated to handle errors by specifying its function name as the argument to the built-in PHP `set_error_handler()` function.

The error handler is called when an error occurs, or can be called explicitly using the `trigger_error()` function to specify an error message as its argument.

![image](images/1b.jpg)
Begin a PHP script by defining a custom error handler function to report an error level and error message

```
<?php
function error_handler( $level , $message )
{
switch( $level )
{
case 2 : $str \= ‘Warning!’ ; break ;
case 8 : $str \= ‘Notice!’ ; break ;
default : $str \= ‘Error!’ ;
}
echo “<b>$str</b><br>$message<hr>”;
}
```

![image](images/commonb.jpg)

`error.php`

![image](images/2b.jpg)
Next, nominate the function to handle errors

```
set_error_handler( ‘error_handler’ ) ;
```

![image](images/3b.jpg)
Now, for some mischief – attempt to access an uninitialized variable and try to open a non-existing file

```
echo( $var ) ;
$file \= fopen( ‘nonsuch.txt’ , ‘r’ ) ;
```

![image](images/4b.jpg)
Explicitly trigger the custom error handler

```
$number \= 2 ;
if( $number \>= 1 )
{
trigger_error( ‘Value of number must be 1 or less’ ) ;
}
```

![image](images/5b.jpg)
Save the document in your web server’s `/htdocs` directory as `error.php` then open the page via HTTP to see the error levels and appropriate messages

![image](images/pg133_1.jpg)

![image](images/forget.jpg)

Notice that the script continues after reporting each error; it does not as terminate on error.

## Catching exceptions

![image](images/pg134_1.jpg)

We can choose how a script should proceed when a specific error condition occurs. This error condition is called an “exception”. When an exception occurs it is said to be “thrown”, and code handling the exception is said to be its “catch”. If an exception is not caught, PHP will treat it as a fatal error and issue an unsightly “Uncaught Exception” message – something like this:

![image](images/pg134_2.jpg)

![image](images/snake.jpg)

Each `try` block must have an associated `catch` block, otherwise a fatal Uncaught Exception error will occur.

The key to handling exceptions is to anticipate the error by trying to execute an action within a try code block, and determine how the script should proceed in an associated catch code block. The catching block is passed an `Exception` class object that has `getMessage()`, `getFile()` and `getLine()` methods to retrieve details.

An instance of the `Exception` class can be created using the `new` keyword, and can be explicitly thrown using the `throw` keyword.

A custom exception handler can also be created as a derived class of the `Exception` class, to provide your own custom methods:

![image](images/1b.jpg)
Begin a PHP script by defining a function that will throw an exception when a conditional test fails

```
<?php
function check_size( $num )
{
if( $num < 10 )
```
