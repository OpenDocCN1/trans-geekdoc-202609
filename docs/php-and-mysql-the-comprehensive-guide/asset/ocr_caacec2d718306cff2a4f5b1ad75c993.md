# 8.4.2 Delete and Replace

The array_slice(array, start_index, length) function reads elements from a numeric array and returns them as an array. It starts at the start_index and you can optionally specify the length—that is, the number of elements that will be sliced from the start index. If you omit the length, all elements up to the end of the array are cut out. The following example therefore returns a new array with two elements (see Figure 8.12).

```
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
$new = array_slice($days, 1, 2);
print_r($new);
?>
```

Listing 8.11 "array_slice()" ("array_slice.php")

![](bbox=[0.145, 0.365, 0.755, 0.505])

Figure 8.12 The New Array: The Original Does Not Change!

> **Note**
> 
> You can also specify a negative value for the start index. In this case, counting starts from the end of the array. The following line only cuts Monday from the array:
> 
> $new = array_slice($stage, -2, 1);
> 
> However, if the length has a negative value, then cutting stops at this position, counted from the end of the array.

For an associative array, array_slice(Array, Length) has only two parameters: the array and the length (i.e., the number of elements to be sliced from the array). The elements are removed from the beginning of the array and placed in the new array. The original does not change here either. Figure 8.13 shows the result of the following instruction:

```
$stockprices = array("IBW" => 232, "Miemens" => 34, "Rheinwerk" => 340);
$new = array_slice($stockprices, 2);
print_r($new);
```