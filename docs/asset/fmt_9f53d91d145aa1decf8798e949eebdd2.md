
![](img/2bc6b006fe018e0018b86f206ab98644_44_0.png)

图 3.1

GitHub 上的数据集仓库。

![](img/2bc6b006fe018e0018b86f206ab98644_44_1.png)

图 3.2

RStudio Cloud。

## 3.3 Dataset Repository on GitHub

我们将使用包含本书数据集的 GitHub 仓库。仓库的名为 `data-for-RMed`。要进入仓库，请点击此链接²

> ²`https://github.com/drkamarul/multivar_data_analysis.git`

## 3.4 RStudio Project on RStudio or Posit Cloud

![](img/2bc6b006fe018e0018b86f206ab98644_45_0.png)

图 3.3

RStudio Cloud 登录页。

![](img/2bc6b006fe018e0018b86f206ab98644_45_1.png)

图 3.4

Rstudio Cloud、工作空间（Workspace）和新项目（New Project）。

![](img/2bc6b006fe018e0018b86f206ab98644_45_2.png)

图 3.5

来自 Git 仓库的新项目。

### 3.4 RStudio Project on RStudio or Posit Cloud

Rstudio 现在被称为 Posit Cloud。通过 RStudio 和 Posit Cloud，你可以轻松方便地访问 RStudio IDE。在本节中，我们将向你展示如何从我们 GitHub 上的书籍仓库复制一个 RStudio 或 Posit Cloud 项目。我们建议你遵循以下步骤：

![](img/2bc6b006fe018e0018b86f206ab98644_46_0.png)

图 3.6

将数据集仓库克隆到 RStudio Cloud。

![](img/2bc6b006fe018e0018b86f206ab98644_46_1.png)

图 3.7

通过粘贴 HTTPS 链接将 GitHub 仓库克隆到 RStudio 或 Posit Cloud。

- 进入你的 RStudio Cloud 页面。
- 接下来，使用你的凭据登录 RStudio 或 Posit Cloud。
- 进入工作空间后，点击 `New Project`。
- 点击 `New Project from Git`。

### 3.4 RStudio Project on RStudio or Posit Cloud

![](img/2bc6b006fe018e0018b86f206ab98644_47_0.png)

图 3.8

一个新的 RStudio Cloud 项目。

![](img/2bc6b006fe018e0018b86f206ab98644_47_1.png)

图 3.9

你机器上的 RStudio。

- 在点击 New Project 后，返回我们 GitHub 上的 `data-for-RMed` 仓库。
- 点击 `Clone`。
- 点击 `HTTPS`。
- 粘贴 HTTPS 链接。
- 你已将仓库克隆到 RStudio 或 Posit Cloud。

## 3.5 RStudio Project on Machine

![](img/2bc6b006fe018e0018b86f206ab98644_48_0.png)

图 3.10

一个新的 RStudio Cloud 项目。

![](img/2bc6b006fe018e0018b86f206ab98644_48_1.png)

图 3.11

你机器上的 RStudio。

- 在点击 New Project 后，返回我们 GitHub 上的 `data-for-RMed` 仓库。
- 点击 `Clone`。
- 点击 `HTTPS`。
- 粘贴 HTTPS 链接。
- 你已将仓库克隆到 RStudio 或 Posit Cloud。

这些是本地机器上的 RStudio 项目。

![](img/2bc6b006fe018e0018b86f206ab98644_49_0.png)

图 3.12

项目向导。

![](img/2bc6b006fe018e0018b86f206ab98644_49_1.png)

图 3.13

来自 Git。

- 启动你的 RStudio IDE。
- 在菜单中，点击 `File`，然后点击 `New Project`。
- 接下来，点击 `Project`，然后点击 `Version Control`。
- 之后，点击 `Git`。
- 正如你之前在步骤中复制了 GitHub 链接，这里也一样；从 `data-for-RMed` 仓库复制。

![](img/2bc6b006fe018e0018b86f206ab98644_50_0.png)

图 3.14

克隆仓库。

![](img/2bc6b006fe018e0018b86f206ab98644_50_1.png)

图 3.15

RStudio 项目。

- 现在，你可以粘贴 HTTPS 链接（参见图 3.14）。你会发现项目目录将自动填充。
- 接下来你可以点击 `Browse`，以便选择你喜欢的任何文件夹作为工作目录。

如果你使用的是 Windows 操作系统，我们建议使用主目录（例如 `Documents`）。

你会发现 RStudio 将在你的本地机器上创建一个新目录。该工作目录包含了与我们的 仓库相同的文件夹和文件结构：

## 3.6 Summary

在本章中，我们向读者展示了如何设置 R 环境，以便他们的 RStudio 工作目录产生与我们相同的文件夹和文件结构。通过这种策略，我们将最大限度地减少读者在使用书中的 R 代码时产生的错误。我们还展示了数据集的位置。它们最初存储在本书的 GitHub 仓库中。然后我们为读者提供了说明，让他们能够在 Posit Cloud（原 RStudio Cloud）远程以及在本地机器的 RStudio IDE 上创建新的 RStudio 项目。

![](img/2bc6b006fe018e0018b86f206ab98644_52_0.png)

## 4 Data Visualization

在本章中，读者将：

- 了解数据可视化概念
- 理解良好图表的要素
- 能够使用 `ggplot` 包生成图表
- 能够以不同的格式和图形设置保存图表

在我们的实体书中，图表将以黑白文字出版。因此，`ggplot2` 自带的某些 R 代码将包含一行额外的代码，例如 `scale_colour_grey() + scale_line_grey()`，以确保图表适合我们实体书内部的黑白文字。我们书在书网站上的在线版本¹将以彩色显示图表。

## 4.3 数据可视化的历史与目标

作者爱德华·塔夫特（Edward Tufte）在他1893年出版的名为《定量信息的视觉显示》的书中，定义了图形化显示以及有效图形展示的原则。书中提到：“统计图表的卓越之处在于用清晰、精确和高效的方式传递复杂的思想”。

可视化是将数据以图表形式表示并与这些表示进行交互的过程。其目标是获得数据的洞察。Watson IBM 网页概述了其中的部分过程。

## 4.4 优秀图表的要素

良好的图表对于视觉化地传达数据中的信息至关重要。它们可以辅助你的书籍、报告或手稿中的文字。然而，在为图表编写内容时，你可能确保考虑以下要素：

- 你拥有良好的数据
- 优先考虑内容而非方法论、图形设计、图表制作技术或其他因素
- 不要扭曲数据想要表达的内容
- 在小空间内展示大量数字的存在
- 大数据集的连贯性
- 引导眼睛比较不同的数据片段
- 图表从多个细节层次揭示数据，从宏观概述到精细结构
- 图表具有合理清晰的目的：描述、探索、制表和装饰
- 与数据集的统计描述和口头描述紧密集成

## 4.5 R 中的图形包

R 中有多个用于创建图形的包。它们包括用于执行通用数据可视化或图形任务的包，另一些则为特定的统计或数据分析提供特定的图形。

## 4.6 ggplot2 包

R 中流行的通用图形包包括：这意味着每当我们打开 R 时，都会加载它们：

- `graphics`: 一个 R 基础包，由 RStudio 用户贡献的包，因此在第一次使用时必须先安装。它作为一个独立的包存在，但也包含在 `tidyverse` 包中。
- `ggplot2`: 这是一个用户贡献的包。它提供了显示多元关系的能力，并改进了基础 R 图形。该包移植了栅格图（trellis graphs）的创建：显示变量或……的图形。
- `lattice`: 这是一个用户贡献的包。

一些更具体的图形包示例包括：

- `surminer`: 该 R 包提供了辅助生存分析和可视化的函数。它包含函数 `ggsurvival()`，用于轻松地绘制带有风险人数表和删失点的、准备发表的生存曲线。
- `sjPlot`: 用于数据可视化的绘图和表格输出函数集。使用 sjPlot，你可以为各种统计分析制作图表，包括简单和交叉频率、直方图、箱线图、（广义）线性模型、混合效应模型、主成分分析和相关矩阵、聚类、散点图、堆叠比例图以及回归模型的效应图（包括交互项）。

除了 `graphics` 包（R 基础包）外，如果你想第一次使用 `ggplot2` 和 `lattice` 等包，则需要将它们安装到你的 R 库（library）中。

### 4.6 ggplot2 包

本书将重点关注使用 `ggplot2` 包。`ggplot2` 包是 R 中一个优雅且多功能的通用图形包。它实现了`图形语法`（grammar of graphics）的概念。这一概念的优势是加快了学习图形的过程。它还方便了创建复杂图形的过程。

使用 ggplot2 时，记住你的 R 代码至少：

- 以 `ggplot()` 开始
- 识别要绘制的数据数据 `data = Your Data`
- 说明要绘制的变量，例如双变量的情况下使用 `aes(x = x 轴上的变量, y = y 轴上的变量)`
- 选择图形类型，例如直方图使用 `geom_histogram()`，散点图使用 `geom_points()`

`ggplot2` 的官方网站在此 `https://ggplot2.tidyverse.org/`，这是一个极佳的资源。该网站指出 ggplot2 是一个基于图形语法的 R 绘图系统，试图吸取基础图形和 lattice 图形的优点，并抛弃其缺点。

## 4.7 准备

### 4.7.1 绘图前的重要问题

在绘图之前，最好问自己这些问题：

- 变量类型是什么？
- 数据的类型是什么？
- 它们是因子（分类）变量还是数值变量？
- 我是要绘制
  - 单个变量？
  - 两个变量？
  - 三变量？

## 4.8 读取数据

R 可以读取几乎（并非所有）类型的数据。常见的数据格式包括：

- 逗号分隔文件 (.csv)
- MS Excel 文件 (.xlsx)
- SPSS 文件 (.sav)
- Stata 文件 (.dta)
- SAS 文件 (.sas)

然而，如果你拥有从统计软件读取数据的连接包将会有帮助。例如：`haven` 和 `rio` 包。

下面展示了使用 haven 包读取 SAS、SPSS 和 Stata 文件的函数。

1. SAS：`read_sas()` 读取 .sas7dat 和sas7cat 文件，`read_xpt()` 读取 SAS 传输文件（版本 5 和 8）。`write_sas()` 写入 .sasbat 文件。
2. SPSS：`read_sav()` 读取 .sav 文件，`read_port()` 读取旧的 .por 文件。`write_sav()` 写入 .sav 文件。
3. Stata：`read_dta()` 读取 .dta 文件（直到版本 15），`write_dta()` 写入 .dta 文件（版本 8-15）。

## 4.10 读取数据集

![](img/2bc6b006fe018e0018b86f206ab98644_59_0.png)

**图 4.1**

Packages 窗口。

![](img/2bc6b006fe018e0018b86f206ab98644_59_1.png)

**图 4.2**

输入要安装的包名称。

### 4.10 读取数据集

在本章中，我们将使用两个数据集：*gapminder* 数据集和胃溃疡数据集。*gapminder* 数据集是 **gapminder** 包中的内置数据集。你可以通过 `https://www.gapminder.org/` 网页了解更多关于 *gapminder* 的信息。gapminder 网站包含许多实用的数据集并展示了出的图表，这些由已故的汉斯·罗斯林（Hans Rosling）博士推广。

要加载 **gapminder** 包，输入：

```
library(gapminder)
```

接下来，我们将 gapminder 导入 R 中。然后，我们将浏览数据的前六行观测值。以下代码：

- 将 gapminder 分配为一个数据集
- 包含一个管道符 `%>%`，它连接了两个代码（gapminder 和 slice）
- 包含一个名为 `slice()` 的函数，用于选择数据集的行

```
gapminder <- gapminder
gapminder %>%
slice(1:4)
```

```
## A tibble: 4 x 6
## country continent year lifeExp pop gdpPercap
## <fct> <int> <dbl> <int> <dbl>
## 1 Afghanistan Asia 1952 28.8 8425333 779.
## 2 Afghanistan Asia 1957 30.3 9240934 821.
## 3 Afghanistan Asia 1962 32.0 1026783 853.
## 4 Afghanistan Asia 1967 34.0 11537966 836.
```

列出数据集的变量并查看每个变量的类型是一个好主意：

```
glimpse(gapminder)
```

```
# Rows: 1,704
## Columns: 6
## $ country <fct> "Afghanistan", "Afghanistan", "Afghanistan", "Afghanistan", ~
## $ continent <fct> Asia, Asia, Asia, Asia, Asia, Asia, Asia, ~
## $ year <int> 1952, 1957, 1962, 1967, 1972, 1977, 1982, 1987, 1992, 1997, ~
## $ lifeExp <dbl> 28.801, 30.312, 31.997, 36.068, 38.438, 39.854, 40.8~
## $ pop <int> 8425333, 9240934, 1026783, 11537966, 13079460, 14880372, 12~
## $ gdpPercap <dbl> 779.4453, 820.8530, 853.1007, 836.1971, 739.9811, 786.1134, ~
```

我们可以看到 gapminder 数据集具有：

- 六 (6) 个变量
- 总共 1704 个观测值
- 两个因子（factor）变量、两个整数变量和两个数值（dbl）变量

我们可以使用 `summary()` 生成 gapminder 数据集的基础统计信息。该函数将列出：

- 频率
- 中心趋势和离散程度，如最小值、第一分位数、中位数、第三分位数和最大值

```
summary(gapminder)
```

```
## country | continent | year | lifeExp
## Afghanistan | Africa : :624 Min. :1952 Min. :23.60
## Albania | Americas:300 1st Qu.:1966 1st Qu.:48.20
## Algeria | Asia :396 Median :1980 Median :60.71
## Angola | Europe :360 Mean :1980 Mean :59.47
## Argentina | Oceania :24 3rd Qu.:1993 3rd Qu.:70.85
## Australia | (Other) Max. :2007 Max. :82.60
## pop gdpPercap ## Min. :6.001e+04 :241.2
## 1st Qu.:7.944e+06 :1202.1
## Median :7.024e+06 :3531.8
## Mean :2.9560e+07 :7215.3
## 3rd Qu.:1.319e+09 :9325.5
```

## 4.11 基础图表

让我们通过以下参数创建一个简单的图：

- data = gapminder
- variables: x = year, y = lifeExp
- 散点图：geom_point()

```
ggplot(data = gapminder) +
geom_point(mapping = aes(x = year, y = lifeExp)) + 
theme_bw()
```

![](img/2bc6b006fe018e0018b86f206ab98644_62_0.png)

从图中可以看出：

- 散点图显示了年份与预期寿命之间的关系
- 随着年份的增长，预期寿命在增加

`geom_point()` 函数告诉 R 准备绘图。用户可以在网页上找到更多关于 ggplot2 的资源（Wickham et al., 2020）。其他优秀资源包括《R Graphics》一书（Chang, 2013）。

## 4.12 复杂图表
