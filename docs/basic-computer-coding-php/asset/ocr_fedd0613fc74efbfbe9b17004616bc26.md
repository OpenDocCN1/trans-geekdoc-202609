```
displayVersion();
?>
```

The function keyword is followed by the function name with round brackets. The body of the function lies between the curly brackets. We say that we call a function. If we call a function, the statements inside the function body are executed.

This line of the code calls the function.
$ php simple.php
is is PHP 5.5.9-ubuntu4.14
Here we see the outcome of the script.

# 3.1.2 PHP Return keyword

The return keyword is used to return a value from the function. function may or may not return a value.

```
<?php
```

```
function maximum($x, $y) {

    if ($x > $y) {

        return $x;
    } else {

        return $y;
    }
}
```

```
$a = 23;
$b = 32;
```