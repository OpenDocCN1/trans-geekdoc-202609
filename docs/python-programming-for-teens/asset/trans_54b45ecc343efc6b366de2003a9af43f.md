
```
mondrian((x2 - x1) / 3 + x1, y1, x2, y2,
    level - 1)
else:                # Horizontal split
    mondrian(x1, y1, x2, y1 - (y1 - y2) / 3,
        level - 1)
    mondrian(x1, y1 - (y1 - y2) / 3, x2, y2,
        level - 1)
```

## 主函数

你以主函数的代码结束。此函数执行以下步骤：

- 1. 提示用户输入绘图的级别。级别 1 将是默认值，也是允许的最小值。
- 2. 初始化海龟。海龟将被隐藏，其画笔大小为 2，速度为 0。
- 3. 计算初始矩形左上角和右下角的坐标。为了在当前海龟图形窗口的边界内显示最外层，提供 20 像素的边距。
- 4. 使用矩形的坐标和级别作为参数调用 mondrian 函数。

以下是主函数的代码：

```
def main():
    # Reset the stats on each call of main.
    stats["calls"] = 0
    stats["rectangles"] = 0
    # Obtain the level from the user.
    level = numinput("Input Dialog", "Enter the level",
                    default = 1, minval = 1)
    if not level:
        level = 1
    paintingWidth = window_width() // 2 - 20  # Offset within edge of
    paintingHeight = window_height() // 2 - 20 # window.
    hideturtle()
    speed(0)
    pensize(2)
```

```
# Delay drawing if level is greater than 6.
if level > 6:
    tracer(False)
mondrian(-paintingWidth, paintingHeight,
    paintingWidth, -paintingHeight, level)
# Draw now if level is greater than 6.
if level > 6:
    update()
```

## tracer 和 update 函数

请注意，如果级别大于 6，你会在调用 mondrian 函数之前调用 tracer 函数。当使用 False 作为参数调用时，tracer 函数会延迟任何绘图，直到调用 update 函数为止。update 函数在 mondrian 函数完成后在对应的 if 语句中被调用。在此期间，海龟仍会执行 mondrian 函数中绘图的所有计算，但直到调用 update 之前不会有任何输出。如果你在大级别时不这样做，绘制图形中的所有矩形将花费很长时间。

通常，输入和输出操作比其他计算慢得多，而后者在 CPU 内部以光速进行。但尽管采取了加快输出的措施，随着级别大小变得相当大，即使是内部计算也无法防止明显的延迟。

mondrian 函数中的这种增长速率有多大？表 7.1 显示了级别 1 到 5 时 mondrian 函数的调用次数和绘制的矩形数量。

表 7.1 mondrian 函数的性能统计

| 级别 | 矩形数量 | 调用次数 |
|---|---|---|
| 1 | 1 | 3 |
| 2 | 3 | 7 |
| 3 | 7 | 15 |
| 4 | 15 | 31 |
| 5 | 31 | 63 |
| N | 2^N-1 | 2^(N+1)-1 |

正如你所见，mondrian 函数的工作量（最终的运行时间）增长速度比级别大小的平方更快。在每种情况下，绘制的矩形数恰好为 2^N−1，其中 N 为级别。对于非常大的级别（例如大于 20），程序最终会完成任务，但不会在合理的时间内完成。（在 shell 中运行表达式 2 ** 20-1 以查看级别 20 图形将绘制多少个矩形。）

请注意，这种指数增长速率是本章前面看到的二分搜索函数的对数增长速率的逆。遗憾的是，没有办法改善 mondrian 函数的指数行为。精美的艺术可能很昂贵！

## 自然界中的递归模式：分形

分形是高度重复或递归的模式。分形物体看起来几何化，但无法用普通的欧几里得几何来描述。奇怪的是，分形曲线不是一维的，分形曲面也不是二维的。相反，每个分形形状都有其自己的分形维度。要理解这意味着什么，你首先要考虑普通曲线的性质，即任意两点之间有精确的有限长度。相比之下，分形曲线在任意两点之间具有不确定的长度。分形曲线的表观长度取决于观察的细节程度。当你放大分形曲线的一个片段时，可以看到越来越多的细节，其长度看起来也越来越大。例如，考虑海岸线。从远处看，它有很多起伏，但长度可辨。现在把海岸线的一段放在放大镜下。它有很多相似的起伏，可辨的长度会增加。放大时的自相似性是分形的定义特征；它出现在山脉的形状、树枝的分支模式以及许多其他自然物体中。

分形曲线的一个例子是 c 曲线。图 7.5 显示了 c 曲线的最初六个级别和一个级别 10 的 c 曲线。

![](img/4dc3f6307b32ff815a6d58ec1c84708c_182_0.png)

## 图 7.5

级别 0 到 6 的 c 曲线以及一个级别 10 的 c 曲线。

© 2014 Python Software Foundation.

级别 0 的 c 曲线是一个简单的线段。级别 1 的 c 曲线用两个较小的级别 0 c 曲线替换级别 0 的 c 曲线，它们在直角处相遇。级别 2 的 c 曲线对级别 1 c 曲线中的两个线段中的每一个都做同样的事情。这种细分模式可以无限地继续，产生相当复杂的形状。在本节的其余部分，你将开发一个使用海龟图形显示 c 曲线的函数。

## 程序的功能

程序提示用户输入 c 曲线的级别。在输入此整数后，程序会显示一个海龟图形窗口，在其中绘制 c 曲线。

## 程序设计

你可以用递归函数绘制 N 级 c 曲线。该函数接收线段的端点和当前级别作为参数。在级别 0 时，函数绘制一条简单的线段。否则，级别 N 的 c 曲线由两个级别 N-1 的 c 曲线组成，构造如下：

```
Let xm be (x1 + x2 + y1 - y2) // 2
Let ym be (x2 + y1 + y2 - x1) // 2
```

第一个级别 N-1 的 c 曲线使用线段 (x1, y1)、(xm, ym) 和级别 N-1，因此函数会递归调用这些参数。

第二个级别 N-1 的 c 曲线使用线段 (xm, ym)、(x2, y2) 和级别 N-1，因此函数会递归调用这些参数。

例如，在级别 0 的 c 曲线中，设 (x1, y1) 为 (50, -50)，(x2, y2) 为 (50, 50)。然后，为了获得级别 1 的 c 曲线，使用计算 xm 和 ym 的公式得到 (xm, ym)，即为 (0, 0)。图 7.6 显示了级别 0 c 曲线的实线段，以及由这些操作产生的级别 1 c 曲线的两条虚线段。实际上，这些操作产生了在直角处相遇的两条较短的线段。

![](img/4dc3f6307b32ff815a6d58ec1c84708c_183_0.png)

## 图 7.6
级别 0 的 c 曲线（实线）和级别 1 的 c 曲线（虚线）。

以下是该函数的递归设计的伪代码：

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

函数 drawLine 使用海龟在两个给定端点之间绘制一条线。

## 程序代码

该程序包括 cCurve、drawLine 和 main 函数的定义。请注意，与 mondrian 程序不同，ccurve 程序在基本情况下绘制线段。

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
