# FIGURE 12.1 File pointers

![](bbox=[0.18, 0.08, 0.85, 0.35])

If the filename begins with http:// then an HTTP connection to the specified server is opened and a pointer to the requested file is returned.

Figure 12.1 illustrates the concept of a file pointer with files open in two modes.

Once you have finished accessing a file, you should close it to free up memory and inform the operating system that you have finished with the file. In PHP, the function fclose() is used to close a file:

```
fclose (filestream);
```

The fclose() function requires the resource stream of the file to close and returns true or false depending on whether it was able to close the file or not. The following script illustrates the use of these two functions in what is at the moment a rather useless example (we will improve it a little later):

```
<?php
// File: example12-1.php

$fileTextFile = fopen ("text.txt",'a');

if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
else
    echo "<p>File Closed</p>";
?>
```

There is no output from the above script (unless there is a problem with opening or closing the file).

| NOTE | If you are running on a UNIX system then you need to ensure that you have the correct permissions in the directory to which you are writing. |