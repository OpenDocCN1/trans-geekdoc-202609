# Using Relative Paths for File Access

```
<?php
$directory = dirname(__FILE__);
$filename = basename(__FILE__);
print "This script is called $filename and resides in $directory.";
?>
```

# *Determining Directory Name and Filename (pathinfos.php)*

To use a relative path, you can now call dirname(__FILE__) and then attach the relative path, taking into consideration the directory separator character, which is / on UNIX/Linux, \ on Windows, and : on Mac OS X. Usually, / works fine on most systems, but you should note the requirements of the system on which you want to host your site.

The sister function to dirname() is basename(); this one determines the filename portion of a path.

The listing at the beginning of this phrase uses both basename() and dirname() and __FILE__ to determine information about the current path: directory and filename. Figure 6.2 shows the script’s output.

![](bbox=[0.18, 0.67, 0.97, 0.84])

Figure 6.2 Detecting the script's name and its directory.