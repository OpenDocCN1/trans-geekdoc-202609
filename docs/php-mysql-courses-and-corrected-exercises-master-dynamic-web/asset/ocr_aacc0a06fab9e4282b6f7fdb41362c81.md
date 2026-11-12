The general syntax of the do...while loop is as follows:

```
do {
  // Block of code to execute
} while (condition)
```

Here's an example of how to use the do...while loop in PHP:

```
<?php

$counter = 1;

do {
  echo "The counter is: $counter <br>";
  $counter++;
} while ($counter <= 10);

?>
```

In this example, the $counter variable is initialized to 1.

+   Next, the block of code inside the braces is executed. It displays the counter value.