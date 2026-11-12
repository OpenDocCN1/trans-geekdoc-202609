+   - After the code block has been executed, the condition `$counter <= 10` is evaluated. As long as this condition is true, the code block is rerun.
+   - The counter is incremented at each iteration.
+   - The loop repeats until the condition becomes false, i.e. when `$counter` reaches the value 11.

As the condition is checked at the end of each iteration, the code block is executed at least once, even if the initial condition is false.

The result returned by this code is exactly the same as that of the previous example using the while loop.

But note that the main difference between the two loops is that the do...while loop guarantees execution of the block of code at least once, whereas the while loop may not execute the block of code at all if the condition is false from the start.

To illustrate the difference, let's suppose, for example, that we initialize the variable `$counter` to 20. In this case, the condition (`$counter <= 10`) is false from the start, because `$counter` is initialized to 20, which is greater than 10.

Consequently, in the case of the while loop, the block of code inside the loop will never be executed.

However, in the case of the do...while loop, the block of code inside the do...while loop will be executed at least once, as the condition is evaluated after the block has been executed. Even if the condition (`$counter <= 10`) is false from the start, the block of code will still be executed once before checking the condition. So, even if `$counter` is initialized to 20, the message will be displayed once.

The for loop

The for loop is a control structure used to repeat a block of code a specified number of times. It is particularly useful when you know in advance the number of iterations you wish to perform.