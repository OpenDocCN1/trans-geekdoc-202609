```
```php
<?php
echo("This is Motortown"); // this PHP comment will be ignored
?>

// this PHP comment will show up in the browser - oops

<!--- this HTML comment will show up in the HTML source, but not in the browser -->
```
```

This can be useful for debugging or for making generated HTML source code more understandable.

# Literals

We've used a lot of literals already in our examples up to this point. PHP understands three basic kinds of literal: textual literals (strings), numeric literals (integers and floating-point numbers), and Boolean literals (true and false).

# Textual Literals

You can specify strings in one of three ways: double quotes, single quotes, or 'here document' syntax.

When you enclose a string literal with double quotes, PHP parses it looking for several types of special character. It looks for the names of variables and substitutes their value in the process. It looks for backslash characters, and reads the following character in order to determine what to replace the two-character code with. Possible values are:

| Value | Meaning |
| --- | --- |
| n | Linefeed (LF) |
| r | Carriage return (CR) |
| t | Tab |
| \\ | Backslash |
| $ | Dollar sign |
| " | Double-quote |
| An octal number of up to three digits | The character whose ASCII code corresponds to the octal number |
| x followed by a hexadecimal number of up to two digits | The character whose ASCII code corresponds to the hexadecimal number |

So, the following code:

```
```php
<?php
echo("This text goes\\nacross several\\nlines\\n\\t\"and this quotation is\\nindented\"\");
?>
```
```