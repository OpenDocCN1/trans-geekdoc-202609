# Functions that search a string

| Function | Description |
|---|---|
| `strpos($str1, $str2[, $offset])` | Searches `$str1` for an occurrence of `$str2`. If `$str2` is found, returns an integer value for the position. If `$str2` isn't found, returns FALSE. By default, the search starts at position 0, but you can use `$offset` to specify the start position. |
| `stripos($str1, $str2[, $offset])` | A version of `strpos` that's case-insensitive. |
| `strrpos($str1, $str2[, $offset])` | A version of `strpos` that searches in reverse, from the end of the string to the start. |
| `strripos($str1, $str2[, $offset])` | A version of `strrpos` that's case-insensitive. |

# Code that searches a string for spaces

```
```php
$name = 'Martin Van Buren';
$i = strpos($name, ' ');      // $i is 6
$i = strpos($name, ' ', 7);   // $i is 10 - use offset to find second space
$i = strrpos($name, ' ');     // $i is 10 - search string in reverse
```
```

# Code that searches a string for a substring

```
```php
$name = 'Martin Van Buren';
$i = strpos($name, 'Van');  // $i is 7
$i = strpos($name, 'van');  // $i is FALSE - case-sensitive
$i = stripos($name, 'van');  // $i is 7     - case-insensitive
$i = strripos($name, 'A');    // $i is 8     - reverse + case-insensitive
```
```

# Code that splits a string into two substrings

```
```php
$name = 'Ray Harris';
$i = strpos($name, ' ');
if ($i === false) {
    $message = 'No spaces were found in the name.';
} else {
    $first_name = substr($name, 0, $i);      // $first_name = Ray
    $last_name = substr($name, $i+1);         // $last_name = Harris
}
```
```

# Functions that replace part of a string

| Function | Description |
|---|---|
| `str_replace($str1, $new, $str2)` | Returns a new string with all occurrences of `$str1` in `$str2` replaced with `$new`. It is case-sensitive. |
| `str_ireplace($str1, $new, $str2)` | A version of `str_replace` that's case-insensitive. |

# Code that replaces periods with dashes in a phone number

```
```php
$phone = '554.555.6624';
$phone = str_replace('.', '-', $phone);    // $phone is '554-555-6624'
```
```

# Code that replaces one string with another string

```
```php
$message = 'Hello Ray';
$message = str_ireplace('hello', 'Hi', $message);    // $message is 'Hi Ray'
```
```

Figure 9-4 — How to search strings and replace parts of strings