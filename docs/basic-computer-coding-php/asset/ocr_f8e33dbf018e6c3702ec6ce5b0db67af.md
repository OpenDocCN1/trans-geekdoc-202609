# Basic Computer Coding: PHP

Here we have the for loop construct. The three phases are divided by semicolons. First, the $i counter is initiated. The initiation part takes place only once. Next, the test is conducted. If the result of the test is true, the statement is executed. Finally, the counter is incremented. This is one cycle. The for loop iterates until the test expression is false.

$ php forloop.php
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
This is the output of the forloop.php script.

# 2.3.5 PHP foreach Statement

The foreach construct simplifies traversing over collections of data. It has no explicit counter. The foreach statement goes through the array one by one and the current value is copied to a variable defined in the construct. In PHP, we can use it to traverse over an array.

```
foreachstm.php
<?php
$planets = [ "Mercury", "Venus", "Earth", "Mars", "Jupiter",
"Saturn", "Uranus", "Neptune" ];

foreach ($planets as $item) {
echo "$item ";n}
```