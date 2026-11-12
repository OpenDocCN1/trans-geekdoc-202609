For example, suppose you’re reading weather data and you want to print out data as long as the temperature is below 95 degrees. If the temperature is 95 degrees or higher, you don’t want to print out any data. In that case, you can be assured that the code in your while loop will not execute the first time. (This is not true in some languages and can be a concern among programmers.)

If you have a situation where you always want the code inside the loop to execute at least once, and then to check the condition after each iteration, you can use a slightly modified form of the while loop, called the do-while loop.

# The do-while loop looks like this:

```
<html><title></title>
<?php

$number = 20;
do {
    print "$number<br>\n";
    $number++;
} while ($number < 30);

?>
</html>
```

This example starts a counter called $number at 20, and continues counting up to, but not including, 30. Now look at the following code, where I changed the final while condition:

```
<html><title></title>
<?php

$number = 20;
do {
    print "$number<br>\n";
    $number++;
} while ($number < 0);

?>
</html>
```

The value in $number will never be less than 0. If this were a standard while loop, the code inside the curly braces would never execute. But because I used the do-while loop, the code executes once. Here’s the resulting HTML: