
# Return statement

The PHP "return" keyword is used in functions to return a final value to the caller of function.

The example below contains a general purpose function called multiply() that can multiply by five argument values and return the total to the caller.

It is called from within the echo() function to multiply three argument values. The total is returned, using the "return" keyword, and the echo() function writes the total on the page.

![](img/7faa63a7fa0add8f53300594ebae949f_51_0.png)

```php
<?php
function multiply($a=1, $b=1, $c=1, $d=1, $e=1) {
    $total = $a * ($b * ($c * ($d * $e) ));
    return $total;
}
```

Each argument to the multiply() function uses a default value of 1 unless passed from the caller. The example illustrated returns the number of minutes in a year, but the function can call multiply(365.25,24,60) would return the number of seconds in a year.

```php
?>
<html><head><title>Return Statement</title></head>
<body>
Each year has 365¼4 days<br>
Each day has 24 hours<br>
Each hour has 60 minutes<br>
Each year has <?php echo (multiply(365.25, 24, 60)); ?> minutes
</body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_51_1.png)

50 | PHP-5 in easy steps

# Using arrays

This chapter deals exclusively with the topic of arrays, and illustrates by example what they are and how to use them. The most useful special PHP array functions are demonstrated to show how to store and retrieve values in array structures.

# Covers

- Creating an array | 52
- Changing array element values | 53
- Listing array elements | 54
- Getting the array size | 55
- Adding & removing array elements | 56
- Array keys and values | 58
- One-based indexing | 59
- Manipulating arrays | 60

![](img/7faa63a7fa0add8f53300594ebae949f_52_0.png)

# Creating an array

An array is a variable that can contain multiple values, unlike a regular variable that contains only a single value. An ordinary variable is given array status by the array() function. Multiple data values can then be assigned to array elements using the array name with an element index number. The index starts at zero and the number is placed inside square brackets, as seen here:

![](img/7faa63a7fa0add8f53300594ebae949f_53_0.png)

```php
<?php
$arr = array();
$arr[0] = "First";
$arr[1] = "PHP";
$arr[2] = "array";

echo($arr[0] . $arr[1] . $arr[2]);

?>
```

Each array element can now be used like a regular variable.

It is often convenient to specify the initial array values as a list of arguments to the array() function. This is demonstrated in the example below, which creates three arrays. The output from this example, and the one above, is shown at the bottom of this page.

![](img/7faa63a7fa0add8f53300594ebae949f_53_1.png)

```php
<?php
$mo = array("Jan", "Feb", "Mar");
$dy = array("21", "22", "23");
$yr = array("2005", "2006", "2007");
echo($mo[1] . $dy[0] . $yr[1]);
```

Remember that array indexing starts at zero. So $arr[2] is the third array - not the second. See page 59 for how to create indexing that starts at one instead of zero.

![](img/7faa63a7fa0add8f53300594ebae949f_53_2.png)

http://localhost/array.php
First array
Feb 21 2006
Done

# Changing array element values

PHP arrays are very versatile and each element can contain data of different type. To demonstrate this feature, the following example creates an array that has three elements initially containing values. These are written on the page using the dot operator to concatenate the element values into a single string.

Next, numeric values are assigned to each of the same elements. The first element is assigned an integer value and the second gets a float value. The total of these is assigned to the third element with the help of addition operator. Finally, the elements are written out on the page.

![](img/7faa63a7fa0add8f53300594ebae949f_54_0.png)

```html
<html><head><title>Changing array values</title></head>
<body>
<?php
# create an array containing 3 strings
$arr = array("Red", "Green", "Blue");

echo($arr[0] . $arr[1] . $arr[2]);

# assign numeric values
$arr[0] = 4;
$arr[1] = 2.5;
$arr[2] = $arr[0] + $arr[1];

echo($arr[0] . $arr[1] . $arr[2]);
?>
</body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_54_1.png)
![](img/7faa63a7fa0add8f53300594ebae949f_54_2.png)

5. Using arrays | 53

# Listing array elements

Retrieving all element values from an array is easy with the PHP foreach() function which loops through each element of an array.

The value of the element on each iteration of the loop can be assigned to a variable using the "as" keyword. This must be specified as an argument to the foreach() function, with the array name and the variable name, using this syntax:

```php
foreach(array as $variable) { ... }
```

The following example loops through an array and writes each element value on the page as an item in an ordered list:

```html
<html><head><title>List array values</title></head>
<body>
<ol>
<?php
$arr = array("Red", "Green", "Blue", "Cyan", "Magenta", "Black", "Yellow");

foreach($arr as $value) {
 echo "<li>Do you like $value?</li>";
}
?>
</ol></body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_55_0.png)

The foreach() function is especially useful to list the nodes of an XML document – see chapter 14.

![](img/7faa63a7fa0add8f53300594ebae949f_55_1.png)

PHP 5 in easy steps

# Getting the array size

The PHP sizeof() function is an alias for the PHP count() function, so either can be used to determine the total number of elements in an array. These functions require the name of the array to be specified as their argument.

The PHP script below first creates an empty array, then fills three elements with data using a "for" loop. Each of the element values is written out on the page, using the foreach() function described on the opposite page. Finally, the array size is assigned to a variable and then printed on the page.

```html
<html><head><title>Getting array size</title></head>
<body><ul>
<?php
$arr = array();

# assign three element values
for ($i = 0; $i < 3; $i++) {
  $arr[$i] = "<li>This is element $i</li>";
}

foreach ($arr as $value) { echo ($value); }

# assign the number of array elements
$size = count($arr);
echo("<li>Total number of elements is $size</li>");
?>
</ul></body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_56_0.png)

Notice that the array size expands dynamically to create more when needed.

![](img/7faa63a7fa0add8f53300594ebae949f_56_1.png)

| Getting array size |
| File | Edit | Favorites | Tools | Help |
| Address | http://localhost/sizearray.php | Go |
| :--- | :--- | :--- |
| * This is element 0 |
| * This is element 1 |
| * This is element 2 |
| * Total number of elements is 3 |

5. Using arrays | 55

# Adding & removing array elements

Additional elements can be created at the beginning of an array using the array_unshift() function, and elements can be added at the end of an array with the array_push() function. Each requires the array name followed by the element data as arguments.

In the example below, an array is created with three elements. Two more elements are added at the beginning, then two further elements are added at the end.

![](img/7faa63a7fa0add8f53300594ebae949f_57_0.png)

```html
<html><head><title>Adding array values</title></head>
<body>
<ol>
<?php
$arr = array("Red", "Green", "Blue");

# add elements at beginning of the array
array_unshift($arr, "Cyan", "Magenta");

# add elements at end of the array
array_push($arr, "Yellow", "Black");

# write out element
foreach($arr as $value) {
 echo "<li>Do you like $value?</li>";
}
?>
</ol></body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_57_1.png)

# ...cont'd

The first element in an array can be removed with the array_shift() function, and the final element can be removed using the array_pop() function. Both these functions return the removed element data, which can be assigned to a variable.

The following example removes the first and last elements from an array, then sorts the remaining elements into alphabetical order using the PHP sort() function.

```html
<html><head><title>Remove array elements</title></head>
<body><ol>
<?php
#create an array containing 5 strings
$arr=array("Orange","Cherry","Apple","Banana","Lemon");

#remove element at beginning of the array
$first = array_shift($arr);

#remove element at end of the array
$last = array_pop($arr);

#sort elements alphabetically
sort($arr);

#write out values
foreach($arr as $value){ echo("$value, " "); }
echo("<br>Removed first element: \$first");
echo("<br>Removed last element: \$last");
?>
</ol></body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_58_0.png)

Each of the PHP array functions in this example requires the array name to be specified as their argument.

![](img/7faa63a7fa0add8f53300594ebae949f_58_1.png)
