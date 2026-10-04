# Creating PHP Pages

![](bbox=[0.152, 0.091, 0.928, 0.563])

Figure 2-12

# How It Works

When PHP comes across an include line in a script, it stops working on the current program and immediately shifts over to whatever file it's told to include. The server parses that second file and carries the results back to the original file, where the parsing continues from where it left off.

Suppose we decided we didn't really want the date to be shown with the trailing zeros. Luckily, PHP has a solution for when formatting the date function. Make the following change to your header.php file and see what happens:

```
<div align="center"><FONT SIZE="4">Welcome to my movie review site!</font>
<br>
<?php
```

67