By default, PHP uses weak typing, meaning that the data types of function parameters and return values are not explicitly declared. This allows great flexibility, but can sometimes lead to errors that are difficult to detect.

# Example of a function without typing :

```
<?php
function addition($a, $b) {
return $a + $b;
}

$result1 = addition(5,10);
echo $result1 ."<br>";

$result2 = addition(5, "10");
echo $result2 ."<br>";

?>
```

This PHP code defines a function named addition that takes two parameters, $a and $b, and returns the sum of these two parameters. The function is then called twice with different arguments.
In this example, the **addition()** function doesn't specify the type of its $a and $b parameters. They can be of any data type, and the function's result will depend on the type of the values passed.