![](bbox=[0.14, 0.1, 0.72, 0.25])

# Figure 28.1 JavaScript Shows the PHP Version

However, it is somewhat more difficult if the variable value to be output contains special characters that would invalidate the resulting JavaScript code. The following characters are particularly “dangerous”:

+   **Quotation marks**
+   These can be conveniently adjusted using addslashes().

+   **All characters for which there is an escape sequence**
+   These are \r, \n, \t, and so on. A line break within a string should not be output as a line break, but as \n. These special characters must therefore be treated specially:

```
$replacement = [
    "\n" => "\\\n",
    "\r" => "\\\r",
    "\t" => "\\\t"
];
$variable = addslashes($variable);
$variable = strtr($variable, $substitution);
```

Finally, the variable is output as JavaScript code:

```
<?php
echo("<script>\n");
echo("var phpVariable = \"$variable\";\n");
echo("</script>");
?>
```

So what happens to the $variable PHP variable in which the following string is stored?

> > "There isn't ever going to be an end," she said.
> > (Jodi Kantor)

After going through the two steps listed previously, $variable has this value:

```
$variable = "\\\\\"There isn\\'t ever going to be an end\\\\\", she said.\n
(Jodi Kantor)";
```