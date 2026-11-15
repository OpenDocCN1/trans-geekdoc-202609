In addition to these two, there are several other functions for iteration:

+   - pos(Array) is a synonym for current().
+   - prev(Array) returns the array element before the current one. If there are no more, then false is returned.
+   - reset(Array) sets the pointer back to the first element. If the array is empty, the function returns false.
+   - end(Array) sets the pointer to the last element. If the array is empty, the function returns false.
+   - each(Array) works like next(), except that the key and value are returned in an array. However, the function is no longer recommended since PHP 7.2 and has been removed from PHP 8.
+   - key(Array) returns the index of the element at the current pointer position in the array.
+   - array_walk(Array, Function, Parameter) automatically walks through an array and calls a function for each element. The function receives the value and the index of the respective element as parameters. Optionally, you can also pass a third parameter. When using array_walk(), you should not change the array. The output is in the input order of the elements. This is the case for all iteration functions. array_walk_recursive() works in the same way as array_walk(), except that it also penetrates multidimensional arrays. The following listing offers a simple example of array_walk(); you can see the output in Figure 8.11.

```
<?php
$stockprices = array("IBW" => 232, "Miemens" => 34, "Rheinwerk" => 340);

function output($stockprices, $index, $text) {
if ($index != "Miemens") {
print $text . $index . ": ";
print $rate . "<br />";
}
}

array_walk($stockprices, "output", "The stock price from: ");
?>
```

# Listing 8.10 "array_walk() ("array_walk.php")"

![](bbox=[0.14, 0.76, 0.75, 0.87])

# Figure 8.11 The Function Returns Two Prices and Singles One Out