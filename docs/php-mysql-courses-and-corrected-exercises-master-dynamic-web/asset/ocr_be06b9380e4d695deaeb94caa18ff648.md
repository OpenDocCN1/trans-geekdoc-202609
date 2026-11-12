```
```php
<?php
$numbers = [10, 20, 30, 40, 50];
foreach ($numbers as $number) {
echo $number . "<br>";
}
?>
```
```

This example uses the **foreach** loop to traverse the $numbers array. In this loop, $number (singular) represents each element of the $numbers array at each iteration. In fact, at each iteration, the $number variable takes on the value of the **current** element in the array. So, on each loop turn, the value of $number is displayed, followed by a <br> tag for a line feed. This loop is handy for browsing through all the elements of an array without needing to explicitly manage an index as with the for loop. The output result of this code is exactly the same as that obtained with the for loop.

# Associative arrays

Associative arrays, as their name suggests, associate keys with values. Unlike indexed arrays, where values are accessible by their numerical position, in an associative array, values are accessible by their associated key. Here's how to declare and initialize an associative array in PHP :

# Declaration of an empty associative array

The method for declaring an empty associative array is the same as for declaring an indexed array: