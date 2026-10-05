# II.3.21. Outputting a Random File

Placing the names of all files into an array reduces the task of displaying a random file to specifying a random array element (Listing II.3.34).

# Listing II.3.34. Outputting a randomly selected file

```
<?php
// The path to the directory
$path = "The_path_to_the_destination_directory/";
// Opening the directory
$dir = opendir($path);
// Reading the directory's contents
while((($file = readdir($dir)) != false)
{
    // If the current item is a file,
    // placing its path into a temporary array
    $filename[] = $path.$file;
}
// Closing the directory
closedir($dir);
```

![](bbox=[0.137, 0.111, 0.943, 0.456])