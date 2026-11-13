# The continue statement

The PHP **continue** keyword is used to halt the current iteration of a loop but it does not terminate the loop.

Just like the **break** statement the **continue** statement is situated inside the statement block containing the code that the loop executes, preceded by a conditional test. For the pass encountering **continue** statement, rest of the loop code is skipped and next pass starts.

![](bbox=[0.36, 0.235, 0.65, 0.515])

# Example

In the following example, the loop prints the value of array, but when the condition becomes true, it just skips the code and next value is printed.

```
<html>
<body>
<?php
$array = array( 1, 2, 3, 4, 5);
foreach( $array as $value )
{
   if( $value == 3 )continue;
   echo "Value is $value <br />";
}
?>
</body>
</html>
```

This will produce the following result: