An array is a data structure that stores one or more similar type of values in a single value. For example, if you want to store 100 numbers, then instead of defining 100 variables, it is easy to define an array of 100 length.

There are three different kind of arrays and each array value is accessed using an ID c which is called array index.

+   - **Numeric array** - An array with a numeric index. Values are stored and accessed in linear fashion
+   
+   - **Associative array** - An array with strings as index. This stores element values in association with key values rather than in a strict linear index order.
+   
+   - **Multidimensional array** - An array containing one or more arrays and values are accessed using multiple indices

**NOTE:** Built-in array functions is given in function reference PHP Array Functions

# Numeric Array

These arrays can store numbers, strings and any object but their index will be represented by numbers. By default, the array index starts from zero.

# Example

The following example demonstrates how to create and access numeric arrays.

Here we have used **array()** function to create array. This function is explained in function reference.

```
<html>
<body>
<?php
/* First method to create array. */
$numbers = array( 1, 2, 3, 4, 5);
foreach( $numbers as $value )
{
   echo "Value is $value <br />";
}
/* Second method to create array. */
$numbers[0] = "one";
$numbers[1] = "two";
$numbers[2] = "three";
```