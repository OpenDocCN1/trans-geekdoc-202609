# PCRE FUNCTIONS USED IN THIS BOOK

The following PCRE functions are used in the applications created in this book.

# PREG_MATCH() This function is similar to the ereg() function in that you can assign the optional third argument an array of matched subpatterns, if any are found in the regular expression. preg_match returns the number of pattern matches found, or FALSE if no match is found.

```
int preg_match (string pattern, string subject [, array matches])
```

# PREG_REPLACE() This function makes replacements based on Perl regular expressions.

```
mixed preg_replace (mixed pattern, mixed replacement, mixed subject [, int limit])
```

preg_replace() is similar to ereg_replace(), though the pattern here must be a Perl regular expression. It can also make use of \digit to echo the matched sub-string into the result. The optional fourth argument limits the number of replaces that preg_replace makes.

Consider the following example:

```
preg_replace("/(<br>|&nbsp;|[\s])*$/i","",$body);
```

Note that \s denotes all whitespace characters. This example will remove all occurrences of breaks (<br>), non-breaking spaces (&nbsp;), or white space (spaces, tabs, new lines) at the end of the string in $body. This replacement is not case-sensitive (the i flag determines that) to ensure that both <BR> and <br> are matched.

The parentheses indicate that you are specifying a pattern made up of several parts. The | character means or here; you want to match <br> or &nbsp; or any whitespace characters. The asterisk after the closing parenthesis indicates that you want to match any number of repeated occurrences of this pattern (for example, in <br>&nbsp;<br>, the pattern occurs three times, and this expression would match all of them). The final dollar sign character represents the end of the string. By using it, you are saying that you want to match only occurrences of this pattern that are at the string's end, and not globally remove every whitespace character from $body, which would likely be a bad thing.

# PREG_GREP()

```
array preg_grep (string pattern, array input)
```

Given a regular expression string and an array, this function returns an array containing only those elements of the input array that match the regular-expression pattern.