# Functions that compare two strings

| Function | Description |
|---|---|
| `strcmp($str1, $str2)` | Compares two strings and returns an integer value that indicates their sequence: -1 if `$str1` comes before `$str2`, 1 if `$str1` comes after `$str2`, or 0 if they’re the same. This comparison is case-sensitive. As a result, uppercase comes before lowercase. |
| `strcasecmp($str1, $str2)` | A version of the strcmp function that’s case-insensitive. |
| `strnatcmp($str1, $str2)` | A version of the strcmp function that uses a “natural” comparison for numbers within the string. |
| `strnatcasecmp($str1, $str2)` | A version of the strcmp function that uses a “natural” comparison for numbers and is not case-sensitive. |

# How a case-sensitive comparison works

```
```php
$result = strcmp('Anders', 'Zylka');       // $result is -1 (A before Z)
$result = strcmp('anders', 'Zylka');       // $result is 1  (Z before a)
$result = strcasecmp('Anders', 'zylka');   // $result is -25 (A before z)
```
```

# How a “natural” number comparison works

```
```php
$result = strcmp('img06', 'img10');       // $result is -1 (img06 first)
$result = strcmp('img6', 'img10');         // $result is 1  (img10 first)
$result = strnatcmp('img6', 'img10');      // $result is -1 (img6 fisrt)
```
```

# How to compare two strings

```
```php
$result = strnatcasecmp($name_1, $name_2);

if ($result < 0) {
    echo $name_1 . ' before ' . $name_2;
} else if ($result == 0) {
    echo $name_1 . ' matches ' . $name_2;
} else {
    echo $name_1 . ' after ' . $name_2;
}
```
```

# Description

+   - You can use the compare functions to determine the sequence of two strings. This can be useful if you need to sort a series of string values.