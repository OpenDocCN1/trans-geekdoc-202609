| Special Character | Description | Example |
|---|---|---|
| \ | Escapes the following character | \. stands for period (.) |

TIP: The de facto standard reference for regular expressions is the title *Mastering Regular Expressions*, by Jeffrey E. F. Friedl—a fun read.

Other special characters and expressions are available (for instance, a character that refers to a digit, \d).

# Using Perl-Compatible Regular Expressions

```
preg_match()

```php
<?php
$string = 'This site runs on PHP ' . phpversion();
preg_match('/php ((\d)\.\d+.\d+)/i',
    $string, $matches);
vprintf('Match: %s<br /> Version: %s; Major: %d.',
    $matches);
?>
```
```

Searching in Strings Using PCRE (preg_match.php)

Matching patterns in PCRE is done using preg_match() if only one occurrence is searched for, or preg_match_all() if multiple occurrences may exist. The syntax is as follows: first the pattern, then the string, and then the resulting array. However, for the pattern you need delimiters; most of the time slashes