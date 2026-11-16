You may be tempted to replace "<script[^>]*>.*.?</script>" with "<script.>" but if you look carefully, or try out the example after modifying it you will find that the returned string is empty because the ">" part of the "<script.*>" will match the last ">" rather than the first, besides a ">" operator in the script will also break the regex.

As explained previously, /e modifier makes preg_replace() treat the replacement parameter as PHP code after the appropriate references substitution is done. Make sure that replacement constitutes a valid PHP code string, otherwise PHP will complain about a parse error at the line containing preg_replace().

# preg_split()

```
array preg_split(string pattern, string subject [, int limit [, int flags]])
```

This function returns an array containing substrings of subject split along boundaries matched by pattern. If limit is specified, then only substrings up to limit are returned. If flags is PREG_SPLIT_NO_EMPTY then only non-empty pieces will be by preg_split().

# preg_quote()

```
string preg_quote(string str [, string delimiter])
```

This function will take str and put a backslash in front of every character that is part of the regular expression syntax ( . \\ + * ? [ ^ ] $ ( ) { } = ! < | : ). If the optional delimiter is specified, it will also be escaped. This is useful for escaping the delimiter that is required by the PCRE functions.

# Summary

In this chapter we dealt with a few simple concepts, but these very concepts make up the major part of user interaction in an application. The things we dealt with included:

+   - Getting user input
+   - Handling user input
+   - A better method for doing the above in an object-oriented manner
+   - Regular expressions and how to use them productively