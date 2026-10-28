# How to replace a regular expression with a string

Figure 15-7 starts by showing how to use the preg_replace function to replace text that matches a pattern. This works similarly to the str_replace and stri_replace functions for working with strings described in chapter 9. However, the preg_replace function allows you to replace any text that can be specified with a regular expression.

The example replaces any text in the string that matches MBT or MBS with ITEM. Note that the function returns the modified string. As a result, you typically store the modified string in a variable. In this example, the code replaces the original string by storing the modified string in the same variable as the original string. However, you can also store the modified string in another variable.

# How to split a string on a regular expression

Figure 15-7 also shows how to use the preg_split function to split a string on a regular expression. This works similarly to the explode function for working with strings that was described in chapter 9. However, the preg_split function allows you to use a regular expression to split the string. As a result, this function is useful when the delimiter is not as simple as one or two characters.

The example splits the string on a regular expression that matches one or more spaces and commas followed by an optional “and” with zero or more spaces. When this pattern is matched, the preg_split function splits the string. In this example, a poorly formatted list of item numbers is correctly split into an array.