
3\. expiration: The date when the cookie will expire and be deleted. If you do not set this expiration date, then it will be treated as a session cookie and be removed when the browser is restarted.

In this example we will be creating a cookie that stores the user's last visit to measure how often people return to visit our webpage. We want to ignore people that take longer than two months to return to the site, so we will set the cookie's expiration date to two months in the future!

PHP Code:

```php
//Calculate 60 days in the future
//seconds * minutes * hours * days + current time
$inTwoMonths = 60 * 60 * 24 * 60 + time();
setcookie(lastVisit, date("G:i - m/d/y"), $inTwoMonths);
```

Don't worry if you can't follow the somewhat involved date calculations in this example. The important part is that you know how to set a cookie, by specifying the three important arguments: name, value and expiration date.

## Retrieving a Cookie

If the cookie has not expired yet, let's retrieve it from the user's PC using the `$_COOKIE` associative array. The name of your stored cookie is the key and will let you retrieve your stored cookie value!

PHP Code:

```php
if(isset($_COOKIE['lastVisit']))
$visit = $_COOKIE['lastVisit'];
else
echo "You've got some stale cookies!";
echo "Your last visit was - ". $visit;
```

This handy script first uses the `isset` function to be sure that our "lastVisit" cookie still exists on the user's PC, if it does, then the user's last visit is displayed. If the user visited our site on may 14, 2015 it might look something like this:

Display:

Your last visit was - 10:41- 05/14/15

# Chapter 12: WORKING WITH FILES

## Opening and closing files

In PHP, the function `fopen()` is normally used to open files. It requires two arguments that state the file name and the mode in which it has to operate. In the event the opening of a file is not successful the function `fopen()` returns the value of false, otherwise it returns a file pointer to read or write to that particular file.

File modes can be specified as stated below

| Filemode | Purpose |
| --- | --- |
| r | Opens the file for reading purposes only. Places the file pointer at the beginning of the file. |
| r+ | Opens the file for reading and writing. Places the file pointer at the beginning of the file. |
| w | Opens the file for writing purposes only. Places the file pointer at the beginning of the file. and truncates the file to zero length. If files does not exist then it attempts to create a file. |
| w+ | Opens the file for reading and writing only. Places the file pointer at the beginning of the file. and truncates the file to zero length. If files does not exist then it attempts to create a file. |
| a | Opens the file for writing purposes only. Places the file pointer at the end of the file. If files does not exist then it attempts to create a file. |
| a+ | Opens the file for reading and writing only. Places the file pointer at the end of the file. If files does not exist then it attempts to create a file. |

## Reading a file

Once a file is opened using `fopen()` function it can be read with a function called `fread()`. This function requires two arguments. These must be the file pointer and the length of the file expressed in bytes.

The files length can be found using the function `filesize()` which takes the file name as its argument and returns the size of the file expressed in bytes.

So here are the steps required to read a file with PHP.

* Open a file using `fopen()` function.
* Get the file's length using `filesize()` function.
* Read the file's content using `fread()` function.
* Close the file with `fclose()` function.

The following example assigns the content of a text file to a variable then displays those contents on the web page.

```php
$filename = "example.txt";
$file = fopen( $filename, "r" );
if( $file == false )
{
    echo ( "Error occurred in opening file" );
    exit();
}
$filesize = filesize( $filename );
$filetext = fread( $file, $filesize );
fclose( $file );
echo ( "File size is : $filesize bytes" );
echo ( "<pre>$filetext</pre>" );
```

## Writing a file

A new file can be written or text can be appended to an existing file using the PHP `fwrite()` function. This function requires two arguments specifying a file pointer and the string of data that is to be written. Optionally a third integer argument can be included to specify the length of the data to write. If the third argument is included, writing would will stop after the specified length has been reached.

The following example creates a new text file then writes a short text heading inside it. After closing this file its existence is confirmed using `file_exist()` function which takes file name as an argument

```php
$filename = "/home/user/guest/newfile.txt";
$file = fopen( $filename, "w" );
if( $file == false )
{
    echo ( "Error occurred in opening new file" );
    exit();
}
fwrite( $file, "This is a simple file\n" );
fclose( $file );
```

```php
$filename = "newfile.txt";
$file = fopen( $filename, "r" );
if( $file == false )
{
    echo ( "Error occured in opening file" );
    exit();
}
$filesize = filesize( $filename );
$filetext = fread( $file, $filesize );
fclose( $file );
echo ( "File size is: $filesize bytes" );
echo ( "$filetext" );
echo("file name: $filename");
```

# Chapter 13: OBJECT ORIENTED PHP

Our universe made of different objects like moon, earth, mars etc. Similarly we can imagine our car made of different objects like wheel, steering, gear etc. Same way there is object oriented programming concepts which assume everything as an object and implement a software using different objects.

## Object oriented concepts

Class − This is a programmer-defined data type, which includes local functions as well as local data. You can think of a class as a template for making many instances of the same kind (or class) of object.

Object − An individual instance of the data structure defined by a class. You define a class once and then make many objects that belong to it. Objects are also known as instance.

Inheritance − When a class is defined by inheriting existing function of a parent class then it is called inheritance. Here child class will inherit all or few member functions and variables of a parent class.

Parent class − A class that is inherited from by another class. This is also called a base class or super class.

Child Class − A class that inherits from another class. This is also called a subclass or derived class.

Polymorphism − This is an object oriented concept where same function can be used for different purposes. For example function name will remain same but it make take different number of arguments and can do different task.

Overloading − a type of polymorphism in which some or all of operators have different implementations depending on the types of their arguments. Similarly functions can also be overloaded with different implementation.

Data Abstraction − Any representation of data in which the implementation details are hidden.

Encapsulation − refers to a concept where we encapsulate all the data and member functions together to form an object.

Constructor − refers to a special type of function which will be called automatically whenever there is an object formation from a class.

## Defining PHP classes

The general form for defining a new class in PHP is as follows −

```php
class phpClass{
    var $var1;
    var $var2 = "constant string";
    function myfunc ($arg1, $arg2) {
        [...]
    }
    [...]
}
```
