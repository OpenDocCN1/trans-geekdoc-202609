# Anchors

You may want to check for the presence of a pattern at the beginning or end of a string rather than simply checking to see if the pattern is contained anywhere within the string. The meta-characters for this are collectively referred to as **anchors**.

```
```php
<?php
// Beginning of the string with a basic string function
$start = (strpos($string, 'foo') === 0);

// Same with a PCRE function
$start = (preg_match('/^foo/', $string) == 1);

// End of the string with basic string functions
$end = (substr($string, - strlen('foo')) == 'foo');

// Same with a PCRE function
$end = (preg_match('/foo$/', $string) == 1);

// Means the same as an exact match with the string
$equal = (preg_match('/^foo$/', $string) == 1);
?>
```
```

+   * `^` (also called the circumflex character) is used at the beginning of an expression within a pattern to indicate that matching should start at the beginning of a string.
* Likewise, `$` is used to indicate that matching of an expression within a pattern should stop at the end of a string.
* When used together, `^` and `$` can indicate that the entirety of `$string` matches the pattern exactly.

> **Start of String or Line**
It's important to note that the behavior of these two operators can vary. By default, they match the beginning and end of `$string`. If the multi-line modifier is used, they match the beginning and end of each line in `$string` instead. This will be covered in more detail later in the Modifiers section of this chapter.