# # How to use look-ahead assertions

In a regular expression, an *assertion* is a fact about the pattern that must be true. For example, you can use the ^ and $ metacharacters to make an assertion about the position of the pattern in the string.

Figure 15-5 shows how to use another type of assertion called a *look-ahead assertion* that places a condition on the characters that follow the assertion. This allows you to specify an additional pattern for a regular expression. Look-ahead assertions are position dependent. In other words, the pattern in the assertion must be matched starting at the current location in the string. To create a look-ahead assertion, you code an opening parenthesis followed by a question mark, an equal sign, the pattern for the assertion to test, and a closing parenthesis.

The first example shows how to use a look-ahead assertion. Without the assertion, the pattern matches a string that consists of six alphanumeric characters. However, the assertion places a further restriction on those six characters that at least one of them must be a digit. To do that, the assertion states that zero or more characters (.*) must be followed by a digit.

A *negative look-ahead assertion* is similar to a look-ahead assertion except that it checks to make sure its pattern is *not* matched. To create a negative look-ahead assertion, you code an opening parenthesis followed by a question mark, an exclamation mark, the pattern for the assertion to test, and a closing parenthesis.

This figure also shows how to use a negative look-ahead assertion. Without the assertion, the pattern matches the digits 0 through 3 followed by any other digit. The negative look-ahead assertion excludes the numbers 32 to 39. It states that if the next digit is a 3 followed by a 2 through 9, the regular expression does not match the pattern.

You could also use a regular expression without the negative look-ahead assertion to perform the same test on the string like this:

```
```regex
/^([0-2][[:digit:]]|3[0-1])$/
```
```

For a simple pattern, either form works equally well. When you have a more complex pattern, however, using an assertion often yields code that's shorter and easier to understand.

The second example shows a pattern that you can use to validate passwords. This example begins by showing the full pattern. Then, it explains the parts of the pattern. In short, the pattern ensures that a password consists of six or more characters with at least one digit and one punctuation character. Finally, the last two statements use the pattern to test two passwords. The first does not match the pattern, but the second does.

If necessary, you can modify this pattern to add, remove, or change some of its restrictions. For example, you can add another assertion that requires an uppercase letter.