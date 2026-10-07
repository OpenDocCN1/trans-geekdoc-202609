
## Variable scope

Variable scope defines which parts of a PHP script have access to a variable. The variables used in the example on the opposite page are both declared inside functions, so are known as “local” variables. These can be used by only the function in which they are declared.

Conversely, “global” variables are declared outside functions and can be accessed by any function in that document. Unlike other languages that make global variables accessible automatically, PHP requires a function to declare explicitly that it wants to use a global variable, otherwise the variable will be deemed to be of local scope by default. A simple declaration inside a function’s code block uses the “global” keyword followed by the variable name.

This example creates a global variable $num, accessible to two functions by including a declaration in each code block.

```php
<?php $num;
function make_triple($arg) {
    global $num;
    $num = $arg + $arg + $arg;
    thrice();
}
function thrice() {
    global $num;
    echo ("The value is $num");
}
?>
<html><head><title>Variable Scope</title></head><body><?php make_triple(4); ?></body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_30_0.png)

Removal of either global declaration will render the code useless, as PHP then assumes the variable reference in the function is made to a local variable.

![](img/7faa63a7fa0add8f53300594ebae949f_30_1.png)

![](img/7faa63a7fa0add8f53300594ebae949f_30_2.png)

2. Getting started with PHP | 29

## Multiple arguments

Functions may specify multiple arguments within their plain brackets to allow several values to be passed to the function code. The argument variable names simply need to be separated by commas in a list.

When a function specifies single or multiple arguments, calls to that function must also normally include the correct number of argument values to avoid an error. Optionally, a default value can be assigned to the argument in the function declaration.

In this example, three arguments are specified, each with a default value to be used if no argument value is passed from the caller:

![](img/7faa63a7fa0add8f53300594ebae949f_31_0.png)

```php
<?php
function addup($a = 32, $b = 32, $c = 32 ) {
    $total = $a + $b + $c;
    echo("$$a + $b + $c = $total");
}
?>
<html><head><title>Function Arguments</title></head>
<body>
<h3> <?php addup(8, 16, 24); ?> </h3>
<h3> <?php addup(8, 16); ?> </h3>
</body></html>
```

|| Function Arguments | File | Edit | View | Favorites | Tools | Help |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Address | http://localhost/args.php | Go | | | | |
| 8 + 16 + 24 = 48 | | | | | | |
| 8 + 16 + 32 = 56 | | | | | | |

## Performing operations

This chapter introduces the different PHP operators and demonstrates how they can be used in script statements to perform comparisons and to manipulate values.

## Covers

- Arithmetical operators | 32
- Logical operators | 34
- Assignment operators | 36
- Comparison operators | 38
- Conditional operator | 40

Chapter Three

## Arithmetical operators

The arithmetical operators commonly used in PHP scripts are listed in the table below together with the operations they perform:

| Operator | Operation |
| :--- | :--- |
| + | Numeric addition |
| . | String concatenation |
| - | Subtraction |
| * | Multiplication |
| / | Division |
| % | Modulus |
| ++ | Increment |
| -- | Decrement |

Notice that the + operator cannot be used to join strings as it can it in other languages. It will add together two numeric values and give the result of the addition. Concatenation of strings can only be performed with the . dot operator.

The modulus operator will divide the first given number by the second given number and return the remainder of the operation. This is most useful to determine if a number is odd or even.

The increment ++ and decrement -- operators alter the given value by 1 and return the resulting value. These are most commonly used to count iterations in a loop.

All the other operators act as you would expect, but care should be taken to bracket expressions where more than one operator is being used, to clarify the operations:

![](img/7faa63a7fa0add8f53300594ebae949f_33_0.png)

```php
a = b * c - d % e / f; // This is unclear
a = (b * c) - ((d % e) / f); // This is clearer
```

## ...cont'd

![](img/7faa63a7fa0add8f53300594ebae949f_34_0.png)

arithmetical.php

```php
$addstr = "I love " "PHP";
$sub = 35.75 - 28.25;
$mul = 8 * 50;
$mod = 65 % 2;
$inc = 5; ++inc;
$dec = 5; --dec;
```

```php
$result = "addnum:$addnum <br>";
$result = "addstr:$addstr <br>";
$result = "sub:$sub <br>";
$result = "mul:$mul <br>";
$result = "mod:$mod <br>";
$result = "inc:$inc <br>";
$result = "dec:$dec <br>";
```

The increment and decrement operators may also be used following the operand where they perform the operation but return the original value.

```html
<html>
<head><title>Arithmetical Operators</title> </head>
<body>
<h3> <?php echo ($result) ; ?> </h3>
</body>
</html>
```

## Arithmetical Operators

| File | Edit | View | Favorites | Tools | Help |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Address | | | | | |
| 8 + 16 + 24 = 48 | | | | | | |
| 8 + 16 + 32 = 56 | | | | | | |

## Logical operators

| Operator | Operation |
| :--- | :--- |
| && | Logical AND |
| || | Logical OR |
| xor | Logical XOR |
| ! | Logical NOT |

```php
<?php
$a = true; $b = false;

# test both for true
$test1 = ($a and $a) ? "true":"false";
$test2 = ($a and $b) ? "true":"false";
$test3 = ($b and $b) ? "true":"false";

# test either operand for true
$test4 = ($a or $a) ? "true":"false";
$test5 = ($a or $b) ? "true":"false";
$test6 = ($b or $b) ? "true":"false";

# test for single operand is true
$test7 = ($a xor $a) ? "true":"false";
$test8 = ($a xor $b) ? "true":"false";
$test9 = ($b xor $b) ? "true":"false";

# invert values
$test10 = (!$a) ? "true":"false";
$test11 = (!$b) ? "true":"false";

$result = "AND - 1:$test1 2:$test2 3:$test3<br>";
$result .= "OR - 1:$test4 2:$test5 3:$test6<br>";
$result .= "XOR - 1:$test7 2:$test8 3:$test9<br>";
$result .= "NOT - 1:$test10 2:$test11";

?>

<html>
<head><title>Logical Operators</title></head>
<body><?php echo ($result) ? ?></body>
</html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_36_0.png)

To display the results this example uses the conditional operator, which is on page 40.

![](img/7faa63a7fa0add8f53300594ebae949f_36_1.png)

![](img/7faa63a7fa0add8f53300594ebae949f_36_2.png)

3. Performing operations | 35
