# Chapter II.3: Working with Files 183

```
// Selecting random array index
$index = rand(0, count($filename)) - 1;
// Displaying the randomly-selected file
echo "<img src=\$filename[$index]";
?>
```

# II.3.22. Determining the Image Creation Date

By opening any JPEG file in a text editor, you can see that among the meaningless binary data is the date stored in the text format, for example, 2006:01:03 14:45:03. Thus, determining the date, on which the file was created or last edited, can be done by opening it as a file and using a regular expression to find the date (Listing II.3.35).

Listing II.3.35. Determining the image creation date

```
<?php
// Extracting the file's contents
$filename = 'file_name';
// Placing the file's contents into the $content variable
$content = file_get_contents($filename);
// Extracting the date
preg_match('/^([\d{4}):([\d{2}):([\d{2})\s([\d{2}):([\d{2}):([\d{2}])$/i',
$content,
$out);
echo echo$out[0];
?>
```

# II.3.23. Copying Contents from One Directory to Another

A directory's contents can be copied to a new directory using the recursive directory traversal method (Listing II.3.36).

Listing II.3.36. Copying contents from one directory to another

```
<?php
// Copying the contents of the home directory to home2
descend("home", "home2");
```