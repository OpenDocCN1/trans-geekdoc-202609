And here’s the output:

```
[Dir] .
[Dir] ..
[File] 1.php
[File] 10.php
[File] 11.php
[File] 12.php
[File] 13.php
[File] 14.php
[File] 15.php
[File] 16.php
[File] 17.php
[File] 18.php
[File] 19.php
[File] 2.php
[File] 3.php
[File] 4.php
[File] 5.php
[File] 6.php
[File] 7.php
[File] 8.php
[File] 9.php
[Dir] demo
[File] extensions.ini
[Dir] ftploads
[File] sample.zip
```

The alternative approach is to use the dir function, which is a “pseudo” class built into PHP. In terms of usage it’s almost exactly the same:

```
File: 12.php
<?php
// Specify current directory
$location = './';
// Open current directory
$dir = dir($location);
// Loop through the directory
while ($entry = $dir->read()) {
// If $entry is a directory...
if (is_dir($location . $entry)) {
echo '|Dir| ' . $entry . '<br />';
}
// If $entry is a file...
} else if (is_file($location . $entry)) {
```