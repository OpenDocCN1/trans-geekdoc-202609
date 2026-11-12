In the index.php file, we put the code that will read the contents of the poem1.txt file:

```
```php
<?php
// Read the contents of a file in a string
$content = file_get_contents('filetext/poem1.txt');

// Display the contents of the file
echo $content;
?>
```
```

This PHP code reads the contents of a text file named "poem1.txt" located in the "filetext" directory ( This is one of Shakspare's most famous poems). The **file_get_contents()** function is used to read the contents of the file and store them in a variable called $content. The contents of the file are then displayed on screen using the **echo $content;** command.

Running index.php will produce the following result:

![](bbox=[0.035, 0.655, 0.955, 0.865])

The result shows that line breaks were not respected when displaying the contents of the "poeme.txt" file.