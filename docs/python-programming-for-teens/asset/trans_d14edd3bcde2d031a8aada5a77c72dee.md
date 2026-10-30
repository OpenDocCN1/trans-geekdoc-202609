
这里有一个简短的测试程序，它显示了 10 个六边形的径向图案，类似于第 3 章中所示的图案。该程序创建了 10 个 RegularPolygon 对象来实现此目的。

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

## 实现：类定义的构造

每个 Python 类都在一个模块文件中定义。到目前为止，你的 Python 文件包含一个 main 函数和其他辅助函数。现在你即将定义一个新的 Python 类，名为 RegularPolygon。按照惯例，这个类放在名为 regularPolygon.py 的模块文件中。要创建此文件，你通过从文件菜单中选择 New File 来打开一个新的集成开发环境（IDLE）文件窗口。

如同往常一样，你以包含文件名和模块用途的文档字符串开始模块的文本。然后你列出此模块的任何导入。以下是 regularpolygon 模块的示例：

```
"""
File: regularpolygon.py
Defines a RegularPolygon class.
"""
```

```
from turtle import Turtle, bgcolor
```

请注意，你不要使用语句 from turtle import * 从 turtle 模块导入所有资源。相反，你只导入正在构建的模块所需的类和函数。这种做法有助于防止因调用你实际上不需要的函数而可能产生的错误。

类定义如下。其形式为

```
class ClassName(ParentClassName):
    methodDefinitions
```

这种形式类似于函数定义，其中有一个头部，后跟缩进的代码体。但在这种情况下，缩进的代码体是一系列方法定义。

程序员定义的类名通常大写，因此你可以从变量和方法名中识别出来。对于此类，括号中的 ParentClassName 应为 object。以下是 RegularPolygon 类头部及其文档字符串的代码：

```
class RegularPolygon(object):
    """Represents a regular polygon."""
```

方法定义一个接一个地列出，就像你之前对函数定义所做的那样。但请注意，它们必须相对于类头部（以 class 开始的行）向右缩进一个制表符或四个空格。

方法定义的格式类似于函数定义：

```
def methodName(self, otherArguments):
    statements
```

然而有一个关键区别。方法定义中的第一个参数必须始终是 self。这个词指的是调用该方法的特定对象。然后你使用 self 在方法体内部定位该对象。请注意，self 仅作为方法定义中的参数出现；在调用方法时，它会被省略在参数列表中。

## 实现：__init__ 方法

在类中定义的第一个方法是名为 __init__ 的特殊方法。请注意该名称开头和结尾的下划线。此方法负责在程序员创建该对象时初始化对象的数据。因此，当程序员进行调用时

```
RegularPolygon(length = 50, xPos = 80, yPos = 80, sides = 6,
    outlineColor = "red", fillOn = True)
```

Python 会自动运行在 RegularPolygon 类中定义的 __init__ 方法。此方法将提供的任何参数或其默认值分配给对象内的适当数据变量，并自动向调用者返回一个新的、已初始化的正多边形对象。

存放对象属性值的变量也称为实例变量。为了将其与参数名和临时变量区分开，实例变量名始终以 self 为前缀，并按惯例使用前导下划线。否则，__init__ 方法的代码与你见过的任何函数定义的代码非常相似，尽管在此方法中你不提供 return 语句。以下是代码：

```
def __init__(self, length, xPos, yPos, heading, sides = 3,
    outlineColor = "black", fillColor = "black",
    fillOn = False, isVisible = True):
    """Sets the initial state of the polygon."""
    self._turtle = Turtle(visible = False)  # Always hide the turtle
    self._turtle.speed(0)
    self._length = length
    self._xPos = xPos
    self._yPos = yPos
    self._heading = heading
    self._sides = sides
    self._outlineColor = outlineColor
    self._fillColor = fillColor
    self._fillOn = fillOn
    self._isVisible = isVisible
    if isVisible:          # Display the polygon if it's
        self.show()        # visible
```

如你所见，当你运行 RegularPolygon 函数时，你会得到一个包含其自身数据值的独立多边形对象；这就是 __init__ 方法对每个对象所做的工作。

## 实现：显示与隐藏

下一个最重要的方法是 `show` 和 `hide` 方法。这些方法在海龟图形窗口中显示多边形或隐藏它。显示多边形很直接：你使用之前开发的 `regularPolygon` 函数中的代码，并根据其 `fillOn` 属性是否为 True 对填充多边形进行调整。隐藏多边形意味着从海龟图形窗口中擦除它。你可以通过在窗口的背景色中绘制多边形来实现这一点。每一个方法也会将 `isVisible` 属性调整为适当的值。

因为 `show` 和 `hide` 方法都绘制多边形，所以开发一个仅用于绘制的辅助方法很有用。你将此方法命名为 `_draw`；前导下划线表示它是一个帮助方法，不会被该类的其他用户调用。以下是此方法的代码：

```
def _draw(self):
    """Draws a regular polygon with the given turtle,
    length and number of sides."""
    interiorAngle = 360 / self._sides
    self._turtle.up()
    self._turtle.setheading(self._heading)
    self._turtle.color(self.outlineColor(), self.fillColor())
    self._turtle.goto(self._xPos, self._yPos)
    self._turtle.down()
    if self.fillOn():
        self._turtle.begin_fill()
    for count in range(self._sides):
        self._turtle.forward(self._length)
        self._turtle.left(interiorAngle)
    if self.fillOn():
        self._turtle.end_fill()
```

请注意，在开始绘制之前，你必须设置海龟的朝向和颜色并将其移动到其位置。然后 `_draw` 方法检查多边形的 `fillOn` 属性，如果为 True，则在海龟对象上调用 `begin_fill`。在绘制循环结束后，该方法会再次检查 `fillOn` 以在必要时结束填充。

相比之下，`show` 方法非常简单。以下是代码：

```
def show(self):
    """Displays the polygon."""
    self._draw()
    self._isVisible = True
```

hide 方法必须设置好条件，使 _draw 方法使用与当前背景颜色（海龟图形画布的颜色）相同的轮廓颜色和填充颜色。这会擦除多边形。为此，hide 方法首先将多边形的轮廓和填充颜色保存在临时变量中，以便在绘制多边形后恢复（多边形的实际颜色不会改变，只是被隐藏）。然后该方法将两个颜色属性都设置为当前背景颜色，并在调用 _draw 之前增大海龟的画笔大小。最后，在恢复多边形的颜色和海龟的画笔大小后，其 isVisible 属性被设置为 False。以下是代码：

```
def hide(self):
    """Erases the polygon."""
    oldOutline = self.outlineColor()      # Save the current colors
    oldFill = self.fillColor()
    erasingColor = bgcolor()
    self._outlineColor = erasingColor   # Prepare to erase
    self._fillColor = erasingColor
    self._turtle.pensize(3)             # Make sure outline goes away
    self._draw()
    self._outlineColor = oldOutline     # Restore the current colors
    self._fillColor = oldFill
    self._turtle.pensize(1)
    self._isVisible = False
```

## 实现：获取与设置

三个多边形方法允许你根据是否存在参数来检查或修改属性。例如，考虑 outlineColor 方法。如果在调用时未提供此方法参数，其默认值是 None。在这种情况下，你只需返回当前的轮廓颜色。但如果它不是 None，则参数存在，并且方法应将轮廓颜色重置为新值，并在可见时重绘多边形。以下是此方法的代码：

```
def outlineColor(self, value = None):
    """Getter and setter for the outline color."""
    if value:
        self._outlineColor = value
        if self.isVisible():
            self.show()
    return self._outlineColor
```

另外两个方法具有类似的结构，留给你作为练习。
