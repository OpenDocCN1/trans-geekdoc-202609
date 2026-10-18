with case 4 is executed followed by the ‘break’ statement which forces the ‘switch’ statement to end. Therefore the output produced in this script with the value of $intTotal being 3 is:

3 is less than or equal to four!

# The ‘default’ statement

Another special case of the ‘switch’ statement is the ‘default’ case. The ‘default’ case will match against anything that wasn’t matched by any of the other cases and thus should always be the last statement. The following script illustrates its use:

```
<?php
// File: example9–10.php

$intTotal = 6;

switch ($intTotal) {
case 0:
case 1:
case 2:
case 3:
case 4:
    echo "<p>$intTotal is less than or equal to four!</p>";
    break;
case 5:
    echo "<p>$intTotal is equal to five!</p>";
    break;
default:
    echo "<p>$intTotal is greater than five!</p>";
}
?>
```

The output from the above script is illustrated in Figure 9.10.

> > **NOTE**  
> > Try adjusting the value contained in the $intTotal variable to check that the other cases within the ‘switch’ construct work as expected.

FIGURE 9.10  Output from the ‘default’ case of the ‘switch’ statement

![](bbox=[0.086, 0.803, 0.8, 0.945])