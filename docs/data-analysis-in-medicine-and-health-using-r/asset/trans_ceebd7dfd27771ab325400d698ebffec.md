

```r
scale_x_continuous(breaks = seq(0,12,1)) + 
theme_bw())
```

## x 比例尺已存在。
## 添加另一个 x 比例尺，这将替换现有的比例尺。

```r
myplot
```

## geom_smooth() 使用方法 'loess' 公式为 'y - x'

GDP（对数形式）和预期寿命：

![](img/2bc6b006fe018e0018b86f206ab98644_86_0.png)

我们现在可以看到一张漂亮的图表了。接下来，我们要把图表（当前在屏幕上）保存为这些格式：

- pdf 格式
- png 格式
- jpg 格式

如果我们要把图表保存到名为 plots 的文件夹中，那么：

- 进入工作目录
- 点击新建文件夹
- 将其命名为 plot

这时 `here()` 函数就非常有用。你可以轻松地指向正确的文件夹，让 R 知道在哪里定位文件。

`here()` 是 `here` 小工具包下的一个函数。该函数可以帮助你从正确的路径（包括文件夹）检索或保存文件、文件或 R 对象。即使在我们使用不同的机器时，它同样有效。

# 4.13 保存图表

![](img/2bc6b006fe018e0018b86f206ab98644_87_0.png)

图 4.3

在 Windows 系统中，点击“新建文件夹”图标。

![](img/2bc6b006fe018e0018b86f206ab98644_87_1.png)

图 4.4

将“新建文件夹”重命名为 plots。

我们中的许多人还记得在不同电脑上，驱动器名称自动变化（尤其是使用 U 盘时）带来的不便体验。通过使用 `here` 包中的 `here()`，我们始终能到达正确的路径或文件夹。

要以不同的图像格式将图表保存到名为 plots 的目录中，我们可以这样做：

```r
ggsave(plot = myplot,
  here("plots", "my_pdf_plot.pdf"))
```

```r
# 保存 6.5 x 4.5 的图像
## geom_smooth() 使用 method = 'loess' 和 formula = 'y ~ x'
```

```r
ggsave(plot = myplot,
  here("plots", "my_png_plot.png"))
```

```r
# 保存 6.5 x 4.5 的图像
## geom_smooth() 使用 method = 'loess' 和 formula = 'y - x'
```

```r
ggsave(plot = myplot,
  here("plots", "my_jpg_plot.jpg"))
```

```r
## 保存 6.5 x 4.5 的图像
## geom_smooth() 使用 method = 'loess' 和 formula = 'y - x'
```

ggplot2 非常灵活，包含许多自定义选项。例如，我们想为图表设置这些参数：

1. width = 10 cm（你也可以使用英寸）
2. height = 6 cm（你也可以使用英寸）
3. dpi = 150。每英寸点数

```r
ggsave(plot = myplot,
  here('plots', 'my_pdf_plot2.pdf'),
  width = 10, height = 6, units = "in",
  dpi = 150, device = "pdf")
```

```r
## geom_smooth() 使用 method = 'loess' 和 formula = 'y - x
```

```r
ggsave(plot = myplot,
  here('plots', 'my_png_plot2.png'),
  width = 10, height = 6, units = "cm",
  dpi = 150, device = "png")
```

```r
## geom_smooth() 使用 method = 'loess' 和 formula = 'y - x
```

```r
ggsave(plot = myplot,
  here("plots", "my_jpg_plot2.jpg"),
  width = 10, height = 6, units = "cm",
  dpi = 150, device = "jpg")
```

```r
## geom_smooth() 使用 method = 'loess' 和 formula = 'y - x
```

# 4.14 总结

在本章中，我们简要描述了绘图之前的重要事项。然后我们教读者如何使用 `ggplot2` 包进行绘图。该包使用了图形语法（Grammar for Graphics）的原理，确保代码对用户更加直观。读者将学习如何生成单个变量的图，以及同时绘制两个或三个变量的图。ggplot2 也非常灵活，包含许多自定义功能，帮助读者生成精彩的图表以及如何保存它们。

# 5
# 数据清洗 (Data Wrangling)

在本章结束时，读者将能够：

- 理解数据清洗的作用
- 理解 `dplyr` 包的基本能力
- 获得使用 `dplyr` 和 `forcats` 包执行常用数据清洗的技能

数据清洗消除错误并合并复杂数据集，使其更易访问和分析。由于今天数据量和数据源的快速扩展，存储和组织大量数据进行分析变得变得日益必要。

数据清洗也被称为 Data Mung 或数据转换（Data Transformation）。它粗义上是指手动将数据从一种“原始”格式转换或映射到另一种格式的。。这一过程使得数据消费变得更加方便。你可以在 mode analytics 网页上找到更多信息。

数据清洗也被称为 data munging。它是将数据从一种“原始”格式转换和映射到另一种格式的过程，使其对于下游目的（如分析）更加合适且更有价值。数据清洗的目标是确保数据的质量和价值。数据分析师的大部分时间花在数据清洗过程中，而不是实际的数据分析上。几乎所有数据都需要数据清洗。

> https://community.modeanalytics.com/sql/tutorial/data-wrangling-with-sql/

![](img/2bc6b006fe018e0018b86f206ab98644_90_0.png)

图 5.1
数据清洗的主要部分。

在进一步分析之前。数据清洗有三个主要部分（Wickham and Grolelemund, 2017）。

# 5.3 使用 dplyr 包进行数据清洗

### 5.3.1 dplyr 包

`dplyr` 是包含在 tidyverse 包集合中的一个包。`dplyr` 包对于清洗、整理或转换你的数据非常有用。它是一个数据操作的语法。它提供了一组一致的动词，帮助你解决最常见的挑战。这个 tidyverse 网页有更多信息和示例。

### 5.3.2 常见的清洗流程

常见的清洗流程包括：

- 通过选择某些变量（列）来减小数据集的
- 从现有变量生成新变量
- 对变量的观测值进行排序
- 根据某些标准对观测值分组
- 将变量分组以估计统计数据

### 5.3.3 一些 dplyr 函数

对于上述步骤，对应的 `dplyr` 函数是：

- `dplyr::select()` —— 从数据框中选择若干变量
- `dplyr::mutate()` —— 从现有变量生成新变量
- `dplyr::arrange()` —— 对变量的观测值进行排序
- `dplyr::filter()` —— 筛选符合标准的观测值
- `dplyr::group_by()` 和 `dplyr::summarize()` —— 将变量分组以提供统计数据

# 5.4 准备

### 5.4.1 创建新项目或设置工作目录

确保知道工作目录在哪里至关重要。建议的做法是每次想开始分析时都创建一个新项目。这样做，可以通过 File -> New Project 创建。如果你没有从 R 新项目开始，你仍然需要知道工作目录的位置。

所以我们再次强调，每次想处理数据时，请确保：

- 使用 R 项目。从新项目开始工作要容易且整洁。一旦完成或需要注销电脑，关闭项目并在下次需要时打开。
- 如果你没有使用 R 项目，你处于正确的工作目录。输入 `getwd()` 显示活动的工作目录。要设置新的工作目录，使用函数 `setwd()`。一旦知道工作目录在哪里，你就可以开始读取或导入数据。

### 5.4.2 加载库

记住，有几个包可以用来数据读入 R。R 可以读取几乎所有（并非所有）类型的数据格式。例如，我们知道常用格式有：

- SPSS (.sav) 格式
- Stata (.dta) 格式
- SAS 格式
- MS Excel (.xlsx) 格式
- 逗号分隔值 .csv 格式

然而，还有其他格式，例如 DICOM 格式的数据。DICOM 数据包括 CT 扫描和 MRI 图像。还有 shapefile 格式的数据存储地理信息。三个包 - `haven`、`rio`、`readr` 和 `foreign` 包对于读取或导入你的数据到 R 内存非常有用。

