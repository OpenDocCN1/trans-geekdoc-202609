
这里有一个简短的测试程序，它在海龟图形窗口的左侧边框显示一列六个菜单项（见图 8.3）。

![](img/4dc3f6307b32ff815a6d58ec1c84708c_203_0.png)

图 8.3
六个菜单项（颜色未显示）。
© 2014 Python Software Foundation.

请注意，当菜单项被创建时，会向所有菜单项传递一个回调函数。这次，回调会在你点击菜单项时更改系统海龟的颜色。

```
"""
testmenuitem.py
A simple tester program for menu items.
"""

from turtle import *
from menuitem import MenuItem

def changePenColor(c):
    """Changes the system turtle's color to c."""
    color(c)

def createMenu(callBack):
    """Displays 6 menu items to respond to the given callback function."""
    x = - (window_width() / 2) + 30
    y = 100
    colors = ("red", "green", "blue", "yellow", "black", "purple")
    shape = "circle"
    for color in colors:
        MenuItem(x, y, shape, color, callBack)
        y -= 30
```

```
def main():
    """Creates a menu for selecting colors."""
    reset()
    shape("turtle")
    createMenu(changeColor)
    return "Done!"

if __name__ == '__main__':
    msg = main()
    print(msg)
    mainloop()
```

## 对用户事件的响应，再次探讨

多个海龟的存在在交互式海龟图形程序中提供了一些有趣的机会和问题。例如，你可能希望在创建后允许用户在窗口中拖动规则多边形对象，或者你可能希望选择一个多边形以便删除。由于多边形包含一个海龟对象，因此在 RegularPolygon 类中定义具有所需行为的 onclick 和 ondrag 方法可能并不太困难。另一方面，任何配置对象以响应 onclick 事件的程序在同时尝试响应屏幕点击事件时都会出现问题，就像第 6 章中讨论的绘图程序一样。在本节中，你将探讨如何让不同类型的对象响应用户事件，以及如何处理这些响应之间可能出现的麻烦交互。

### 到底是谁的点击呢？

考虑前面介绍的菜单项测试程序。该程序在用户点击菜单项时更改系统海龟的颜色。现在，假设你还希望系统海龟响应鼠标事件。例如，用户可以拖动系统海龟来绘制线条，就像第 6 章中所示。这里没有问题，因为系统海龟将是程序中唯一响应此类事件的对象。（请回忆 ondrag 函数针对的是系统海龟。）

然而，假设你还希望能够像第 6 章中那样，通过在海龟图形窗口中任何位置点击来移动系统海龟。你必须使用 onscreen click 函数来告诉屏幕响应点击事件。只要你不尝试用点击来选择菜单项，一切都会很好；系统海龟会按预期移动到点击位置。然而，当你尝试选择一个菜单项时，系统海龟也会移动到该菜单项的位置！

以下是程序中相关函数的代码，以便你可以看到为什么会发生这种情况：

```
def changeColor(c):
    """Changes the pen's color to c."""
    color(c)

def skip(x, y):
    "Moves the pen to the given location without drawing."
    up()
    goto(x, y)
    down()

def main():
    """Creates a menu for selecting colors."""
    reset()
    shape("triangle")
    createMenu(changePenColor)
    onscreenclick(skip)
    listen()
    return "Done!"
```

当你在菜单项上点击鼠标时，菜单项会识别点击事件，屏幕也会识别。因此，changePenColor 和 skip 函数都会被调用。第一个函数更改系统海龟的颜色，第二个函数将海龟移动到菜单项的位置。

幸运的是，菜单项检测到鼠标点击并首先调用 changeColor，然后屏幕检测到鼠标点击并调用 skip。因此，如果 changeColor 能够通知 skip 这一事实，skip 就可以简单地返回而不执行任何操作。

为了解决这个问题，你可以设置一个特殊的对象，称为标志，来跟踪菜单项选择何时发生。该对象包含一个布尔值。如果发生菜单项选择，则值为 True，否则为 False。你的新对象属于 Flag 类，其定义如下：

```
"""
File: flag.py
Defines a Flag class.
"""

class Flag(object):
    """Represents a Boolean flag."""
```

```
def __init__(self, value = False):
    """Sets the initial state."""
    self._value = value

def value(self, newValue = None):
    """Getter and setter."""
    if not newValue is None:
        self._value = newValue
    return self._value
```

现在你可以向程序添加一个标志对象，以便你的 changeColor 和 skip 函数能够通信。你在函数定义之上初始化名为 clickFlag 的变量。由于 clickFlag 是一个模块变量，两个函数都可以定位并更改该标志。它的初始值为 False，因为尚未发生任何点击。

当调用 changeColor 时，它将 clickFlag 的值设置为 True。随后不久调用 skip 时，它会看到标志的值为 True，从而避免移动系统海龟。但 skip 会将标志的值重置为 False，因为下一次点击事件可能不在菜单项上。

如果点击没有发生在菜单项上，则不会调用 changeColor。在这种情况下，标志的值保证为 False，因此 skip 会将系统海龟移动到鼠标坐标。

以下是使用新标志对象的修订代码：

```
from flag import Flag
clickFlag = Flag()            # Create a global flag, initially False

def changeColor(c):
    """Changes the pen's color to c and sets clickFlag to True."""
    clickFlag.value(True)      # Menu item selected, make flag True
    color(c)

def skip(x, y):
    """Moves the pen to the given location without drawing, if a menu
    item has not been clicked. Otherwise, sets clickFlag to False"""
    if not clickFlag.value():   # Menu item not selected, so ok to move
        up()
        goto(x, y)
        down()
    else:                       # Menu item selected, so reset flag to False
        clickFlag.value(False)
```

## 用于井字棋游戏的网格类

要玩井字棋游戏，你首先绘制一个 3×3 的方格网格。（餐巾纸甚至海滩上的平坦区域都可以作为书写表面。）你和对手然后轮流在方格上放置 X 和 O，直到获胜者在一行、列或对角线上连成三个字母为止。图 8.4 显示了该游戏在海龟图形窗口中的一个示例结果。

![](img/4dc3f6307b32ff815a6d58ec1c84708c_207_0.png)

图 8.4
一场井字棋游戏。
© 2014 Python Software Foundation.

在本节中，你将开发一个网格类和支持代码来玩两人井字棋游戏。在练习中，你可以修改程序，以便与计算机对战。

### 建模网格

二维网格按行和列布局。例如，考虑一个有三行三列的网格，其中每个位置包含一个整数。整数范围从 0 到 8。你可以通过使用以下嵌套循环结构在每一行中打印连续整数，从而轻松地在 Python shell 中查看此网格：

```
>>> number = 0
>>> for row in range(3):
    for column in range(3):
        print(number, end=" ")
        number = number + 1
    print()
```

```
0 1 2
3 4 5
6 7 8
>>>
```

如果你想将这些数据存储以供以后使用，可以用列表结构表示网格。以下会话将数据放入列表中，然后以二维网格格式输出它们：

```
>>> grid = list(range(9))
>>> index = 0
>>> for row in range(3):
    for column in range(3):
        print(grid[index], end = " ")
        index = index + 1
    print()
```

```
0 1 2
3 4 5
6 7 8
>>>
```

如果用像列表这样的线性结构来建模二维结构似乎很奇怪，你可以定义自己的 Grid 类来更直接地表示网格。你通过提供两个索引值来访问此结构中的每个数据：一个用于行，一个用于列。与海龟图形的坐标系统不同，位置 (0, 0) 位于此结构的左上角。因此，第 1 行第 2 列的数据位于位置 (1, 2)。随着你在网格中向下移动，行索引会变大；向右移动时，列索引会变大。

下一个会话假设此类在 grid 模块中可用。你使用所需行数和列数创建一个 Grid 对象，然后可以向该对象加载数据并打印其内容：

```
>>> from grid import Grid
>>> datum = 0
>>> gryd = Grid(3, 3)      # Create a 3 by 3 Grid object
>>> for row in range(3):
    for column in range(3):
        gryd[row][column] = datum
        datum = datum + 1
```
