
I like to use the following conventions when creating variables, functions, methods, constants, and classes in PHP, which I will be using throughout this book:

| Property | Example |
|---|---|
| Variable Names | $snake_case |
| Function/Method Names | function camelCase() |
| Classes | class StudlyCaps |
| Constants | const ALL_CAPS |

Regarding naming your variables, a recommended practice is to choose good descriptive names for your variables (e.g., $temperature_fahrenheit). Also, most predefined PHP variables start with a $_ (i.e. $_POST[]). I recommend that you do not create any variables starting with an underscore (_) as this might be confusing to other PHP developers that have to maintain your code.

### Types of Variables

All data is eventually represented to a computer using 1s and 0s. However, a programming language interpreter or compiler must know the data type representation before correctly converting the data into a format the computer can use. Like several other programming languages (e.g., JavaScript), PHP is a dynamically typed language (as opposed to a statically typed language like Java). A variable will dynamically change its type implicitly based on the data type of the value assigned to it or the context in which it's used.

### Scalar Data Types

PHP supports the following scalar data types:

- Boolean
- integer
- float
- string

## 3. WHY VARIABLES MATTER

### Booleans

A Boolean data type contains a logical value that is either TRUE or FALSE. Boolean values are typically used in conditional logic statements:

```
$passed_drivers_license_exam = TRUE;

if ($passed_drivers_license_exam == TRUE)
{
    echo "Award driver's license.<br/>";
}
```

The online PHP documentation has more information about Boolean data types[4].

### Integers

An integer data type contains a whole number that can be negative, zero, or positive. They are typically represented in the base-10 number system but can be represented using base 2, 8, 10, or 16.

For more information, see the PHP docs about integer data types[5].

### Floats

A floating-point data type contains real numbers which can be expressed either using decimals and/or scientific notation:

```
// Pascal to Pound per square inch
$pa_to_psi = 0.000145037738;

// Pascal to Pound per square inch
$pa_to_psi = 145037738e-12;

// Pascal to Pound per square inch
$pa_to_psi = 1.45037738e-4;
```

See the PHP documentation for more information about floating point data types[6].

[4] Boolean data types: http://php.net/language.types.boolean
[5] integer data types: http://php.net/language.types.integer
[6] floating point data types: http://php.net/language.types.float

### Strings

A string is a group of characters enclosed in either single (') or double (") quotes. The type of opening quote must match the closing quote:

```
echo "This is a string";
echo 'This is also a string';
echo "This is a string with 'single-quotes' embedded";
echo 'This is a string with "double-quotes" embedded';
```

If you have a string surrounded by double-quotes (") you can contain a double-quote in your string by escaping it with the back-slash (\). Likewise, you can embed single-quotes by escaping them if they are inside of a string surrounded by single-quotes:

```
echo "This is a string surrounded by \\";
echo 'I don\'t like using contractions';
```

See the PHP manual for more information about string data types[7].

### Compound Data Types

PHP defines several “compound” data types which allow you to contain or aggregate multiple pieces of data of the same data type under a single entity. PHP supports the following compound data types:

- array
- object
- callable
- iterable

### Array

Arrays in PHP are ordered maps, which are a way to associate a key with its corresponding value. Therefore, arrays in PHP are known as “associative arrays.”

An array is created using the array() language construct. Here’s how to create an empty array:

```
$fahrenheit_temperatures = array();
```

> *PHP also supports short array syntax, which lets you define an array like this:*
> `$temperatures = [];`

To add (or push) values onto the end of an array, use the [] syntax immediately following the variable name. Without specifying a key when adding values to an array, the key will be the next integer value:

```
$fahrenheit_temperatures[] = 32; // 32 is associated with key 0
$fahrenheit_temperatures[] = 100; // 100 is associated with key 1
```

Keys can be specified using either strings or integers. Associative arrays often use strings as keys to give meaning to the values they associate with in the array. To initialize an array with named keys, use the rocket (=>) operator:

```
$us_state_capitals = array(
    "Wisconsin" => "Madison",
    "California" => "Sacramento"
);
```

To add a named key to the end of the array, specify it in between []s:

```
$us_state_capitals["Florida"] = "Tallahassee";
```

Note that array keys are unique, so if you specify a key that already exists, you will be replacing its value.

A useful function for viewing the contents of an array is print_r()[8]. Embed print_r() in a set of <pre> tags as shown in Listing 3.1.

### Listing 3.1.

```
1. <pre>
2. <?php
3. $us_state_capitals = array(
4.     "Wisconsin" => "Madison",
5.     "California" => "Sacramento"
6. );
7. 
8. print_r($us_state_capitals);
9. ?>
10. </pre>
```

[8] print_r(): http://php.net/print_r

This function call produces the following output:

```
Array
(
        [Wisconsin] => Madison
        [California] => Sacramento
)
```

You can find more information on array data types[^9] online.

### Object

PHP is an “Object-Oriented” programming language, and it allows you to create objects. Objects are created from “class” definitions. Class definitions are like complex types that allow you to group your program data (what your program knows) and your program functions (what your program does) in one place to represent modular components in software better. We will cover object-oriented programming in more detail later in the book.

To create an object, you “instantiate” it from a class definition using the new keyword as in Listing 3.2.

### Listing 3.2.

```
<?php

class Radio
{
    function turnOnRadio()
    {
        echo "Turning radio on";
    }
}

$car_radio = new Radio();
$car_radio->turnOnRadio();
```

The PHP manual has more information on objects[^10].

[^9] array data types: http://php.net/language.types.array
[^10] objects: http://php.net/language.types.object

### Callable

“Callables” can be created in PHP by naming a function to call as a string and invoking it with the call_user_func() function[11]. You can do this with simple functions, static class methods, and instantiated class methods. The following is a simple example of using a callback.

```php
function exampleCallbackFunction()
{
    echo "Hello world!";
}

call_user_func('exampleCallbackFunction');
```

For more information on callables[12], check the online manual.

### Iterable

An iterable[13] is a pseudo-type. It enforces arguments to functions or return values from functions are traversable like arrays. You may see this typehint when looking at the API for PHP functions. It mainly means that you can loop through the variable using a foreach.

### Special Data Types

PHP defines a couple of special data types as well. These are:

- resource
- NULL

### Resource

A “resource” is a special variable containing a reference to an external resource. Resources are typically used for working with files and databases:

```php
$db_connection = mysqli_connect(
    'localhost', 'db_user', 'db_password', 'db_to_use'
);

$file_handle = fopen('file.txt', 'r');
```

For more information on resources[14] and their usages, see the online documentation.

[11] call_user_func() function: http://php.net/call_user_func
[12] callables: http://php.net/language.types.callable
[13] iterable: http://php.net/language.types.iterable
[14] resources: http://php.net/language.types.resource
