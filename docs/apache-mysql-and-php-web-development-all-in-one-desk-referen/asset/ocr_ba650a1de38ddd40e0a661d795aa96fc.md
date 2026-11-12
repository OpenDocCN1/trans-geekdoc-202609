```
<html><title></title>
20<br>
</html>
```

# Doing for Loops

If you have a block of code and you know the exact number of times you want to execute the block of code, or if you know specific beginning and ending conditions, you can use a for loop.

Here is a simple example of a for loop:

```
<?php
for ($counter = 10; $counter<20; $counter++) {
    print "$counter<br>\n";
}
?>
```

The for statement contains three expressions inside parentheses. The first expression, $counter = 10, sets the initial conditions. Before the code inside the curly brackets starts, the PHP processor stores 10 in the variable called $counter. (If the variable doesn't already exist, PHP creates it at this time.)

Next, the PHP processor tests whether the second expression inside the if line is true. If so, the PHP processor runs the code inside the curly brackets. After the code is finished, the PHP processor performs the code in the third expression, $counter++. That is, the PHP processor adds 1 to $counter.

If, at the end of any iteration, after incrementing $counter, the middle expression $counter < 20 is no longer true, the for loop finishes.

Think of the parts like this:

+   - The first expression is the initial condition.
+   - The middle expression is the while condition.
+   - The final expression is what the PHP processor does at the end of each iteration.

Thus, this for loop runs a counter that changes like this: 10, 11, 12, 13, 14, 15, 16, 17, 18, and 19.

![](bbox=[0.135, 0.845, 0.23, 0.93])

If you prefer the syntax of the while loop, you can code the preceding for loop by using a while loop as follows: