| Modifier | Description |
| :--- | :--- |
| i | Causes the matching to be case insensitive: letters in the pattern match both uppercase and lowercase characters in the string |
| m | Causes the target string to be treated as separate lines of text if it contains newlines. This means that ^ and $ characters in the expression match not only the beginning and end of the string, but also the beginning and end of each line in the string |
| s | Normally, the dot (.) character in an expression matches any character except newline characters. By adding this modifier you can make the dot character match newlines too |
| x | This modifier causes whitespace characters in the pattern to be ignored, rather than treated as characters to match. (However, whitespace inside a character class is never ignored.) This allows you to split your regular expression over lines and indent it, much like regular PHP code, to aid readability. You can also include comments in the expression by preceding them with a # symbol. If you explicitly want to match whitespace characters when using this modifier, use " " (for a space), "\t" (for a tab), or "\s" (for any whitespace character) |
| e | Only used by `preg_replace()`. This modifier allows you to use PHP code in your replacement string. Any backreferences ($1, $2, and so on) in the replacement string are first replaced by their matched text. Then the string is evaluated as PHP code, and the resulting expression used for the replacement |
| U | Inverts the "greediness" of quantifiers within the expression: any non-greedy quantifiers become greedy, and any greedy quantifiers become non-greedy |

For example, you can make an expression case insensitive by adding `i` after the closing delimiter of the expression:

```
```php
$text = "Hello, world!";
echo preg_match( "/hello/", $text ) . "<br />"; // Displays "0"
echo preg_match( "/hello/i", $text ) . "<br />"; // Displays "1"
```
```

The following example shows how the `m` modifier works. The first expression attempts to match the characters “world!” followed by the end of the string. Because “world!” is not at the end of the target string, the match fails. However, the second expression uses the `m` modifier. This causes the `$` character to match the newline after “world!”:

```
```php
$text = "Hello, world!\nHow are you today?\n";
echo preg_match( "/world!$/", $text ) . "<br />"; // Displays "0"
echo preg_match( "/world!$/m", $text ) . "<br />"; // Displays "1"
```
```

The `m` modifier is useful if you're working with a multiline string (such as that read from a file or database query) that you want to treat as multiple lines of text rather than as one long string.

By adding the `x` modifier to your expression you can split the expression over multiple lines and add comments — very handy for complex expressions: