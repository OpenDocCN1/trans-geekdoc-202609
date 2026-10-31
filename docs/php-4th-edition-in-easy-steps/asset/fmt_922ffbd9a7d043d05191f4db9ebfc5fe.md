
- Strings may be enclosed in either single quotes or double quotes, and inner quote marks can be escaped using a backslash.
- String values can be joined together into a single string using the `.` concatenation operator.
- An array variable can store multiple items of data in sequential array elements that are numbered starting at zero by default.
- Optionally, key names may be specified for each array element.
- A `foreach` loop can traverse each element in an array.
- The `implode()` and `explode()` functions convert between strings and arrays by adding or removing specified separators.
- Arrays can be sorted into alphanumeric order by value or key.
- A multi-dimensional array is simply an array whose element values are themselves arrays.
- The `gettype()` and `var_dump()` functions can be used to check data types.
- A constant is a named container in which a fixed integer, floating-point number, or text string can be stored.
- Constant names are not prefixed by a `$` and are all uppercase.
- A constant is initialized using the `define()` function.
- Superglobal variables are always globally available anywhere within any script.

# 3 Performing operations

*This chapter demonstrates the various PHP operators for arithmetic, comparison and logical evaluation.*

- [Doing arithmetic](#chapter03.xhtml#sec19)
- [Making comparisons](#chapter03.xhtml#sec20)
- [Examining conditions](#chapter03.xhtml#sec21)
- [Assessing logic](#chapter03.xhtml#sec22)
- [Comparing bits](#chapter03.xhtml#sec23)
- [Changing values](#chapter03.xhtml#sec24)
- [Grasping precedence](#chapter03.xhtml#sec25)
- [Summary](#chapter03.xhtml#sec26)

## Doing arithmetic

![image](images/pg44_1.jpg)

The arithmetic operators commonly used in PHP scripts are listed in the table below, together with the operation they perform:

| Operator | Operation |
|---|---|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulus |
| `**` | Exponentiation |

Operators for addition, subtraction, multiplication and division act as you would expect. Care must be taken, however, to group expressions for clarity where more than one operator is used:

`a = b * c - d % e / f ;` # This is unclear.
`a = ( b * c ) - ( ( d % e ) / f ) ;` # This is clearer.

The `%` modulus operator divides the first given number by the second given number and returns the remainder of the operation. This is useful to determine if a number has an odd or even value.

![image](images/hot.jpg)

The numbers used along with operators to form expressions are known as “operands” – in the expression `2 + 3` the numbers `2` and `3` are the operands.

The `**` exponentiation operator gives the result of raising the first operand to the power of the second operand.

`a ** b` # Result of raising a to the b’th power.

Shorthand expressions can usefully be created by combining an arithmetic operator with the `=` assignment operator – for example:

`a += b ;` # Equivalent to `a = ( a + b ) ;`
`a -= b ;` # Equivalent to `a = ( a - b ) ;`
`a *= b ;` # Equivalent to `a = ( a * b ) ;`
`a /= b ;` # Equivalent to `a = ( a / b ) ;`

![image](images/forget.jpg)

Group expressions with parentheses to specify evaluation precedence – innermost groups get evaluated first. See [herepage 55](#chapter03.xhtml#sec25) for more on operator precedence.

![image](images/1g.jpg)Create a valid HTML document, like the one listed [hereon page 16](#chapter01.xhtml#sec5), then insert PHP tags into the body section

```
<?php
# Statements to be inserted here.
?>
```

![image](images/commong.jpg)

`arithmetic.php`

![image](images/2g.jpg)Now, insert statements between the PHP tags to create and initialize two variables

```
$a = 5 ;
$b = 2 ;
```

![image](images/3g.jpg)Next, insert statements to display the results of simple arithmetical operations using the variable values

```
$result = $a + $b ; echo "Addition : $result <br>" ;
$result = $a - $b ; echo "Subtraction : $result <br>" ;
$result = $a * $b ; echo "Multiplication : $result <br>" ;
$result = $a / $b ; echo "Division : $result <br>" ;
```

![image](images/4g.jpg)Finally, insert a statement to display the results of arithmetical evaluations of the variable values

```
$result = $a % $b ; echo "Modulus : $result <br>" ;
$result = $a ** $b ; echo "Exponentiation : $result" ;
```

![image](images/5g.jpg)Save the document in your web server’s `/htdocs` directory as `arithmetic.php` then open the page via HTTP to see the results and variable values get displayed

![image](images/pg45_1.jpg)

![image](images/hot.jpg)

PHP has some useful functions to work with numbers. For example, `round($a)` rounds `$a` to the nearest integer and `number_format($a)` adds commas to `$a` denoting groups of thousands.

## Making comparisons

![image](images/pg46_1.jpg)

The operators that are commonly used in PHP scripts to compare two values are listed in the table below:

| Operator | Comparative test |
|---|---|
| `==` | Equality |
| `===` | Identicality |
| `!==` | Non-identicality |
| `!=` | Inequality |
| `<>` | Inequality |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal to |
| `<=` | Less than or equal to |
| `<=>` | Spaceship |

The `==` equality operator compares two operands and returns a Boolean TRUE result if both are numerically equal in value, otherwise it returns FALSE. Characters and strings are also compared numerically by their ASCII code value. Conversely, the `!=` inequality operator returns TRUE if the two operands are not equal, otherwise it returns FALSE.

The `>` “greater than” operator compares two operands and returns TRUE if the first is greater in value than the second, or it returns FALSE if it is equal or less in value. The `<` “less than” operator makes the same comparison but returns TRUE if the first operand is less in value than the second, otherwise it returns FALSE. Adding the `=` operator after a `>` “greater than” or `<` “less than” operator makes it also return TRUE when the two operands are exactly equal.

The `<=>` spaceship operator returns an integer value of 1 when the first operand is greater than the second, -1 when the first operand is less than the second, or 0 when the operands are equal.

The PHP `var_dump()` function can be used to see the type and value resulting from each kind of comparison.

![image](images/hot.jpg)

Equality and inequality operators are useful in testing the state of two variables to perform conditional branching in a PHP script.

![image](images/1g.jpg)Create a valid HTML document, like the one listed [hereon page 16](#chapter01.xhtml#sec5), then insert PHP tags into the body section

```
<?php
# Statements to be inserted here.
?>
```

![image](images/commong.jpg)

`comparison.php`

![image](images/2g.jpg)Now, insert statements between the PHP tags to create and initialize five variables

```
$zero = 0 ; $nil = 0 ; $one = 1 ; $upr = 'A' ; $lwr = 'a' ;
```

![image](images/3g.jpg)Next, insert statements to display equality comparisons

```
echo "0 == 0 : " ; var_dump( $zero == $nil ) ;
echo "<br>0 == 1 : " ; var_dump( $zero == $one ) ;
echo "<br>A == a : " ; var_dump( $upr == $lwr ) ;
echo "<br>A != a : " ; var_dump( $upr != $lwr ) ;
```

![image](images/4g.jpg)Insert statements to display comparison evaluations

```
echo "<hr>1 > 0 : " ; var_dump( $one > $nil ) ;
echo "<br>0 >= 0 : " ; var_dump( $zero >= $nil ) ;
echo "<br>1 <= 0 : " ; var_dump( $one <= $nil ) ;
echo "<hr>1 <=> 0 : " ; var_dump( $one <=> $nil ) ;
echo "<br>1 <=> 1 : " ; var_dump( $one <=> $one ) ;
echo "<br>0 <=> 1 : " ; var_dump( $nil <=> $one ) ;
```
