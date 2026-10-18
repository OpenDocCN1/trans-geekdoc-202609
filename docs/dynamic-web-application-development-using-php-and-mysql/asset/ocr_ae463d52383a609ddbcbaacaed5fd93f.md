# FIGURE 11.5 Array output

![](bbox=[0.21, 0.075, 0.92, 0.3])

# An array with a key

We can create an array and specify our own index key at the same time.:

```
$arrColors = array (0=>"Red", 1=>"Green", 2=>"Blue", 3=>"Yellow", 4=>"White");
```

A key index is specified using the operator =>. In the above example, the index has been specified exactly as the default index would: a numerical index starting from 0 and incremented by one each time. But what if we put the index items in a different order and even missed out an index number, for example:

```
$arrColors = array (0=>"Red", 2=>"Green", 3=>"Blue", 5=>"", 1=>"Yellow", 4=>"White");
```

In the above example, the index has not been created in numerical order and in addition a blank index key, number 5, has been included. If we use the above array with a slightly modified version of our simple ‘for’ loop example, we can see what is displayed when we cycle through the array:

```
<?php
// File: example11-9.php

$arrColors = array (0=>"Red", 2=>"Green", 3=>"Blue", 5=>"", 1=>"Yellow", 4=>"White");

for($intCount = 0;$intCount<6;$intCount++)
    echo "<p>$intCount " . $arrColors[$intCount] . "</p>";
?>
```

Note that the for loop now uses the expression <6 to determine the last item in the array as we have included an extra key. The output from the script is shown in Figure 11.6.

| NOTE | Note that the array elements are output in key order not the order in which they were defined in the ‘array’ construct. |