# Basic Computer Coding: PHP

The array_slice() function returns a new array consisting of a consecutive series of values from the original array. The offset parameter identifies the initial element to copy (0 represents the first element in the array), and the length parameter identifies the number of values to copy. The new array has consecutive numeric keys starting at 0. For example:

```
$people = array("Tom", "Dick", "Harriet", "Brenda", "Jo");
$middle = array_slice($people, 2, 2); // $subset is array("Harriet", "Brenda")
```

It is generally only meaningful to use array_slice() on indexed arrays (i.e., those with consecutive integer indices starting at 0):

```
// this use of array_slice() makes no sense
$person = array("name" => "Fred", "age" => 35, "wife" => "Betty");
$subset = array_slice($person, 1, 2); // $subset is array(0 => 35, 1 => "Betty")
```

Combine array_slice() with list() to extract only values to variables:

```
$order = array("Tom", "Dick", "Harriet", "Brenda", "Jo");
list($second, $third) = array_slice($order, 1, 2);
// $second is "Dick", $third is "Harriet"
```

# Splitting an Array into Chunks

To divide an array into smaller, evenly sized arrays, use the array_chunk() function:

Boolean value is one with two choices: true or false, yes or no, 1 or 0:

$chunks = array_chunk(array, size [, preserve_keys]);
The function returns an array of the smaller arrays. The third argument, serve_keys, is a Boolean value that determines whether the elements of the new arrays have the same keys as in the original (useful for associative arrays) or new numeric keys starting from 0 (useful for indexed arrays). The default is to assign new keys, as shown here: