# A URL for a list of all PHP string functions

http://www.php.net/manual/en/ref.strings.php

# Functions for working with string length and substrings

| Function | Description |
|---|---|
| empty($str) | Returns TRUE if $str is an empty string (""), a NULL value, or "0" (0 as a string). This function also returns TRUE if $str isn't set. |
| strlen($str) | Returns the length of the string. |
| substr($str, $i[, $len]) | Returns a substring of $str starting at the position specified by $i and containing the number of characters specified by $len. If $len is omitted, the function returns the substring from $i to the end of the string. |

# Code that checks a string to determine if a string is empty

```
```php
if (empty($first_name)) {
    $message = 'You must enter the first name.';
}
```
```

# Code that gets the length of a string and two substrings

```
```php
$name = 'Ray Harris';
$length = strlen($name);            // $length is 10
$first_name = substr($name, 0, 3);    // $first_name is 'Ray'
$last_name = substr($name, 4);        // $last_name is 'Harris'
$last_name = substr($name, -6);       // $last_name is 'Harris'
```
```

# Code that formats a phone number in two ways

```
```php
$phone = '5545556624';
$part1 = substr($phone, 0, 3);
$part2 = substr($phone, 3, 3);
$part3 = substr($phone, 6);
$format_1 = $part1 . '-' . $part2 . '-' . $part3;    // 554-555-6624
$format_2 = '(' . $part1 . ')' . $part2 . '-' . $part3;  // (554) 555-6624
```
```

# Code that displays each letter in a string on a separate line

```
```php
$input = 'JAN';
for ($i = 0; $i < strlen($input); $i++) {
    $vert_str .= substr($input, $i, 1);
    $vert_str .= '<br>';
}
```
```

# Description

+   - The length of a string is the number of characters in the string.
+   - A substring is a part of a string.
+   - To specify the position of a character from the left side of a string, use a positive integer value where 0 is the first character, 1 is the second character, and so on. To specify a position from the right side, use a negative integer value.