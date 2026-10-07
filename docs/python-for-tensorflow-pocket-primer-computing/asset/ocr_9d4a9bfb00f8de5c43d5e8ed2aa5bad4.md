# SOME STANDARD MODULES IN PYTHON

The Python Standard Modules Library provides many modules that can simplify your own Python scripts. A list of the Standard Library modules is here:

http://www.python.org/doc/

Some of the most important Python modules include cgi, math, os, pickle, random, re, socket, sys, and time.

The code samples in this book use the modules math, os, random, re, sys, and urllib. You need to import these modules in order to use them in your code. For example, the following code block shows you how to import four standard Python modules:

```
import datetime
import re
import sys
import time
```

Some code samples in this book import one or more of the preceding modules, as well as other Python modules.

# THE HELP() AND DIR() FUNCTIONS

An Internet search for Python-related topics usually returns a number of links with useful information. Alternatively, you can check the official Python documentation site: docs.python.org

In addition, Python provides the help() and dir() functions that are accessible from the Python interpreter. The help() function displays documentation strings, whereas the dir() function displays defined symbols.

For example, if you type help(sys) you will see documentation for the sys module, whereas dir(sys) displays a list of the defined symbols.

Type the following command in the Python interpreter to display the string-related methods in Python: