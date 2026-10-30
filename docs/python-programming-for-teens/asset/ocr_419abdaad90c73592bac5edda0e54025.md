```
if not newValue is None:
    self._value = newValue
    return self._value

"""
File: menuitem.py
Defines a class for menu items.
"""

from turtle import Turtle

class MenuItem(Turtle):
    """Represents a menu item."""

    def __init__(self, x, y, shape, color, callBack):
        """Sets the initial state of a menu item."""
        Turtle.__init__(self, shape=shape, visible=False)
        self.speed(0)
        self.up()
        self.goto(x, y)
        self.color(color, color)
        self._callBack = callBack
        # Pass my color to the callback function when I'm clicked
        self.onclick(lambda x, y: self._callBack(color))
        self.showturtle()

"""
sketching.py
Simple drawing by dragging the mouse; also allows movement by clicking.
Also allows change of color by click on menu item.
"""

from turtle import *
from flag import Flag
from menuitem import MenuItem

clickFlag = Flag()

def changeColor(c):
    """Changes the system's turtle's color to c and sets clickFlag to True."""
    clickFlag.value(True)    # Menu item selected, make flag True
    color(c)

def createMenu(callBack):
    """Displays 6 menu items to respond to the given callback function."""
    x = - (window_width() / 2) + 30
    y = 100
```