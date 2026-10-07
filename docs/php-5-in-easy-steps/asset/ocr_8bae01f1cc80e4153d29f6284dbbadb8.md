# Switch statement

Conditional branching using an “if-else” statement can often be performed more efficiently using a “switch” statement, when the test expression evaluates the value of just one variable.

The “switch” statement works in an unusual way. First it evaluates a given expression, then seeks a label to match the resulting value. The code associated with the matching label will be executed, or if none of the labels match, the statement will execute any specified default code.

The PHP “case” keyword is used to denote a label, and the “default” keyword is used to specify the default code. All label code must be terminated by a break statement using the PHP “break” keyword.

The labels may be numbers, strings, or booleans, but all will be of the same type, like this example uses numbers:

![](bbox=[0.052, 0.198, 0.258, 0.273])

```
<html><head><title>Switch Statement</title></head>
<body>
<?php
$num = 2;
switch($num) {
case 1 : echo("This is case 1 code\ ); break;
case 2 : echo("This is case 2 code\ ); break;
case 3 : echo("This is case 3 code\ ); break;
default : echo("This is default code\ );
}
?>
?></body></html>
```

![](bbox=[0.203, 0.443, 0.298, 0.523])

![](bbox=[0.052, 0.613, 0.258, 0.713])

![](bbox=[0.301, 0.753, 0.946, 0.933])