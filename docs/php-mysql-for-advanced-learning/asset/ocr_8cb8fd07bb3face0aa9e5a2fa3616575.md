# Output

+   1
+   1 2
+   1 2 3
+   1 2 3 4
+   1 2 3 4 5

# Reverse For Loop:

In PHP you can also use For Loop from a higher value to a lower value. To achieve this we need to mention our progressive in negative.

```
<?php
for($var=10; $var>=1; $var=$var-1)
{
    echo $var . " ";
} ?>
```

Output: 10 9 8 7 6 5 4 3 2 1

# The While loop

A While loop is used when we have to repeat a set of statements as long as the condition is false. It could be the best where number of repetition is not known earlier or in advance.

It can be explain in plain English as "*Keep doing something until a condition is true*."

# Syntax

```
while (condition)
{
    // Set of statements goes here;
}
```