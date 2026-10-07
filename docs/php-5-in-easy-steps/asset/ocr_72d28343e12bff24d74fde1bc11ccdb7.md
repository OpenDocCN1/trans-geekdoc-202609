# Creating an array

An array is a variable that can contain multiple values, unlike a regular variable that contains only a single value. An ordinary variable is given array status by the PHP() function. Multiple data values can then be assigned to array elements using the array name with an element index number. The index starts at zero and the number is placed inside square brackets, as seen here:

![](bbox=[0.206, 0.235, 0.276, 0.345])

```
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

![](bbox=[0.206, 0.563, 0.286, 0.683])

```
$mo = array("Jan \ "Feb \ "Mar \);\n$dy = array("21 \ "22 \ "23 \);\n$yr = array("2005", "2006", "2007 \);\n
echo($mo[1] . $dy[0] . $yr[1]);
```

Remember that array indexing starts at zero. So $arr[2] is the third array - not the second. See page 59 for how to create index numbering that starts at one, instead of zero.

![](bbox=[0.053, 0.712, 0.131, 0.793])

http://localhost/array.php
First PHP array
Feb 21 2006
Done Local intranet