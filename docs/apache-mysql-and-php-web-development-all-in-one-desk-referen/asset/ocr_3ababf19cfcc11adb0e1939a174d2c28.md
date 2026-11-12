Instead, put the comment on a line before or after the command you're discussing:

```
# Store 100 in the variable x
set x 100
```

# Breaking up long lines

Tcl is picky about its format. Although some languages let you break up a statement among multiple lines, Tcl does this only if it's looking for a terminator to a bracket or curly brace. But you can divide up a command elsewhere, provided you end the first line with a space followed by a backslash.

For example, suppose you have a command like this:

```
label .mylabel -text .
```

You can break up this command into multiple lines like this:

```
label \\
.mylabel \\
-text
.
```

![](bbox=[0.04, 0.52, 0.145, 0.6])

When the Tcl interpreter sees a line ending with a space and a backslash, the interpreter continues reading what's on the next line as if the text is still on the previous line. In other words, Tcl fuses all the lines together into a single line.