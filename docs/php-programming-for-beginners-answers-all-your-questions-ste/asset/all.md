PHP Programming 

For Beginners:

Answers all your Questions 

Step-by-Step

 

 

RYSHITH DOYLE

 

 

 

 

 

 

 

Copyright © 2019 Ryshith Doyle

All rights reserved.

ISBN:

 

 

  

CONTENTS

 

CHAPTER 1INTRODUCTION TO PHP PROGRAMMING

CHAPTER 2OPERATORS IN PHP

CHAPTER 3BUILT –IN FUNCTIONS IN PHP

CHAPTER 4BRANCHING IN PHP

CHAPTER 5LOOPING IN PHP

CHAPTER 6ARRAY IN PHP 

CHAPTER 7USER-DEFINED FUNCTIONS AND GLOBAL VARIABLES IN PHP

CHAPTER 8PHP FORMS HANDLING, FORM VALIDATIONS

(USING $\_GET, $\_POST, $\_REQUEST)

CHAPTER 9WORKING WITH TEXT FILES 

CHAPTER 10PHP ERROR HANDLING  

  

CHAPTER 1: INTRODUCTION TO PYTHON LANGUAGE 

 

1What is PHP?

i)PHP stands for “Hypertext Preprocessor”

ii)It is used to create “Dynamic Web Pages”

iii)It is “Server-side Scripting” Language and can be used in place of ASP,JSP,PERL.

iv)It is an “Open Source Software “

2List the Features of PHP:

i)PHP is easy to read and understand.

ii)There is no need to include libraries like C.

iii)It is Open Source – thus “free to use”

iv)It is a Server-side scripting language

v)It is Cross platform (ie. It can run on any OS – Windows, Mac etc)

vi)It provides connectivity to databases (ie. Oracle, MySQL, Ms-Access etc)

vii)PHP is Object Oriented.

3List the Requirements to run PHP.

i)A web server (such as IIS Web server, Apache Web server etc)

ii)Web browser (ie. IE, Google Chrome)

iii)Text Editor (Notepad, or Notepad++)

4Difference between PHP and HTML.

 
| S.NO || PHP || HTML |
| --- | --- | --- |
| 1 || PHP is used  to design dynamic web pages || HTML is used to design static web pages |
| 2 || PHPfiles are executed on the server side || HTML files are interpreted and execute by the browser |
| 3 || PHPfile first executed by the PHPengine and converted into HTML code before sending it to the client || As it runs on client’s browser, so it is faster |

 

5Difference between Server Side Scripting and Client Side Scripting.

 
| S.no || Server Side Scripting || Client Side Scripting |
| --- | --- | --- |
| 1 || It is usually written in ASP, JSP or PHP || It is written in VBScript or JavaScript |
| 2 || It is always processed by the Web Server || It is processed by the Web Browser on the client side |
| 3 || It is capable of creating HTML files on demand of the user. || It is not cable of creating HTML files on demand. |

 

 

6What is IIS Web server?

i)Internet Information Services (IIS) is an web server created by Microsoft Inc.

ii)It is one of the options to develop and run PHP files

iii)When using IIS, the PHP file have to be saved in “C:\\ INETPUB\\ WWWROOT\\” folder.

 

7What is Apache Web server?

i)Apache is the most widely used web server software

ii)Apache is an open source software available for free

iii)Apache web server can be installed using XAMPP software package.

iv)When using XAMPP, the PHP file  have to be saved in “C:\\ XAMPP \\ HTDOCS\\” folder.

8How to include PHP script in web pages?

i)Using <?php        ?>

Example: <?php  echo “hello world”;  ?>

ii)Using <script language=”php”> … </script>

9What is the use of semicolon (;) in php code?

i)Semicolon (;) is used to terminate/end a php command.

ii)Example: <?php  echo “hello world”;  ?>

10How are comments given in php?

i)Single Line Comment (//)

ii)Multiline Comment(/\* … \*/)

iii)Example:

<?php

/\* This echo statement will 

print the meggage I give it  \*/

echo “Hello World”;

 

// I can also display a welcome message

echo “Welcome Ajay”;     // In case the users name is Ajay

11What is meant by Variable?

i)Variable is a named memory location.

ii)The value of a variable can change during program execution.

iii)Example of php variable: 

<?php

$x = 52;

echo $x;

?>

12Points to remember about php variables:

i)All variable is php start with a $ sign followed by the name of the variable

ii)A variable name must start with a letter or an underscore “\_” after $ sign

iii)A variable name can only contain alpha-numeric characters and underscore (a-z,A-Z,0-9 and \_)

iv)A variable name should not contain spaces

v)Variable names are case-sensitive ($EMP and $emp are not same)

vi)Variable in php does not have Intrinsic types.

vii)Variable that are used before they are assigned values will have default values

viii)Php is able to automatically convert the variable type when required

ix)Php does not support Explicit declaration of variables

13What is meant by “Variable Variables” or Dynamic Variables?

i)Php allows you use Dynamic Variable Names, called Variable Variables.

ii)You can name a variable with the value stored in another variable.

iii)Example:

<?php

$var1=”hello” ;      // variable named var1 is created and value “hello” is stored

$$var1=”world”;   // variable named hello is created and value “world” is stored

?>

14What is meant by Variable Reference?

i)Variable reference means creating another name (alias) for the variable.

ii)The “&” is used for creating Variable Reference

iii)Example: 

<?php

$var1=”hello”;       // variable named var1 is created and value “hello” is stored

$var2 =&$var1;   // now var2 is another name given to var1, and var2 also contains “hello”

?>

15Difference between echo and print.

 
|   || echo || print |
| --- | --- | --- |
| Parameters || echo can take more than one parameter when used without parentheses. The syntax is echo expression \[, expression\[, expression\] ... \]. Note that echo ($arg1,$arg2) is invalid.Example:echo "Don't", " ", "panic", "!"; //This is valid. || print only takes one parameter.Example:print "The ", "answer is", "42."; //This is invalid.  |
| --- | --- | --- |
| Return value || echo does not return any value || print always returns 1 (integer) |
| Syntax || void echo ( string $arg1 \[, string $... \] ) || int print ( string $arg ) |
| What is it? || In PHP, echo is not a function but a language construct. || In PHP, print is not a really function but a language construct. However, it behaves like a function in that it returns a value. |

 

16What is meant by PHP Data types?

i)A data type refers to the data a variable can store.

ii)PHP has no command to declare a variable, a variable is created the moment you first assign a value to it.

iii)In PHP a variable cannot be declared as a specific data type.

iv)PHP supports 8 Data Types:

a.Integer : These are whole numbers, without decimal point.

b.Double or Float: These are decimal point numbers.

c.Boolean: Only two possible values either true or false

d.NULL: It is a special type that only has one value NULL.

e.String : These are sequence of characters/text.

f.Array : These are named and indexed collection of values.

g.Object: These are instances of programmer-defined classes. 

h.Resource : These are special variables that hold references to resources external to PHP (such as database connection)

 

![](Images/image00171.jpeg)

 

17What is meant by Special Characters?

i)In PHP strings we can escape/skip a characters by preceding it with a “\\” backslash.

ii)The following are the commonly used special characters and are preceded by a backslash :

a.\\n – Newline character (same as <br>)

b.\\r – Carriage Return (Enter Key)

c.\\t – TAB Key

d.\\$ - Literal Dollar($)

e.\\’ – Literal Single Quote (‘)

f.\\”– Literal Double Quote (“)

g.\\\\ - Replaced with a Single Backslash (\\)

18What is meant by Type Casting?

i)Type Casting means changing the data type of a variable from one type to another.

ii)gettype() : the function used to return the name of the data type of the variable.

iii)settype(): the function used to set the data type of a variable.

iv)Example:

$myAge=17;

Print gettype($myAge);        // Returns : Integer

settype($myAge,”String”); 

Print gettype($myAge);        // Returns : String

19What is meant by Type Casting Operators?

i)PHP offers Type Casting Operators that help to convert one type to another.

ii)List of Type Casting Operators:

a.(int)

b.(bool)

c.(float)

d.(string)

e.(array)

f.(object)

iii)Example:

$myAge=17;

Print gettype($myAge);        // Returns : Integer

$age=(string) $myAge;

Print gettype($age);        // Returns : String

 

 

  

 

CHAPTER 2: OPERATORS IN PHP

 

1What is meant by Expression?

i)An Expression is a combination of values, variables, operators, and functions, that results in a value.

ii)Example: $Num=5+15/2;

2What is meant by Operators?

i)Operators are characters (or set of characters) that perform a special operation within the PHP code

ii)Example : $ Num=5+15/2;      // ‘=’,‘+’,’ /’ are operators

3Explain the types of PHP operators:

i)Assignment Operators

ii)Arithmetic Operators

iii)Unary and Binary Operators

iv)Compound Assignment Operators

v)Comparison Operators

vi)Logical Operators

vii)Increment and Decrement Operator

viii)Conditional Operator

4Explain Assignment Operator with examples:

i)Assignment operator ‘=’ is used to assign a value to a variable.

ii)Example: $Num=7

5Compound assignment

Assignment operators can be combined with arithmetic operators to create operator. 

Such as += , -= , /= , \*= , %= . Compound assignment operator allows to write shorter expression. For e.g: 

<?php

    $i = 100;

    $i = $i + 10;

    echo $i;

 ?>

can be written as

<?php

     $i = 100;

    $i += 10;

 ?>

6What are the String operators in PHP?

i)The operators used to do string concatenation and append operations.

ii)List of String Operators:

iii)PHP has two operators that are specially designed for strings.

 
| Op || Name || Example || Result |
| --- | --- | --- | --- |
| . || Concatenation || $txt1 . $txt2 || Concatenation of $txt1 and $txt2 |
| .= || Concatenation assignment || $txt1 .= $txt2 || Appends $txt2 to $txt1 |

 

7Explain Arithmetic Operator with examples:

i)These are general mathematical operators

ii)List of arithmetic operators

OperatorUse

+Addition

\-Subtraction

\*Multiplication

/Division

%remainder division

iii)/  operator returns the quotient and % (modulo) returns the remainder obtained during division

8Explain Unary Operator with examples:

i)Unary operators are operators that only deal with one argument (which is generally a single variable).  In PHP, there's only a few of these as shown below:

 

OperatorUse

!Negation

++increment by 1

\--decrement by 1

ii)Below are some examples of these operators being used.

 

<?php

// negation

$bool = true;

$bool = !$bool;   // $bool will now be false

 

$k = 0;           // initializes the value of k to 0

 

// increment by 1

$k++;             // increments k by 1

echo "k = ".$k;   // outputs: k = 1

 

// decrement by 1

$k- -;             // decrements k by 1

echo "k = ".$k;   // outputs: k = 0

?>

9Explain Binary Operator with examples:

i)Binary operators are operators that deal with two arguments, both generally being either variables or constants. Some examples of binary operators found in PHP:

 

OperatorUse

+Addition

\-Subtraction

\*Multiplication

/Division

%remainder division

\=Assignment

\==boolean equality comparision

\>boolean greater than

<boolean less than

&&boolean AND

||boolean OR

ii)These operators are the most straight forward type of operators in PHP.  They are very easy to understand because we have seen them all our lives in school.  For example, take a look at the example code below:

 

<?php

$a = 5;

$b = 6;

$c = $a + b;  // $c is now 11

?>

10What are the Comparisons operators in PHP?

1.The operators used to do comparison and return true or False.

2.List of the comparison operators of PHP:

 
| 

 
| Op || Name || Example || Result |
| --- | --- | --- | --- |
| \= = || Equal || $x = = $y || Returns true if $x is equal to $y |
| \= = = || Identical || $x = = = $y || Returns true if $x is equal to $y, and they are of the same type |
| != || Not equal || $x != $y || Returns true if $x is not equal to $y |
| <> || Not equal || $x <> $y || Returns true if $x is not equal to $y |
| ! = = || Not identical || $x !== $y || Returns true if $x is not equal to $y, or they are not of the same type |
| \> || Greater than || $x > $y || Returns true if $x is greater than $y |
| < || Less than || $x < $y || Returns true if $x is less than $y |
| \>= || Greater than or equal to || $x >= $y || Returns true if $x is greater than or equal to $y |
| <= || Less than or equal to || $x <= $y || Returns true if $x is less than or equal to $y |

 |
| --- |

 

 

11What are the Logical operators in PHP?

1.The operators used to do Logical operations.

2.They are also called Boolean operators, since they return true or False.

3.List of the comparison operators of PHP:

 
| Operator || Name || Example || Result |
| --- | --- | --- | --- |
| and || And || $x and $y || True if both $x and $y are true |
| or || Or || $x or $y || True if either $x or $y is true |
| && || And || $x && $y || True if both $x and $y are true |
| || || Or || $x || $y || True if either $x or $y is true |
| ! || Not || !$x || True if $x is not true |

 

12What are the increment and decrement operators in PHP?

i)The PHP increment operators are used to increment a variable's value.

ii)The PHP decrement operators are used to decrement a variable's value.

 
| Operator || Name || Description |
| --- | --- | --- |
| ++$x || Pre-increment || Increments $x by one, then returns $x |
| $x++ || Post-increment || Returns $x, then increments $x by one |
| \--$x || Pre-decrement || Decrements $x by one, then returns $x |
| $x-- || Post-decrement || Returns $x, then decrements $x by one |

 

13What are the Conditional operators in PHP?

i)It is used as shorthand for when writing an if/else statement that assigns a values o a variable.

ii)Syntax:

Variable=(condition) ? expression1 if true  : expression2 if false

iii)Example1:

$x=10;

$y=15;

$z=($x > $y) ? $x : $y;

Echo $z;                           // result : 15

iv)Example 2:

$age=20;

$flag=($age>18) ? “Eligible to vote” , “Not Eligible to vote”;

14What are the Array operators in PHP?

1.The operators used to do array related operations.

2.List of array Operators

3.The PHP array operators are used to compare arrays.

 
| Op || Name || Example || Result |
| --- | --- | --- | --- |
| + || Union || $x + $y || Union of $x and $y |
| \= = || Equality || $x == $y || Returns true if $x and $y have the same key/value pairs |
| \= = = || Identity || $x === $y || Returns true if $x and $y have the same key/value pairs in the same order and of the same types |
| != || Inequality || $x != $y || Returns true if $x is not equal to $y |
| <> || Inequality || $x <> $y || Returns true if $x is not equal to $y |
| != = || Non-identity || $x !== $y || Returns true if $x is not identical to $y |

 

15What is meant by Constant?

i)Constant is a named memory location.

ii)The value of a variable cannot change during program execution.

iii)A constant is defined using the Keyword define

iv)Normally constants names are in upper case.

v)constant() can be used to display the value of a constant

vi)Example of php Constants: 

define (“PI”,3.14);

define (“MAXSIZE”,100);

echo “Value of Pi is “. PI . “<BR>”;

echo “six is “. MAXSIZE;

echo constant(“PI”);

16What is a Literal?

A literal is a sequence of characters used in a program to represent a constant value.

17Explain the String Types:

i)Single quotes

Single quotes are used to denote a “literal string”. Literal strings do not attempt to parse special characters or variables.

<?php

echo' This is my string, look at how pretty it is.';// no need to parse a simple string

 

/\*\*

 \* Output:

 \*

 \* This is my string, look at how pretty it is.

 \*/Double quotes

ii)ii) Double will not only parse variables, but all sorts of special characters, like \\n for newline, \\t for a tab, etc.

<?php

echo 'phptherightway is '.$adjective.'.'// a single quotes example that uses multiple concatenating for

."\\n"// variables and escaped string

.'I love learning'.$code.'!';

 

// vs

 

echo"phptherightway is $adjective.\\n I love learning $code!"// Instead of multiple concatenating, double quotes

//enablesustouseaparsablestring

Double quotes can contain variables; this is called “interpolation”.

<?php

$juice='plum';

echo"I like $juicejuice";//Output:Ilikeplumjuice

When using interpolation, it is often the case that the variable will be touching another character. This will result in some confusion as to what is the name of the variable, and what is a literal character.

To fix this problem, wrap the variable within a pair of curly brackets.

<?php

$juice='plum';

echo"I drank some juice made of $juices";// $juice cannot be parsed

 

// vs

 

$juice='plum';

18What are the difference between constants and variable?

Differences between constants and variables are

i)There is no need to write a dollar sign ($) before a constant, where as in Variable one has to write a dollar sign.

ii)Constants cannot be defined by simple assignment, they may only be defined using the define() function.

iii)Constants may be defined and accessed anywhere without regard to variable scoping rules.

iv)Once the Constants have been set, may not be redefined or undefined.

19What is meant by operator precedence?

i)Operator precedence determines the grouping of term in an expression. Certain operators will be performed before others.

ii)Example: 

$x=7+3\*2;

Here $x is assigned 13, not 20 because operator \* has higher precedence than +, so it first gets multiplied with 3\*2 and then adds into 7.

 

List the Operator Precedence.

OrderOperatorOperation

1!Logical NOT

2\+ +Increment

3\- -Decrement

5\*Multiplication

6/Division

7%Modulus

8+Addition

9\-Subtraction

10.String concatenation

11<, < =Less than, less than or equal

12\>, > =Greater than, greater than or equal

13\= =Value equality

14!=, <>Inequality

15\= = =Type and value equality

16!==Type and value inequality

17&&Logical AND

18||Logical OR

19?:Conditional operator

20\=Assignment

21+=, -=, \*=, /=, .=, %=, &=, |=, ^=, ~=, <<=, >>=Assignment with operation

22andLogical AND

23xorLogical XOR

24orLogical OR

25,List separator

 

  

 

CHAPTER 3: BUILT –IN FUNCTIONS IN PHP

 

1What is meant by Function?

i)A function is a piece of code which takes one or more input in the form of parameter and does some processing and returns a value.

ii)Functions can be reused again and again.

2What are the two types of Function?

i)In-built/system defined functions

ii)User defined functions

3What are the benefits of Functions?

i)Functions can be reused again and again

ii)Easy debugging

4What is meant by In-Built Functions?

i)In-built functions are the system defined functions

ii)Example: 

5Explain the String Manipulation functions:

i)strtoupper() : convert your strings to all UPPERCASE

    $name = "Matthew ";

    echo strtolower($name); // matthew

 

ii)strtolower() : convert your strings to all lowercase

    $name = "Matthew ";

    echo strtolower($name); // matthew

iii)strlen():It works by passing a string or variable and then returns the total number of characters including spaces.

$name = "Matthew ";

echo strlen($name); // 8

iv)strchr(): This function is used to find the first occurrence of the string and return all the characters from the search position to the end of the string.

$x=”CBSE Multimedia and Web Technology”;

$y = strchr($x, ‘M’)

echo $y             // the output will be  : Multimedia and Web Technology

v)strpos():This function is used to find the position of first occurrence of the string and return value is a number.

Syntax: srtpos(string, find, start)

start is optional

 

$x=”CBSE Multimedia and Web Technology”;

$y = strpos($x, ‘M’,0)

echo $y             // the output will be  : 5

vi)ord() : This function is used to find the ASCII value of first character of a string.

$x=”CBSE Multimedia and Web Technology”;

$y = ord($x)

echo $y             // the output will be  : 67

 

vii)chr() : This function is used to convert a specified ASCII value to its corresponding character and return it.

$x= chr(67)

Echo $x              // the output will be  : C

viii)trim(), ltrim(), rtrim() :trim() is used to trim the white space from both the sides, ltrim and rtrim from 

left and right side respectively.

ix)substr() : This function returns a string or part of string containing a specified number of characters from an original string.

Syntax: substr(string, start, length)

Length is optional

 

$x=” Multimedia and Web Technology - 2016”;

echo substr($x, 0,10)         // returns : Multimedia

echo substr($x, 19,10)       // returns : Technology

echo substr($x, -4)            // returns : 2016

echo substr($x, -4,-2)       // returns : 20

echo substr($x, 0, -6)       // returns : Multimedia and Web Technology

x)strrev() : It returns a string in which the character order of the string is reversed

$x=” Multimedia”

echo strrev($x)    // returns: aidemitluM

xi)strcasecmp(): This is used to compare two strings and return an integer. It is case-Insensitive.

The function returns the following values:

0     –  if the two strings are equivalent

<0  - if smaller byte value is found in String1

\>0  - if smaller byte value is found in String2

xii)strcmp() : similar to strcasecmp() but srtcmp is Case-Sensitive.

xiii)      stripsashes() : This will remove any backslashes(\\) from the string.

xiv)str\_word\_count(): This function is used to count the number of words in a string.

Syntax:

str\_word\_count(string,return,char)

 

 
| Parameter || Description |
| --- | --- |
| string || Required. Specifies the string to check |
| return || Optional. Specifies the return value of the str\_word\_count() function.Possible values:

*   0 - Default. Returns the number of words found
*   1 - Returns an array with the words from the string
*   2 - Returns an array where the key is the position of the word in the string, and value is the actual word

 |
| char || Optional. Specifies special characters to be considered as words. |

 

Example:  echo str\_word\_count("Hello world!");    // return: 2

6Explain the Numeric functions:

i)abs(): This function returns the absolute value of a number. ie removes the negative sign.

Example: echo abs(-48.6);      // return: 48.6

ii)atan(): This function return the arctangent of a specified number.

iii)cos():This function return the cosine of a specified number.

iv)ceil(): This function returns the ceiling value for x. The smallest integer not less than x.

Example: echo ceil(48.6);      // return: 49

                echo ceil(48.1);      // return: 49

                echo ceil(-48.1);      // return: 48

v)exp(): This function returns the exponent of e, that is e raised to the power.

Example:  echo exp(1);      // return: 2.718281828459

vi)floor():This function returns the floor value for x. The largest integer not greater than x. That is the next integer after x.

Example: echo ceil(48.6);      // return: 48

                echo ceil(48.1);      // return: 48

                echo ceil(-48.1);      // return: -49

vii)log(): This function returns the natural logarithm of a specified number.

viii)pow(): This function returns the value x to y.

Example: echo pow(5,2);      // return: 25

ix)rand(): The function returns a random number.

Syntax : rand\[(min,max)\]

min  and max are optional.

If you use rand() without parameters then any number between 0 to 32767 will be returned.

Example: echo rand();      // return: 1254    ie any number between 0 to 32767

Example: echo rand(5,15);      // return: 13 ie any number between 5 to 15

x)round(): This function is used to round up or down based on their values. Any decimal .5 or above is rounded up, any under .5 is rounded down. Even the number of decimal places required can be specified as an optional argument.

Syntax: round(number, optional\_decimal)

Example : echo round(3.141)     // return: 3

                 echo round(3.67)     // return: 4

                 echo round(3.9078, 2)     // return: 678.91

xi)sin():This function return the sine of a specified number.

xii)sqrt():This function returns the square root of a number.

Example: echo sqrt(144)    // return: 12

xiii)tan():This function return the tangent of a specified number.

 

7Explain the Date and Time functions:

| Parameter string |
| --- |
| format || Description || Example returned values |
| Day |
| d || Day of the month, 2 digits with leading zeros || 01 to 31 |
| D || A textual representation of a day, three letters || Mon throughSun |
| j || Day of the month without leading zeros || 1 to 31 |
| l(lowercase 'L') || A full textual representation of the day of the week || Sunday throughSaturday |
| N || ISO-8601 numeric representation of the day of the week (added in PHP 5.1.0) || 1 (for Monday) through 7 (for Sunday) |
| S || English ordinal suffix for the day of the month, 2 characters || st, nd, rd or th. Works well with j |
| w || Numeric representation of the day of the week || 0 (for Sunday) through 6 (for Saturday) |
| z || The day of the year (starting from 0) || 0 through 365 |
| Week |
| W || ISO-8601 week number of year, weeks starting on Monday (added in PHP 4.1.0) || Example: 42 (the 42nd week in the year) |
| Month |
| F || A full textual representation of a month, such as January or March || January throughDecember |
| m || Numeric representation of a month, with leading zeros || 01 through 12 |
| M || A short textual representation of a month, three letters || Jan through Dec |
| n || Numeric representation of a month, without leading zeros || 1 through 12 |
| t || Number of days in the given month || 28 through 31 |
| Year |
| L || Whether it's a leap year || 1 if it is a leap year, 0otherwise. |
| o || ISO-8601 year number. This has the same value as Y, except that if the ISO week number (W) belongs to the previous or next year, that year is used instead. (added in PHP 5.1.0) || Examples: 1999or 2003 |
| Y || A full numeric representation of a year, 4 digits || Examples: 1999or 2003 |
| y || A two digit representation of a year || Examples: 99 or03 |
| Time |
| a || Lowercase Ante meridiem and Post meridiem || am or pm |
| A || Uppercase Ante meridiem and Post meridiem || AM or PM |
| B || Swatch Internet time || 000 through 999 |
| g || 12-hour format of an hour without leading zeros || 1 through 12 |
| G || 24-hour format of an hour without leading zeros || 0 through 23 |
| h || 12-hour format of an hour with leading zeros || 01 through 12 |
| H || 24-hour format of an hour with leading zeros || 00 through 23 |
| i || Minutes with leading zeros || 00 to 59 |
| s || Seconds, with leading zeros || 00 through 59 |
| u || Microseconds (added in PHP 5.2.2). Note that date() will always generate000000 since it takes an integer parameter, whereas DateTime::format()does support microseconds if DateTime was created with microseconds. || Example: 654321 |
| Timezone || \--- || \--- |
| e || Timezone identifier (added in PHP 5.1.0) || Examples: UTC,GMT,Atlantic/Azores |
| I (capital i) || Whether or not the date is in daylight saving time || 1 if Daylight Saving Time, 0otherwise. |
| O || Difference to Greenwich time (GMT) in hours || Example: +0200 |
| P || Difference to Greenwich time (GMT) with colon between hours and minutes (added in PHP 5.1.3) || Example: +02:00 |
| T || Timezone abbreviation || Examples: EST,MDT ... |
| Z || Timezone offset in seconds. The offset for timezones west of UTC is always negative, and for those east of UTC is always positive. || \-43200 through50400 |
|  ||  ||  |

 

 

8Date and time functions

1)date\_default\_timezone\_set() : Function used to set the time zone. For India the valid code is “Asia/Calcutta”.

2)date\_default\_timezone\_get() : Function to display the time zone that has been set.

Example: 

<?php

date\_default\_timezone\_set('Asia/Calcutta');

echo date\_default\_timezone\_get();?>

Result: Asia/Calcutta

3)date() : This function returns a string formatted according to the given format string using timestamp or the current time.(ie. Timestamp is optional)

Syntax

date(format,timestamp)

Example: To display Date

<?php

echo "Today is " . date("Y/m/d") . "<br>";

echo "Today is " . date("Y.m.d") . "<br>";

echo "Today is " . date("Y-m-d") . "<br>";

echo "Today is " . date("l");?>

Here are some characters that are commonly used for dates:

•d - Represents the day of the month (01 to 31)

•m - Represents a month (01 to 12)

•Y - Represents a year (in four digits)

•l (lowercase 'L') - Represents the day of the week

Result:

Today is 2016/08/03

Today is 2016.08.03

Today is 2016-08-03

Today is Wednesday

Example: To display Time

<?php

echo "The time is " . date("h:i:sa");?>

Here are some characters that are commonly used for times:

•h - 12-hour format of an hour with leading zeros (01 to 12)

•i - Minutes with leading zeros (00 to 59)

•s - Seconds with leading zeros (00 to 59)

•a - Lowercase Ante meridiem and Post meridiem (am or pm)

Result: The time is 11:01:19am

4)time() : Return the current time as a Unix timestamp. 

Returns the current time measured in the number of seconds since the Unix Epoch (January 1 1970 00:00:00 GMT).

oThis will be a large number, it has to be formatted using date() to display is understandable format.

oExample:

<?php

$t=time();

echo($t . "<br>");

echo(date("Y-m-d",$t));?>

Result:

1470236933         // this number cannot be understood

2016-08-03          // using date() we have formatted it to year,month,day

5)gettimeofday(): it returns the current time as an array

Array Items:

•"sec" - seconds since the Unix Epoch

•"usec" - microseconds

•"minuteswest" - minutes west of Greenwich

•"dsttime" - type of dst correction

Example:

<?php

// Print the array from gettimeofday()

print\_r(gettimeofday());

// Print the float from gettimeofday()

echo gettimeofday(true);?>

Result:

Array ( \[sec\] => 1470237375 \[usec\] => 298062 \[minuteswest\] => 240 \[dsttime\] => 1 ) 

1470237375.2982

6)mktime():Returns the Unix timestamp corresponding to the arguments given

Syntax

mktime(hour,minute,second,month,day,year,is\_dst);

Example:

<?php

echo(date("M-d-Y H:i:s",mktime(23,43,26,4,27,2015))."<br />");  

echo(date("M-d-Y",mktime(0,0,0,17,4,2005))."<br />");  

echo(date("M-d-Y",mktime(0,0,0,1,36,2000))."<br />");  

echo(date("M-d-Y",mktime(24,0,0,1,1,99))."<br />");  ?>

Result:

Apr-27-2015  23:43:26

May-04-2006

Feb-05-2000

Jan-02-1999

Example: Each of the following lines produces the string "Jan-01-1998".

<?php

echo date("M-d-Y", mktime(0, 0, 0, 12, 32, 1997));

echo date("M-d-Y", mktime(0, 0, 0, 13, 1, 1997));

echo date("M-d-Y", mktime(0, 0, 0, 1, 1, 1998));

echo date("M-d-Y", mktime(0, 0, 0, 1, 1, 98));?>

7)strtotime():Parse English textual datetimes into Unix timestamps

Example:<?php

echo(date("Y/m/d",strtotime("now"))."<br>");

echo(date("Y/m/d",strtotime("3 October 2005")) . "<br>");

echo(date("Y/m/d",strtotime("+5 hours")) . "<br>");

echo(date("Y/m/d",strtotime("+1 week")) . "<br>");

echo(date("Y/m/d",strtotime("+1 week 3 days 7 hours 5 seconds"))."<br>");

echo(date("Y/m/d",strtotime("next Monday")) . "<br>");

echo(date("Y/m/d",strtotime("last Sunday")));?>

Return:

2016/08/03

2005/10/03

2016/08/03

2016/08/10

2016/08/14

2016/08/08

2016/07/31

8)cal\_days\_in\_months(): It returns the number of days in a month for a specified year.

Syntax: cal\_days\_in\_month(calendar,month,year)

Example:<?php

$d=cal\_days\_in\_month(CAL\_GREGORIAN,10,2005);

echo "There was $d days in October 2005";?>

Result:There was 28 days in February 1965.

There was 29 days in February 2004.

 

 

  

 

CHAPTER 4: BRANCHING IN PHP

 

 

 

1Branching 

 The two main structures for branching are if and switch. 

 If is a workhorse and is usually the first conditional structure anyone learns. 

 Switch is a useful alternative for certain situations where you want multiple possible branches based on a single value and where a series of if statements would be cumbersome. 

1.If-else 

 Syntax: 

if (condition) 

{ 

statement-1 

} 

 

Or with an optional else branch: 

 

if (condition) 

{ 

statement-1 

} 

else 

 

 

 

 

 

 

{ 

statement-2 

} 

 When an if statement is processed, the test expression is evaluated, and the result is interpreted as a Boolean value. 

 If condition is true, statement-1 is executed. If condition is not true, and there is an else clause, statement-2 is executed. 

 If condition is false, and there is no else clause, execution simply proceeds with the next statement after the if construct. 

 

 Example:-1 (Simple If) 

<?php

 $a=10; 

 if ($a == 10) 

 

 

 { 

 echo $a; 

 } 

?>

Example:-2 (Simple If and Else) 

<?php

 $a=10;

$b=4; 

 if ($a > $b) 

 { 

 echo "A is greater than"; 

 } 

 else 

 { 

 echo "B is greater than"; 

 } 

?>

Example:-3 (Elseif) 

<?php

 $a=2; 

 if ($a == 1) 

 { 

 print "Mon"; 

 } 

elseif($a==2) 

 { 

 print "Thu"; 

 } 

 else 

 { 

 print "wrong choice"; 

 } 

?>

 

 Example:-4 (Nested if……else) 

<?php

 $a=1; 

 $b=2; 

 $c=3; 

 if ($a > $b) 

 { 

 if ($a > $c)  {  print "a is max";  } 

 else  {  print "c is max";  }  } 

 else 

 { 

 if ($b > $c) 

 { 

 print "b is max";

} 

 else 

 { 

 print "c is max"; 

 } 

 } 

?>

Switch

 For a specific kind of multi way branching, the switch construct can be useful. 

 Rather than branch on arbitrary logical expressions, switch takes different paths according 

to the value of a single expression. 

 The syntax is as follows, with the optional parts enclosed in square brackets (\[\]) 

switch(expression) 

{ 

case value-1: 

statement-1 

statement-2 

... 

\[break;\] 

case value-2: 

statement-3 

statement-4 

... 

\[break;\] 

..... 

…… 

\[default: 

default-statement\] 

} 

 The expression can be a variable or any other kind of expression, as long as it evaluates to a 

simple value (that is, an integer, a double, or a string). 

 The construct executes by evaluating the expression and then testing the result for equality 

against each case value. 

 As soon as a matching value is found, subsequent statements are executed in sequence 

until the special statement (break ;) or until the end of the switch construct. 

 A special default tag can be used at the end, which will match the ex pression if no other 

case has matched it so far. 

Example: 

<?php

 $a=6; 

 switch($a) 

 { 

 case 1: 

 print "Mon"; 

 break; 

 case 2: 

 print "Tue"; 

 break;

case 3: 

 print "Wen"; 

 break; 

 case 4: 

 print "Thu"; 

 break; 

 case 5: 

 print "Fri"; 

 break; 

 case 6: 

 print "sat"; 

 break; 

 case 7: 

 print "Sun"; 

 break; 

 default: 

 print "Wrong Choice"; 

 } 

?>

  

 

CHAPTER 5: LOOPING IN PHP

 

Looping : It allows the programmer to perfom an action that can be repeated till the given condition is true.

 

1.While 

 The simplest PHP looping construct is while, which has the following syntax: 

while (condition) 

{ 

Statement 

} 

 The while loop evaluates the condition expression as a Boolean —if it is true, it executes 

statement and then starts again by evaluating condition. 

 If the condition is false, the while loop terminates. Of course, just as with if, statemen t may 

be a single statement or it may be a brace-enclosed block. 

 Example:- 

<?php

 $a=1; 

 while ($a <= 10) 

 { 

 print "count is $a<BR>"; 

 $a = $a + 1; 

 } 

?>

2.do-while

 The do-while construct is similar to while, except that the test happens at the end of the 

loop. 

 The syntax is: 

do 

{ 

code to be executed; 

} 

while (condition); 

 The statement is executed once, and then the expression is evaluated. 

 If the expression is true, the statement is repeated until the expression becomes false. 

 The only practical difference between while and do-while is that the latter will always 

execute its statement at least once. 

 Example:- 

<?php

 $a=1; 

 do 

 { 

 print "count is $a<BR>"; 

 $a = $a + 1; 

 } 

 while ($a <= 10); 

?>

3.for 

The most complicated looping construct is for, which h as the following syntax: 

for (initial-expression;termination-check;loop-end-expression

{ 

Number of statements 

} 

 In executing a for statement, first the initial-expression is evaluated just once, usually to 

initialize variables. 

 Then termination-check is evaluated—if it is false, the for statement concludes, and if it is 

true, the statement executes. 

 Finally, the loop-end-expression is executed and the cycle begins again with termination-

check. 

 As always, by statement we mean a single (semicolon -terminated) statement, a brace-

enclosed block, or a conditional construct. 

 Example:- 

<?php

 for ($i = 1; $i<= 5; $i++) 

 { 

 echo $i; 

 } 

?>

4.foreach loop

 There exists a foreach Constructs (command) that will apply a set of statements for each 

value in an array. 

 It works only on arrays, however, and will give you a big old error if you try to use it with 

another type of variable. 

 Your syntax for the foreach command looks like this: 

foreach ($array\_variable as $value\_variable) 

 { 

// .. do something with the value in $value\_variable

} 

 

foreach ($array\_variableas $key\_var => $value\_var) 

{ 

// .. do something with $key\_var and/or $value\_var

 

} 

 

 Example: 

<html>

<head>

<title>

 For Each Constructs 

</title>

</head>

<body>

<?php

 $a\[\] = "Rahul"; 

 $a\[\] = "Ravi"; 

 $a\[\] = "Pratik"; 

 echo "My Name -->".'</br>'; 

foreach ($a as $b) 

 { 

 //these lines will execute as long as there is a value in $a 

 echo $b.'</br>'; 

 } 

?>

</body>

</html>

5.Break and continue 

 The standard way to get out of a looping structure is for the main test condition to become 

false. 

 The special commands break and continue offer an optional side exit from all the looping 

constructs, including while, do-while, and for: 

 The break command exits the innermost loop construct that contains it. 

 The continue command skips to the end of the current iteration of the innermost loop 

that contains it. 

 Example(Break):- 

<?php

 $i = 0; 

 while ($i<100) 

 { 

 if ($i> 6) 

 break; 

 echo $i; 

 $i=$i+1; 

 } 

?>

 Example(Continue):- The following code prints the number 0 to 9, except 5. 

<?php

 for ($i = 0; $i<10; $i++) 

 { 

 if ($i == 5) 

 { 

 continue; 

 } 

 echo $i;  } ?>

 CHAPTER 6: ARRAY IN PHP

 

Arrays

 An array is a single variable that can hold more than one value at once. 

 You can think of an array as a list of values. 

 Each value within an array is called an element, and each element is referenced by its own index, which is unique to that array. 

 To access an element’s value — whether you’re creating, reading, writing, or deleting the 

element — you use that element’s index. 

 

For example, the first element has an index of 0. the second has an index of 1, and so on  Associative arrays 

 

With associative arrays, each element is referenced by a string index. 

 

For example, you might create an array element representing a customer’s age and give it an index of “age”. 

 

Creating Arrays 

 This takes a list of values and creates an array containing those values, which you can then 

assign to a variable: 

$a = array( “Rahul”, “ravi”, “ajit”, “pratik” ); 

 In this line of code, an array of four elements is created, with each element containing a 

string value. 

 The array is then assigned to the variable $authors. You can now access any of the array 

elements via the single variable name, $a , as you see in a moment. 

 This array is an indexed array, which means that each of the array elements is accessed via 

its own numeric index, starting at zero. 

 In this case, the “Rahul” element has an index of 0 , “ravi” has an index of 1 , “ajit” has an 

index of 2 , and “pratik” has an index of 3 . 

 

 Accessing Array Elements: 

 Once you’ve created your array, how do you access the individual values inside it? In fact, you do this in much the same way as you access the individual characters within a 

string: 

$a = array( “Rahul”, “ravi”, “ajit”, “pratik” ); 

 

$b = $a\[0\]; // $myAuthor contains “Rahul” 

$c = $a\[1\]; // $anotherAuthor contains “ravi” 

 

$a = array( “Rahul”, “ravi”, “ajit”, “pratik” ); 

$pos = 2; 

echo $a\[$pos + 1\]; // Displays “ajit”

 

Output an Entire Array with print\_r() 

 You can’t just print an array with print() or echo() , like you can with regular variables, because these functions can work with only one value at a time. 

 

 However, PHP does give you a function called print\_r() that you can use to output the 

contents of an array for debugging. 

 

 Using print\_r() is easy — just pass it the array you want to output: 

 

print\_r( $a); 

 

  The following example code creates an indexed array and an associative array, then displays both arrays 

<?php

 $a = array( "Rahul", "ravi", "ajit", "pratik" ); 

print\_r ( $a ); 

?>

 

foreach loop Constructs: 

 There exists a foreach Constructs (command) that will apply a set of statements for each 

value in an array. 

 It works only on arrays, however, and will give you a big old error if you try to use it with 

another type of variable. 

 Your syntax for the foreach command looks like this: 

 

foreach ($array\_variable as $value\_variable) 

 { 

// .. do something with the value in $value\_variable

} 

 

foreach ($array\_variable as $key\_var => $value\_var) 

{

// .. do something with $key\_var and/or $value\_var

 

} 

 

 Example: 

<html>

<head>

<title>

 For Each Constructs 

</title>

</head>

<body>

<?php

 $a\[\] = "Rahul"; 

 $a\[\] = "Ravi"; 

 $a\[\] = "Pratik"; 

echo "My Name -->".'</br>'; 

foreach ($a as $b) 

 { 

 //these lines will execute as long as there is a value in $a 

 echo $b.'</br>'; 

 } 

?>

</body>

</html>

 

In-Built Functions used with Arrays:sort() and rsort()

 

i. sort(): 

 Sorts an array 

 Definition and Usage:- The sort() function sorts an array by the values. 

 This function assigns new keys for the elements in the array. Existing keys will be removed. 

 This function returns TRUE on success, or FALSE on failure. 

 Syntax:- sort(array,sorttype) 

 Array:- Required. Specifies the array to sort 

 Sorttype:- Optional. Specifies how to sort the array values. Possible values: 

 SORT\_REGULAR - Default. Treat values as they are (don't change types) 

 SORT\_NUMERIC - Treat values numerically 

 SORT\_STRING - Treat values as strings 

 SORT\_LOCALE\_STRING - Treat values as strings, based on local settings 

 Example:- 

<?php

 $animal = array("a" => "Dog", "b" => "Cat", "c" => "Horse"); 

 sort($animal); 

print\_r($animal); 

?>

 Output:- 

Array 

( 

\[0\] => Cat 

\[1\] => Dog 

\[2\] => Horse 

)

 

ii.rsort()

 Returns an array in the descending order 

 Definition and Usage:- The rsort() function returns an array in the descending order. 

 Array:- Required. Specifies an array 

 Preserve:-Optional. Possible values: true OR false 

 Specifies if the function should preserve the array's keys or not. 

 Example 

<?php

$a=array("a"=>"Dog","b"=>"Cat","c"=>"Horse"); 

print\_r(rsort($a)); 

?>

 Output:- 

Array ( \[c\] => Horse \[b\] => Cat \[a\] => Dog )

 

 

 

 

  

 

CHAPTER 7: USER-DEFINED FUNCTIONS AND 

GLOBAL VARIABLES IN PHP

 

 

1Function

Functions are most useful when you will be using the code in more than one place, but they can 

be helpful even in one-use situations, because they can make your code much more readable.

 

Syntax 

 Function definitions have the following form: 

function function-name ($argument-1, $argument-2, ..) 

{ 

statement-1; 

statement-2; 

... 

} 

 

Example:-1 

<?php

 function add($a, $b) 

 { 

 $c=$a+$b; 

 echo "Total-->".$c; 

 } 

 $x = 10; 

 $y = 20; 

 add($x,$y); 

?>

 

 Example:-2 (Return A value) 

<?php

 function add($a, $b) 

 { 

return $a+$b; 

 } 

 $x = 10; 

 $y = 20; 

 $c=add($x,$y); 

 echo "Total-->".$c; 

?>

 

Formal parameters versus actual parameters: 

 In the preceding examples, the arguments we passed to our functions happened to be 

variables, but this is not a requirement. 

 The actual parameters (that is, the arguments in the function call) may be any expression 

that evaluates to a value. 

 In our examples, we could have passed numbers to our function calls rather than variables, as in: 

 add(10,20); 

 Also, notice that in the examples we had a couple of cases where the actual parameter 

variable had the same name as the formal parameter (for example, $ a), and we also had 

cases where the actual and formal names were different. ($ x is not the same as $a.) 

 As we will see in the next section, this name agreement doesn’t matter either way—the 

names of a function’s formal parameters are completely independent of the world outside 

the function, including the function call itself.

 

 Example:- 

<?php

 function add($a,$b) 

 { 

 $c=$a+$b; 

 echo "Addition-->".$c.'</br>'; 

 } 

 function sub($d,$e) 

 { 

 $f=$d-$e; 

 echo "Sub-->".$f; 

 } 

 add(10,20); 

 $x=20; 

 $y=10; 

 sub($x,$y); 

?>

 

Argument passes : Call By Value and Call By Reference

 

 In PHP we can pass argument to the function by two way Call By Value and Call By Reference. 

 

 Call-by-Value 

 The default behavior for user-defined functions in PHP is call-by-value. 

 This means that when you pass variables to a function call, PHP makes copies of the variable 

values to pass on to the function. 

 So, whatever the function does, it is not able to change the actual variables that appear in 

the function call. This behavior can be good or bad. It’s a nice reassurance if you only want 

to use a function for its returned value, but it can also be a source of confusion and frustration if changing the passed variable is actually your goal. 

 Example:- 

<?php

 function display($b1,$b2) 

 { 

 $b1 = 30; 

 $b2 = 40; 

 } 

 $a1=10; 

 $a2=20; 

 display($a1,$a2); 

 echo $a1; 

 echo $a2; 

?>

 Output:- 

 10 

 20 

 

 Call-by-Reference 

 PHP offers two different ways to have functions actually modify their arguments: in the function definition and in the function call. 

 

Example:- 

<?php

 function display(&$b1,&$b2) 

 { 

 $b1 = 30; 

 $b2 = 40; 

 } 

 $a1=10; 

 $a2=20; 

 display($a1,$a2); 

 echo $a1; 

 echo $a2; 

?>

 Output:- 

 30 

 40 

 

Return Function

 Values are returned by using the optional return statement. 

 Any type may be returned, including arrays and objects. 

 This causes the function to end its execution immediately and pass control back to the line from which it was called. 

 If called from within a function, the return() function immediately ends execution of the current function, and returns its argument as the value of the function call.

 

Example:- 

<?php

 function sum($a,$b) 

 { 

 $c=$a+$b; 

 return $c; 

 } 

 $x=10; 

 $y=20; 

 $z=sum($x,$y); 

 echo $z; 

?>

 Output :- 

 30

 

Default arguments:

 To define a function with default arguments, simply turn the formal parameter name into an assignment expression. 

 If the actual call has fewer parameters than the definition has formal parameters, PHP will 

match actual with formal until the actual parameters are exhausted and then will use the 

default assignments to fill in the rest. 

 Example:- 

<?php

 function info($fname="rahul",$lname="patel") 

 { 

 echo $fname; 

echo $lname.'</br>'; 

 } 

 info(); 

 info("ravi"); 

 info("ravi","dave"); 

?>

 Output:- 

Rahulpatel

Ravipatel

Ravidave

 The main limitation of default arguments is that the matching of actual to formal parameters is determined by the ordering of both—it’s first-come, first-served.

 

Scope and Lifetime of Variables:

 

Local Variables

As you’ve seen, variables that are local to a function don’t exist outside the function. 

 In fact, all variables declared within a function are deleted when the function exits, and created a new when the function is next called. 

 This is usually what you want to happen, because it allows you to write nicely self-contained functions that work independently of each other.

 However, sometimes it’s useful to create a local variable that has a somewhat longer 

lifespan. 

 Static variables let you do just this. These types of variables are still local to a function, in 

the sense that they can be accessed only within the function’s code. 

 However, unlike local variables, which disappear when a function exits, static variables 

remember their values from one function call to the next. 

 To declare a local variable as static, all you need to do is write the word static before the 

variable name, and assign an initial value to the variable: 

 static $var = 0; 

 The first time the function is called, the variable is set to its initia l value (zero in this 

example). 

 However, if the variable ’ s value is changed within the function, the new value is 

remembered the next time the function is called. 

 The value is remembered only as long as the script runs, so the next time you run the script 

the variable is reinitialized. 

 Example:(Local variable) 

<?php

function nextNumber() 

{ 

 $counter = 0; 

 return ++$counter; 

} 

echo "I’ve counted to:".nextNumber()." <br/> "; 

echo "I’ve counted to:".nextNumber()." <br/>"; 

echo "I’ve counted to:".nextNumber()." <br/>"; 

?>

 Output: 

 I’ve counted to: 1 

 I’ve counted to: 1 

 I’ve counted to: 1 

 Each time the next Number() function is called, its $counter local variable is re - created and initialized to zero. 

 Then it’s incremented to 1 and its value is returned to the calling code. 

 So the function always returns 1, no matter how man y times it’s called. 

 Example:(Static variable) 

<?php

function nextNumber() 

{ 

 static $counter = 0; 

 return ++$counter; 

} 

echo "I’ve counted to:".nextNumber()." <br/> "; 

echo "I’ve counted to:".nextNumber()." <br/>"; 

echo "I’ve counted to:".nextNumber()." <br/>"; 

?>

 output: 

 I’ve counted to: 1 

 I’ve counted to: 2 

 I’ve counted to: 3

 You probably won’t use static variables that often, and you can often achieve the same 

effect (albeit with greater risk) using global variables.

 

Global variable 

 

 Although the concept of variable scope is extremely useful, occasionally you do actually 

want to create a variable that can be accessed anywhere in your script, whether inside or 

outside a function. Such a variable is called a global variable. 

 PHP supports global variables, but if you’re used to other pro gramming languages you’ll find 

PHP handles global slightly differently. 

 In PHP, all variables created outside a function are, in a sense, global in that they can be 

accessed by any other code in the script that ’ s not inside a function. 

 To use such a variable inside a function, write the word global followed by the variable 

name inside the function’s code block. 

 Example: 

<?php

$myGlobal = "RAHUL PATEL"; 

function hello() 

{ 

 global $myGlobal; 

 echo "$myGlobal"; 

} 

hello(); // Displays “RAHUL PATEL” ?>

 You can see that the hello() function accesses the $myGlobal variable by declaring it to be 

global using the global statement. 

 The function can then use the variable to display the greeting. 

 In fact, you don’t need to have created a variable outside a function t o use it as a global 

variable. 

 Take a look at the following script: 

<?php

function setup() 

{

global $myGlobal; 

$myGlobal = "Hello there!";

 

} 

function hello() 

{ 

 global $myGlobal; 

 echo "$myGlobal"; 

} 

setup(); 

hello(); // Displays “Hello there!” 

?>

 

 In this script, the setup() function is called first. 

 It declares the $myGlobal variable as global, and gives it a value. 

 Then the hello() function is called. 

 It too declares $myGlobal to be global, which means it can now access its value — 

previously set by setup() — and display it. 

 By the way, you can also declare more than one global variable at once on the same line — 

just separate the variables using commas: 

function myFunction() 

{ 

global $oneGlobal, $anotherGlobal; 

} 

 

 Finally, you can also access global variables using the $GLOBALS array. 

 This array is a special type of variable called a superglobal , which means you can access it 

from anywhere without using the global statement. 

 It contains a list of all global variables, with the variable names stored in its keys and the 

variable’s values stored in its values. Here’s an example that uses $GLOBALS : 

<?php

$myGlobal = "Hello"; 

function hello() 

{ 

 echo $GLOBALS\["myGlobal"\]; 

} 

hello(); // Displays “Hello there!” 

?>

 The hello() function accesses the contents of the $myGlobal variable via the $GLOBALSarray. 

 Notice that the function doesn’t have to declare the $myGlobal variable as global in order 

to access its value.

 

PHP SUPERGLOBALS

 

1.PHP Super Global Variables:

•Several predefined variables in PHP are "superglobals", which means that they are always accessible, regardless of scope - and you can access them from any function, class or file without having to do anything special

 

 

2.List PHP superglobals:

 

•$GLOBALS

•$\_SERVER

•$\_REQUEST

•$\_POST

•$\_GET

•$\_FILES

•$\_ENV

•$\_COOKIE

•$\_SESSION

 

$GLOBALS

 

$GLOBALS is a PHP super global variable which is used to access global variables from anywhere in the PHP script (also from within functions or methods).

a.PHP stores all global variables in an array called $GLOBALS\[index\]. The index holds the name of the variable.

b.The example below shows how to use the super global variable $GLOBALS:

<?php 

$x = 75; 

$y = 25;

function addition() { 

    $GLOBALS\['z'\] = $GLOBALS\['x'\] + $GLOBALS\['y'\]; 

}

 addition(); 

echo $z; 

?>

Output:100

 

$\_SERVER

a.$\_SERVER is a PHP super global variable which holds information about headers, paths, and script locations.

b.The example below shows how to use some of the elements in $\_SERVER:

<?php 

echo $\_SERVER\['PHP\_SELF'\];

echo "<br>";

echo $\_SERVER\['SERVER\_NAME'\];

echo "<br>";

echo $\_SERVER\['HTTP\_HOST'\];

echo "<br>";

echo $\_SERVER\['HTTP\_REFERER'\];

echo "<br>";

echo $\_SERVER\['HTTP\_USER\_AGENT'\];

echo "<br>";

echo $\_SERVER\['SCRIPT\_NAME'\];

?>

OUTPUT:

/php/demo\_global\_server.php

www.w3schools.com

www.w3schools.com

http://www.w3schools.com/php/showphp.asp?filename=demo\_global\_server

Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/52.0.2743.116 Safari/537.36

/php/demo\_global\_server.php

 

The following table lists the most important elements that can go inside $\_SERVER:

 

 
| Element/Code || Description |
| --- | --- |
| $\_SERVER\['PHP\_SELF'\] || Returns the filename of the currently executing script |
| $\_SERVER\['GATEWAY\_INTERFACE'\] || Returns the version of the Common Gateway Interface (CGI) the server is using |
| $\_SERVER\['SERVER\_ADDR'\] || Returns the IP address of the host server |
| $\_SERVER\['SERVER\_NAME'\] || Returns the name of the host server (such as www.w3schools.com) |
| $\_SERVER\['SERVER\_SOFTWARE'\] || Returns the server identification string (such as Apache/2.2.24) |
| $\_SERVER\['SERVER\_PROTOCOL'\] || Returns the name and revision of the information protocol (such as HTTP/1.1) |
| $\_SERVER\['REQUEST\_METHOD'\] || Returns the request method used to access the page (such as POST) |
| $\_SERVER\['REQUEST\_TIME'\] || Returns the timestamp of the start of the request (such as 1377687496) |
| $\_SERVER\['QUERY\_STRING'\] || Returns the query string if the page is accessed via a query string |
| $\_SERVER\['HTTP\_ACCEPT'\] || Returns the Accept header from the current request |
| $\_SERVER\['HTTP\_ACCEPT\_CHARSET'\] || Returns the Accept\_Charset header from the current request (such as utf-8,ISO-8859-1) |
| $\_SERVER\['HTTP\_HOST'\] || Returns the Host header from the current request |
| $\_SERVER\['HTTP\_REFERER'\] || Returns the complete URL of the current page (not reliable because not all user-agents support it) |
| $\_SERVER\['HTTPS'\] || Is the script queried through a secure HTTP protocol |
| $\_SERVER\['REMOTE\_ADDR'\] || Returns the IP address from where the user is viewing the current page |
| $\_SERVER\['REMOTE\_HOST'\] || Returns the Host name from where the user is viewing the current page |
| $\_SERVER\['REMOTE\_PORT'\] || Returns the port being used on the user's machine to communicate with the web server |
| $\_SERVER\['SCRIPT\_FILENAME'\] || Returns the absolute pathname of the currently executing script |
| $\_SERVER\['SERVER\_ADMIN'\] || Returns the value given to the SERVER\_ADMIN directive in the web server configuration file (if your script runs on a virtual host, it will be the value defined for that virtual host) (such as someone@w3schools.com) |
| $\_SERVER\['SERVER\_PORT'\] || Returns the port on the server machine being used by the web server for communication (such as 80) |
| $\_SERVER\['SERVER\_SIGNATURE'\] || Returns the server version and virtual host name which are added to server-generated pages |
| $\_SERVER\['PATH\_TRANSLATED'\] || Returns the file system based path to the current script |
| $\_SERVER\['SCRIPT\_NAME'\] || Returns the path of the current script |
| $\_SERVER\['SCRIPT\_URI'\] || Returns the URI of the current page |

 

  

 

CHAPTER 8: PHP FORMS HANDLING, FORM VALIDATIONS

(USING $\_GET, $\_POST, $\_REQUEST)

 

 

1.The ACTION attribute of the <FORM> :

The ACTION attributes calls the given ASP file, when the SUBMIT button is clicked. If the ACTION attribute is not given for a <FORM> then the ASP is requesting itself, it is a “Self-referencing” page.

2.The GET and POST method:

a.The GET method sends the variable names and the value pairs of the Form by concatenating it along with the URL as a Query String.

b.The POST method sends the variable names and value pairs of the Form as encoded along with the HTTP headers.

i.Advantage of POST : Security of information

ii.Disadvantage of POST: The resulting response page cannot be bookmarked.

3.PHP has two global variables $\_GET and $\_POST which are used to retrieve user input information from HTML forms.

4.Super global variable $\_REQUEST to collect the value of the input field instead of $\_GET or $\_POST.

5.Practical Examples: Separate HTML and PHP files.

 

Q. Write the HTML and PHP program to create the Welcome message:

 ![](Images/image00172.jpeg)

Ans: HTML file save on desktop(wel.html)

<html>  

<body>

 

<form action="welcome.php" method="post">

Name: <input type="text" name="name"><br>

E-mail: <input type="text" name="email"><br>

<input type="submit">

</form>

 

</body>

</html>

PHP file saved in htdocs (welcome.php)

 

<?php

echo "Your name is: " . $\_POST\["name"\], "<br>";

echo "You Email is " . $\_POST\["email"\];

?>

Output :

Welcome John

Your email address is john.doe@example.com

Practical Examples: Single  PHP file with HTML form.

 Q. Write a single PHP file which contains the form that accepts the Name and Age of the user displays it back when the submit button is clicked. (Note: In the example $\_GET is used.)

Ans:

<html>

<head>

<title>$\_POST result in URL</title>

</head>

<body>

<FONT SIZE="6pt" color=blue FACE="Comic Sans MS">

<H3>Handling HTML forms</H3>

</FONT>

<HR>

<form name="DisplayDetails" method="GET" 

action="<?php echo $\_SERVER\["PHP\_SELF"\]; ?>">

Name: <input type="text" name="fname" />

Age: <input type="text" name="age" />

<input type="submit" name="btnSubmit" id="btnSubmit" value="Submit"/>

</form>

<?php

echo "Your name is: " . $\_GET\["fname"\], "<br>";

echo "You age is " . $\_GET\["age"\];

?>

</body>

</html>

 

Practical Examples: Validating Forms

Q. Write the PHP program which displays a form that accepts User Name. Then it validates if the User Name is empty and display messages.  (Note: In the example $\_REQUEST is used.)

Ans:

<html>

<body>

<form method="post" action="<?php echo$\_SERVER\['PHP\_SELF'\];?>">

  Name: <input type="text" name="fname">

  <input type="submit">

</form>

 

<?php

if ($\_SERVER\["REQUEST\_METHOD"\] == "POST") {

    // collect value of input field

    $name = $\_REQUEST\['fname'\]; 

    if (empty($name)) {

        echo "Name is empty";

    } else {

        echo $name;

    }

}?>

 

PHP $\_FILES,$\_EVN, $\_COOKIE, $\_SESSION

1.$\_FILES:  This this the superglobal array that help us to upload files to the server.

It has various values that can provide information regarding the file that is to be uploaded, they are as follows:

 

 
| Superglobal || Description |
| --- | --- |
| $\_FILES\['my-file'\]\['name'\] || Original Name of File Before It Was Uploaded |
| $\_FILES\['my-file'\]\['type'\] || The MIME Type of File, Provided By the Browser |
| $\_FILES\['my-file'\]\['size'\] || Size of the File (In Bytes) |
| $\_FILES\['my-file'\]\['tmp\_name'\] || Location of Temporary File on Server |
| $\_FILES\['my-file'\]\['error'\] || Any Error Codes Resulting From the File Upload |

 

 

Procedure to upload a file to the server:

 

a)Create a HTML form to get the name of the file that is required to be uploaded.

We’ll start with the basics: let’s write an HTML form that allows users to upload files. HTML makes this quite easy with its<input type="file"/> tag. By default, however, only the name of the file selected by the user is sent. To have the file itself submitted with the form data, we need to add enctype="multipart/form-data" to the <form> tag:

 

b)Next, create the PHP file that will check if the file was successfully uploaded using is\_uploaded\_file() function.

 

 

Example 1: Write the HTML and PHP programs to upload a file onto the server.

 ![](Images/image00173.jpeg)

a)HTML form named:myupload.html

<form action="http://localhost/fup.php" method="post" enctype="multipart/form-data">

<input type="file" name="my-file" size="50" maxlength="25"><br>

<input type="submit" name="upload" value="Upload">

</form>

 

b)PHP program named fup.php

 

<?php

  if (is\_uploaded\_file($\_FILES\['my-file'\]\['tmp\_name'\]) && $\_FILES\['my-file'\]\['error'\]==0) {

    echo "The file was uploaded successfully but has not been saved.<br>";

echo "The file is temporarily stored: " . $\_FILES\['my-file'\]\['tmp\_name'\] . "<br>";

echo "The file name was: " . $\_FILES\['my-file'\]\['name'\] . "<br>";

echo "The file type is: " . $\_FILES\['my-file'\]\['type'\] . "<br>";

echo "The file size is: " . $\_FILES\['my-file'\]\['size'\] . "<br>";

  } else {

echo "The file was not uploaded successfully.";

echo "(Error Code:" . $\_FILES\['my-file'\]\['error'\] . ")";

  } ?>

Output:

The file was uploaded successfully but has not been saved.

The file is temporarily stored: C:\\xampp\\tmp\\php734D.tmp

The file name was: UPTEST.txt

The file type is: text/plain

The file size is: 9

 

2.$\_COOKIE:A cookie is a piece of date(file) that the browser saves on the client’s machine, that is can access the next time the browers visits the website.

(i)The common uses of Cookies are:

a.To store username/password information so that the user doesnot have to log in every time they visit the website.

b.To remember the user’s theme

(ii)setcookies(): The setcookies() function is used to create a cookie.

The syntax is: setcookie(name, value, expire, path, domain);

(iii)The superglobal$\_cookieis used to access the cookies.

Example 2: Write a PHP program to create a cookie and another PHP program to display its value.

PHP File 1: mycookie.html

<?php

setcookie("Example", "Whatever Value I Want", time()+2592000);

?>

 

PHP File 2: displaycookie.php

 

<?php

  if (isset($\_COOKIE\["Example"\])) 

 {

    echo $\_COOKIE\["Example"\];

  } 

else 

{

    echo "No Cookie Named 'Example' Is Set";

  }

?

Output : Whatever Value I Want

 

3.$\_SESSION\[ \]: This is the superglobal variable that is used to Session level variables.

a.What is a Session?

Ans:

The interation of a client with the server is called as a session.

A session is started with the session\_start() function.

A session ends when the user closes the browser window or session\_destroy() function is called.

Every session has an unique SessionID.

A session variables can be created to store information about the user.

Session variables are more secure than Cookies because session variables are stoted on the serverside whereas the cookies are stored on the clients computer.

Examples

<?php

// Start the session

session\_start();

?>

 

<?php

// Set session variables

$\_SESSION\["favcolor"\] = "green";

$\_SESSION\["favanimal"\] = "cat";

echo "Session variables are set.";

?>

 

<?php

session\_start();

?>

 

<?php

// Echo session variables that were set on previous page

echo "Favorite color is " . $\_SESSION\["favcolor"\] . ".<br>";

echo "Favorite animal is " . $\_SESSION\["favanimal"\] . ".";

?>

 

<?php

session\_start();

?>

 

<?php

print\_r($\_SESSION);

?>

Modify a PHP Session Variable

<?php

session\_start();

?>

 

 

<?php

// to change a session variable, just overwrite it 

$\_SESSION\["favcolor"\] = "yellow";

print\_r($\_SESSION);

?>

 

Destroy a PHP Session

To remove all global session variables and destroy the session, use session\_unset() and session\_destroy():

<?php

session\_start();

?>

 

<?php

// remove all session variables

session\_unset(); 

 

// destroy the session 

session\_destroy(); 

?>

 

 

 

 

  

CHAPTER 9: WORKING WITH TEXT FILES

AND ERROR HANDLING IN PHP

 

 

This chapter will explain following functions related to files −

•Opening a file

•Reading a file

•Writing a file

•Closing a file

I.Opening and Closing Files

1.fopen() function :

i)The PHP fopen() function is used to open a file. It requires two arguments stating first the file name and then mode in which to operate.

ii)If an attempt to open a file fails then fopen returns a false value, otherwise it returns a file pointer which is used for further reading or writing of that file.

iii)Files modes can be specified as one of the six options in this table.

 

 
| Mode || Purpose |
| --- | --- |
| r || Opens the file for reading only.Places the file pointer at the beginning of the file. |
| r+ || Opens the file for reading and writing.Places the file pointer at the beginning of the file. |
| w || Opens the file for writing only.Places the file pointer at the beginning of the file and truncates the file to zero length. If files does not exist then it attempts to create a file. |
| w+ || Opens the file for reading and writing only.Places the file pointer at the beginning of the file and truncates the file to zero length. If files does not exist then it attempts to create a file. |
| a || Opens the file for writing only.Places the file pointer at the end of the file.If files does not exist then it attempts to create a file. |
| a+ || Opens the file for reading and writing only.Places the file pointer at the end of the file.If files does not exist then it attempts to create a file. |

 

If files does not exist then it attempts to create a file.

2.fclose() function :

a.After making a changes to the opened file it is important to close it with the fclose() function. The fclose() function requires a file pointer as its argument and then returns true when the closure succeeds or false if it fails.

II.Reading a file

1.fread() function:

a.Once a file is opened using fopen() function it can be read with a function called fread(). 

b.This function requires two arguments. These must be the file pointer and the length of the file expressed in bytes.

2.fgets() function : The fgets() function is used to read a single line from a file and after a call to this function the file pointer has moved to the next line.

3.The fgetc() function is used to read a single Character from a file and after a call to this function the file pointer has moved to the next character.

4.filesize() function :The files length can be found using the filesize() function which takes the file name as its argument and returns the size of the file expressed in bytes.

5.feof() function : Returns True if the end of text file has been reached, else returns False.

 

So here are the steps required to read a file with PHP.

•Open a file using fopen() function.

•Get the file's length using filesize() function.

•Read the file's content using fread() function.

•Close the file with fclose() function.

EXAMPLE 1: File Reading in PHP

<?php

$fileName="d:\\myFile.txt";

$fp = fopen($fileName,"r");

if( $fp==false)

{

  echo ("Error in opening file");

exit();

}

 

$fileSize=filesize( $fileName);

$fileData=fread( $fp, $fileSize);

?>

EXAMPLE 2 : Reading a File Line by Line

Example:

<?php

$fileName="d:\\myFile.txt";

$fp = fopen($fileName,"r");

if( $fp==false)

{

  echo ("Error in opening file");

exit();

}

 

while(!feof($fp))

{

echo fgets($fp). "<br>";

}

?> 

EXAMPLE 3 : Reading a File Character by Character and display the number of times character “s” appears.

Example:

<?php

$fileName="d:\\myFile.txt";

$fp = fopen($fileName,"r");

if( $fp==false)

{

  echo ("Error in opening file");

exit();

}

 

while(!feof($fp))

{

 if  (fgetc($fp)= =”s”)

{

   $count=;

}

}

echo “The total number of times character s appeared is :”.$count;

?> 

 

III.File Writing in PHP

1.fwrite() function :

a)Using the PHP fwrite() function, a new file can be written or text can be appended to an existing file. 

b)This function requires two arguments, first specifying a file pointer and the string of data that is to be written. Optionally a third integer argument can be used to specify the length of the data to write. If the third argument is used, file writing would will stop after the specified length has been reached.

EXAMPLE 1: File Writing in PHP :

<?php

$fileName="d:\\myFile.txt";

$fp = fopen($fileName,"w");

if( $fp==false)

{

  echo ("Error in opening file");

exit();

}

fwrite( $fp,"This is a sample text to write\\n");

?>

IV.Closing a File in PHP

1.fclose() function :

In PHP it is not system critical to close all your files after using them because, file will auto close after PHP code finishes execution.

You can close file, using fclose() function.

Example:

<?php

$fileName="d:\\myFile.txt";

$fp = fopen($fileName,"w");

if( $fp==false)

{

  echo ("Error in opening file");

exit();

}

 

//some code to be executed

 

fclose( $fp);

?>

 

V.file() function :

a. The PHP file() function is used to  read the entire content of a file in to an array.

b. This function also opens the file in read mode and there is no need to open and close the file separately.

c. Each array element contains one line form the file.

Example : PHP program to read the entire text file and display is line-by-line using file().

<?php

$FArray=file('myFile.txt');

foreach($FArray as $line)

{

echo $line.'<br>';

} ?> 

  

CHAPTER 10: PHP ERROR HANDLING

 

1.Types of Error :

a.Syntax Error: Occurs when we break any gramatic rules of programing. 

Example: $abc=”hello”    // the ; is missed out

b.Run time error:This is an error that occurs when the program is running:

Example: Trying to connect to a database when the database server is down.

c.Logical Error: It is an error cause because of wrong algorithm in programming.

2.PHP handles errors in three methods:

a.PHP die() function

b.Setting custom handler and error triggering

c.Error reporting

3.Using PHP die() function: die() function displays a message and stops executing the current script.

Example: When opening a text file if the file doesnot open – then error message is displayed and script stops.

<?php

$file=fopen("welcome.txt","r");

if(!file\_exists("welcome.txt")) 

{

  die("File not found");

} 

else 

{

  $file=fopen("welcome.txt","r");

echo “File is ready for reading”;

} ?>

4.Creating Custom Error Handler & PHP Error Reporting: 

a.It is possible to override the default PHP errors by using CustomError() function.

b.The function has to handle minimum 2 parameters (error level and error message)

c.Example of custom error handlers:

<?php

   function handleError($errno, $errstr,$error\_file,$error\_line) 

    {

      echo "<b>Error:</b> \[$errno\] $errstr – 

$error\_file:$error\_line";

      echo "<br />";

      echo "Terminating PHP Script";

      die();

   }      //set error handler

set\_error\_handler("handleError");

      //trigger error

myFunction();

?>

d.set\_error\_handler() function:The default error handler for PHP can be changed using this function.

e.trigger\_error() function :PHP also provides trigger\_error() function that can be used to trigger an error.

Example:

<?php

$test=2;

if ($test>=1) {

  trigger\_error("Value must be 1 or below");

}  ?>