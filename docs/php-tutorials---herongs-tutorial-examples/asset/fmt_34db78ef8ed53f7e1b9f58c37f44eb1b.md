
# FunctionTips.php

```php
<?php
#  FunctionTips.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#

function msg() {
  print("Hello world!\n");
}
msg();
print("\n");

function hello($f) {
  print("Hello $f!\n");
}
hello("Bob");
print("\n");

function getYear() {
  $year = date("Y");
  return $year;
}
print("This year is: ".getYear()."\n");
print("\n");

function f2c($f) {
  return ($f - 32.0)/1.8;
}
print("Celsius: ".f2c(100.0)."\n");
print("Celsius: ".f2c(-40.0)."\n");
print("\n");

function swap($a, $b) {
  $t = $a;
  $a = $b;
  $b = $t;
}
$x = "PHP";
$y = "JSP";
print("Before swapping: $x, $y\n");
swap($x, $y);
print("After swapping: $x, $y\n");
print("\n");

# Passing arguments by value with references not allowed any more
# $x = "PHP";
# $y = "JSP";
# print("Before swapping: $x, $y\n");
# swap(&$x, &$y);
# print("After swapping: $x, $y\n");
# print("\n");

function ref_swap(&$a, &$b) {
  $t = $a;
  $a = $b;
  $b = $t;
}
$x = "PHP";
$y = "JSP";
print("Before swapping: $x, $y\n");
ref_swap($x, $y);
print("After swapping: $x, $y\n");
print("\n");

function average($array) {
  $sum = array_sum($array);
  $count = count($array);
  return $sum/$count;
}
$numbers = array(5, 7, 6, 2, 1, 3, 4, 2);
print("Average: ".average($numbers)."\n");
print("\n");

function shrink($array) {
  array_splice($array,1);
}
$numbers = array(5, 7, 6, 2, 1, 3, 4, 2);
print("Before shrinking: ".join(",",$numbers)."\n");
shrink($numbers);
print("After shrinking: ".join(",",$numbers)."\n");
print("\n");

# Passing arguments by value with references not allowed any more
# $numbers = array(5, 7, 6, 2, 1, 3, 4, 2);
# print("Before shrinking: ".join(",",$numbers)."\n");
# shrink(&$numbers);
# print("After shrinking: ".join(",",$numbers)."\n");
# print("\n");

function ref_shrink(&$array) {
  array_splice($array,1);
}
$numbers = array(5, 7, 6, 2, 1, 3, 4, 2);
print("Before shrinking: ".join(",",$numbers)."\n");
ref_shrink($numbers);
print("After shrinking: ".join(",",$numbers)."\n");
print("\n");

function powerBall() {
  $array = array(rand(1,55), rand(1,55), rand(1,55),
                 rand(1,55), rand(1,55), rand(1,42));
  return $array;
}
$numbers = powerBall();
print("Lucky numbers: ".join(",",$numbers)."\n");
print("\n");

function myPassword() {
  $password = "U8FIE8W0";
  print("Defined inside the function? ". isset($password)."\n");
}
myPassword();
print("Defined outside the function? ". isset($password)."\n");
print("\n");

$login = "fyicenter";
function myLogin() {
  print("Defined inside the function? ". isset($login)."\n");
}
myLogin();
print("Defined outside the function? ". isset($login)."\n");
print("\n");

$intRate = 5.5;
function myAccount() {
  global $intRate;
  print("Defined inside the function? ". isset($intRate)."\n");
}
myAccount();
print("Defined outside the function? ". isset($intRate)."\n");
print("\n");

$favor = "Blue";
function getFavor() {
  global $favor;
  return $favor;
}
$myFavor = getFavor();
print("Favorite tool: $myFavor\n");
$favor = "Pink";
print("Favorite tool: $myFavor\n");
print("\n");

$favor = "Blue";
function &getFavorRef() {
  global $favor;
  return $favor;
}
$myFavor = &getFavorRef();
print("Favorite tool: $myFavor\n");
$favor = "Pink";
print("Favorite tool: $myFavor\n");
print("\n");

function printKey($key="download") {
  print("PHP $key\n");
}
printKey();
printKey("hosting");
print("\n");

function myAverage() {
  $count = func_num_args();
  $args = func_get_args();
  $sum = array_sum($args);
  return $sum/$count;
}
$average = myAverage(102, 121, 105);
print("Average 1: $average\n");
$average = myAverage(102, 121, 105, 99, 101, 110, 116, 101, 114);
print("Average 2: $average\n");
print("\n");
?>
```

## 运行结果

If you run this sample script, you should get:

```
herong> \php\php FunctionTips.php

Hello world!

Hello Bob!

This year is: 2019

Celsius: 37.777777777778
Celsius: -40

Before swapping: PHP, JSP
After swapping: PHP, JSP

Before swapping: PHP, JSP
After swapping: JSP, PHP

Average: 3.75

Before shrinking: 5,7,6,2,1,3,4,2
After shrinking: 5,7,6,2,1,3,4,2

Before shrinking: 5,7,6,2,1,3,4,2
After shrinking: 5

Lucky numbers: 48,16,54,26,2,30

Defined inside the function? 1
Defined outside the function?

Defined inside the function?
Defined outside the function? 1

Defined inside the function? 1
Defined outside the function? 1

Favorite tool: Blue
Favorite tool: Blue

Favorite tool: Blue
Favorite tool: Pink

PHP download
PHP hosting

Average 1: 109.33333333333
Average 2: 107.66666666667
```

# Arrays - Ordered Maps

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml) ∟ Arrays - Ordered Maps

This chapter provides tutorial examples and notes about arrays. Topics include creating arrays with the array constructor, using integer keys or string keys in arrays, accessing values through keys, array related built-in functions.

> [What Is an Array](#part0058.xhtml)
>
> [Creating Arrays - Examples](#part0059.xhtml)
>
> [Array Related Built-in Functions](#part0060.xhtml)
>
> [Usage Examples of Array Functions](#part0061.xhtml)

## Takeaways

*   An array can be created with the array constructor, `array()`.
*   A pair of key and value can be specified as `key=>value` as an argument in the constructor.
*   A value stored in an array can be accessed as `$array_variable["key"]`.
*   An array can be used as a stack through `array_push()` and `array_pop()` functions.
*   `foreach () {}` statement can be used to loop through all values in an array.

# What Is an Array

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml) ∟ [Arrays - Ordered Maps](#part0057.xhtml) ∟ What Is an Array

This section describes what is an array - an ordered pairs of keys and values. If sequential integer keys are used, an array is a simple indexed list. If string keys are used, an array is a map.

## What Is an Array?

An array is a data type that represents an ordered pairs of keys and values. Arrays in PHP are different than arrays in most of other languages. Basic rules for PHP's arrays are:

1.  An array can be constructed by the array constructor, like:

    ```
    $myArray = array(k1=>v1, k2=>v2, ..., kn=>vn);
    ```

    where `k1`, `k2`, ..., and `kn` are keys of integer type or string type. `v1`, `v2`, ..., and `vn` are values of any data types.

2.  The value of a given key in an array can be expressed by the array variable followed by the key in square brackets, like:

    ```
    print $myArray[kn];
    ```

3.  The value of a given key in an array can be modified by an assignment statement, like:

    ```
    $myArray[kn] = new_value.
    ```

4.  A new pair of key and value can be added to an array by an assignment statement, like:

    ```
    $myArray[kx] = vx
    ```

5.  If a string key represents an integer, it will be used as an integer key. So `$myArray['7']` is the same as `$myArray[7]`.

6.  If the key is missing in an array assignment or an array constructor, an integer key of 0, or the highest integer key plus 1, will be provided. So `$myArray[] = "Last"` assigns "Last" to a new integer key.

7.  An empty string is also a valid string key, like:

    ```
    $myArray[''] = vy;
    ```

8.  A pair of key and value can be removed by using the `unset()` function, like:

    ```
    unset($myArray[kn]);
    ```

9.  Pairs of keys and values are ordered in an array like a queue. New pairs are always added at the end of the array.

# Creating Arrays - Examples

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml) ∟ [Arrays - Ordered Maps](#part0057.xhtml) ∟ Creating Arrays - Examples

This section provides a tutorial example on how to create arrays in different ways.

Here is a tutorial example PHP script to show you some of array rules described in the previous section:
