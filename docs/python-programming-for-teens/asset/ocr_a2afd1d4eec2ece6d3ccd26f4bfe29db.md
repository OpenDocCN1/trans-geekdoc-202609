Here is the pseudocode for the recursive design of the function:

```
Function cCurve(x1, y1, x2, y2, level)
    If level == 0:
        drawLine(x1, y1, x2, y2)
    Else
        xm = (x1 + x2 + y1 - y2) // 2
        ym = (x2 + y1 + y2 - x1) // 2
        cCurve(x1, y1, xm, ym, level - 1)
        cCurve(xm, ym, x2, y2, level - 1)
```

The function drawLine uses the turtle to draw a line between two given endpoints.

# Code for the Program

The program includes definitions of the functions cCurve, drawLine, and main. Note that, unlike the mondrian program, the ccurve program draws a line segment as the base case.

```
"""
Program file: ccurve.py

This program prompts the user for the level of
a c-curve and draws a c-curve of that level.
"""

from turtle import *

def drawLine(x1, y1, x2, y2):
    """Draws a line segment between the endpoints."""
    up()
    goto(x1, y1)
    down()
    goto(x2, y2)

def cCurve(x1, y1, x2, y2, level):
    if level == 0:
        drawLine(x1, y1, x2, y2)
    else:
        xm = (x1 + x2 + y1 - y2) // 2
        ym = (x2 + y1 + y2 - x1) // 2
        cCurve(x1, y1, xm, ym, level - 1)
        cCurve(xm, ym, x2, y2, level - 1)

def main():
    # Obtain the level and size from the user.
    level = numinput("Input Dialog", "Enter the level",
                     default = 0, minval = 0)
```