```
<?php
print(linkinfo("data.txt"));
?>
```

# array lstat(string filename)

The stat function executes C's stat function and returns an array. The array contains 13 elements, numbered starting with zero. If the filename argument points to a symbolic link, the array will reflect the link, not the file to which the link points. To get information about the files to which the link points, use the stat function. Table 8.7 lists the contents of the array.

Figure 8-4. lstat.