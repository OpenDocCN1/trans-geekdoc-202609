# Functions that convert between strings and arrays

| Function | Description |
|---|---|
| explode($sep, $str) | Returns an array of strings that are separated in $str by the string delimiter specified by $sep. This delimiter can be any length. If it is the empty string, it returns FALSE. |
| implode($sep, $sa) | Returns a string that results from joining the elements in the array $sa with the $sep string between them. The $sep parameter is required, but it may be an empty string. |

# How to convert a string to an array

```
$names = 'Mike|Anne|Joel|Ray';
$names = explode('|', $names);
$name1 = $names[0];    // $name1 is 'Mike'
$name2 = $names[1];    // $name2 is 'Anne'
```

# How to convert an array to a string

```
$names = implode('|', $names);    // $names is 'Mike|Anne|Joel|Ray'
```

# How to convert an array to a tab-delimited string

```
$names = implode('\t', $names);
```

# Functions that convert between strings and ASCII integer values

| Function | Description |
|---|---|
| chr($value) | Returns a string with the character who's ASCII value is specified by $value. |
| ord($string) | Returns an integer which is the ASCII value of the first character in $string. |

# How to convert an integer value to a character

```
$char = chr(65);    // $char is 'A'
$char = chr(66);    // $char is 'B'
```

# How to convert a character to an integer value

```
$val = ord('A');    // $val is 65
$val = ord('B');    // $val is 66
$val = ord('Bike');    // $val is 66
```

# Description

+   - The ASCII character set is a set of characters that provides for most characters, numbers, and symbols in the English language. This character set has an integer value that corresponds with each character.