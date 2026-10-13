
# PHP Variables and Constants

Since the `$var` variable stores a floating point number so it's a float variable.

## PHP Constants

An identifier which holds a value and that value remain the same throughout the script. The value cannot be changed throughout the script. It starts with a letter or underscore. It is global throughout the script.

To create a constant in your script you can use `define()` function.

```php
<?php
define("STORE", "Estore Diversity");
echo STORE;
?>
```

In the above example I have define a constant named `STORE`. It holds the value `Estore Diversity`.

Now whenever I will use and print the `STORE` constant in my script it will display the value as `Estore Diversity`.

So the main purpose to define constant is that when we want to define some identifiers that will hold some value that are not going to change throughout the code and are available globally to the script.

# CHAPTER 6: PHP Datatypes

Datatype tells the type of data. A value which is stored in a variable can be of any datatype. There are number of datatypes:

- String
- Integer
- Boolean
- Array
- Object
- NULL
- Float

Any sequence of characters included between single or double quote is a String. For example:

```php
<?php
$var = "Hello World";
echo $var;
?>
```

The above `$var` is a string variable as it holds sequence of characters between double quotes.

A variable holding digits which is a non-decimal number is an Integer. Integer can be positive or negative but it should be whole numbers.

For example:

```php
<?php
$a = 10;
echo $a;
?>
```

In the above example variable `$a` holds a number 10 which donot have any decimal point and thus it is an Integer.

A variable which holds boolean value ie true or false is a boolean variable. Boolean values are used in conditional blocks. For example if some variable value is equal to true or false then the following condition will be executed. If and Else condtion have been explained in next section.

A floating point number is a number which has decimal point. For example:

```php
<?php
$b = 2.45;
?>
```

Arrays are the datatype which stores multiple values of same type in one variable. We can define array by using `array()` function. This has been explained in detail in Array section.

Objects are the datatype which stores data and also the information on how to process the data. An object must be explicitly declared. First we define a class with `Class` keyword. It holds some properties and methods. Then we create an instance ie the object of the class to use the methods and properties.

```php
<?php
class A {
    public $var = "hello";
    public function demo() {
        echo $this->var;
    }
}
$object = new A();
echo $object->demo();
?>
```

Here we have declared a class `A`. It holds `$var` property and a method `demo()`. Property is the variable and method is the function in the class.

![](image_rsrcDV.jpg)
Illustration 2: Class Datatype

`demo()` method is accessing the variable `$var` and value "hello" will get printed. `$object` is the object created for class `A`. Check the output of the code below:

NULL is a special data type which holds no value. It has only NULL as value. A variable can be set with NULL value.

```php
<?php
$x = NULL;
var_dump($x);
?>
```

![](image_rsrcDW.jpg)
Illustration 3: NULL Datatype

# CHAPTER 7: PHP Operators

Operators are used to perform different operations on variable and values. Suppose we want two variables and we want to know the summation of that. Then we will perform and addition of that two variables using Arithmetic Operators.

We can divide the operations into different groups:

- Arithmetic Operators
- Assignment operators
- Comparison Operators
- Increment/Decrement Operators
- Logical Operators
- String Operators
- Array operators
- Conditional assignment operators

## Arithmetic Operators

### Addition

`+` is the addition operator. This is used when we want sum of two variables. For example:

```php
<?php
$x = 10;
$y = 20;
echo $x + $y;
?>
```

![](image_rsrcDX.jpg)
Illustration 4: Addition Operator

### Subtraction

`-` is the subtraction operator. This is used when we want to subtract one variable from other variable.

```php
<?php
$x = 50;
$y = 25;
echo $x - $y;
?>
```

Here by using subtraction operator `$y` variable is deducted from `$x` variable. Check the output below:

![](image_rsrcDY.jpg)
Illustration 5: Subtraction Operator

### Multiplication

`*` is the multiplication operator. This is used when we want a product of two variables.

```php
<?php
$x = 10;
$y = 20;
echo $x * $y;
?>
```

Here in above example we have two variable `$x` and `$y`. We are mutiplying it to get the product of two variables. Check the output below:

![](image_rsrcDZ.jpg)
Illustration 6: Mutiplication operator

### Division

`/` is the divison operator which is used when we want to divide one variable by another variable. For example:

```php
<?php
$x = 100;
$y = 10;
echo $x / $y;
?>
```

Here we have one variable `$x` which is getting divided by `$y` and return a value. Check the output below:

![](image_rsrcE0.jpg)

### Modulus

`%` is the modulus operator which returns the remainder when one variable is divided by another variable. For example:

```php
<?php
$x = 100;
$y = 40;
echo $x % $y;
?>
```

In the above example we have taken a variable `$x` and it is getting divided by `$y`. The result will be the remainder we are getting by dividing the two variables. Check out the output below:

![](image_rsrcE1.jpg)
Illustration 7: Modulus Operator

### Exponentiation

`**` is the exponentiation operator. It is used when we want to print any variable with some power. For example:

```php
<?php
$x = 2;
$y = 3;
echo $x ** $y;
?>
```

In the above example we are finding 2 to power of 3. Check the outut below:

![](image_rsrcE2.jpg)
Illustration 8: Exponentiation Operator

## Assignment Operators

With assignment operators we can set values in a variable. Basic assignment operator in PHP is `=`.

For example:

- `$x += $y;` is same `$x = $x + $y;`
- `$x -= $y;` is same as `$x = $x - $y;`
- `$x *= $y;` is same as `$x = $x * $y;`
- `$x /= $y;` is same as `$x = $x / $y;`
- `$x %= $y` is same as `$x = $x % $y;`

## Comparison operators

- `==` is Equal operator. For example `$x == $y` Here this will return true if `$x` value is equal to `$y` value.
- `===` is the identical operator. For example: `$x === $y` returns true if and only if the values and type of both variables re same.
- `!=` is the not equal to operator. For example: `$x != $y` returns true if value of both variables are different.
- `<>` is the not equal to operator. For example: `$x != $y` returns true if value of both variables are different.
- `!==` Not identical operator. For example `$x !== $y` returns true if either the value is not same or the type is not same.
- `>` is the Greater operator. For example: `$x > $y` is true when `$x` value is greater than `$y`.
- `<` is the Less than operator. For example: `$x < $y` is true when `$x` value is less than `$y`.
- `>=` is Greater than or equal to operator. For example: `$x >= $y` is true when `$x` value is greater than or equal to `$y`.
- `<=` is Less than or equal to operator. For example: `$x <= $y` is true when `$x` value is less than or equal to `$y`.
- `<=>` is the spaceship operator. For example: `$x <=> $y` returns an integer less than, equal to or greater than zero if value of `$x` is less than, equal to or greater than `$y`.

## Increment and Decrement operators

- `$x++` will return `$x` and then increment it's value by one.
- `++$x` will increment value of `$x` by one and then return `$x`.
- `$x--` will return `$x` and then decrease it's value by one.
- `--$x` will decrement the value by one and then return `$x`.

## Logical operators

- **And operator**: `$x and $y` gives a result true if both `$x` and `$y` are true.
- **`&&` operator**: `$x && $y` gives a result true if both `$x` and `$y` are true.
- **OR operator**: `$x or $y` gives a result true if either `$x` and `$y` are true.
- **`||` operator**: `$x || $y` gives a result true if either `$x` and `$y` are true.
- **`!` Not operator**: `!$x` gives a result true if `$x` is not true.

# CHAPTER 8
