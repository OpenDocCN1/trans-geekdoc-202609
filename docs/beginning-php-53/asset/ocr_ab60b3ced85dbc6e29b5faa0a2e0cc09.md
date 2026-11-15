The print_r() example shows that the second element of $myBooks is in fact an associative array containing information on “The Trial.” Meanwhile, the two echo() examples show how to access elements in the nested associative arrays. As you can see, you use two keys within two sets of square brackets. The first key is the index of an element in the top-level array, and the second key is the index of an element in the nested array. In this example, the first key selects the associative array you want to access, and the second key selects an element within that associative array.

# Looping Through Multidimensional Arrays

You know how to use foreach to loop through one-dimensional arrays, but how do you loop through multidimensional arrays? Well, because multidimensional arrays are basically arrays nested inside other arrays, you can loop through them using nested loops!

# Try It Out Displaying an Array of Books

The following example uses two nested foreach loops to loop through the $myBooks array. Save it as multidimensional_array_loop.php within your document root folder, then browse to the script’s URL to see it in action. You should see something like Figure 6-5.

```
<!DOCTYPE html PUBLIC "--//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
	<title>Looping Through a Two-Dimensional Array</title>
	<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
	<h1>Looping Through a Two-Dimensional Array</h1>

	<?php

	$myBooks = array(
		array(
			"title" => "The Grapes of Wrath",
			"author" => "John Steinbeck",
			"pubYear" => 1939
		),
		array(
			"title" => "The Trial",
			"author" => "Franz Kafka",
			"pubYear" => 1925
		),
		array(
			"title" => "The Hobbit",
			"author" => "J. R. R. Tolkien",
			"pubYear" => 1937
		),
		array(
			"title" => "A Tale of Two Cities",
			"author" => "Charles Dickens",
```