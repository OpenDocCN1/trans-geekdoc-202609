
# Basic Computer Coding: PHP

```php
$addresses[0] = "spam@cyberpromo.net";
echo $addresses;    // prints "Array"
```

Using simple assignment to initialize an array in your program can lead to code like this:

```php
$addresses[0] = "spam@cyberpromo.net";
$addresses[1] = "abuse@example.com";
$addresses[2] = "root@example.com";
```

That's an indexed array, with integer indices beginning at 0. Here's an associative array:

```php
$price['gasket'] = 15.29;
$price['wheel'] = 75.25;
$price['tire'] = 50.00;
```

An easier way to initialize an array is to use the array() construct, which builds an indexed array, and the index values (starting at 0) are created automatically:

```php
$addresses = array("spam@cyberpromo.net", "abuse@example.com", "root@example.com");
```

To create an associative array with array(), use the => symbol to separate indices (keys) from values:

```php
$price = array(
  'gasket' => 15.29,
  'wheel' => 75.25,
  'tire' => 50.00
);
```

> The use of whitespace and alignment. We could have bunched the code, but it would not have been as easy to read (this is equivalent to the previous code), or as composed of (key, value) pairs, such that each possible is easy to add or remove values:

Associative array is an data type composed of a collection of (key, value) pairs, each at once in the collection.

```php
$price = array('gasket' => 15.29, 'wheel' => 75.25, 'tire' => 50.00);
```

You can also specify an array using a shorter, alternate syntax:

```php
$days = ['gasket' => 15.29, 'wheel' => 75.25, 'tire' => 50.0];
```

# PHP Arrays

To construct an empty array, pass no arguments to array():
```php
$addresses = array();
```

You can specify an initial key with => and then a list of values.
The values are inserted into the array starting with that key, with subsequent values having sequential keys:

```php
$days = array(1 => "Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun");
// 2 is Tue, 3 is Wed, etc.
```

If the initial index is a nonnumeric string, subsequent indices are integers beginning at 0. Thus, the following code is probably a mistake:

```php
$whoops = array('Fri' => "Black", "Brown", "Green");
```

```php
// same as
$whoops = array('Fri' => "Black", 0 => "Brown", 1 => "Green");
```

# Adding Values to the End of an Array

To insert more values into the end of an existing indexed array, use the [] syntax:

```php
$family = array("Fred", "Wilma");
$family[] = "Pebbles"; // $family[2] is "Pebbles"
```

This construct assumes the array's indices are numbers and assigns elements to the next available numeric index, starting from 0. Attempting to append to an associative array without appropriate keys is almost always a programmer mistake, PHP will give the new elements numeric indices without issuing a warning:

```php
$person = array('name' => "Fred");
$person[] = "Wilma"; // $person[0] is now "Wilma"
```

# Assigning a Range of Values

The range() function creates an array of consecutive integer or character values between and including the two values you pass to it as arguments. For example:

```php
$numbers = range(2, 5); // $numbers = array(2, 3, 4, 5);
$letters = range('a', 'z'); // $letters holds the alphabet
$reversedNumbers = range(5, 2); // $reversedNumbers = array(5, 4, 3, 2);
```

Only the first letter of a string argument is used to build the range:
range("aaa", "zzz"); // same as range('a','z')

# Getting the Size of an Array

The count() and sizeof() functions are identical in use and effect.
They return the number of elements in the array. There is no stylistic preference about which function you use. Here's an example:

```php
$family = array("Fred", "Wilma", "Pebbles"); // $size is 3
$size = count($family);
```

This function counts only values that are actually set:
$confusion = array(10 => "ten", 11 => "eleven", 12 => "twelve"); // $size is 3
$size = count($confusion);

# Padding an Array

To create an array with values initialized to the same content, use array_pad(). The first argument to array_pad() is the array, the second argument is the minimum number of elements you want the array to have, and the third argument is the value to give any elements that are created. The array_pad() function returns a new padded array, leaving its argument (source) array alone.

Here's array_pad() in action:

```php
$scores = array(5, 10);
$padded = array_pad($scores, 5, 0); // $padded is now array(5, 10, 0, 0, 0)
$padded = array_pad($scores, -5, 0); // $padded is now array(0, 0, 0, 5, 10);
```

Notice how the new values are appended to the end of the array. If you want the new values added to the start of the array, use a negative argument:

If you pad an associative array, existing keys will be preserved. New elements will have numeric keys starting at 0.

# 5.2.5 PHP Arrays

A multi-dimensional array each element in the main array can also be an array. And each element in the sub-array can be an array, and so on. Values in the multi-dimensional array are accessed using multiple index.

![](img/f8aa82c4ef45031ca4eadc2bb946c87a_158_0.png)

The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays:
```php
$row0, $row1, $row2
```
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays
The values in an array themselves can be arrays

..
