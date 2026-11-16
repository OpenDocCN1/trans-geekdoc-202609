# Numeric Literals

PHP understands both integer and floating-point numbers. Integers can be specified in decimal, octal, or hexadecimal notation:

```
<?php
echo (255);
echo (0xFF);
echo (0377);
?>
```

Hexadecimal numbers are identified by the preceding zero followed by an x. Octal numbers simply begin with a zero.

The echo command always outputs integers using decimal notation, even if they were specified as hex or octal, so the above code writes out the number 255 three times.

You can declare negative integers by preceding any of these notations with a minus sign. To declare floating-point numbers, you can use either decimal point or exponential notation. The following are all valid:

```
<?php
echo (0.001);
echo (1e-3);
echo (-3.8716E32);
?>
```

The e or E character in the last two versions is regular "exponent".

# Boolean Literals

PHP also understands the words true and false, and you can use them in certain operations which require a Boolean value. Like all PHP keywords, these are case insensitive, and you can use true, TRUE, and True interchangeably.

# Variables

A variable in PHP, like in most other languages, is simply a container for some data. You can give your variables names, put data into them, and then refer back to them at a later point in your program to access the stored data.

PHP identifies variables using the dollar sign ($). The name for a variable will always begin with this character whenever you refer to it. After the dollar sign, your variable name can consist of any number of alphanumeric characters and underscores, although the first character cannot be a number or an underscore. So, the following are all valid variable names:

```
$a
$a2
$my_name
$height_in_metres_above_sea_level
```