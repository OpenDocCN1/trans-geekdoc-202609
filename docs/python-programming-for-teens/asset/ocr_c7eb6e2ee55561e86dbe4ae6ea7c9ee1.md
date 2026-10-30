# EXERCISE SOLUTIONS FOR CHAPTER 7

# Exercise 1

```
"""
File: factorial.py
Define and test a recursive factorial function.
"""

def factorial(n):
    """Returns the factorial of n.
    Assumes that n must be >= 1."""
    if n <= 1:
        return 1
    else:
        return n * factorial(n - 1)

def main(upper = 9):
    for n in range(1, upper):
        print("The factorial of", n, "is", factorial(n))

if __name__ == "__main__":
    main()
```

# Exercise 2

```
"""
Program file: mondrian.py

Draws an abstract painting after the style of Piet Mondrian.
"""

from turtle import *
from random import randint

def randomColor():
    "Returns a random RGB color."
    return (randint(0, 255), randint(0, 255), randint(0, 255))

def drawRectangle(x1, y1, x2, y2):
    """Draws a rectangle with the given corner points
    using a random color."""
    (red, green, blue) = randomColor()
    pencolor(red, green, blue)
    fillcolor(red, green, blue)
    begin_fill()
```