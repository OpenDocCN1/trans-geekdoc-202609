# Reading a file

A file can be opened with the fopen() function, which requires two arguments specifying the file name and one of the file modes listed on the previous page. The fopen() function returns a file pointer that references the file and can be used to read the file's contents.

The file can then be read with a function called fread(), which also requires two arguments: the file pointer, and the length of the file in bytes.

The file's length can be found using the filesize() function, which takes the file name as its argument and returns the size of the file expressed in bytes.

So the technique to read a file with PHP follows this pattern:

+   - open the file using fopen()
- get the file's length with filesize()
- read the file's contents using fread()
- close the file with fclose()

The following example assigns the contents of a text file to a variable, then displays those contents on the page.

![](bbox=[0.198, 0.584, 0.283, 0.683])

```
<html<head><title>Reading a file</title></head>
<body>
<?php
$filename = "quote.txt";
$file = fopen($filename, "r");
$filesize = filesize($filename);
$text = fread($file, $filesize);
fclose($file);
echo("File Size: $filesize bytes");
echo("<pre>$text</pre>");
?>
</body></html>
```