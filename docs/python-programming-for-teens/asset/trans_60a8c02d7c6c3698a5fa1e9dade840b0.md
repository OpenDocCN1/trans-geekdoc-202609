
最近鼠标点击的位置。现在唯一剩下的问题是：这个变量在哪里初始化为空列表？

因为变量 positionHistory 必须在函数调用之间保留其值，所以它必须是模块变量。因此，它在模块开头附近初始化，就像你在之前的示例中对 PI 所做的那样。下面是完整程序的代码：

```
"""
triangle.py
Draws triangles with 3 mouse clicks.
"""

from turtle import *

positionHistory = []

def setVertex(x, y):
    """Sets vertices and possibly connects them."""
    if len(positionHistory) == 0:            # The first click skips
        positionHistory.append((x, y))      # to the first vertex
        skip(x, y)
    elif len(positionHistory) == 1:         # The second click connects
        positionHistory.append((x, y))      # two vertices
        goto(x, y)
    else:
        (xCoord, yCoord) = positionHistory.pop()  # The third click
        skip(xCoord, yCoord)                  # connects the remaining
        goto(x, y)                            # vertices
        (xCoord, yCoord) = positionHistory.pop()
        goto(xCoord, yCoord)

def skip(x, y):
    "Moves the pen to the given location without drawing."
    up()
    goto(x, y)
    down()

def main():
    shape("circle")
    width(2)
    speed(0)
    pencolor("blue")
    onscreenclick(setVertex)
    listen()
    return "Done!"
```

```
if __name__ == '__main__':
    msg = main()
    print(msg)
    mainloop()
```

因为第三次点击清空了位置历史列表，所以你可以继续在其他位置绘制新的三角形。

## 使用两个鼠标按钮

如你所知，鼠标通常至少有两个按钮，位于设备顶部的左侧和右侧。点击左键称为左键单击，点击右键称为右键单击。对于没有右键的鼠标，你可以通过按住 Ctrl 键的同时点击左键来执行右键单击。

你可能通过点击或按住左键来完成大部分与鼠标相关的任务，但右键偶尔也会派上用场。例如，右键单击通常会弹出与当前窗口上下文相关的选项菜单。在本节中，你将学习如何在 turtle 图形中响应右键单击，以为你的应用程序添加一些命令选项。

### 为右键添加事件处理函数

turtle 图形中的每种鼠标事件——单击、拖动或释放——都可能由左键或右键按下引起。函数 onscreenclick、onclick、ondrag 和 onrelease 允许你为左右键指定不同的事件处理函数。你可以通过向这些函数提供第二个可选参数来实现这一点。表 6.2 列出了它们的签名。

表 6.2 注册鼠标事件处理函数的函数

| 函数 | 其作用 |
|---|---|
| onscreenclick(fun, btn = 1, add = None) | 将 fun 注册为处理窗口任意位置点击事件的函数。 |
| onclick(fun, btn = 1, add = None) | 将 fun 注册为处理海龟上的点击事件的函数。 |
| ondrag(fun, btn = 1, add = None) | 将 fun 注册为处理海龟上的拖动事件的函数。 |
| onrelease(fun, btn = 1, add = None) | 将 fun 注册为处理海龟上的释放事件的函数。 |

如你所见，事件处理函数 fun 是必需参数，而按钮编号 btn 是可选参数。（记住：后面没有 = 的参数是必需的。）默认按钮编号为 1，表示左键鼠标按钮。这就是本章迄今为止用于任何鼠标事件的选项。但如果你提供 2 作为第二个参数，turtle 图形会将右键鼠标按钮绑定到该事件的事件处理函数。因此，当用户操作右键鼠标按钮时，你的函数会被触发。

add 选项默认会用新函数替换指定按钮的任何现有事件处理函数。但如果你为此参数提供值 True，turtle 图形会将你的新函数添加到在该事件发生时被触发的函数集合中。因此，你可以为所有四个鼠标事件的两个按钮注册多个事件处理函数。

### 示例 1：使用随机颜色的简单绘图

为了尝试使用右键鼠标按钮，你可以回到 shell 中进行素描。在此会话中，你将 goto 函数注册为左键鼠标按钮的屏幕点击事件。这会在海龟的位置与左键单击的位置之间绘制一条线段。（参见本章前文的图 6.2。）你还将一个 lambda 表达式注册为右键鼠标按钮的屏幕点击事件。该表达式构建了一个函数，将画笔颜色设置为随机颜色。以下是此会话的记录：

```
>>> from turtle import *
>>> from random import choice
>>> colors = ("red", "blue", "green", "purple", "orange")
>>> shape("circle")
>>> onscreenclick(goto)
>>> onscreenclick(lambda x, y: pencolor(choice(colors)), btn = 2)
>>> listen()
```

现在，当你左键单击时，海龟会像之前一样绘制一条线段。但当你右键单击时，海龟的画笔颜色会重置为随机选择的颜色（可能与之前相同，因为这里的颜色集合比较小）。

### 示例 2：绘图和移动

现在，假设你不想改变画笔颜色，而是想在不绘制线段的情况下将海龟移动到新位置。你可以通过将右键绑定到本章前面讨论的 skip 函数来实现这一点。以下是如何在 shell 会话中执行此操作的方法：

```
>>> from turtle import *
>>> def skip(x, y): up(); goto(x, y); down()
>>> shape("circle")
>>> onscreenclick(goto)
>>> onscreenclick(skip, btn =2)
>>> listen()
```

注意 skip 函数定义中使用了分号。它们允许你在一行代码上编写单独的 Python 语句，以便更简洁地呈现。

### 示例 3：绘图、移动和随机颜色

假设你希望右键单击既将海龟移动到新位置又改变其颜色。要做到这一点，你需要将两个事件处理函数都注册到右键单击，注意在注册第二个函数时提供可选的 add 参数 True。以下是此版本的代码：

```
>>> from turtle import *
>>> from random import choice
>>> colors = ("red", "blue", "green", "purple", "orange")
>>> def skip(x, y): up(); goto(x, y); down()
>>> shape("circle")
>>> onscreenclick(goto)
>>> onscreenclick(lambda x, y: pencolor(choice(colors)), btn =2)
>>> onscreenclick(skip, btn =2, add =True)
>>> listen()
```

与右键关联的两个事件处理函数按 onscreenclick 注册的顺序触发。

### 示例 4：形状属性的对话框

也许你想在 turtle 图形窗口的不同位置交互式地绘制一些多边形。每个多边形都有长度、边数和颜色。给定这些属性，你可以用鼠标左键单击将多边形放置在窗口的任何位置。右键单击应允许你更改下一个要绘制的多边形的任何属性。一系列弹出对话框允许你输入这些信息（长度、
边数和颜色）。作为初步尝试，这里有一个程序允许你使用默认属性绘制多边形：

```python
"""
drawpolygon1.py
Draw polygons with a left-click.
"""

from turtle import *
properties = {"length":30, "numSides":4, "color":"black"}

def regularPolygon(length, numSides):
    """Draws a regular polygon.
    Arguments: the length and number of sides."""
    interiorAngle = 360 / numSides
    for count in range(numSides):
        forward(length)
        left(interiorAngle)

def skip(x, y):
    "Moves the pen to the given location without drawing."
    up()
    goto(x, y)
    down()

def moveAndDraw(x, y):
    """Draws a polygon with the current properties at
    position (x, y)."""
    skip(x,y)
    pencolor(properties["color"])
    regularPolygon(properties["length"], properties["numSides"])

def main():
    width(2)
    speed(0)
    hideturtle()
    onscreenclick(moveAndDraw)
    listen()
    return "Done!"

if __name__ == "__main__":
    msg = main()
    print(msg)
    mainloop()
```
