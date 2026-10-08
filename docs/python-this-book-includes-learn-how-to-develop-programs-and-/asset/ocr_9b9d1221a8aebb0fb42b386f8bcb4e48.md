```
for i in [1, 2, 3, 4, 5]:
# notice the blank line
print i
```

The following error will pop up:
**Indentation**: expected an indented block

This error pops up because the interpreter assumes that the blank lines indicate the end of the for loop block.

IPython features a magic function %paste, which accurately pastes everything that's on the clipboard, whitespace and all. This is why you should use IPython.

# Modules

Specific properties of Python language don't appear by default. These include both the ones considered as part of the languages as well as third-party features that you can download yourself. To apply these features, you'll require to import the modules that hold them.

```
import re
my_regex = re.compile("[0-9]+", re.I)
```

In this example, re is the module carrying functions and constants for working with regular expressions. After this import, you can only access those functions by prefixing them using re...

If you already have a separate re in the code, you can use an alias. You can still do this if the module contains an unwieldy name or if you're going to type it a lot. For instance, if you visualize data using matplotlib, then the standard convention to use is:

```
import matplotlib.pyplot as plt
```

# Functions

A function is a directive for accepting zero or more inputs and returning equivalent output. In Python, functions are defined using the def keyword: