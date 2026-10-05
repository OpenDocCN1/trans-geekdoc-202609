
# non_static.php

Static Variable is a variable that has been allocated “statically”, meaning that its lifetime (or "extent") is the entire run of the program.

```php
<?php

function nonstatic() {

  $value = 0;
  $value += 1;

  return $value;
}

nonstatic();
nonstatic();
nonstatic();
nonstatic();

echo nonstatic(), "\n";

?>
```

In the above example, we have a normal, non-static variable. We increment the variable each time the function is called. We call the function 5 times. However, non-static variables are initiated for each call of the function. After 5 function calls the $value equals to 2.
The static variables are initiated only once, when the function is first called. They retain their value afterwards.

# static.php

```php
<?php

function staticfun() {
static $value = 0;
$value += 1;
return $value;
}

staticfun();
staticfun();
staticfun();
staticfun();

echo staticfun(), "\n";

?>
```

After 5 consecutive calls, the $value is equal to 5.

```
$ php nonstatic.php
2
$ php static.php
6
```

# 3.1.7 PHP anonymous functions

Anonymous functions do not have a name.
anonymous.php

```php
<?php
$var = function() {
echo "This is anonymous function\n";
};

$var();
```

## PHP Function

We assign a function body to a variable. It is possible to call the function only via this variable.

```php
$var = function () {
echo "This is anonymous function\n";
};
```

Notice the semicolon after the closing bracket. It is required because the construct is an assignment.

```bash
$ php anonymous.php

This is anonymous function
```

This is the output of the example.

# Remember

A function name must start with a letter or underscore character not with a number, optionally followed by the more letters, numbers, or underscore characters. Function names are case-insensitive.

# 3.1.8 Passing arguments by value and by reference

PHP supports two ways of passing arguments to functions. The default way is passing arguments by value. When we pass arguments by value, the function works only with the copies of the values. This may lead to performance overheads when we work with large amounts of data.

When we pass values by reference, the function receives a reference to the actual value. The original values are affected when modified. This way of passing values is more time and space efficient. On the other hand, it is more error prone.

Which of passing arguments should we use? It depends on the situation. Say we have a set of data, salaries of employees. If we want to compute some statistics of the data, we do not need to modify them. We pass by values. If we work with large amounts of data and the speed of computation is critical, we pass by reference. If we want to modify the data, e.g. do some reductions or raises to the salaries, we might pass by reference.
The following two examples cover both concepts.

![](img/f8aa82c4ef45031ca4eadc2bb946c87a_89_0.png)

1993, the National Center for Supercomputing Applications (NCSA), a unit of the University of Illinois at Urbana-Champaign, released NCSA Mosaic, the first popular graphical Web browser, which played an important part in expanding the growth of the nascent World Web.

```php
swap1.php
<?php
function swap($a, $b) {
    $temp = $a;
    $a = $b;
    $b = $temp;
    echo "inside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";

    $a = 4;
    $b = 7;

    echo "outside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";

    swap($a, $b);

    echo "outside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";
}
?>
```

## PHP Function

The swap function swaps the numbers between $a and $b. Variable is a storage location memory address paired with an associated symbolic name (identifier), which contains some known or unknown quantity referred to as a value. At the beginning, these two variables are initiated. We call the swap() function. The function takes $a and $b as parameters.

$a = 4;
$b = 7;

Inside the swap() function, we change the values. Note that $a$ and $b$ variables are defined locally. They are valid only inside the swap() function.

```bash
$ php swap1.php

outside swap function:
$a is 4
$b is 7
inside swap function:
$a is 7
$b is 4
outside swap function:
$a is 4
$b is 7
```

The output shows that the original variables were not affected. The next code passes values to the function by reference. The original variables are changed inside the swap() function.

```php
swap2.php
<?php
function swap(&$a, &$b) {
    $temp = $a;
    $a = $b;
    $b = $temp;
    echo "Inside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";

    $a = 4;
    $b = 7;

    echo "outside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";

    swap(&$a, &$b);

    echo "outside swap function:\n";
    echo "\$a is $a \n";
    echo "\$b is $b \n";
}
?>
```

The example is almost identical to the previous one. Except for ampersand characters.

```bash
$ php swap2.php

outside swap function:
$a is 4
$b is 7
inside swap function:
$a is 7
$b is 4
outside swap function:
$a is 4
$b is 7
```

Here we see that the swap() function really changed the values of the variables.

# 3.1.9 PHP recursion

Recursion, in mathematics and computer science, is a method of defining functions in which the function being defined is applied within its own domain. In other words, a recursive function calls itself to do its job. Recursion is an alternative to iteration. Recursion is the main approach in functional languages.

Factorial of a non-negative integer, denoted by n!, is the product of all positive integers less than n.

A typical example is the calculation of the factorial.

```php
recursion.php
<?php
function factorial($n) {
    if ($n==0) {
        return 1;
    } else {
        return $n * factorial($n - 1);
    }
}
echo factorial(4), "\n";
echo factorial(10), "\n";

?>
```

In this code example, we calculate the factorial of numbers. Inside the body of the factorial function, we call the factorial function with a modified argument. The function calls itself.

```bash
$ php recursion.php
24
3628800
```

These are the results.

![](img/f8aa82c4ef45031ca4eadc2bb946c87a_93_0.png)

So what does the syntax for defining function look like? Here is a simple example:

```php
<?php
function addNumbers($num1, $num2) {
    $result = $num1 + $num2;
    return $result;
}
```

# 3.1.10 PHP global and local variables

Next we will talk about the scope of the variables in PHP. A scope is the range in which a variable can be referenced. When we work with functions, there are two basic scopes: the global and the local scope. The local scope is also called a function scope.

scope1.php

```php
<?php
$value = 1;

function simple() {
    var_dump($value);
}

simple();
?>
```

A variable defined outside a function body cannot be referenced within a function.

```bash
$ php scope1.php
PHP Notice: Undefined variable: value in /home/janbodnar/prog/php/functions/scope1.php on line 7
NULL
```

The $value variable is NULL in the simple() function.

scope2.php

```php
<?php
$value = 4;

function simple() {
    $value = 3;
    echo $value, "\n";
}

simple();
echo $value, "\n";

?>
```

In this example, we have two variables with the same name. They do not collide because they exist in different scopes.

```bash
$ php scope2.php
3
4
```

The value is 3 inside the function and 4 outside the function. In the next example, we will modify a value inside the function.

```php
scope3.php
<?php
$value = 1;

function simple() {
    global $value;
    $value = 2;
}

echo $value, "\n";
simple();
echo $value, "\n";

?>
```

We use the global keyword to reference a variable defined outside the body of the function.

```bash
$ php scope3.php
1
2
```

The $value was successfully modified inside the simple () function.
In this part of the PHP tutorial, we covered PHP functions.
