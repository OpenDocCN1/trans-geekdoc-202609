+   "^" matches the *beginning* of the string. The expression "^ab" matches any string with "ab" at the beginning of it. Note that "^" is outside a bracket expression. Strings "about","abbe", and "abhor" are valid examples.

+   "$" matches the end of the string. The expression "ab$" matches any string with "ab" at the end of it. Strings "drab","scab", and "wxab" will match the regex "ab$".

> To use these characters as ordinary characters, you have to escape them. For example, if you want to search for a $ in your string, you have to escape,that $ in the expression: "\\$".

Character classes are shorthand notations used in regular expressions:

+   "[[:alnum:]]" matches any string containing *alphanumeric* characters of the set locale. This is equivalent to writing the regex "[a-zA-Z_0-9]" for English.

+   "[[:digit:]]" matches any string containing *digits*. An equivalent regex would be "[0-9]".

+   "[[:alpha:]]" matches strings containing *alphabetic characters* of the set locale. The equivalent regex for English is "[a-zA-Z]".

Within a bracket expression, a multi-character sequence enclosed in ".[." and ".]" stands for the sequence of characters of that element. The sequence is a single element of the bracket expression's list. A bracket expression containing a multi-character element can thus match more than one character. For example, if the sequence includes a 'ch' element, then the regex "[[.ch.]]*c" matches the first five characters of 'chchcc'. \

Within a bracket expression, an element enclosed in "[=" and "=]" is an *equivalence class*, standing for the sequences of characters of all elements equivalent to that one, including itself. (If there are no other equivalent collating elements, the treatment is as if the enclosing delimiters were ".[." and ".]"). For example, if `o` and `^` are the members of an equivalence class, then "[[=o=]]", "[[=^=]]", and "[o^]" are all synonymous.

For further information, refer http://linux.ctyme.com/man/man1860.htm/.

# Creating a Regular Expression

Let's create a regex for matching currency:

+   10000
+   10,000
+   10000.00
+   10,000.00

All these formats are valid, and "0" should be a valid amount as well. The number should satisfy the following criteria:

+   It should be either 0 or any number which does not start with a zero

+   It can have up to two digits after the decimal