gettext and locale— Internationalization and localization modules.

processing; standard input, standard output and standard error streams.

json—JavaScript Object Notation (JSON) processing used with web services and NoSQL document databases.

tkinter—Graphical user interfaces (GUIs) and canvas-based graphics.

turtle—Turtle graphics.

webbrowser—For conveniently displaying web pages in Python apps.

# 4.7 MATH MODULE FUNCTIONS

The math module defines functions for performing various common mathematical calculations. Recall from the previous chapter that an `import` statement of the following form enables you to use a module's definitions via the module's name and a dot (.):

```
In [1]: import math
```

For example, the following snippet calculates the square root of 900 by calling the `math` module's `sqrt` function, which returns its result as a `float` value:

```
In [2]: math.sqrt(900)
Out[2]: 30.0
```

Similarly, the following snippet calculates the absolute value of -10 by calling the `math` module's `fabs` function, which returns its result as a `float` value:

```
In [3]: math.fabs(-10)
Out[3]: 10.0
```

Some `math` module functions are summarized below—you can view the complete list at