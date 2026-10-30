Here is a short tester program that displays a radial pattern of 10 hexagons, similar to the one shown in Chapter 3. The program creates 10 RegularPolygon objects to do so.

```
"""
testregularpolygon.py
A simple tester program for regular polygons.
"""

from turtle import *
from regularpolygon import RegularPolygon

def main():
    """Draws 10 hexagons in a radial pattern around the origin."""
    reset()
    hideturtle()      # Hide the system turtle
    length = 50
    xPos = 0
    yPos = 0
    sides = 6
    outline = "blue"
    fill = "yellow"
    for heading in range(0, 360, 36):
        RegularPolygon(length, xPos, yPos, heading, sides, outline,
                       fill, fillOn = True)

    return "Done!"

if __name__ == '__main__':
    msg = main()
    print(msg)
    mainloop()
```

# Implementation: The Structure of a Class Definition

Each Python class is defined in a module file. Your Python files thus far have contained a main function and other supporting functions. Now you are about to define a new Python class, named RegularPolygon. By convention, this class goes in a module whose file is named regularPolygon.py. To create this file, you open a new Integrated Development Environment (IDLE) file window by selecting New File from the File menu.