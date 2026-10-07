# Conditional if statement

The “if” keyword is used to perform the basic conditional PHP test to evaluate an expression for a boolean value. The statement following the evaluation will be executed only when the expression is true. The syntax for the “if” statement looks like this:

```
if ( test-expression ) statement-to-execute-when-true ;

{
```

The code to be executed may contain multiple statements if they are enclosed in a pair of curly brackets to form a “statement block”.

In the example below the expression to be tested uses the modulus operator to determine if the value contained in the variable $num is exactly divisible by 2. The statement block has two statements – one to assign a string value to a variable and another to call the PHP echo function.

```
<html>
<head><title>If Statement</title></head>
<body>
<?php
$num = 7;
if ( $num % 2 != 0 ) {

$msg = "$num is an odd number.";
echo( $msg );
}
?>
</body>
</html>
```

![](bbox=[0.206, 0.442, 0.293, 0.545])

This example could have used ($num%2!=1) to detect an even number.

![](bbox=[0.046, 0.587, 0.137, 0.659])

![](bbox=[0.296, 0.712, 0.946, 0.923])