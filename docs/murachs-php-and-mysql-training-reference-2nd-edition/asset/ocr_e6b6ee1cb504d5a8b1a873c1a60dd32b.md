# How to match special characters

| Pattern | Matches |
|---|---|
| `\\` | Backslash character |
| `\/` | Forward slash |
| `\t` | Tab |
| `\n` | New line |
| `\r` | Carriage return |
| `\f` | Form feed |
| `\xhh` | The Latin-1 character whose value is the two hexadecimal digits |

# Special characters

```
```php
$string = "© 2010 Mike's Music. \\ All rights reserved (5/2010).";
preg_match('/\\xA9/', $string)                 // Matches © and returns 1
preg_match('/\/\//', $string)                 // Returns FALSE and issues a warning
preg_match('/\\/', $string)                   // Matches / and returns 1
preg_match('/\\\\/', $string)                 // Matches \\ and returns 1
```
```

# How to match types of characters

| Pattern | Matches |
|---|---|
| `.` | Any single character except a new line character (use `\.` to match a period) |
| `\w` | Any letter, number, or the underscore |
| `\W` | Any character that’s not a letter, number or the underscore |
| `\d` | Any digit |
| `\D` | Any character that’s not a digit |
| `\s` | Any whitespace character (space, tab, new line, carriage return, form feed, or vertical tab) |
| `\S` | Any character that’s not whitespace |

# Types of characters

```
```php
$string = 'The product code is MBR-3461.';
preg_match('/MB./', $string)       // Matches MBT and returns 1
preg_match('/MB\A/', $string)      // Matches nothing and returns 0
preg_match('/MBT-\d/', $string)    // Matches MBT-3 and returns 1
```
```

# Description

+   - The backslash is the *escape character* in regular expressions. It gives special meaning to some characters and removes the special meaning from others.
+   - Since the backslash is the escape character in patterns, any backslash in your pattern must be preceded by another backslash. Then, since the backslash is also the escape character in PHP strings, each backslash must be preceded by another backslash.
+   - When a character has a special meaning in a pattern, it’s called a *metacharacter*.

Figure 15-2　How to match characters