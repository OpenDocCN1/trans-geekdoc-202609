![](bbox=[0.14, 0.1, 0.74, 0.225])

# Figure 6.7 You Now Have Access to the Global Variable within the Function.

# $GLOBALS

The $GLOBALS array contains all global variables. You can use it to access global variables or change their value from anywhere.

```
<?php
$global = "Global variable";
function output() {
echo $GLOBALS["global"];
}
output();
?>
```

# Listing 6.11 The "$GLOBALS" Array ("function_globalsArray.php")

# 6.1.3 Return Value

With parameters, you can pass values to a function. To get something back from a function, you need the return keyword. It terminates the function; that is, all statements after return are ignored. The value at return is returned.

```
function Name(Parameter) {
Statements;
return ReturnValue;
}
```

You then have to do something with this return value. You can, of course, output it immediately. However, you will usually save it in a variable:

```
$Variable = Name(Parameter);
```

> > **Note**
> > Anyone who has programmed with Pascal knows the exact distinction. A function without a return value is actually a _procedure_. There are some languages that use different keywords for procedure and function (e.g., Visual Basic). In PHP, however, this distinction is meaningless. That is why we generally speak of _functions_.