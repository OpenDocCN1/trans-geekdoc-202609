
彼此之间，没有更多项目需要检查，且目标项目不存在。因此，只要

```
left <= right
```

搜索必须继续。

你对 myIn 函数的新版本保留了其头部，并定义了一个名为 binaryIn 的递归辅助函数。该函数将列表的左端点和右端点作为参数。它们的初始值分别为 0 和列表长度减一。以下是 myIn 新版本的完整代码：

```
def myIn(targetItem, lyst):
    def binaryIn(left, right):
        if left <= right:
            midPoint = (left + right) // 2
            if lyst[midPoint] == targetItem:
                return True
            elif targetItem < lyst[midPoint]:
                return binaryIn(left, midPoint - 1)
            else:
                return binaryIn(midPoint + 1, right)
        else:
            return False
    return binaryIn(0, len(lyst) - 1)
```

回想一下，顺序搜索函数在最坏情况下必须检查列表中的每个项目，当目标项目不存在时即为这种情况。因此，在这种情况下，如果有 16 个项目，顺序搜索函数必须进行 16 次递归调用。相比之下，二分搜索函数快多少？二分搜索在每次递归调用之前会丢弃剩余列表项目的一半。那么在发现目标项目不在列表中之前必须进行多少次递归调用？该数字等于在列表段长度达到 0 之前可以将列表长度除以 2 的次数。例如，对于长度为 16 的列表，递归调用检查的列表段长度为 8、4、2、1 和 0。那就是最多 5 次调用，而顺序搜索最多需要 16 次调用。用数学术语来说，二分搜索具有对数运行时间（5 等于 1 + 16 的 log₂，其中 log₂ 的一个数的对数是使用 2 得到该数的指数）。这意味着运行时间仅随列表大小对数增长。也就是说，当列表大小加倍时，二分搜索执行的工作量不会加倍，而只会增加 1 次递归调用！

## 艺术中的递归模式：抽象绘画

二十世纪的荷兰艺术家皮特·蒙德里安发展出一种展现简单递归模式的抽象绘画风格。要用计算机生成此类图案，你首先绘制一个随机颜色的矩形，然后反复绘制两个不等分的子区域并使用随机颜色。图 7.3 中展示了几个示例绘图（实际颜色未显示）。

![](img/4dc3f6307b32ff815a6d58ec1c84708c_175_0.png)

![](img/4dc3f6307b32ff815a6d58ec1c84708c_175_1.png)

![](img/4dc3f6307b32ff815a6d58ec1c84708c_175_2.png)

![](img/4dc3f6307b32ff815a6d58ec1c84708c_175_3.png)

Figure 7.3
以皮特·蒙德里安风格生成简单的递归图案。
© 2014 Python Software Foundation.

正如你所见，程序会继续细分过程，直到达到“美学上恰当的时刻”。在此版本中，程序将当前矩形划分为代表其面积三分之一和三分之二的部分，并在水平和垂直轴上随机交替这些细分。程序的用户指定绘图的细节级别。在图 7.3 中，你从左到右看到的是 level-1 绘图、level-3 绘图、level-4 绘图和 level-8 绘图。

在本节中，你将开发创建类似图 7.3 中绘图的程序的各个部分。练习为你提供了添加装饰的机会。

## 程序设计

你的艺术绘图程序出现在单个模块文件 `mondrian.py` 中。像往常一样，程序包含一个 `main` 函数和几个支持函数。因为你使用随机颜色绘图，所以可以使用第 5 章中讨论的 `randomColor` 函数。此外，因为你可能要绘制许多矩形，你将定义一个 `drawRectangle` 函数。最后，你将定义一个用于绘制完整艺术作品的函数。其名称恰如其分地为 `mondrian`。图 7.4 显示了程序员定义的函数的调用图。

![](img/4dc3f6307b32ff815a6d58ec1c84708c_176_0.png)

Figure 7.4

mondrian 程序的调用图。

正如你所见，`main` 函数对 `mondrian` 函数进行一次调用。然后该函数调用 `drawRectangle` 函数并递归调用自身两次。你稍后将学习如何停止这些递归调用。

## 性能跟踪

仅供娱乐，你可以维护程序性能的一些统计数据。这些数据包括绘制的矩形数量和 `mondrian` 函数的调用次数。你将这些值保存在名为 `stats` 的字典中，该字典作为模块变量设置。此变量在模块开头附近初始化，其数据在 main 函数开始时重置为 0。以下是初始化 stats 的代码：

```
# Data to track performance
stats = {"calls":0, "rectangles":0}
```

每次调用 mondrian 时，你增加调用次数，每次调用 drawRectangle 时，你增加矩形数量。你将很快使用这些统计数据来分析程序的行为。

## drawRectangle 函数

与你在第 5 章中为绘制几何形状而开发的函数不同，drawRectangle 函数期望两个角点的坐标——左上角和右下角——作为参数。在这种情况下，你可以通过调用 goto 函数来绘制矩形的线段。在绘制这些线段之前，你必须获取随机颜色，将画笔设置为该颜色，抬起画笔移动到角点，然后放下画笔。剩余的步骤使用 goto 绘制四条线段，需要你计算出另外两个角点的正确坐标。以下是 drawRectangle 函数的代码：

```
def drawRectangle(x1, y1, x2, y2):
    """Draws a rectangle with the given corner points
    using a random color."""
    stats["rectangles"] = stats["rectangles"] + 1
    (red, green, blue) = randomColor()
    pencolor(red, green, blue)
    up()
    goto(x1, y1)
    down()
    goto(x2, y1)
    goto(x2, y2)
    goto(x1, y2)
    goto(x1, y1)
```

## mondrian 函数

mondrian 函数期望一个矩形的两个角点坐标和一个级别号作为参数。该函数为该级别绘制完整的艺术作品。现在，这最后一句话到底是什么意思？

假设函数在其顶层调用时接收到级别 3。level-3 绘图由两个矩形组成，每个矩形都是一个 level-2 绘图。每个 level-2 绘图又由两个矩形组成，每个矩形都是一个 level-1 绘图。level-1 绘图是一个不包含更小矩形的简单矩形。

这里的主要点是，只要它们的级别大于或等于 1，你就使用同一个 mondrian 函数来创建所有这些绘图。每个绘图都是在 mondrian 的顶层调用或递归调用上绘制的。

递归何时停止？当级别变为 0 时。在这种情况下，函数 simply 返回且不执行任何操作。以下是此递归过程的伪代码设计：

```
Function mondrian(x1, y1, x2, y2, level)
    If level > 0
        Call drawRectangle(x1, y1, x2, y2)
        Compute the corner points of two smaller rectangles
        Call mondrian with one set of corner points and level - 1
        Call mondrian with the other set of corner points and level - 1
```

正如你所见，因为每次递归调用级别都会减少 1，所以它最终会达到 0，递归就会停止。

mondrian 函数最复杂的部分是计算两个新矩形的角点。这里有很多选择。最简单的策略是根据穿过当前矩形中部的垂直线来定位两个矩形的角点。然而，如果每次都这样做，你会在绘图中看到一连串乏味的等间距垂直线。

更好的替代方案是以相等概率垂直或水平细分当前矩形。此外，你可以将当前矩形分割成不等面积的部分，也许使用当前矩形大小的 1/3 和 2/3 的比例。

以下用于 mondrian 函数的 Python 代码使用了此策略。你将在练习中有机会对其进行改进。

```
def mondrian(x1, y1, x2, y2, level):
    """Draws a Mondrian-like painting at the given level."""
    stats["calls"] = stats["calls"] + 1
    if level > 0:
        drawRectangle(x1, y1, x2, y2)
        vertical = randint(1, 2)
        if vertical == 1: # Vertical split
            mondrian(x1, y1, (x2 - x1) / 3 + x1, y2,
                     level - 1)
```
