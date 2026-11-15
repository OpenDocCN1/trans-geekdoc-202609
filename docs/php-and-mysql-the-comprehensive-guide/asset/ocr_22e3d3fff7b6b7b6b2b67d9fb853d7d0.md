```
echo "Parameter 2: $par2";
}
output("Hello", "World");
?>
```

# Listing 6.2 Passing Parameters to a Function ("function_parameters.php")

![](bbox=[0.143, 0.22, 0.73, 0.355])

# Figure 6.2 The Parameters Are Output

**Note**

As of PHP 7.3, the parser allows a comma after the last specified parameter in function and method calls—a so-called trailing comma. The following call therefore would not lead to a parser error, although it looks rather ugly:

`output("Hello", "World",);`

As of PHP 8, this is also permitted when defining parameters in methods and functions:

`function output($par1, $par2,) {`

Even if it still doesn't look very nice, it allows you to simply copy and paste long parameter lists (which can be spread over several lines), making life a little more flexible.

# Default Values

If it is not clear whether a value is always passed for a parameter, you can also specify a default value for the parameter.

```
<?php
function output($par = "Default") {
    echo "Parameter value: $par<br />";
}

output();
output("Exclusive");
?>
```

# Listing 6.3 A Default Value for a Parameter ("function_default.php")