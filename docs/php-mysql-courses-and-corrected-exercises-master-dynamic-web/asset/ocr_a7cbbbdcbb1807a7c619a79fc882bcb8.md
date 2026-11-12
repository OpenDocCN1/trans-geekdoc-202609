# Exercise 10

Write the multiplication table of 7 (for all numbers from 1 to 100), using a for loop. This table should be presented as an unordered list.

# Correction

```
<?php
echo '<ul>';
for($i = 1; $i <= 10; $i++)
echo '<li>' . $i . ' x 7 = ' . ($i * 7) . '</li>';
echo '</ul>';
```

# Exercise 11

Write a program to calculate the following sum:

![](bbox=[0.05, 0.845, 0.95, 0.905])