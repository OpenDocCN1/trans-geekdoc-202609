# Perspective

Although you can code a data validation application in many different ways, the Registration application in this chapter is worth studying because it presents a highly structured, object-oriented approach to data validation. Although this may seem like it takes a lot of time and effort to set up, it will save you time and effort in the long run because it makes your code easier to test, debug, and maintain. In addition, once you set up a structured approach like this, you can easily modify it to use it for the data on other forms.

# Terms

+   - regular expression
+   - escape character
+   - metacharacter
+   - character class
+   - bracket expression
+   - assertion
+   - look-ahead assertion
+   - negative look-ahead assertion
+   - multiline regular expression
+   
+   - global regular expression
+   - exception
+   - throw statement
+   - stack trace
+   - try-catch statement
+   - try block
+   - catch block
+   - exception handling

# Summary

+   - *A regular expression* defines a pattern that can be searched for in a string. The pattern is case sensitive and enclosed in forward slashes in a text string. A case-insensitive regular expression ignores the case in both the pattern and string.
+   - The backslash is the *escape character* in regular expressions. It gives special meaning to some characters and removes the special meaning from others. When a character has a special meaning in a pattern, it’s called a *metacharacter*.
+   - A *character class* lets you match a single character from a list of possible characters. You can use a *bracket expression* inside a character class for several predefined character ranges, and you can combine several bracket expressions in one character class.
+   - A *look-ahead assertion* is a special type of subpattern that must be matched for the overall pattern to be matched. A *negative look-ahead assertion* is similar to a look-ahead assertion except that its pattern must *not* be matched.
+   - In a *multiline regular expression*, the `^` pattern matches the beginning of a line and the `$` pattern matches the end of a line. In a *global regular expression*, the pattern finds multiple matches in the string.
+   - You can use the *throw statement* to throw an Exception object. That will trigger a runtime error called an *exception*. Then, you can use the methods of the object to get more information about the exception.