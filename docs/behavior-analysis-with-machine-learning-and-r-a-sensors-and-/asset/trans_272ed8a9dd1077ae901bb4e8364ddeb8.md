

# 第 4 章 行为数据的探索与可视化

一组是从音频中提取的特征，另一个是从加速度计传感器提取的特征。首先，使用 `cor()` 函数计算每对变量之间的皮尔逊相关系数，然后使用 `corrplot()` 函数生成图表。在这里，我们指定只显示上三角部分，即设置 `type = "upper"`。`tl.pos` 参数控制标签的打印位置。在本示例中，设置在顶部和对角线上。设置 `diag = FALSE` 指函数不要打印对角线，因为对角线全是每个变量与其自身的相关性。

```
library(corrplot)

# 加载家庭活动数据集。
dataset <- read.csv(file.path(datasets_path,
"home_tasks",
"sound_acc.csv"))
```

```
CORRS <- cor(dataset[,-1])
corrplot(CORRS, diag = FALSE, tl.pos = "td", tl.lex = 0.5,
method = "color", type = "upper")
```

看起来声音特征（v1_）和加速度特征（v2_）之间的相关性不是很大。在这种情况下，由于我们希望这两个信息源尽可能独立，以便正如第 3.4 节所示，它们能够捕捉不同的特征并互为补充。另一方面，某些加速度特征之间存在高相关性。例如 v2_magY 与 v2_sdMagnitude 之间。

> 请注意，皮尔逊相关仅捕捉线性关系。

## 4.6.1 交互式相关性图

在绘制相关性图时，可视化实际的相关性值是有用的。当变量很多时，这样做变得困难。克服这一局限的一种方法是使用交互式图表。以下代码段使用 `qilcharts` 包中的 `iplotCorr()` 函数来生成交互式相关性图。它的好之处在于，你可以通过鼠标悬停来检查单元格的值。如果你点击一个单元格，还会渲染相应的散点图。这使得这类图表成为探索变量关系的非常方便的工具。

![](img/91c149cc24c3e5af2971580c9dda9d8b_139_0.png)

![](img/91c149cc24c3e5af2971580c9dda9d8b_140_0.png)

图 4.5：HOME TASKS 数据集的相关图。

# 第 4 章 行为数据的探索与可视化

library(qtlcharts) # 用于交互式图表的库。

```
# 加载家庭活动数据集。
dataset <- read.csv(file.path(datasets_path,
    "home_tasks",
    "sound_acc.csv"))
```

```
oplCorr(dataset[-1])
```

![](img/91c149cc24c3e5af2971580c9dda9d8b_141_0.png)

> 请注意，在本书编写时，纸质书籍不支持交互式图表。请查看在线版本以查看实际结果，或在计算机上运行代码。

## 4.7 时间序列

行为通常是依赖于时间的。因此，能够可视化时间序列数据就变得至关重要。为了说明如何绘制时间序列数据，我将使用 `ggplot` 包和 HAND GESTURES 数据集。记住数据是使用三轴加速度计收集的，因此对于每个手势，我们都有 3 维时间序列。每个维度代表 x、y 和 z 轴之一。首先，我们读取存储用户 1 手势的一个文本文件。每列代表一个轴。然后，我们需要进行一些格式化我们将创建一个包含三列的数据框。第一列是整数时间步，从 1 到每个轴的点的数量。第二列是代表 x、y 或 z 轴的因子。最后一列包含实际值。

```
dataset <- read.csv("../data/hand_gestures/1/1_20130703-120056.txt",
header = F)
# 进行一些预处理。
type <- c(rep("x", nrow(dataset)),
rep("y", nrow(dataset)),
rep("z", nrow(dataset)))
type <- as.factor(type)
values <- c(dataset$V1, dataset$V2, dataset$V3)
t <- rep(1:nrow(dataset), 3)
f <- data.frame(timestep = t, type = type, values = values)
```

```
# 打印前几行。
head(df)
# timestep type x values
# 1 1 0.0864655
# 2 2 0.9512450
# 3 3 1.3140911
# 4 4 1.4317709
# 5 5 1.5102241
# 6 6 1.5298374
```

注意最后一列（values）包含了所有轴的值，而不是每个轴一列。然后我们可以使用 `ggplot()` 函数。线条根据轴的类型着色，通过 `colour = type` 指定。type 列应该是一个因子。线条也取决于轴的类型，并通过 `linetype = type` 指定。

```
tsPlot <- ggplot(data = df,
             aes(x = timestep,
                  y = values,
                  colour = type) +
linetype = type) +
title("Hand gesture '1', user 1") +
xlab("Timestep") +
ylab("Acceleration") +
theme_minimal() +
theme(plot.title = element_text(hjust = 0.5),
legend.position="right",
legend.key.width = unit(1.0,"cm"),
legend.key.size = unit(0.5,"cm"))
print(tsPlot)
```

![](img/91c149cc24c3e5af2971580c9dda9d8b_143_0.png)

图 4.6：用户 1 手势 '1'的时间序列图。

## 4.7.1 交互式时间序列

有时，能够交互式地缩放、高亮、选择图表的区域是有用的。在 R 中，有一个名为 `dygraphs` 的包，允许你为时间序列数据生成复杂的图表。以下代码读取手势文件并在开头添加了一个名为 `timestep` 的列。

```
library(dygraphs)

# 读取用户 1 的手势 '1'。
dataset <- read.csv("../data/hand_gestures/1/1_20130703-120056.txt")
dataset <- cbind(timestep = 1:nrow(dataset), dataset)
```

然后我们可以生成一个带有一线的极简图：

```
dygraph(dataset)
```

![](img/91c149cc24c3e5af2971580c9dda9d8b_144_0.png)

在在线版本中，可以通过点击和拖拽来缩放。双击恢复缩放。可以对图表进行许多自定义。例如下面的代码添加了标题、填充了并阴影了 30 到 40 之间的区域。

```
dygraph(dataset, main = "Hand Gesture '1'") %>%
options(fillGraph = TRUE, fillAlpha = 0.25) %>%
dyEvent("30", "Point of interest", labelLoc = "top") %>%
dyShading(from = "30", to = "40", color = "#CCCCCC")
```

![](img/91c149cc24c3e5af2971580c9dda9d8b_145_0.png)

## 4.8 多维缩放 (MDS)

在某些情况下，我们的数据由多个变量组成。如果变量的数量超过 3（三维数据），绘制数据点将变得困难。例如 HOME TASKS 数据集，它包含 27 个来自加速度计和声音的预测变量。我们可能想做的一件事是可视化数据点，检查同类点是否更接近。这让你了解问题的难度。如果同类点非常接近并聚集，分类模型可能无法区分数据点。但我们如何绘制此类高维关系？一种方法是使用多维缩放（MDS），它由一组旨在降低数据维度组成，以便在 2D 或 3D 中可视化。目标是在给定的低维度保留点对之间的原始距离。

存在多种 MDS 方法，但大多数方法接受距离矩阵作为输入（例如欧式距离）。在 R 中，从点集生成距离矩阵很容易。作为一个示例，让我们生成一些数据点。

```
# 生成 3 个2维随机点。
x <- runif(3)
y <- runif(3)
d <- data.frame(x,y)
labels <- c("a","b","c")
print(d)
#      x          y
# 1 0.4457900 0.5978606
# 2 0.4740106 0.5013938
# 3 0.8890085 0.4109234
```

可以使用 `dist()` 函数计算距离矩阵。默认情况下，该函数计算行之间的欧式距离：

```
dist(d)
#      1          2
# 2 0.0999863
# 3 0.48102824 0.42486143
```

输出是行对之间的欧式距离。

