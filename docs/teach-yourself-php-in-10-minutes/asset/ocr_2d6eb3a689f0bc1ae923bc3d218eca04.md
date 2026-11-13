# Loops

PHP offers three types of loop constructs that all do the same thing repeat a section of code a number of times in slightly different ways.

# The while Loop

The while keyword takes a condition in parentheses, and the code block that follows is repeated while that condition is true. If the condition is false initially, the code block will not be repeated at all.

> **Infinite Loops** The repeating code must perform some action that affects the condition in such a way that the loop condition will eventually no longer be met; otherwise, the loop will repeat forever.

The following example uses a while loop to display the square numbers from 1 to 10:

```
$count = 1;
while ($count <= 10) {
    $square = $count * $count;
    echo "$count squared is $square <br>";
    $count++;
}
```

The counter variable $count is initialized with a value of 1. The while loop calculates the square of that number and displays it, then adds one to the value of $count. The ++ operator adds one to the value of the variable that precedes it.

The loop repeats while the condition $count <= 10 is true, so the first 10 numbers and their squares are displayed in turn, and then the loop ends.

# The do Loop

The do loop is very similar to the while loop except that the condition comes after the block of repeating code. Because of this variation, the loop code is always executed at least once even if the condition is initially false.

The following do loop is equivalent to the previous example, displaying the numbers from 1 to 10, with their squares: