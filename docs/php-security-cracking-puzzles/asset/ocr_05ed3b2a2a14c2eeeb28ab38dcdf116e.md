# # Chapter II.2: Regular Expressions

![](bbox=[0.116, 0.187, 0.946, 0.355])

# ## II.2.1. Removing HTML Tags

HTML tags can be removed using regular expressions with the `preg_replace()` function. The function’s general format is as follows:

```
mixed_preg_replace (mixed pattern, mixed replacement, mixed subject [, , int limit)
```

The function searches the `subject` string for a substring matching the `pattern` regular expression and replaces the found substring with the `replacement` argument. The optional parameter `limit` specifies the number of substitutions to be made. If this parameter is not set or is set to -1, all matches are replaced. The replacement argument can contain references of the `\n` type; each reference of this type is replaced by to the substring matching the regular expression in the nth parentheses.

The n parameter can take values from 0 to 99; the `\0` reference corresponds to the entire pattern. Subpatterns in parentheses are numbered from left to right, starting with 1. If a substring is found that matches the pattern, the function returns the modified value of the subject string; otherwise, the original value of the subject string is returned.