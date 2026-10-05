# 106 Part II: Solutions

```
echo "<tr>\nfor($j = 0; $j < $numcols; $j++) {
    echo "<td>$arr[$i][$j]</td>";
    echo "</tr>";
}
echo "<table>";
?>
```

The variants presented in Listings II.1.7 and II.1.8 can be extended to any number of columns in the output table. To achieve this, it is enough to change the value of the $numcols variable.

# II.1.5. Passing an Array from Page to Page

The script that passes an array from the first.php file to the second.php file using the include instruction is presented in Listing II.1.9.

```
<php
// Including the file containing the $filename array
include "first.php";
// Outputting the array contents
foreach($filename as $value) echo "$value<br>";
?>
```

This method of passing arrays is not always acceptable. For example, an array might be formed dynamically. Such a method of passing arrays is also not suitable when the first.php file, in addition to defining an array, carries out of actions that must be avoided on the second.php page.

There are two instructions for including files into the script body: include and require. The include and require instructions differ in their reaction to the lack of the included file. If the file to be included is missing, the include instruction generates a warning but continues its operation, while the require instruction terminates