# While Loop Example 1

```
<?php
$ct=5;
while($ct<=50)
{
echo $ct ."<br>";
$ct = $ct+5;
}
?>
```

# Output:

5 10 15 20 25 30 35 40 45 50

# The do...While Loop in PHP

The do..while loop is almost similar to while loop but one major difference between them. The do...while loop will always execute the block of code at least once.

# Difference Between while and do...while Loop:

With a while loop, the condition to be evaluated is tested at the beginning of each loop statement, so if the conditional expression evaluates to false, the loop will never be executed.

With a do -while loop, on the other hand, the loop will always be executed once, even if the conditional expression is false, because the condition is evaluated at the end of the loop statement.