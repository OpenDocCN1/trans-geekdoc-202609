
# Core PHP Programming

- <http://www.hotscripts.com/PHP/Scripts%20and%20Programs/> - HotScripts' PHP Section
- <http://www.samoun.com/alain/ultraedit/> -UltraEdit wordfiles for PHP
- <http://www.dcl.sourceforge.net/> - Double Choco Latte, a bug tracking system
- <http://www.phorum.org/> - Phorum, threaded discussions
- <http://horde.org/imp/> - Web to mail interface
- <http://www.htmlwizard.net/phpMyAdmin/> - MySQL Web interface
- <http://www.kidsister.twj.org/> - KidSister, software for tracking tasks
- <http://www.midgard-project.org/> - Midgard

# Jobs and Services

- <http://hosts.php.net/> - Searchable database of hosting services that offer Searchable database of hosting services that offer PHP
- <http://www.phpbuilder.com/jobs/> - Jobs listing at PHP Builder
- <http://www.schaffner.net/emp/> - Brian Schaffner's Jobs listing

# Appendix G. PHP STYLE GUIDE

This is a sample style guide based on the one used by the FreeTrade project <http://www.working-dogs.com/freetrade>.

# Comments

Every file should start with a comment block describing its purpose, version, author, and a copyright message. The comment block should be a block comment in the style below.

```
/
** File: test
** Description: This is a test program
** Version: 1.0
** Created: 1/1/2000
** Author: Leon Atkinson
** Email: leon@clearink.com
**
** Copyright (c) 2000 Your Group. All rights reserved.
/
```

Every function should have a block comment specifying name, input/output, and what the function does. 

```
/
** Function: doAdd
** Input: INTEGER a, INTEGER b
** Output: INTEGER
** Description: Adds two integers
/
function doAdd($a, $b)
{
    return(a+b);
}
```

Ideally, while, if, for or similar block of code should be preceded by a comment explaining what happens in the block. Sometimes this is unnecessary. 

```
// get input from user char by char
while(getInput($inputChar))
{
  storeChar($inputChar);
}
```

Explain sections of code that aren't obvious.

```
//TAB is ASCII 9
def (TAB, 9);

// change tabs to spaces in userName
while ($index=0; $index < ($userName); $index++) {
  $userName[$index] = ereg_replace(TAB, " ", $userName[$index]);
}
```

# Function Declarations

As previously, functions should have a comment block explaining what they do and their input/output. The function block should align starting at one tab from the left margin unless the function is part of a class definition. Opening and closing braces should also be one tab from the left margin. The body of the function should be indented two tabs.

```php
<?php
/**
** doAdd
** Adds two integers
** Input: $a, $b
** Output: sum of $a and $b
*/
function doAdd($a, $b) {
  return(a+b);
}
?>
```

# Compound Statements

Flow control primitives should be compound statements, even if they only contain one instruction. Like functions, compound statements should have opening braces that start at column zero relative to scope.

Code within the braces forms a new scope and should be indented.

```
// tell the user if a is equal to ten
if ($a==10)
{
    printf("a is ten.\n");
}
else
{
    printf("a is not ten.\n");
}
```

# Naming

The names of variables, constants, and functions are to begin with a lowercase letter. In names that consist of more than one word, the words are written together and each word starts with an uppercase letter. Use short names for variables in a small scope, such as just inside a for loop. Use longer names for variables in larger scopes.

Function names should begin with a lowercase letter and use capitals for subsequent words.

```
/*
** Function getAddressFromEnvironment
** Input: $Prefix - prefix used to generate address form
** Return: array suitable for addressFields
*/
function getAddressFromEnvironment ($Prefix)
{
    global $AddressInfo;
    // get list of all address fields
    //from the AddressInfo array
    reset($AddressInfo);
    while ($field, $info) = each ($AddressInfo))
    {
        $ReturnValue[$field] = trim ($GLOBALS[$Prefix][$info[ADDR_VAR]])
    }
    return ($ReturnValue);
}
```

FunctionState names should suggest an action or verb. Use names like updateAddress makeStateSelector. Variable names should suggest a property or noun, such as userName, and Width. Use pronounceable names, such as User, not usr. Use descriptive names for variables used globally, or short names for variables used locally.

Be consistent and use parallelism. If you are abbreviating name like num, always use that abbreviation. Don't switch to no or nmbr.

Values that are treated as constants, that is not changed by the program, should be declared in the beginning of the scope in which they are used. In PHP this is done with the define function. Each of these constants should be paired with a comment that explains use. They should be named exclusively with uppercase letters, with underscores to separate words. You should use constants in place of any arbitrary values to improve readability.

```
// maximum length of a name to accept
define("MAX_NAME_LENGTH", 32);
print("Maximum name length is " . MAX_NAME_LENGTH);
```

Constants that belong to a specific module should use a consistent prefix.

```
//text with which to label the field
define("ADDR_LABEL", 0);
```

```
//name of the form field (sans prefix of course)
define("ADDR_VAR", 1);
```

```
//error message to display for missing fields
define("ADDR_ERROR", 2);
```

Variables are to be declared with the smallest possible scope. This means using function parameters when it's appropriate.

Lines should not exceed 78 characters. Break long lines at common separators and align the fragments in an indented block.

```
if(($size > max_size) OR
(isSizeInvalid($size)))
{
    print("Invalid size");
}
```

# Expressions

Write conditional expressions so that they read naturally aloud. Sometimes eliminating not operator (!) will make an expression more understandable. Use parentheses liberally to resolve ambiguity. Using parentheses can force an order of evaluation. This saves the time a reader may spend remembering precedence of operators.

Keep each line simple. The ternary operator (x ? 1 : 2) usually indicates too much code on one line. if..elseif..else is usually more readable. Don't sacrifice clarity for cleverness.

# WORLD WIDE WEB

SECOND EDITION

# core PHP programming

USING PHP TO BUILD DYNAMIC WEB SITES

LEON ATKINSON

Master PHP 4,
an open source,
high-performance,
cross-platform
solution for
server-side
scripting!

Core PHP Programming, Second Edition is the #1 practical guide to PHP 4 Web developers. With the guidance of top PHP developer Leon Atkinson,
you'll learn everything you'll need to build robust, fast Web applications—and deploy them on leading Web servers, including Apache and Microsoft Internet servers.

Atkinson covers PHP syntax, the key building blocks of PHP scripts, and every every PHP function including I/O data, and math functions, time, date, configuration, database, graphics, and network functions. He presents PHP work in sample code that demonstrates sorting, searching, parsing, string evaluation, and more. You'll even find detailed, real-world insights into PHP 4 program design and debugging!

# Core Programming delivers

- Thorough, easy-to-understand coverage of PHP syntax and functions
- Step-by-step guide for PHP database integration
- Design and optimization techniques for maximum performance and extensibility
- Practical debugging solutions

> PRAISE FOR THE FIRST:
"Core PHP Programming has proved itself an invaluable technical reference handy recommended for every developer. Their detail PHP manual is often assumes too much knowledge on behalf of the user. Leon's strength is that he does not try to sound more technical than needed, simply for the sake of impressing other programmers. In short, a must-have for any PHP user beginning advanced!"
Zark Beatty,
Enterprise Web Engineer

CD-ROM includes PHP 4 source code and Windows binaries all the code examples from the book!

# About the Author

LEON ATKINSON is Chief Technologist for Clear Ink Corporation, an agency
offering traditional and Web communication services. He is creator and
maintainer of the Firetrade project, an Open Source ecommerce toolkit, and
an enthusiastic supporter of PHP.

U.S. $44.99 | Canada $54.00

PRENT HALL
Upper Saddle River, NJ 07458

www.php.net

ISBN 0-13-069398-6 90000

0 76092 00825 5 9 780130 893987
