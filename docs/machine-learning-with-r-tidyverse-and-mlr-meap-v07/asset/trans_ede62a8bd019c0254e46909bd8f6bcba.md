
## 练习 2.3

筛选你的 `mtcars` tibble，只保留气缸数（`cyl`）**不等于 8** 的观测。

接下来，我们希望按单个植物*分组*并*汇总*数据，以得到每组的吸收量平均值和标准差。我们可以分别使用 `group_by()` 和 `summarize()` 函数实现这一点。

在 `group_by()` 函数中，第一个参数是——你猜对了——数据（看到规律了吗？），后面跟着分组变量。我们可以用逗号分隔多个分组变量。当我们打印 `groupedData` 时，除了数据上方会显示这些数据已按哪个变量分组、以及共有多少组之外，变化并不大。这告诉我们，之后应用的任何操作都将按组进行。

## 代码清单 2.10 使用 `group_by()` 函数对数据分组

```r
groupedData <- group_by(filteredData, Plant)

groupedData

# A tibble: 66 x 4
# Groups:   Plant [11]
   Plant Type Treatment  uptake
   <ord> <fct> <fct>     <dbl>
 1 Qn1   Quebec nonchilled  30.4
 2 Qn1   Quebec nonchilled  34.8
 3 Qn1   Quebec nonchilled  37.2
 4 Qn1   Quebec nonchilled  35.3
 5 Qn1   Quebec nonchilled  39.2
 6 Qn1   Quebec nonchilled  39.7
 7 Qn2   Quebec nonchilled  27.3
 8 Qn2   Quebec nonchilled  37.1
 9 Qn2   Quebec nonchilled  41.8
10 Qn2   Quebec nonchilled  40.6
# ... with 56 more rows
```

你可以通过将 tibble 包装在 `ungroup()` 函数中来移除分组结构。

在 `summarize()` 函数中，第一个参数是数据，第二个参数中我们为新创建的变量命名，后跟一个等号，再跟该变量的定义。我们可以用逗号分隔创建任意多个新变量，因此在代码清单 2.11 中，我创建了两个汇总变量：每组的 `uptake` 平均值（`meanUp`）和每组的 `uptake` 标准差（`sdUp`）。现在当我们打印 `summarizedData` 时，可以看到除了分组变量外，原始变量已被我们刚创建的汇总变量取代。

## 代码清单 2.11 使用 `summarize()` 函数创建变量汇总

```r
summarizedData <- summarize(groupedData, meanUp = mean(uptake),
                             sdUp = sd(uptake))

summarizedData

# A tibble: 11 x 3
   Plant meanUp   sdUp
   <ord> <dbl>   <dbl>
 1 Qn1    36.1   3.42
 2 Qn2    38.8   6.07
 3 Qn3    37.6  10.3
 4 Qc1    32.6   5.03
 5 Qc3    35.5   7.52
 6 Qc2    36.6   5.14
 7 Mn3    26.2   3.49
 8 Mn2    29.9   3.92
 9 Mn1    29.0   5.70
10 Mc3    18.4   0.826
11 Mc1    20.1   1.83
```

最后，我们将根据现有变量*变换（mutate）*出一个新变量，以计算各组的变异系数，然后按刚创建的新变量对数据*排序（arrange）*。我们可以使用 `mutate()` 和 `arrange()` 函数完成这一步。

## 代码清单 2.12 使用 `mutate()` 函数创建新变量

```r
mutatedData <- mutate(summarizedData, CV = (sdUp / meanUp) * 100)

mutatedData

# A tibble: 11 x 4
   Plant meanUp   sdUp    CV
   <ord> <dbl>   <dbl>  <dbl>
 1 Qn1    36.1   3.42    9.48
 2 Qn2    38.8   6.07   15.7
 3 Qn3    37.6  10.3    27.5
 4 Qc1    32.6   5.03   15.4
 5 Qc3    35.5   7.52   21.2
 6 Qc2    36.6   5.14   14.1
 7 Mn3    26.2   3.49   13.3
 8 Mn2    29.9   3.92   13.1
 9 Mn1    29.0   5.70   19.6
10 Mc3    18.4   0.826   4.48
11 Mc1    20.1   1.83    9.11
```

dplyr 函数中的参数求值是按顺序进行的，这意味着我们本可以在 `summarize()` 函数中通过引用 `meanUp` 和 `sdUp` 变量来定义 `CV` 变量，即使这些变量当时尚未被创建！

还记得我特别强调过，每个 dplyr 函数的第一个参数都是数据吗？之所以这一点如此重要且有用，是因为它允许我们通过管道将上一个操作的数据传送到下一个操作中，因此我们在 2.4.1 节中完成的整个数据操作过程就变成了：

## 代码清单 2.14 使用 `%>%` 运算符将 dplyr 操作串联起来

```r
arrangedData <- CO2tib %>%
  select(c(1:3, 5)) %>%
  filter(uptake > 16) %>%
  group_by(Plant) %>%
  summarize(meanUp = mean(uptake), sdUp = sd(uptake)) %>%
  mutate(CV = (sdUp / meanUp) * 100) %>%
  arrange(CV)

arrangedData

# A tibble: 11 x 4
   Plant meanUp  sdUp    CV
   <ord> <dbl>  <dbl> <dbl>
 1 Mc3    18.4  0.826  4.48
 2 Mc1    20.1  1.83   9.11
 3 Qn1    36.1  3.42   9.48
 4 Mn2    29.9  3.92  13.1
 5 Mn3    26.2  3.49  13.3
 6 Qc2    36.6  5.14  14.1
 7 Qc1    32.6  5.03  15.4
 8 Qn2    38.8  6.07  15.7
 9 Mn1    29.0  5.70  19.6
10 Qc3    35.5  7.52  21.2
11 Qn3    37.6 10.3   27.5
```

从上到下通读这段代码，每遇到一个 `%>%` 运算符，就念一次“然后”。你可以这样读它：“获取 CO2 数据，然后选择这几列，然后过滤这些行，然后按这个变量分组，然后用这些变量生成汇总，然后变换出这个新变量，然后按该变量排序，并将结果保存为 `arrangedData`。”你能看出，这正是一种可以用通俗易懂的语言向同事解释数据处理流程的方式吗？这就是 dplyr 的强大之处：能够以符合逻辑、易于人类阅读的方式执行复杂的数据操作。

`%>%` 运算符之后另起一行是惯例，这有助于让代码更易读。

## 练习 2.4

将 `mtcars` tibble 按 `gear` 变量分组，汇总 `mpg` 和 `disp` 变量的中位数，并变换出一个新变量，即 `mpg` 中位数除以 `disp` 中位数，所有这些操作都用 `%>%` 运算符串联起来。

## 2.5 ggplot2 包是什么以及它的作用

在 R 中，主要有三种绘图系统：
-   Base graphics
-   lattice
-   ggplot2

美学属性的示例包括 x 轴、y 轴、颜色、形状、大小，甚至数据点的透明度。

可以说，ggplot2 是数据科学家中最流行的绘图系统，而且由于它是 tidyverse 的一部分，在本书中我们将使用该系统绘制图形。

让我们加载 R 自带的 `iris` 数据集，并创建其中两个变量的散点图。该数据由埃德加·安德森于 1935 年收集并发表，包含三种鸢尾花的花瓣和萼片的长度与宽度测量值。

![](img/a22105d68c35e8d5bd3c7bafb4644881_37_0.png)

**图 2.1** 使用 ggplot2 创建的散点图。`Sepal.Length` 变量映射到 x 美学属性，`Sepal.Width` 变量映射到 y 美学属性。通过添加 `theme_bw()` 图层应用了黑白主题。

## 代码清单 2.15 使用 `ggplot()` 函数绘图

```r
library(ggplot2)
data(iris)
myPlot <- ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width)) +
  geom_point() +
  theme_bw()

myPlot
```

请注意，我们不需要给这些变量加引号；`ggplot` 很聪明！

我们以 `+` 符号结束该行，用它在图中添加额外的图层（我们可以添加任意多的图层，直到创建出想要的图形）。惯例是，当我们要在图中添加额外图层时，当前图层要以 `+` 结尾，并把下一层放在新行中。这有助于保持代码的可读性。

在初始的 `ggplot()` 函数调用中添加图层时，每一行都需要以 `+` 结尾；你不能把 `+` 放在新的一行。

下一个图层是一个名为 `geom_point()` 的函数。*Geom* 代表 *geometric object（几何对象）*，即一种用于表示数据的图形元素，例如点、条形、线、箱线图等，因此产生这些图层的函数都被命名为 `geom_[图形元素]`。例如，让我们为图形添加两个新图层：`geom_density_2d()` 用于添加密度等高线，`geom_smooth()` 用于在数据上拟合一条带置信带的平滑线。

![](img/a22105d68c35e8d5bd3c7bafb4644881_38_0.png)

**图 2.2** 与前面相同的散点图，但分别使用 `geom_density_2d()` 和 `geom_smooth()` 函数添加了二维密度等高线和一条平滑线作为图层。
