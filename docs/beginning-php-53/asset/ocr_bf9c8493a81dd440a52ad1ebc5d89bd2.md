```
print_r ( $Authors );
echo "<br/> ";

// Displays "Array ( [0] => A Tale of Two Cities [1] => The Trial [2] => East
of Eden [3] => Of Mice and Men [4] => The Grapes of Wrath [5] => The Hobbit )"
print_r ( $titles );
echo "<br/> ";

// Displays "Array ( [0] => 1859 [1] => 1925 [2] => 1952 [3] => 1937 [4] =>
1939 [5] => 1937 )"
print_r ( $pubYears );
```

These arrays contain information on three books by Steinbeck. You can see that `array_multisort()` has sorted all the arrays by author in ascending order as before. However, it has also sorted the three Steinbeck books — *East of Eden*, *Of Mice and Men*, and *The Grapes of Wrath* — into ascending order.

You can also use `array_multisort()` to sort multidimensional arrays. This works in much the same way as for multiple arrays, except that you only pass in one array. The function then sorts the array by the first element of each nested array, then by the second element, and so on. The order of the elements in the nested array is untouched.

The following code illustrates how `array_multisort()` sorts a two-dimensional array. Figure 6-6 shows the output from the script.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Using array_multisort() on a Two-Dimensional Array</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Using array_multisort() on a Two-Dimensional Array</h1>
<?php
$myBooks = array(
array(
"title" => "The Grapes of Wrath",
"author" => "John Steinbeck",
"pubYear" => 1939
),
array(
"title" => "Travels With Charley",
"author" => "John Steinbeck",
"pubYear" => 1962
),
array(
"title" => "The Trial",
"author" => "Franz Kafka",
"pubYear" => 1925
),

```