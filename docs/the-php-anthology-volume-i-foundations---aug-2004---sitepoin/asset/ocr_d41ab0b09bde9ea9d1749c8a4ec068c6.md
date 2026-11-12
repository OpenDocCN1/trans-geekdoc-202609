```
widely-used Open Source general-purpose scripting language that
is especially suited for Web development and can be embedded
into HTML.
EOD;

$lines = explode("\n", $text);

echo "<table border=\"1\"/\>\n";
foreach ($lines as $line) {
    echo "<tr>\n<td>$line</td>\n</tr>\n";
}
echo "</table>\n";
?>
```

This breaks the text at the line feed characters and places it in an HTML table, as shown in Figure 5.1.

# Figure 5.1. Exploding Tables

| PHP (recursive acronym for "PHP: Hypertext Preprocessor") is a widely-used |
| Open Source general-purpose scripting language that is especially suited |
| for Web development and can be embedded into HTML. |

> The implode function can be used to reverse the effects of explode, building a string out of a list of array values.

# Short Back and Sides, Please

The trim function is another handy tool; it removes white space characters at the start and end of strings. It might be useful when, for example, you're dealing with form submissions. It works as follows:

```
<?php
$string = ' This has whitespace at both ends ';

// Remove that whitespace!
$string = trim($string);
?>
```