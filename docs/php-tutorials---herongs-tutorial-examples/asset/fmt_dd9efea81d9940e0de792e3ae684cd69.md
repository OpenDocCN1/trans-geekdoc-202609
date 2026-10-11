
# PHP Script File Syntax

## PHP Statement Delimiter and Comments

This section provides a tutorial example on how to write PHP statements and comment in PHP source code files. PHP uses semicolon `;` as the statement delimiter. Comments can be entered in Perl, Java, or C styles.

PHP uses semicolon `;` as the statement delimiter. PHP statements can be written in the source code file in different ways:

* The most common way is to write one statement per one code line.
* But you can split one statement into multiple code lines if you have a long statement.
* You can also write multiple statements in one code line, if you want to.

If you want to enter comments into the PHP source code, you can do it in 3 ways:

* Perl style: Using `#`
* Java style: Using `//`
* C style: Using `/*` and `*/`

Here is a tutorial example on how to write PHP statements and comments:

```php
<?php
/* StatementSamples.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
*/

# The next 1 statement is written in 2 code lines.
print "I am tossing a coin now. "
   . "Guess what the result will be?\n";

/* I am using the rand() function to simulate the randomness of
tossing a coin. The rand(min,max) function returns a random integer
between the specified minimum number and maximum number.
-- This is a sample of C style comment
*/

# The next 1 statement is written in 1 code line.
$count = 0;
while ($count < 7) {
   # Next 2 statements are written in 1 code line.
   $count++; print "Round # $count:\n";

   $coin = rand(0,1);
   if ($coin==1) {
      print "   Head\n"; // Java style comment
   } else {
      print "   Tail\n"; # Perl style comment
   }
}
?>
```

There is no surprises in the output:

```
herong> \php\php StatementSamples.php

I am tossing a coin now. Guess what the result will be?
Round # 1:
   Tail
Round # 2:
   Tail
Round # 3:
   Head
Round # 4:
   Tail
Round # 5:
   Tail
Round # 6:
   Head
Round # 7:
   Tail
```

# PHP Data Types and Data Literals

This chapter provides tutorial notes and example codes on PHP data types and data literals. Topics include 8 data types supported in PHP; data literals to provide data values in PHP code for different data types; integer and float value overflow conditions.

* [Data Types Supported in PHP](#part0018.xhtml)
* [Data Literals Supported in PHP](#part0019.xhtml)
* [Data Literals Examples for Integer, String and Other Data Types](#part0020.xhtml)
* [Overflow of Integer and Float Values](#part0021.xhtml)

## Takeaways

* PHP supports 8 data types: boolean, integer, float, string, array, object, resource, null.
* PHP integer data type uses the 32-bit signed integer storage format.
* PHP float data type uses the 64-bit floating-point number storage format, the IEEE 754 double-precision standard.
* PHP string data type uses the 8-bit byte storage format.
* PHP array data type uses key-value pairs to manage array elements. PHP arrays are really associate arrays, maps or hash tables in other programming languages.
* PHP handles integer value overflow conditions by automatically converting results to float data type.
* PHP handles float value overflow conditions by automatically converting results to "infinite" or 0.

## Data Types Supported in PHP

This section describes all 8 data types supported in PHP with a tutorial example showing how to use them: boolean, integer, float, string, array, object, resource, null.

PHP supports 8 data types:

* **boolean**: It has only two literal values: `true` and `false`. I am not sure what is the storage size of a boolean data item.
* **integer**: It is stored as signed integers with 32 bits. That means an integer data item can hold an integer value in the range of -2,147,483,648 and 2,147,483,647. Integer literals have 3 forms: decimal, octal (prefixed with `0`), and hexadecimal (prefixed with `0x`).
* **float**: It is stored as IEEE double floating point numbers with 64 bits. Float literals have the standard floating point number form.
* **string**: It is a sequence of 8-bit characters. String literals have 3 forms: single quoted, double quoted, and heredoc syntax. These forms are very similar to Perl.
* **array**: It stores an ordered map of pairs of keys and values. This is quite different than the array type used in other languages. Arrays in PHP are similar to associate arrays in Perl.
* **object**: It stores an instance of a class.
* **resource**: It represents an external resource like a file, or a database connection.
* **null**: It represents a status of a variable in which no value is assigned the variable. Null type has only one literal value: `null`.

Here is a tutorial sample PHP script that shows you all 8 data types:

```php
<?php
/* DataTypeSamples.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
*/

$isValid = '1'==1; // boolean data type
print "\n Boolean data type - '1'==1 evaluation result: ".$isValid;

$yearDays = 365; // integer data type
print "\n Integer data type - Days in a year: ".$yearDays;

$equatorLength = 3.14159*2*6371; // float data type
print "\n Float data type - Length of the equator: ".$equatorLength;

$greetingMessage = "Hello Herong!"; // float data type
print "\n String data type - Greeting message: ".$greetingMessage;

$monthDays = array("Jan"=>31,"Feb"=>28,"Mar"=>31); // array data type
print "\n Array data type - Days in each month: "
   .$monthDays['Jan'].", ".$monthDays['Feb'].", ".$monthDays['Mar']
   ."...";

$currentTime = new DateTime(); // object data type
print "\n Object data type - Current time: "
   .$currentTime->format(DATE_ATOM);

$currentDirectory = opendir("."); // resource data type
print "\n Resource data type - First item in the current directory: "
   .readdir($currentDirectory);
closedir($currentDirectory);

$nothing = null; // null data type
print "\n Null data type - Null means nothing:".$nothing;
?>
```

If you run this sample script, you should get:

```
herong> \php\php DataTypeSamples.php

 Boolean data type - '1'==1 evaluation result: 1
 Integer data type - Days in a year: 365
 Float data type - Length of the equator: 40030.13978
 String data type - Greeting message: Hello Herong!
 Array data type - Days in each month: 31, 28, 31...
 Object data type - Current time: 2005-02-12T21:19:47-05:00
 Resource data type - First item in the current directory: .
 Null data type - Null means nothing:?>
```

## Data Literals Supported in PHP

This section describes data literals to specify values for different data types: reserved key words; decimal, octal and hexadecimal numbers; floating point number format; single quoted, double quoted, and heredoc strings.

Data literals are ways to provide values for different data types in PHP source code. PHP data literals rules are summarized below:

1. **boolean data literals**: Data literals for boolean data type are two reserved key words: `true` and `false`. Note that `true` and `false` are case in-sensitive - `TRUE` and `FALSE` are also valid boolean literals.

2. **integer data literals**: Data literals for integer data type have 3 forms:

* **Decimal form**: A sequence of decimal digits, 0 to 9, with the first digit being > 0. Integer data literals in decimal form can be prefixed with or without positive or negative signs. For example: `366`, `-42`, `6371`, ...
