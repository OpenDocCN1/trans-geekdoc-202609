This function returns a string consisting of the input string concatenated to itself the specified number of times.

# STR_REPLACE()

```
mixed str_replace (mixed search, mixed replace, mixed subject)
```

Given three arguments as input, this function returns a string consisting of a modified version of the third argument with every instance of the first argument replaced by the second argument. This is a lightweight alternative to the regular expression functions and should be used when the power of regular expressions is not required.

# STRCHR() AND STRSTR()

```
string strchr (string subject, string search)
string strstr (string subject, string search)
string stristr (string subject, string search)
```

These functions behave identically, except that strchr() and strstr() are case-sensitive and stristr() is case-insensitive. They search for the second argument in the first, and return the part of subject following the first instance of search.

# STRLEN()

```
int strlen (string str)
```

Given a string, this function returns a character count.

# STRPOS()

```
int strpos (string haystack, string needle [, int offset])
```

This function returns the position of the first occurrence of the string needle in the string haystack, starting at the position in haystack specified by offset, or at 0 (the beginning of the string) if offset is not specified. If needle is not found, the function returns FALSE.

# STRRPOS()

```
int strrpos (string haystack, char needle)
```