

# Table of Contents

- Chapter 1: PHP INTRODUCTION
- Chapter 2: VARIABLES
- Chapter 3: DATA TYPES
- Chapter 4: OPERATORS
- Chapter 5: CONTROL STRUCTUERS
- Chapter 6: ARRAYS
- Chapter 7: FUNCTIONS
- Chapter 8: FORMS IN PHP
- Chapter 9: GLOBAL VARIABLES
- Chapter 10: SESSIONS
- Chapter 11: COOKIES
- Chapter 12: WORKING WITSH FILE
- Chapter 13: OBJECT ORIENTED PHP

# INTRODUCTION

I want to thank you and congratulate you for choosing this book. This book contains elaborate steps, strategies and guidelines on how to create codes using the correct syntax, keywords, and punctuation marks. It also provides tips on how to correctly use arrays, forms, conditional statements, sessions etc. You will also learn how to open, read, write, and close files in PHP. There are sample programs(examples) that can serve as your guidelines when writing your code. This book also contains useful information about PHP, including their features. I hope it will be of help to you!

# COPYRIGHT

By www.computingtutorial.com

This document is oriented towards providing exact and reliable information in regards to the topic and chapters covered. It is not legal in any way to reproduce, duplicate, or transmit any part of this document in either electronic means or in printed format.

Recording of this publication is strictly prohibited and any storage of this document is not allowed unless with permission from the author. The information provided herein is stated to be truthful and consistent, in that any liability, in terms of inattention or otherwise, by any usage or abuse of any policies, processes, or directions contained within is the solitary responsibility of the recipient reader.

Under no circumstances will any blame be held against the author for any damages, or monetary loss due to the information herein, either directly or indirectly. Respective authors own all copyrights not held by the publisher. The information herein is offered for informational purposes only, and is universal as so. The presentation of the information is without contract or any type of guarantee assurance.

All rights reserved (2015)

# Chapter 1: PHP INTRODUCTION

## Requirement

Before you proceed to study php, it is recommended that you have a basic understanding of the following:

- CSS
- HTML

## What is PHP

- PHP is an acronym for Hypertext Preprocessor
- PHP is a HTML embedded scripting language
- PHP scripts are executed on the server
- PHP files have extension ".php"

## What PHP can do

It is also helpful to think of PHP in terms of what it can do for you.

- Reduce the time to create large websites.
- Create a customized user experience for visitors based on information that you have gathered from them.
- can generate dynamic page content
- can collect form data
- can send and receive cookies
- can add, delete, modify data in your databases
- can create, open, read, write, and close files on the server
- can encrypt data

## Why choose PHP

- PHP runs on various operating system platforms (Windows, Unix, etc.)
- PHP is easy to learn and runs efficiently on the server side
- PHP is compatible with almost all servers used today (Apache,etc.)
- PHP supports a wide range of databases
- PHP is freely available

## PHP Syntax

A PHP script starts with `<?php` and ends with `?>`:

```php
<?php 

// PHP code here 

?>
```

A PHP file usually contains HTML tags, and some PHP scripting code.

As you notice in the below example, there was a semicolon after the line of PHP code. The semicolon signifies the end of a PHP statement and should never be forgotten. The semi colon terminates that statement.

Here is an example of a simple PHP file, with a PHP script that uses a PHP function (built-in) `echo` to output the text "Hello World!":

```html
<html> 
<head> 
<title>My First PHP Page</title> 
</head> 
<body> 
<?php 
echo "Hello World!"; 
?> 
</body> 
</html>
```

Display:

Hello World!

## Comments in PHP

A comment in PHP code is a line that is not executed as part of the program. Its purpose is to be read by someone who is editing the code.

PHP supports three forms or ways of expressing a comment.

Comments are useful for:

- To remind yourself what you did - Most programmers have experienced coming back to their Comments, this remind you of what you were thinking when you wrote the code
- To let others understand what you are doing - Comments let other programmers understand each of your steps

`// This is a single line comment`

`\# This is also a single line comment`

```
/*
This is a multiple lines comment block that spans over more than one line
*/
```

## Case sensitivity in PHP

In PHP, all variables are case-sensitive.

In the next chapter is a detailed discussion of the variables.

In the example below, only the first statement will display the value of the `$pet` variable (because `$pet`, `$PeT`, and `$PET` are treated as three totally different variables):

Example

```html
<html> 
<body> 
<?php 
$pet="cat"; 
echo "My animal is a " . $pet . "<br>"; 
echo "My animal is a " . $PeT . "<br>"; 
echo "My animal is a " . $PET. "<br>"; 
?> 
</body> 
</html>
```

In PHP, all user-defined functions, keywords, and classes are case-insensitive.

In the example below, all two `echo` statements below are legal:

Example

```html
<html> 
<body> 
<?php 
echo "Hello World!<br>"; 
ECHO "Hello World!<br>";
?> 
</body> 
</html>
```

## White spaces

With HTML, whitespace is ignored between PHP statements. This is to mean that there can be one line of PHP code, then 2 or more lines of blank space before the next line of PHP code. Because of this you can indent your code and the PHP interpreter will ignore those spaces as well.

Here is an elaborate example:

```html
<html> 
<head> 
<title>My First PHP Page</title> 
</head> 
<body> 
<?php 
echo "Hello World!"; 
echo "Hello World!"; 
?> 
</body> 
</html>
```

Display:

Hello World!Hello World!

# Chapter 2: PHP VARIABLES

## Variable defination

A variable is a means of storing a value, such as text string "Hello World!" or the integer value 30. A variable can then be reused throughout your code, instead of having to type out the actual value over and over again, in other words variables can be termed as "containers" for storing information.

In PHP you define a variable with the following form:

`$variable_name = Value;`

just Like in mathematics

`r=1`
`s=2`
`t=r+s`

the letters `r`, `s` hold the numbers 1, 2 respectively.

From the expression `t=r+s` above, we can calculate the value of `r` to be 3.

In PHP these letters are called variables.

Example

```php
<?php 
$r=1; 
$s=2; 
$t=$r+$s; 
echo $t; 
?>
```

Example

```php
<?php 
$txt="Hello world"; 
?>
```

## Conventions for assigning variables

- Variables with more than one word should be separated with underscores. `$my_variable`
- A variable starts with the `$` sign, followed by the name of the variable
- Variable names are case sensitive (`$r` and `$R` are two different variables)
- A variable name cannot start with a number
- A variable name must start with a letter or the underscore character
- A variable name can only contain alpha-numeric characters and underscores (`A-z`, `0-9`, and `_`)

# Chapter 3: PHP DATA TYPES

## PHP Data Types

String, Integer, Floating point numbers, Boolean, Array.

## String

A string is a sequence of characters, like "Hello world!".

A string can be any text inside quotes. You can use single or double quotes, either will work efficiently.

Example

```php
<?php 
$x = "Hello world!"; 
echo $x;  
?>
```

## Integers

An integer is a number without decimals.

Rules for integers:

