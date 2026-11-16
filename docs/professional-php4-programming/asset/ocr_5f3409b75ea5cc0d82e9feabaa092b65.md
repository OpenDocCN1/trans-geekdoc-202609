# ereg_replace()

```
string ereg_replace(string pattern, string replacement, string string)
```

This is a function that replaces pattern in string with replacement. This function returns the modified string if a match was found:

A common mistake is to use an integer as the replacement value. This does not result in a proper substitution. The number has to be expressed as a string for this to work:

```
$num = '10';
$string = "Ten Little Indians sitting ...";
$string = ereg_replace('Ten', $num, $string);
echo($string);
/* Output: 10 Little Indians sitting ...*/
```

If pattern contains parenthesized substrings, replacement may contain substrings of the form \\digit, which will be replaced by the text in the parenthesized string that matches the values of the digit. \\0 will produce the entire contents of string. Up to nine substrings may be used. Parentheses may be nested, in which case they are counted by the opening parenthesis.

# eregi()

```
int eregi(string pattern, string string [, array regs])
```

This function is identical to ereg() except that this ignores case when matching alphabetic characters:

# eregi_replace()

```
string eregi_replace(string pattern, string replacement, string string)
```

This function is identical to ereg_replace() except that it ignores case distinction when matching alphabetic characters:

```
$text_with_links =
eregi_replace("(([:alnum:])+)://([^<[:space:]]*)([[:alnum:]#?/&=])", "<a
href="\\1://\\2\\3" target="_blank">\\1://\\2\\3</a>", $see_also);
```

This takes the string $see_also, looks for URL-like patterns within it, and returns linked HTML with proper <a href = ... > tags.

([[:alnum:]]+) will match at least one alphanumeric character, this could be "http" or "ftp" or "mailto". This is followed by "://". The second set of parenthesis (([[:space:]]*) ensures that there is no whitespace after the "://". The third set of parenthesis (([[:alnum:]]#?/&=)) matches all alphanumeric characters after the second set of parenthesis and some extra characters which can occur in a URL.

The replacement string which looks so cryptic is simply a series of backreferences. The <a href=\" portion generates the start of the HTML anchor tag. \\1 refers to the match of the first set of parenthesis, as mentioned above. Similarly \\2 and \\3 refer to the matches of second and third set of parenthesis. The system is not foolproof because it will also hyperlink a match like wxyz://nofile.ece but will not match www.sanisoft.com/.