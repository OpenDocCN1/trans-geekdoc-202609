```
$filename = "site.tm";$i;
// If a file with this name exists,
// adding its contents to $buffer
if (file_exists($filename)) {
    $fp = fopen($filename, "r");
    $buffer = fread($fp, filesize($filename));
    fclose($fp);
} else {
    // If there is no file with such a name,
    // leaving the loop
    break;
}
// Placing the parts assembled in the $buffer
// variable into the final file
$fp = fopen("site_final.rar", "w");
fwrite($fp, $buffer);
fclose($fp);
}
?>
```

# II.3.14. Deleting Directories

A directory and all its contents can be deleted in a recursive procedure that removes all files in the current directory, with the help of the unlink() function, before removing the directory itself, using the rmdir() function (Listing II.3.17).

# Listing II.3.17. Deleting a directory and its contents

```
<?php
// Defining a recursive function for deleting
// directories with an unlimited nesting level
function full_del_dir($directory) {
    $dir = opendir($directory);
    while(($file = readdir($dir))) {
```