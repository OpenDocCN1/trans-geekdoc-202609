
`here()`是`here`小工具包下的一个函数。该函数可以帮助你从正确的路径（包括文件夹）检索或保存文件、文件或R对象。即使在我们使用不同的机器时，它同样有效。

# 4.13 保存图表

![](img/2bc6b006fe018e0018b86f206ab98644_87_0.png)

图 4.3

在Windows系统中，点击“新建文件夹”图标。

![](img/2bc6b006fe018e0018b86f206ab98644_87_1.png)

图 4.4

将“新建文件夹”重命名为`plots`。

我们中的许多人还记得在不同电脑上，驱动器名称自动变化（尤其是使用U盘时）带来的不便体验。通过使用`here`包中的`here()`，我们始终能到达正确的路径或文件夹。

要以不同的图像格式将图表保存到名为`plots`的目录中，我们可以这样做：

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

`ggplot2`非常灵活，包含许多自定义选项。例如，我们想为图表设置这些参数：

1. `width = 10 cm`（你也可以使用英寸）
2. `height = 6 cm`（你也可以使用英寸）
3. `dpi = 150`。每英寸点数

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

## 4.14 总结

在本章中，我们简要描述了绘图之前的重要事项。然后我们教读者如何使用`ggplot2`包进行绘图。该包使用了图形语法（Grammar for Graphics）的原理，确保代码对用户更加直观。读者将学习如何生成单个变量的图，以及同时绘制两个或三个变量的图。`ggplot2`也非常灵活，包含许多自定义功能，帮助读者生成精彩的图表以及如何保存它们。

# 5 数据清洗 (Data Wrangling)

在本章结束时，读者将能够：

- 理解数据清洗的作用
- 理解`dplyr`包的基本能力
- 获得使用`dplyr`和`forcats`包执行常用数据清洗的技能

数据清洗消除错误并合并复杂数据集，使其更易访问和分析。由于今天数据量和数据源的快速扩展，存储和组织大量数据进行分析变得变得日益必要。

数据清洗也被称为Data Mung或数据转换（Data Transformation）。它粗义上是指手动将数据从一种“原始”格式转换或映射到另一种格式的。。这一过程使得数据消费变得更加方便。你可以在mode analytics网页上找到更多信息。

数据清洗也被称为data munging。它是将数据从一种“原始”格式转换和映射到另一种格式的过程，使其对于下游目的（如分析）更加合适且更有价值。数据清洗的目标是确保数据的质量和价值。数据分析师的大部分时间花在数据清洗过程中，而不是实际的数据分析上。几乎所有数据都需要数据清洗。

> https://community.modeanalytics.com/sql/tutorial/data-wrangling-with-sql/

![](img/2bc6b006fe018e0018b86f206ab98644_90_0.png)

图 5.1

数据清洗的主要部分。

在进一步分析之前。数据清洗有三个主要部分（Wickham and Grolelemund, 2017）。

## 5.3 使用 dplyr 包进行数据清洗

### 5.3.1 dplyr 包

`dplyr`是包含在`tidyverse`包集合中的一个包。`dplyr`包对于清洗、整理或转换你的数据非常有用。它是一个数据操作的语法。它提供了一组一致的动词，帮助你解决最常见的挑战。这个`tidyverse`网页有更多信息和示例。

### 5.3.2 常见的清洗流程

常见的清洗流程包括：

- 通过选择某些变量（列）来减小数据集的
- 从现有变量生成新变量
- 对变量的观测值进行排序
- 根据某些标准对观测值分组
- 将变量分组以估计统计数据

### 5.3.3 一些 dplyr 函数

对于上述步骤，对应的`dplyr`函数是：

- `dplyr::select()` —— 从数据框中选择若干变量
- `dplyr::mutate()` —— 从现有变量生成新变量
- `dplyr::arrange()` —— 对变量的观测值进行排序
- `dplyr::filter()` —— 筛选符合标准的观测值
- `dplyr::group_by()`和`dplyr::summarize()` —— 将变量分组以提供统计数据

## 5.4 准备

### 5.4.1 创建新项目或设置工作目录

确保知道工作目录在哪里至关重要。建议的做法是每次想开始分析时都创建一个新项目。这样做，可以通过File -> New Project创建。如果你没有从R新项目开始，你仍然需要知道工作目录的位置。

所以我们再次强调，每次想处理数据时，请确保：

- 使用R项目。从新项目开始工作要容易且整洁。一旦完成或需要注销电脑，关闭项目并在下次需要时打开。
- 如果你没有使用R项目，你处于正确的工作目录。输入`getwd()`显示活动的工作目录。要设置新的工作目录，使用函数`setwd()`。一旦知道工作目录在哪里，你就可以开始读取或导入数据。

### 5.4.2 加载库

记住，有几个包可以用来数据读入R。R可以读取几乎所有（并非所有）类型的数据格式。例如，我们知道常用格式有：

- SPSS (`.sav`)格式
- Stata (`.dta`)格式
- SAS格式
- MS Excel (`.xlsx`)格式
- 逗号分隔值`.csv`格式

然而，还有其他格式，例如DICOM格式的数据。DICOM数据包括CT扫描和MRI图像。还有shapefile格式的数据存储地理信息。三个包 - `haven`、`rio`、`readr`和`foreign`包对于读取或导入你的数据到R内存非常有用。

- **readr**提供了一种快速且友好的方法读取矩形数据（如csv, tsv和fwf）。该包包含在**tidyverse**元包中。
- **rio**提供了一种快速读取几乎所有类型电子表格和统计软件数据的方法。
- **readxl**读取`.xls`和`.xlsx`工作表。
- **haven**读取SPSS、Stata和SAS数据。

我们将使用**here**包来方便我们与工作目录的操作，并使用**lubridate**包来帮助我们处理日期。

```r
library(tidyverse)
```

```r
## -- Attaching tidyverse packages tidyverse 2.0.0 --
# v dplyr       1.1.1      v readr      2.1.4
# v forcats     1.0.0      v string     1.5.0
# v ggplot2     3.4.2      v tibble     3.2.1
# v lubridate   1.9.2      v tidyr      1.3.0
# v purrr       1.0.1
##                               Conflicts
tidyverse_conflicts()-
# x dplyr::filter()     masks stats::filter()
# x dplyr::lag()        masks stats::lag()
# i      Use      the         package      (http://conflicted.r-lib.org/) to force all conflicts to become errors
```

```r
library(rio)
```

```r
library(here)
```

```r
here() starts at C:/Users/drkim/Downloads/multivar_data_analysis/multivar_data_analysis
```

```r
library(lubridate)
```

当我们读取带有长变量名和空格的数据集时——尤其是读取MS Excel数据集后——我们可以使用**janitor**包来生成更符合R用户习惯的变量名。

### 5.4.3 数据集

我们将使用两个数据集。

- **csv**格式的stroke数据集
- **xlsx**格式的peptic ulcer数据集

## 5.4 准备

让我们读取数据集并为它们命名，分别为：

- `stroke`
- `pep`

```r
stroke <- read_csv(here("data", "stroke_data.csv"))

# Rows: 213 Columns: 12
# -- Column specification --------------------

# Delimiter: \
```

```r
perp <- import(here("data", "peptic_ulcer.xlsx"))
```

查看一下`stroke`和`pep`数据集。

`stroke`数据集包含：

- 219个观测值
- 12个变量

```r
glimpse(stroke)
```

```
# Rows: 213
# Columns: 12
# $ doa
<chr> "17/2/2011", "20/3/2011", "9/4/2011", "12/4/2011", "12/4-
# $ dod
<chr> "18/2/2011", "21/3/2011", "10/4/2011", "13/4/2011", "13/-
# $ status
<chr> "alive", "alive", "dead", "dead", "alive", "dead", "aliv-
# $ sex
<chr> "male", "male", "female", "male", "female", "female"
# $ dm
<chr> "no", "no", "no", "no", "yes", "no", "no", "yes", "yes",-
# $ gcs
<dbl> 15, 15, 13, 15, 3, 11, 15, 6, 15, 4, 4, 12, 1-
# $ sbp
<dbl> 151, 196, 126, 178, 103, 91, 171, 106, 123, 144, 233, -
# $ dbp
<dbl> 73, 128, 78, 103, 62, 55, 80, 97, 83, 89, 120, -
# $ wbc
<dbl> 12.5, 8.1, 15.3, 13.9, 14.7, 14.2, 8.7, 5.5, 10.5, 7,-
# $ time2
<dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,-
# $ stroke_type
<chr> "IS", "IS", "HS", "IS", "HS", "HS", "IS", "IS", "HS", "I-
# $ referral_from<chr> "non-hospital", "non-hospital", "hospital", "hospital", -
```

`pep`数据集包含：

- 121个观测值
- 34个变量

```r
glimpse(pep)
```

接下来，我们检查数据的前五行观测值。其余观测值未显示。你可以看到变量类型：

## 5.4 准备

- `chr` (字符),
- `int` (整数),
- `dbl` (双精度)

```r
stroke <- slice_head(5)

# table: 5 x 12
# doa dod status sex dm gcs sbp dbp wbc time2 stroke_type referral_from
# <chr> <chr> <chr> <chr> <chr> <dbl> <dbl> <dbl> <dbl> <dbl> <chr> <chr>
# 17/2/2011 20/3/2011 9/4/2011 12/4/2011 12/4-
# 18/2/2011 21/3/2011 10/4/2011 13/4/2011 13/-
# alive alive dead dead alive dead aliv-
# male male female male female female
# no no no no yes no no yes yes,-
# 15 15 13 15 3 11 15 6 15 4 4 12 1-
# 151 196 126 178 103 91 171 106 123 144 233 -
# 73 128 78 103 62 55 80 97 83 89 120 -
# 12.5 8.1 15.3 13.9 14.7 14.2 8.7 5.5 10.5 7,-
# 1 1 1 1 1 1 1 1 1 1 1 1 1,-
# IS IS HS IS HS HS IS IS HS I-
# non-hospital non-hospital hospital hospital, -
```

```r
pep <- slice_head(5)

# table: 5 x 10
# age diastolic perforation wc gender malena ASA outcome
# <dbl> <dbl> <dbl> <dbl> <chr> <chr> <chr> <chr> <chr>
# 42 141 0.5 12.5 male nausea no no
# 66 197 1.0 8.1 female fever no no
# 67 126 0.5 15.3 male diarrhea no no
# 19 90 0.5 13.9 female no no no
# 77 147 1.0 14.7 female yes no no
```

## 5.5 数据清洗

我们将使用这些函数：

- `dplyr::select()`
- `dplyr::mutate()`和
- `dplyr::rename()`

### 5.5.1 使用 dplyr::select 选择变量

当你处理具有许多列的数据集时，只选择必要的列可以减小数据集的大小。通过创建一个较小的数据集来实现。然后你就可以对这部分数据进行探索了。例如，在`pep`数据集中，我们有34个变量。让我们创建一个包含10个变量的新数据集`pep2`：

```r
pep2 <- pep %>%
  select(age, diastolic, perforation, wc, gender, vomiting, malena, outcome)

glimpse(pep2)

# Rows: 12
# Columns: 10
# $ age diastolic perforation wc gender vomiting malena ASA outcome
# <dbl> <dbl> <dbl> <dbl> <chr> <chr> <chr> <chr> <chr>
# 42 141 0.5 12.5 male nausea no no
# 66 197 1.0 8.1 female fever no no
# 67 126 0.5 15.3 male diarrhea no no
# 19 90 0.5 13.9 female no no no
# 77 147 1.0 14.7 female yes no no
```

## 5.5.3 使用 rename() 重命名变量

现在，我们想要重命名：

- 将变量`gender`重命名为`sex`
- 将变量`ASA`重命名为`asa`

```r
pep2 <- pep2 %>%
  rename(sex = gender,
         asa = ASA)
```

## 5.6 数据排序与观测筛选
