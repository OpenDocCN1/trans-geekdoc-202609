They are sequences of characters, like "PHP supports string operations".

Built-in string functions is given in function reference PHP String Functions

Following are valid examples of string

$string_1 = "This is a string in double quotes";

$string_2 = "This is a somewhat longer, singly quoted string";

$string_39 = "This string has thirty-nine characters";

$string_0 = ""; // a string with zero characters

Singly quoted strings are treated almost literally, whereas doubly quoted strings replace variables with their values as well as specially interpreting certain character sequences.

```
<?php
$variable = "name";
$literally = 'My $variable will not print!\n';

print($literally);
print "<br />";

$literally = "My $variable will print!\n";

print($literally);
?>
```

This will produce the following result =
My $variable will not print!\nnMy name will print!\n