# Part II: Solutions

```
$fd = fopen($filename, "w");
fwrite($fd, $buffer);
close($fd);
?>
```

# ## II.3.17. Scrambling Text File Lines

Lines in a file can be randomly scrambled in the following way (Listing II.3.20): The lines are extracted from the text.txt file and placed into an array using the file() function, with the contents of the array scrambled using the shuffle() function.

# Listing II.3.20. Scrambling text file lines

```
<php
// The file's name
$filename = "text.txt";
// Reading the file's contents
$lines = file($filename);
// Scrambling the array's elements
shuffle($lines);
// Removing all trailing spaces
array_walk($lines, 'trim_array');
// Saving the updated results
$fd = fopen($filename, "w");
fwrite($fd, implode("\r\n", $lines));
close($fd);

function trim_array(&$item, $key)
{
$item = trim($item);
}
?>
```

The array_walk() function and the trim_array() function are used to pass each element of the intermediate $lines array through the trim() function to delete possible leading and trailing space characters and carriage return characters.

The results of the script's operation the text.txt file may look like as shown in Listing II.3.21.