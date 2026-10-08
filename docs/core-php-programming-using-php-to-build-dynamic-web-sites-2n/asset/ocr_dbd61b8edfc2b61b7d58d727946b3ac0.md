# Core PHP Programming

![](bbox=[0.195, 0.091, 0.393, 0.362])

```
<?php
//create a test array
$colors = array("red", "blue", "green");

//show array like [0] => red
print("<PRE>");
print_r($colors);
print("</PRE\n");

//flip indices for elements
$colors = array_flip($colors);

//show array like [red] => 0
print("<PRE>");
print_r($colors);
print("</PRE\n");
?>

//create random test data with 0 or 1
```

# array array_keys(array data, string value)

The array_keys function returns an array of the keys used in the data array. If the optional value argument is supplied, only the subset of indices that point the given element value are returned.

IT-SC book 223