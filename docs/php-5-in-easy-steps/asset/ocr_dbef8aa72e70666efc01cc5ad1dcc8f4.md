# Changing array element values

PHP arrays are very versatile and each element can contain data of a different type.

To demonstrate this feature, the following example creates an array that has three elements initially containing string values. These are written on the page using the dot operator to concatenate the element values into a single string.

Next, new numeric values are assigned to each of the same three elements. The first element is assigned an integer value and the second gets a float value. The total of these is assigned to the third element with the help of the + addition operator. Finally, the elements' new values are written out on the page.

![](bbox=[0.183, 0.375, 0.273, 0.473])

```
<html><head><title>Changing array values</title></head>
<body>
<?php
# create an array containing 3 strings
$arr = array("Red \ "Green", "Blue\ );

echo($arr[0] . $arr[1] . $arr[2] . "<hr>");

#assign new numeric values
$arr[0] = 44;
$arr[1] = 12.5;
$arr[2] = $arr[0] + $arr[1];

echo("$arr[0] + $arr[1] = $arr[2]");
</body></html>
```

![](bbox=[0.037, 0.611, 0.238, 0.693])

![](bbox=[0.289, 0.722, 0.933, 0.926])

5. Using arrays | 53