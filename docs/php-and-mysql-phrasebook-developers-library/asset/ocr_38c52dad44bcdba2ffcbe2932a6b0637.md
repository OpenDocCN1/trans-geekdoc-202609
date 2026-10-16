PHP also supports several functions related to printf():

+   - sprintf() works like printf(), but returns the string and does not print it.
+   - vprintf() works like printf(), but expects the values for the placeholders in the string to be in the form of an array.
+   - vsprintf() is a mixture of sprintf() and vprintf(): The placeholder values are provided in an array, and the function returns the string but does not print it.

# Scanning Formatted Strings

```
sscanf($date, '%d/%d/%d')

<?php
$date = '02/01/06';
$values = sscanf($date, '%d/%d/%d');
vprintf('Month: %d; Day: %d; Year: %d.', $values);
?>
```

Scanning Formatted Strings (sscanf.php)

Another function related to printf() is sscanf(). This one parses a string and tries to match it with a pattern that contains placeholders. The $input string contains a date and is scanned using the string '%d-%d-%d' with several placeholders, as shown in the preceding phrase. The function returns an array with all values for the matched placeholders. Then this array is passed to vprintf() to print it.