The **fgets()** function: reads an entire line from the file opened by fopen(). It takes as argument the file pointer returned by fopen(). This function reads the line up to the end-of-line character, usually a line feed or carriage return. It returns the line read as a string, including the end-of-line character. If it reaches the end of the file, it returns false.

# Example:

```
<?php
$handle = fopen("filetext/poem1.txt", "r");
$content = fgets($handle);
echo $content;
?>
```

# Result: