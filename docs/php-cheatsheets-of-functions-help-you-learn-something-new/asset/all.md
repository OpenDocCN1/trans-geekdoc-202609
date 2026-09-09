## PHPCheatsheets of Functions

Get to Know Functions and Constants Used for PHP DateTime Format…

 

By: Daniel Billotte

PHP date and time can be formatted in multiple different ways in your PHP code. You might need a Unix timestamp or GMT date, a DateTime object or an ISO date. Therefore, it is important to learn functions that are applied to manipulate PHP DateTime format.

PHP date formatting is not that hard, but you still have to have specific knowledge and expertise. Fetching the date and time from the server you are using is only the first step. Don't let a wrong time zone or PHP date format throw you off your feet!

| 

## Contents

 |
| --- |
| [DateTime Functions](#part0002.xhtml#_DateTime_Functions) || 4 |
| [Error Functions](#part0002.xhtml#_Error_Functions) || 10 |
| [File Function](#part0002.xhtml#_File_Function) || 17 |
| [Filter](#part0002.xhtml#_Filter) || 26 |
| [Math Functions](#part0003.xhtml#_Math_Functions) || 32 |
| [Mail Function](#part0003.xhtml#_Mail_Function) || 38 |
| [Miscellaneous Functions](#part0004.xhtml#_Miscellaneous_Functions) || 42 |
| [PHP Date Format](#part0004.xhtml#_PHP_Date_Format) || 47 |
| [String Functions](#part0004.xhtml#_String_Functions) || 53 |
| [Array Functions](#part0004.xhtml#_PHP_Array_Functions) || 61 |
| [Directory Functions](#part0004.xhtml#_Directory_Functions) || 68 |
|  ||  |

 

 

 Copyright 2019 by Daniel Billotte- All rights reserved.

 

This is a legally binding declaration that is considered both valid and fair by both the Committee of Publishers Association.

# DateTime Functions

#### Contents

1. PHP DateTime Format: Main Tips

2. Runtime Configuration

3. Time And Date Functions

4. List of Predefined Constants

5. PHP DateTime Format: Summary

 

## PHP DateTime Format: Main Tips

*   Time and date PHP functions allow you to get date and time from the server you're using.
*   These functions are inbuilt into the PHP core.
*   Keep in mind that these functions are dependant on your server's locale setting.

## Runtime Configuration

When using these functions to set PHP DateTime format, remember that how they behave will be affected by the settings located in php.ini:

 
| Name || Description || Default || PHP Version |
| --- | --- | --- | --- |
| date.timezone || Default timezone (is used by all PHP date/time functions) || "" || PHP 5.1 and newer |
| date.default\_latitude || Default latitude (is used by date\_sunrise() and date\_sunset()) || "31.7667" || PHP 5.0 and newer |
| date.default\_longitude || Default longitude (is used by date\_sunrise() and date\_sunset()) || "35.2333" || PHP 5.0 and newer |
| date.sunrise\_zenith || Default sunrise zenith (is used by date\_sunrise() and date\_sunset()) || "90.83" || PHP 5.0 and newer |
| date.sunset\_zenith || Default sunset zenith (is used by date\_sunrise() and date\_sunset()) || "90.83" || PHP 5.0 and up |

## Time And Date Functions

Analyze the table below. It is a handy guide for the inbuilt functions that can be used for all your needs when it comes to setting the PHP DateTime format. Feel free to return to it whenever you need a reminder.

![](Images/image00055.jpeg)

![](Images/image00056.jpeg)

![](Images/image00057.jpeg)

![](Images/image00058.jpeg)

![](Images/image00059.jpeg)

![](Images/image00060.jpeg)

![](Images/image00061.jpeg)

## List of Predefined Constants

There are also a few predefined constants that can be used in PHP date formatting. Take a look at their names and descriptions:

![](Images/image00062.jpeg)

![](Images/image00063.jpeg)

## PHP DateTime Format: Summary

*   To get dates and time, inbuilt PHP time and date functions and constants are used.
*   These functions are related to the locale settings of the server you're using.
*   Always keep time inconsistencies (such as daylight savings, time zones and leap years) in mind when working with PHP date functions.

# Error Functions

### How to Fix PHP Error: A Guide on Handlers, Functions and Constants

 

You already learned how PHP error handling works, what PHP errors are in their essence, and how to work with them. Still, there is a lot of functions you don't know. Some of them (like PHP display errors) may come in handy often.

PHP error handling is not a task you'd want to put away for long. Therefore, in this tutorial, we will introduce you with various functions and constants that will prove helpful to you as you're using PHP error handlers and creating custom error logs.

#### Contents

1. PHP Error: Main Tips

2. Settings for Runtime Configuration

3. List of Functions to Handle Errors

4. Relevant Predefined Constants

5. PHP Error: Summary

 

## PHP Error: Main Tips

*   PHP error functions are meant for dealing with error handling and logging tasks.
*   Error functions allow you to define how PHP errors will be handled and logged.
*   Logging errors means sending their messages to be saved in specified files, emails and other kind of system logs.
*   Error report functions let you customize how certain PHP errors are reacted to, and the level of feedback.
*   The functions are inbuilt into the PHP core.
*   This tutorial explains in detail what is a PHP error.

## Settings for Runtime Configuration

The way these functions behave is affected by the settings located in php.ini:

![](Images/image00064.jpeg)

![](Images/image00065.jpeg)

![](Images/image00066.jpeg)

![](Images/image00067.jpeg)

![](Images/image00068.jpeg)

## List of Functions to Handle Errors

For the PHP error management, you are welcome to use the following functions. The table below indicates the most common methods that might be applied to get information on the latest errors, set different handler functions and perform other related actions:

![](Images/image00069.jpeg)

![](Images/image00070.jpeg)

## Relevant Predefined Constants

In PHP error handling, you can use the predefined constants that are designed for allowing you to set which errors are supposed to be displayed. Take a look at the following table and learn the meaning of each constant:

![](Images/image00071.jpeg)

![](Images/image00072.jpeg)

![](Images/image00073.jpeg)

## PHP Error: Summary

*   To handle and log errors, you should use special PHP error functions.
*   When an error is logged, their messages are sent and saved in a log, such as a specified file or email.
*   Using PHP error reporting, you can define system's feedback to particular PHP errors and its level.
*   These functions don't require special installation.

 

# File Function

### How to Use Any PHP File Function: Copy, Delete and Many More

 

In developing, functions are tools that you combine with your skills to achieve the desired effect. For example, using any PHP file function, you can quickly and easily read a file into an array, be it characters or binary data such as pictures.

The navigation of the filesystem becomes effortless when you know which PHP file function needs to be applied in certain situations. In this tutorial, we will provide you with a handy list of functions used to manipulate PHP filesystems and files.

We will review the most frequently used method: the PHP file() function, applied when it is necessary to read a file into an array. Additionally, you will learn the techniques to change groups, modes, and owners of files.

 

#### Contents

1. PHP File Function: Main Tips

2. Most Common Method: file()

3. Options for Runtime Configuration

4. List of Functions

5. PHP File Function: Summary

 

## PHP File Function: Main Tips

*   PHP file functions allow accessing and manipulating filesystems.
*   These functions are inbuilt into the PHP core.
*   When using this function on Unix, forward slash (/) is used to separate directories.
*   On Windows, forward (/) and backward (\\) slashes may be used for that.
*   One of the most important methods is the PHP file() function, used to read a file into array.

## Most Common Method: file()

As we have mentioned, among the most used methods stands the PHP file function that reads a file into an array. Each element of the array will represent a line from a file. Before PHP 4.3, using file() PHP could only read character data, but now it also works with binary data such as pictures.

Let's view the correct syntax that is needed for PHP file function to be executed correctly:

file(path,include path,context)

Only the first of the parameters is required, as it names the exact file for PHP file() to read.

## Options for Runtime Configuration

The way PHP filesystem functions behave is inevitably affected by the settings located in php.ini. Let's see the different options we can use for the configuration:

![](Images/image00074.jpeg)

![](Images/image00075.jpeg)

## List of Functions

In the table below, you have the list of functions PHP provides to make your work with the PHP filesystem easier.

Some of them (such as [fopen()](https://www.bitdegree.org/learn/php-fopen#fopen)) you might also recognize from our previous lessons, in which we learned to work with PHP code to open external files:

![](Images/image00076.jpeg)

![](Images/image00077.jpeg)

![](Images/image00078.jpeg)

![](Images/image00079.jpeg)

![](Images/image00080.jpeg)

![](Images/image00081.jpeg)

![](Images/image00082.jpeg)

![](Images/image00083.jpeg)

![](Images/image00084.jpeg)

![](Images/image00085.jpeg)

![](Images/image00086.jpeg)

## PHP File Function: Summary

*   Inbuilt PHP functions that are used to access and manipulate filesystems can simply called filesystem functions. They don't require installation.
*   Directories are separated using forward slashes (/). On Windows you can use backward slashes (\\) as well.
*   PHP file function is probably used the most. You can read a file into array using it. PHP file() is able to read both binary data and characters.

 

 

# Filter

### Learn to Use PHP Filter: Functions to up Your Security Level

 

We might have already discussed PHP filters once or twice. Using them is important for the safety of the website or application you are creating.

We prepared a clear list of PHP filter functions and predefined constants that you can quickly refer to. If suddenly you need to PHP validate strings, encode special characters or perform other filtering duties, we are here for your every need.

 

#### Contents

1. PHP Filter: Main Tips

2. Options for Runtime Configuration

3. List of Functions to Apply

4. Relevant Predefined Constants

5. PHP Filter: Summary

 

 

## PHP Filter: Main Tips

*   PHP filters are used to sort, validate and otherwise filter data using PHP script.
*   Since the PHP version 5.2.0, the filter functions are available by default, so they don't have to be installed.
*   filter\_var in PHP might be considered one of the most valuable functions.

## Options for Runtime Configuration

Always remember that the work of these functions is affected by the settings located in php.ini:

![](Images/image00087.jpeg)

## List of Functions to Apply

In the table below, you can see a list of useful functions that can be used with PHP filters. They are valid in PHP 5.2 and all newer versions:

![](Images/image00088.jpeg)

## Relevant Predefined Constants

Take a look at these predefined constants. You may find them useful when performing PHP filtering as well:

![](Images/image00089.jpeg)

![](Images/image00090.jpeg)

![](Images/image00091.jpeg)

## PHP Filter: Summary

*   PHP filtering is useful for coders who need to handle (in most cases, validate and sort) the data.
*   Inbuilt PHP filters have been introduced with version 5.2. If you're using this version or a newer one, there's no need to install these functions separately.
*   Coders use filter\_var in PHP codes very often for its flexibility.

 

# Math Functions

### Use PHP Math Functions: Understand Mathematical Processes in Your Code

 

Out of eight PHP data types, only two hold numerical values. You can perform the most basic arithmetic actions using operators, such as PHP modulo or PHP division.

For more complex mathematical operations, PHP math functions are used. To start using them, you do not need to install any extensions or packages.

 

#### Contents

1. PHP Math Functions: Main Tips

2. List of Functions

3. Predefined Constants

4. PHP Math Functions: Summary

 

## PHP Math Functions: Main Tips

*   PHP math functions are used for handling float and integer variables.
*   These functions are inbuilt into PHP.

## List of Functions

In the table below, all the PHP math functions are listed alphabetically. If you are using PHP 4 or a newer version, you can use any of them freely. In case you forget any of these functions, return to this table to refresh your memory! Have a look:

![](Images/image00092.jpeg)

![](Images/image00093.jpeg)

![](Images/image00094.jpeg)

![](Images/image00095.jpeg)

![](Images/image00096.jpeg)

![](Images/image00097.jpeg)

![](Images/image00098.jpeg)

## Predefined Constants

Now, let's see some predefined constants that are also used in PHP mathematics. The column on the right indicates version of PHP in which a particular constant has been introduced:

![](Images/image00099.jpeg)

![](Images/image00100.jpeg)

![](Images/image00101.jpeg)

![](Images/image00102.jpeg)

![](Images/image00103.jpeg)

## PHP Math Functions: Summary

*   PHP math functions don't need to be installed separately, as they are inbuilt.
*   They are meant to only be used with variables that contain numerical values: integers and floats.

 

# Mail Function

### PHP Mail Function: Communicating With Your Users via Emails

 

The easiest way to interact with your users is to make PHP send emails, using special [forms](https://www.bitdegree.org/learn/php-form-example) and the PHP mail function. The main idea of it is that a developer can create special PHP email forms for sending emails straight from the script.

Using PHP mail() you can, for example, send weekly newsletters, or configure your email box to receive error messages. Therefore, the function provides with not only means of communication but also a custom error log.

 

#### Contents

1. PHP mail Function: Main Tips

2. Options for Runtime Configuration

3. Functions for Email Sending

4. PHP mail Function: Summary

 

## PHP mail Function: Main Tips

*   PHP mail function allows you to send emails directly by using PHP script.
*   This function is integrated into PHP's core, but requires a working email system installed to your system (which must be defined in the php.ini file)

## Options for Runtime Configuration

The way PHP mail() function behaves is always affected by the settings defined inside php.ini. The table below provides a list of these runtime configurations that you can apply:

![](Images/image00104.jpeg)

![](Images/image00105.jpeg)

## Functions for Email Sending

In the table below, you can see the functions you can use when you want to PHP send email:

![](Images/image00106.jpeg)

## PHP mail Function: Summary

*   Using an inbuilt mail() function, you can send emails via your PHP script.
*   For this function to work properly, your system must have an email system installed, working, and defined in php.ini.

 

# Miscellaneous Functions

### PHP Function Use Guide: Miscellaneous Functions and Constants

 

Explaining PHP function use is smoother when methods can be categorized into clear groups. However, some single functions and constants stand alone and don't belong to any specific categories.

Even though such functions are not a part of a chain of similar methods, they still need to be addressed. Therefore, we dedicate a tutorial to PHP miscellaneous functions.

#### Contents

[1. PHP Function Use: Main Tips](https://www.bitdegree.org/learn/php-function-use#php-function-use-main-tips)

[2. Runtime Configuration](https://www.bitdegree.org/learn/php-function-use#runtime-configuration)

[3. List of Methods](https://www.bitdegree.org/learn/php-function-use#list-of-methods)

[4. Predefined Constants](https://www.bitdegree.org/learn/php-function-use#predefined-constants)

5. PHP Function Use: Summary

 

## PHP Function Use: Main Tips

*   PHP miscellaneous functions are functions which just don't fit into the other major categories.
*   They can prove useful in PHP configuration or other tasks.
*   Every function in this tutorial is a PHP built in function.

## Runtime Configuration

The way PHP miscellaneous functions behave always depends on the settings inside the php.ini file. Let's have a look at the options we have for PHP configuration using miscellaneous functions:

![](Images/image00107.jpeg)

![](Images/image00108.jpeg)

## List of Methods

In this section, you will be informed of the PHP function use of this miscellaneous category. For instance, you can set a function to be executed later with the PHP sleep() method. There are many methods to analyze in the table below. However, we are sure that some of them will prove themselves to be useful.

 

![](Images/image00109.jpeg)

![](Images/image00110.jpeg)

![](Images/image00111.jpeg)

![](Images/image00112.jpeg)

## Predefined Constants

This list below contains the constant names, descriptions and versions in which these PHP constants can be executed:

![](Images/image00113.jpeg)

## PHP Function Use: Summary

*   All the functions that just don't seem to belong to any particular category are defined as PHP miscellaneous functions.
*   While they stand alone, every miscellaneous PHP built in function is still very useful in the process of PHP configuration.
*   If you are using PHP 5 or a newer version, none of these functions require installation.

 

# PHP Date Format

### PHP Date Format

 

#### Contents

1. PHP Date Format: Main Tips

2. Syntax Rules Explained

3. Common Formatting Characters

4. List of Predefined Constants

 

 

## PHP Date Format: Main Tips

*   This date() function is used in formatting date and time in your code.
*   There are special formatting characters: PHP year, week, day, etc.
*   You can use it to make PHP get timestamp automatically and update the copyright dates on your website.

 

## Syntax Rules Explained

The syntax rules for entering a date are rather simple:

date(format, timestamp)

The timestamp part describes an integer Unix timestamp. Entering it is optional - if you don't do it, it will result in making PHP get timestamp automatically and display the current local time (time()).

Now, for the format part, it's a different story. It is necessary to enter because that's how you specify how your PHP date formats will look.

 

## Common Formatting Characters

In PHP years, months and days are often referred to by using special symbols. There are four characters most commonly used with PHP date function:

*   d (01-31) represents the day number.
*   m (01-12) represents a month number.
*   Y (four digits) represents a year number.
*   l (lowercase 'L') indicates the day of the week.

More symbols (/, ., \-) can be added for additional PHP date formatting.

In the code example below, you can see four different ways to create PHP date formats:

<?php

  echo "Today is " . date("Y/m/d") . "<br>";

  echo "Today is " . date("Y.m.d") . "<br>";

  echo "Today is " . date("Y-m-d") . "<br>";

  echo "Today is " . date("l");

?>

![](Images/image00114.jpeg)

Now, the four characters listed above might be the most commonly used with datetime PHP function, but your choices are not limited to them. Let's have a look at the whole list of characters you can use for PHP date formats and what they indicate:

![](Images/image00115.jpeg)

![](Images/image00116.jpeg)

![](Images/image00117.jpeg)

![](Images/image00118.jpeg)

![](Images/image00119.jpeg)

![](Images/image00120.jpeg)

## List of Predefined Constants

There are also a few predefined constants for datetime PHP that developers use. Take a look at the table below:

![](Images/image00121.jpeg)

![](Images/image00122.jpeg)

# String Functions

### PHP String Functions Made Easy: Handle Strings in a More Efficient Way

 

Out of all eight data types, PHP strings is considered one of the simplest, along with integers, floats, and booleans.

There are built-in PHP string functions for manipulating strings. One of the common uses is to use one of the PHP functions to split the string into smaller parts if the length of a string. You can also use them to have a specific PHP string replaced, modified, or perform other actions.

 

#### Contents

1. PHP String Functions: Main Tips

2. List of Methods

3. PHP String Functions: Summary

 

## PHP String Functions: Main Tips

*   As the naming suggests, PHP string functions help to perform different actions on string data.
*   They are integrated into the core of PHP.
*   Among the most basic and widely used are PHP compare strings and PHP trim string functions.

## List of Methods

Let's see the complete list of PHP string functions and their descriptions. The table is organized in alphabetical order, so you can always find a particular one quickly when you need to, say, have a certain PHP string replaced:

 

![](Images/image00123.jpeg)

![](Images/image00124.jpeg)

![](Images/image00125.jpeg)

![](Images/image00126.jpeg)

![](Images/image00127.jpeg)

![](Images/image00128.jpeg)

![](Images/image00129.jpeg)

![](Images/image00130.jpeg)

![](Images/image00131.jpeg)

![](Images/image00132.jpeg)

![](Images/image00133.jpeg)

![](Images/image00134.jpeg)

![](Images/image00135.jpeg)

![](Images/image00136.jpeg)

![](Images/image00137.jpeg)

![](Images/image00138.jpeg)

## PHP String Functions: Summary

*   When performing various actions using string data, PHP string functions come in handy. For example, you can easily turn PHP array to string or PHP string to array.
*   PHP string functions are inbuilt and don't require any installation.
*   One of the most commonly used methods are applied to PHP compare strings and PHP trim string.

 

 

# PHP Array Functions

### PHP Array Functions

 

#### Contents

1. PHP array Functions: Main Tips

2. Usage of array ()

2.1. Correct Syntax

2.2. Practice: Code Examples

 

## PHP array Functions: Main Tips

*   Introduced in PHP 4, it creates an array of the specified parameters.
*   A PHP array functions as a variable that holds multiples values.
*   There are 3 types of PHP arrays: indexed (numeric index), associative (named keys) and multidimensional (multiple arrays in one).

 

## Usage of array ()

You could call array() the base of all PHP array functions. To put it shortly, it is used to create an array. Let's see a simple example:

<?php

  $food = \['IceCream', 'Pizza', 'Burger'\]; 

  echo "I like " . $food\[0\] . ", " . $food\[1\] . " and " . $food\[2\] . ".";

?>

![](Images/image00139.jpeg)

## Correct Syntax

You are probably aware that it's crucial to pay attention to correct syntax when coding, and it's no different when you're using PHP array functions. Let's see how a piece of script should be written for an indexed array:

array(value1,value2,value3,...);

Now, for the associative array PHP syntax is a bit different. They can also be called PHP key value arrays, as pairs of keys and values define them. Note that either numbers or a string can represent the key:

array(key=>value,key=>value,key=>value,...);

In both cases of using PHP array functions, value elements define each value an array contains to make PHP create array.

In the short version of array syntax introduced in PHP 5.4, array() can be replaced with \[\]. For example, instead of $food=array("IceCream","Pizza"); you can simply type $food=\["IceCream","Pizza"\]; to make PHP create array. It will not change the way the new PHP array functions.

## Practice: Code Examples

The code in the example below creates an associative array PHP script refers to as $age:

<?php

  $age = \[

    'Drago' => 69,

    'Mark' => 32,

    'Luke' => 35

  \];

  echo "Mark is " . $age\['Mark'\] . " years old.";

?>

![](Images/image00140.jpeg)

If we wanted to execute an associative array PHP loop and print its values, our code would look like this:

<?php

  $food = \[

    'Pizza' => 5.90,

    'IceCream' => 1.90,

    'Burger' => 2.90

  \];

 

  foreach($food as $z => $z\_value) {

    echo "Key=" . $z . ", Value=" . $z\_value;

    echo "<br>";

  }

?>

![](Images/image00141.jpeg)

Now, the script in this example loops through an indexed array and prints its values:

 

<?php

  $food = \['IceCream', 'Pizza', 'Burger'\];

  $arrayLength = count($food);

 

  for($z = 0; $z < $arrayLength; $z++) {

    echo $food\[$z\];

    echo "<br>";

  }

?>

![](Images/image00142.jpeg)

 

Note: when looping though arrays, choose for and foreach loops.

 

Now, let's see how creating a multidimensional array would look like:

 

<?php

  // A two-dimensional array

  $food = \[

    \['IceCream', 50, 32\],

    \['Pizza', 40, 39 \],

    \['Burger', 35, 20 \]

  \];

 

  echo $food\[0\]\[0\].": Ordered: ".$food\[0\]\[1\].". Sold: ".$food\[0\]\[2\]."<br>";

  echo $food\[1\]\[0\].": Ordered: ".$food\[1\]\[1\].". Sold: ".$food\[1\]\[2\]."<br>";

  echo $food\[2\]\[0\].": Ordered: ".$food\[2\]\[1\].". Sold: ".$food\[2\]\[2\]."<br>";

?>

![](Images/image00143.jpeg)

 

 

# Directory Functions

### The Complete Guide on PHP Directory: Master Functions

 

A PHP directory is a structure used to catalog and keep our files. It's a part of an organizing system that lets us keep track of our projects and code files more easily.

PHP has a bunch of inbuilt functions that let us quickly fetch information about particular PHP files in the directory. Additionally, it is possible to retrieve data about a whole specific PHP directory. We can easily make PHP list files in directory, open specified handles, and perform other tasks.

 

#### Contents

1. PHP Directory: Main Tips

2. List of Useful Functions

3. PHP Directory: Summary

 

## PHP Directory: Main Tips

*   Directory functions allow you to get info about various PHP directories and what they contain.
*   These functions are inbuilt into the PHP's core.

## List of Useful Functions

The following list contains the functions you can apply in order to manipulate every PHP directory you create:

 

![](Images/image00144.jpeg)

![](Images/image00145.jpeg)

## PHP Directory: Summary

*   Information on any PHP file directory and the files it contains can be obtained using PHP directory functions.
*   These functions are inbuilt, and therefore don't require installation.

 

THE END

 

## •        PHP and MySQL

## •        PHP and XML