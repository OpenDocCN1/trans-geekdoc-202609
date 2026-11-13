| Expression | Description |
| :--- | :--- |
| [[[:alpha:]]] | It matches any string containing alphabetic characters aA through zZ. |
| [[[:digit:]]] | It matches any string containing numerical digits 0 through 9. |
| [[[:alnum:]]] | It matches any string containing alphanumeric characters aA through zZ and 0 through 9. |
| [[[:space:]]] | It matches any string containing a space. |

# # PHP's Regexp POSIX Functions

PHP currently offers seven functions for searching strings using POSIX-style regular expressions:

| Function | Description |
| :--- | :--- |
| ereg() | The ereg() function searches a string specified by string for a string specified by pattern, returning true if the pattern is found, and false otherwise. |
| ereg_replace() | The ereg_replace() function searches for string specified by pattern and replaces pattern with replacement if found. |
| eregi() | The eregi() function searches throughout a string specified by pattern for a string specified by string. The search is not case sensitive. |
| eregi_replace() | The eregi_replace() function operates exactly like ereg_replace(), except that the search for pattern in string is not case sensitive. |
| split() | The split() function will divide a string into various elements, the boundaries of each element based on the occurrence of pattern in string. |
| spliti() | The spliti() function operates exactly in the same manner as its sibling split(), except that it is not case sensitive. |
| sql_regcase() | The sql_regcase() function can be thought of as a utility function, converting each character in the input parameter string into a bracketed expression containing two characters. |

# # PHP—Function ereg()

# ## Syntax

```
int ereg(string pattern, string originalstring, [array regs]);
```