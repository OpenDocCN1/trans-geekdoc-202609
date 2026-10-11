
# 让我们加载 tidyverse

让我们加载 tidyverse，它将加载 dplyr 以及其他包。tidyverse 是由 RStudio 开发的一组 R 包（Wickham 等人，2019），已成为数据分析最流行的框架之一。

```r
# 加载数据
data(gapminder)

# 要熟悉此数据集，您可能想要使用以下函数
?gapminder

# 检查 gapminder 数据集的数据类型
class(gapminder)
## "data.frame"
```

您可以运行 `View(gapminder)` 来查看整个数据集，这将在 RStudio 查看器中打开数据集。如果您只对显示 DataFrame 的前 6 行感兴趣，可以使用 `head(gapminder)`，最后 6 行可以使用 `tail(gapminder)` 获取。

有哪些变量，它们各自的数据类型是什么？

该数据集包含九个变量，您可以使用 `str` 函数查看其详细信息：

```r
# 显示 gapminder 数据集的结构
str(gapminder)

## 'data.frame': 10545 obs. of 9 variables:
## $ country         : Factor w/ 185 levels "Albania","Algeria",..: 1 2 3 4 5 6 7 8 9 10 ...
## $ year            : int 1960 1960 1960 1960 1960 1960 1960 1960 1960 1960 ...
## $ infant_mortality: num 115.4 148.2 208 NA 59.9 ...
## $ life_expectancy : num 62.9 47.5 36 63 65.4 ...
## $ fertility       : num 6.19 7.65 7.32 4.43 3.11 4.55 4.82 3.45 2.7 5.57 ...
## $ population      : num 1636054 11124892 5270844 54681 20619075 ...
## $ gdp             : num NA 1.38e+10 NA NA 1.08e+11 ...
## $ continent       : Factor w/ 5 levels "Africa","Americas",..: 4 1 1 2 2 3 2 5 4 3 ...
## $ region          : Factor w/ 22 levels "Australia and New Zealand",..: 19 11 10 2 15 21 2 1 22 21 ...
```

但是，如果您只对检查列名感兴趣，只需插入以下代码即可简单地使用 `colnames()`：

```r
# 显示数据框的所有列
colnames(gapminder)
## "country" "year" "infant_mortality" "life_expectancy" "fertility"
## "population" "gdp" "continent" "region"

# 维度
dim(gapminder)
## 10545 9

# 检查数据集的行数
nrow(gapminder)
## 10545

# 检查数据集的列数
ncol(gapminder)
## 9
```

# 介绍 dplyr

想象一下，您正在发出指令来探索和操作 Gapminder 数据集。`dplyr` 函数提供了这些指令，称为动词，用于数据操作语言。这些动词具有统一的结构：您将要操作的 DataFrame 作为第一个参数，随后是您想要用变量操作的任务作为后续参数，所有这些都不需要使用引号。输出将是一个具有所需操作的新 DataFrame。`dplyr` 使数据操作更快、更直观、更易于理解。

# 重命名列

如何在数据集中将 population 列重命名为 `country_population`，将 GDP 列重命名为 `country_gdp`？

为了使我们的数据更易于处理，我们经常需要重命名列名以更好地反映其内容。以下是使用 `dplyr` 包中的 `rename()` 函数执行此操作的示例：

```r
# 重命名 population 和 GDP 列名
gapminder <- rename(gapminder, country_population = population, country_gdp = gdp)
```

> **注意：** 我们在上述命令中重命名了两列（population 和 gdp），并且在整个章节中将使用此更新后的 Gapminder DataFrame。

探索数据是在数据准备和核心分析阶段都要完成的任务之一。

# 选择列

当处理包含大量列的大型数据集时，定位相关列可能既耗时又令人不知所措。`select()` 函数通过指定列名，帮助您轻松地将数据集缩小到仅包含感兴趣的列。这将使您能够专注于分析中最相关的变量。

让我们探索一些可以向数据集提出的问题。

## 如何从数据集中选择 country、year、infant mortality 和 life expectancy 变量？

```r
# 选择 country、year、infant mortality 和 life expectancy 变量
gapminder_subset <- select(gapminder, country, year, infant_mortality, life_expectancy)

# base R 中的等效命令
gapminder_subset <- gapminder[, c("country", "year", "infant_mortality", "life_expectancy")]

# 方括号 [] 用于子集化数据。逗号 , 分隔行和列。在这种情况下，未指定行的条件，因此选择所有行。接下来，c() 函数创建一个我们想要保留的列名向量。最后，我们在方括号内使用列名向量来选择所需的列。
```

在该解决方案中，`select()` 创建了一个名为 `gapminder_subset` 的 DataFrame，并保留您感兴趣的变量：`country`、`year`、`infant_mortality` 和 `life_expectancy`。我们从数据集中排除了所有其他变量。

您在上述命令中选择了 `country` 和 `life_expectancy` 之间（含）的所有列。在这种情况下，您也可以使用以下代码检索这些列：

```r
# 选择 country 和 life_expectancy 之间（含）的所有列
gapminder_subset2 <- select(gapminder, country:life_expectancy)
```

您可以在 `select()` 中使用几个辅助函数：

*   `starts_with()`
*   `ends_with()`
*   `matches()`
*   `contains()`

这些函数让您能够快速匹配满足某些标准的较大变量块。有关更多详细信息，请参阅 `?select`。让我们检查其中几个：

## 如何从数据集中仅选择列名以字符串 country 开头的列？

```r
# 选择所有以 "country" 开头的列
gapminder_subset3 <- select(gapminder, starts_with("country"))
```

上述命令通过从原始 Gapminder DataFrame 中选择所有以单词 country 开头的列，创建了一个名为 `gapminder_subset3` 的新 DataFrame。

```r
# 检查数据框 gapminder_subset3 的列名
colnames(gapminder_subset3)
## "country" "country_population" "country_gdp"
```

`starts_with()` 函数在 `select()` 内部使用，用于选择以特定字符串开头的列。在本例中，它用于选择所有以单词 country 开头的列。

## 如何排除 continent 和 region 列？

```r
# 选择除 continent 和 region 之外的所有列
gapminder_subset4 <- select(gapminder, -continent, -region)
```

通过在我们想要消除的列名前放置一个减号（`-`），我们实际上是在指示 R 选择除指定列之外的所有列。

## 数据是针对哪些年份收集的？

您需要从 `year` 列中提取此数据。使用 `dplyr` 包，您可以使用两个主要函数来提取变量：`pull()` 和 `select()`。

```r
# 显示数据集中存在的唯一年份
unique(pull(gapminder, year))

## 1960 1961 1962 1963 1964 1965 1966 1967 1968 1969 1970 1971 1972 1973 1974 1975 1976 1977
## 1978 1979
## 1980 1981 1982 1983 1984 1985 1986 1987 1988 1989 1990 1991 1992 1993 1994 1995 1996 1997
## 1998 1999
## 2000 2001 2002 2003 2004 2005 2006 2007 2008 2009 2010 2011 2012 2013 2014 2015 2016
```

在上述命令中，`pull()` 函数将单个列作为向量提取。然后使用 `unique()` 函数仅提取该列中的唯一值，以查看数据集中的所有唯一年份。另一方面，如果您想将结果存储在 DataFrame 中，可以使用 `select()`，如以下命令所示：

```r
# 将数据集中存在的唯一年份存储在数据框中
unique_years <- unique(select(gapminder, year))

# 在这里，结果存储在数据框 unique_years 中，可以使用 View() 显示
View(unique_years)
```
