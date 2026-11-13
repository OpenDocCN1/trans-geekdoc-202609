MySQL query. To solve this problem, I used some string manipulation functions to examine the end of the user's query and remove instances of the letter s. Let's explore these functions in turn.

The substr() function allows you to extract part of a string for use in comparisons and other operations. For example, if the last letter in the string is an s character, you can chop it off and try again if the initial query produces no results.

The invocation of substr() is as follows:

```
substr(str, begin, end)
```

Here, str is the original string, begin is the starting character index, and end is the number of characters to remove. The start of a string is index 0. For example, the following code prints cde, the three characters starting at index 2:

```
echo substr('abcdef', 2, 3);
```

> NOTE In order to calculate an index for substr(), you may need to know the length of your string. Use strlen(str) to determine a string's length.

One very useful shortcut is that if you omit the end argument, substr() returns all of the characters from the starting index (begin) to the end of the string. Here's how to get all characters in a string starting at index 2:

```
echo substr('abcdef', 2); // cdef
```

In addition, if you specify a negative value for begin, substr() (and many other string functions) starts counting from the end of the string, as in this example that extracts the next-to-last two characters of a string:

```
echo substr('abcdef', -3, 2); // de
```

Once you find a substring that interests you, there are quite a number of things you can do to the string, including the following:

+   **Reassign a specified portion of the string** by using substr() to chop off the excess characters. For example, $string = substr($string, 0, 10); sets $string to the first 10 characters of its original value.

+   **Remove the final N characters** by using the substr() and strlen() functions together. For example, $string = substr($string, 0, strlen($string) - 3); sets $string to all but the last three characters of the initial value.

+   **Replace characters** by using the substr_replace() function, which allows you to specify a substring and replace it with a string of your liking. For example, substr_replace('abcdef', 'bbb', 1, 2) returns abbbdef.