# Multiple functions

PHP functions may call other functions during the execution of their code in just the same way that the previous examples called the echo() function.

The following example demonstrates the use of multiple functions to manipulate and display an integer value.

![](bbox=[0.183, 0.235, 0.276, 0.345])

```
<?php
function show_number($num) {
    $new_number = make_double($num);
    echo("The value is $new_number");
}

function make_double($arg) {
    return $arg + $arg;
}
```

Note the code format of this example - when defining functions, the source code is clearer if all declarations appear before any HTML or page content.

```
<html><head><title>PHP Functions</title></head>
<body>
<h3><?php show_number(4); ?></h3>
</body>
</html>
```

The argument value is passed from the calling statement to the make_double() function via the show_number() function. The passed argument value is doubled, then the result is returned to a variable in the show_number() function. Finally the echo() function is called to write the new value out the page.

| PHP Functions |
 File | Edit | View | Favorites | Tools | Help |
| Address | http://localhost/functions.php | Go |
| The value is 8 |
| Done | Local intranet |