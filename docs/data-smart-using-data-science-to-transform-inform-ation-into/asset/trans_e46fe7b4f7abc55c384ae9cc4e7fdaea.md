

![](img/9c4b3d77873bec9e7da149a75c568d36_392_0.png)

图 11.2：你的新变量出现在 Environment 窗格中。

你或许可以想象，当你刚开始时，需要在控制台中编写的文本量以及要跟踪的变量数量可能会让人感到压力山大。有时候，你只需要清除一切并重新开始。现在就让我们这样做。

按键盘上的 Ctrl+L 清除控制台。接下来，按一下 Environment 窗格中的扫帚图标按钮，清除环境中的所有变量。这是 Environment 选项卡上方菜单中的最后一个图标（图 11.2）。你也可以在控制台中使用 `rm()` 函数来删除变量。例如，`rm(var1)` 会从环境中删除 `var1`。

## 让我们看数字！向量数学与因子化

R 在处理数字时 truly 表现出色。你可以使用 `c()` 函数插入一个数字向量（`c` 代表 "combine"，即“组合”）。让我们把一些质数丢进一个变量里。

```
> someprimes <- c(1,2,3,5,7,11)
> someprimes
[1] 1 2 3 5 7 11
```

使用 `length()` 函数，你可以统计向量中的元素个数。

```
> length(someprimes)
[1] 6
```

你也可以使用括号索引来引用向量中的单个值。

```
> someprimes[4]
[1] 5
```

括号索引从 1 开始，而不是 0。这意味着 `[4]` 返回向量中的第四个值，碰巧是 5。你可以使用 `c()` 函数或 `:` 字符来提供索引向量，以指定一个范围。

```
> someprimes[c(4,5,6)]
[1] 5 7 11
> someprimes[4:6]
[1] 5 7 11
```

在这两种情况下，你都在提取向量中从第四个到第六个值。你也可以使用逻辑语句来提取值。例如，如果你只想要小于七的质数，可以使用 `which()` 函数来返回它们的索引。

```
> which(someprimes<7)
[1] 1 2 3 4
```

```
> someprimes[which(someprimes<7)]
[1] 1 2 3 5
```

一旦将数据放入变量，你就可以对整个数据集执行操作，并将结果存储在新变量中。例如，你可以将所有数据乘以 2。

```
> primestimes2 <- someprimes * 2
> primestimes2
[1]  2  4  6 10 14 22
```

R 允许你为那一列或一行数据命名，并将该变量作为单个实体进行操作。这与使用 Excel 表格非常相似。

检查数据中条目是否异常的一个有用函数是 `summary` 函数。

```
> summary(someprimes)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max.
1.000   2.250   4.000   4.833   6.500  11.000
```

你也可以处理文本数据。

```
> somecolors <- c('blue','red','green','blue','green','yellow','red','red')
> somecolors
[1] "blue"  "red"   "green" "blue"  "green" "yellow" "red"   "red"
```

如果对 somecolors 汇总，你得到的只是少量描述性数据。

```
> summary(somecolors)
 Length Class   Mode
     8 character character
```

但你可以将这些颜色视为类别，通过“factoring”将此向量转换为类别数据。

```
> somecolors <- factor(somecolors)
> somecolors
[1] blue red green blue green yellow red red
Levels: blue green red yellow
```

现在当你汇总数据时，你会得到每个“level”（级别本质上是一个类别）的计数。

```
> summary(somecolors)
blue green red yellow
2 2 3 1
```

迄今为止你一直在操作的向量是一维的。在 R 中，更类似于电子表格的东西可能是矩阵，即一个二维数字数组。你可以使用 matrix 函数构建一个。

```
> amatrix <- matrix(data=c(someprimes,primestimes2),nrow=2,ncol=6)
> amatrix
[,1] [,2] [,3] [,4] [,5] [,6]
[1,] 1 3 7 2 6 14
[2,] 2 5 11 4 10 22
```

你可以统计列和行。

```
> nrow(amatrix)
[1] 2
> ncol(amatrix)
[1] 6
```

如果你想转置数据，请使用 t() 函数。

```
> t(amatrix)
[,1] [,2]
[1,] 1 2
[2,] 3 5
[3,] 7 11
[4,] 2 4
[5,] 6 10
[6,] 14 22
```

要提取单个记录或范围，你使用相同的括号索引法，只是用逗号分隔列和行引用。

```
> amatrix[1:2,3]
[1] 7 11
```

这会返回第 3 列中第 1 到第 2 行的值。但你无需引用第 1 和第 2 行，因为那正是你拥有的全部行——你可以相反地留空括号的那部分，所有行都会被打印。

```
> amat[ ,3]
[1] 7 11
```

使用 rbind() 和 cbind() 函数，你可以将新行和列的数据“压入”矩阵中。

```
> primestimes3 <- someprimes*3
> amat <- rbind(amat,primestimes3)
> amat
 [,1] [,2] [,3] [,4] [,5] [,6]
 1   3   7   2   6   14
 2   5  11   4  10  22
primestimes3
 3   6   9  15  21  33
```

在这里，你创建了一行新数据（primestimes3），并在 amat 变量上使用了 rbind() 将 primestimes3 附加到其上，并将结果重新赋值给 amat。

有趣的是，这并不是处理数据集的唯一方式。在数据清理方面，我更喜欢一个名为 dplyr 的库，它允许你以类似于 Power Query 的方式处理数据集。我们将在本章后面了解其工作原理。

## 所有数据类型中最好的：数据框

数据框是处理 R 中现实世界、数据库表格样式数据的理想方式。本质上，它是一个面向列的二维数据表，其中列可以被视为数值或类别向量。你可以通过在导入或填入的数据数组上调用 data.frame() 函数来创建数据框。从许多方面来说，数据框类似于 Excel 表格。

下面的示例使用詹姆斯·邦德电影的数据来演示。首先，创建一些向量。

```
> bondnames <- c('connery', 'lazenby', 'moore', 'dalton', 'brosnan', 'craig')
> firstyear <- c(1962,1969,1973,1987,1995,2006)
> eyecolor <- c('brown', 'brown', 'blue', 'green', 'blue', 'blue')
```

到此时，你有三个向量——一些是文本，一些是数值——且长度都相同。你可以像这样将它们合并到一个名为 bonddata 的数据框中：

```
> bonddata <- data.frame(bondnames, firstyear, eyecolor)
> bonddata
 bondnames firstyear eyecolor
1 connery 1962 brown
2 lazebny 1969 brown
3   moore   1973   blue
4   dalton  1987   green
5   brosnan 1995   blue
6   craig   2006   blue
```

`data.frame` 函数将负责识别这些列中哪些是因子，哪些是数值。你可以通过调用 `str()` 和 `summary()` 函数来查看这种差异（`str` 代表 "structure"）。

```
> str(bonddata)
'data.frame':   6 obs. of  3 variables:
$ bondnames: chr  "connery" "lazenby" "moore" "dalton" ...
$ firstyear: num  1962 1969 1973 1987 1995 ...
$ eyecolor : chr  "brown" "brown" "blue" "green" ...
> summary(bonddata)
bondnames      firstyear        eyecolor
Length:6       Min.   :1962   Length:6
Class :character   1st Qu.:1970   Class :character
Mode :character   Median :1980   Mode :character
          Mean   :1982
          3rd Qu.:1993
          Max.   :2006
```

请注意，年份被视为数字。如果你希望将其视为类别，可以使用 `factor()` 函数对该列进行因子化。

关于数据框的一个很棒的特性是，你可以使用 `$` 字符加上列名来引用每一列，如下所示：

```
> bonddata$firstyear <- factor(bonddata$firstyear)
> summary(bonddata)
bondnames      firstyear        eyecolor
Length:6       1962:1         Length:6
Class :character 1969:1         Class :character
Mode :character 1973:1         Mode :character
          1987:1
          1995:1
          2006:1
```

当你运行 `summary` 函数时，年份将按类别计数汇总，而不是按分布数据汇总。

## 如何在 R 中寻求帮助

要了解函数的作用，只需在将其放入控制台之前输入一个问号。

```
> ?sqrt
```

这将在 IDE 右下角弹出该函数的帮助窗口（参见图 11.3）。

![](img/9c4b3d77873bec9e7da149a75c568d36_397_0.png)

**图 11.3：平方根函数的帮助窗口**

你也可以在函数前输入两个问号来搜索信息，如下所示：

```
> ??log
```

`log` 搜索将产生图 11.4 所示的结果。

## 更上一层楼……超越基础 R

在继续之前，需要注意的是，迄今为止我向你展示的许多内容构成了所谓的 _基础 R_。基础 R 是在 R 中工作的原生方式。例如，我们处理矩阵的方式就在基础 R 中。就像学习任何事物的基础一样，了解基础 R 很重要。R 已经存在了一段时间，在网上搜索如何做某事时，你经常会发现用基础 R 编写的旧代码（甚至一些较新的代码），你需要理解这些代码才能将其背后的定量工作转译为更新的东西。此外，还有一些旧包和库更希望你使用基础 R 而非较新的惯例——因此你需要了解足够的知识来应对。

