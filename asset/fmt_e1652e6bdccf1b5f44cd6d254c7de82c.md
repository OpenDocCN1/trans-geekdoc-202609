
学习并熟练掌握快捷键值得花费时间，这能提高您的工作效率和流程效率。如果您想个性化外观，RStudio 提供了大量选项。请转到 `Tools | Global Options | Appearance` 探索各种选择。

## 包

当您下载并安装 R 时，它附带一组默认函数，可用于各种用途。然而，随着全球 R 社区开发新的函数和功能，将它们全部纳入核心软件包已变得不切实际。相反，许多函数被捆绑到包中，可根据需要下载和安装，以解决这一问题。

R 包是函数、数据集和文档的集合，旨在协同工作。例如，一些包专门用于数据整理，而另一些则专门用于数据可视化。

例如，安装一个包就像为您的汽车订购一项新功能，例如导航系统。您不能立即使用它，因为您需要先安装它。一旦新功能安装在您的车上，您就可以打开并使用它。

同样，要使用一个新的 R 包，您首先需要使用 `install.packages()` 函数将其安装在您的计算机上。此外，您还需要使用 `library()` 函数将包加载到您的工作会话中，以访问它提供的新函数和功能。

就像您可以在车上安装多个功能，但在特定时间只开启您需要的那些一样，您可以在计算机上安装多个 R 包，但只为特定项目加载所需的包。下图展示了汽车显示系统和车载导航应用的示意图：

![](img/Figure2.6.png)

图 2.6：汽车显示系统中的显示系统和导航应用

例如，要安装 `lubridate` 包（包含处理日期的实用函数），您只需将包名 `lubridate` 作为字符串参数传递给该函数：

```r
# install the lubridate package
install.packages("lubridate")
```

包下载并安装完成后，您可以使用 `library()` 函数将其加载到 R 会话中：

```r
# load the lubridate package
library(lubridate)
```

加载后，您就可以在代码中使用该包提供的函数，就像使用任何其他 R 函数一样。

> **注意：** R 中的井号（`#`）是注释符号。请为您的代码添加注释，以阐明每部分代码的功能。如果您这样做，其他人（以及未来的您自己！）会更容易理解您的代码。

有几个良好的实践可以帮助您更高效、更有效地使用包。

*   **在脚本开头加载包**：最好在脚本开头加载您将要使用的所有包。这将确保在代码运行前安装并加载所有必要的包，避免因缺少依赖项而导致的潜在错误或问题。
*   **定期更新包**：R 社区不断更新和改进包，因此保持包的更新很重要。您可以通过定期运行 `update.packages()` 函数来实现这一点，该函数将检查已安装包的更新并安装任何可用的新版本。
*   **注意包的依赖关系**：某些包可能依赖于其他包，这意味着您需要安装并加载这些依赖包，才能使用您想要的包。

## 避免命名空间冲突

如果您使用来自多个包且名称相同的函数，可能会遇到命名空间冲突。为避免这种情况，您可以使用 `::` 运算符来指定要使用哪个包的函数。例如，不使用 `summarize()`，而是可以使用 `dplyr::summarize()` 来指定要使用 `dplyr` 包中的 `summarize()` 函数。

## 工作目录

使用 R 时，保持文件井然有序至关重要。这意味着为您正在处理的每个项目创建一个文件夹，并将相关文件保留在该文件夹中。R 工作目录是 R 默认启动时所在的文件夹。

R 使用您计算机上的一个指定文件夹（称为工作目录）来定位与特定项目相关的文件。在这里，R 查找要加载的文件并保存文件。在不同的计算机上，您的工作目录位置可能不同，并且一次只能打开一个工作目录。要确定当前工作目录，可以运行以下代码：

```r
### 查看当前工作目录
getwd()
## “C:/Users/Hp/Documents”
```

在整理数据集时，您有两个选择：第一，将文件放入您的工作目录中；第二，将工作目录更改为存储文件的文件夹。您可以使用函数 `setwd()` 并指定新工作目录的文件路径，将工作目录修改为计算机上的任意文件夹。请看以下示例：

```r
### 设置工作目录
setwd(“E:/Book_Project”)
```

从菜单栏，您可以点击 `Session | Set Working Directory | Choose Directory`（会话 | 设置工作目录 | 选择目录）来更改工作目录。要查看工作目录中的文件，可以使用函数 `list.files()`。

在 R 中读写文件时，注意您的工作目录至关重要。如果您不在正确的文件夹中工作，可能会遇到错误或覆盖现有文件。保持文件井然有序并适当设置工作目录，可确保您的 R 代码具有可复现性，且易于与他人共享。

## 对象

让我们回到 Aarya 的例子。为了分析她的 Netflix 使用情况，Aarya 首先必须理解 R 中对象的概念。对象是一种通过将数据存储在指定名称内来保存数据的方式，该名称可用于调用存储的数据。所有数据都存储在对象中，范围从简单的数字或字符串到复杂的结构，如统计分析摘要和绘图。

为了继续她的分析，Aarya 创建了三个不同的 R 对象，分别称为 `hours_watched_movies`、`hours_watched_tv` 和 `total_hours_watched`，以分别保存她观看电影、电视节目以及观看 Netflix 总共花费的小时数。有了这些对象，Aarya 可以执行许多操作来高效地分析她的数据。要将名称分配给数字，您可以使用赋值运算符：`<-`（`<` 和 `-` 之间无空格）。请看以下示例：

```r
# 定义 hours_watched_movies
hours_watched_movies <- 6

# 存储观看电视节目所花费的时间（小时）
hours_watched_tv <- 12

# 将总花费时间（小时）保存到 total_hours_watched
total_hours_watched <- 18
```

要检查 `total_hours_watched` 对象中存储的内容，Aarya 只需在 R 控制台中输入其名称 `total_hours_watched`，它将在下一行显示对象值：

```r
# 显示存储在 total_hours_watched 中的值
total_hours_watched
## 18
```

> **注意：** 全书中，R 代码的输出将后跟 `##`。

现在，让我们看看 Aarya 如何创建各种 R 对象并为它们赋值，以高效地分析她的数据。

## 向量

向量是相同数据类型元素的集合。向量可以包含数字、字符或逻辑值，但不能包含这些数据类型的混合。向量是 R 最基本的数据结构，用于许多不同的目的，例如存储数据或执行数学运算。向量可以被视为一维数组，向量中的每个元素都有一个索引或位置。理解如何创建和操作向量至关重要，因为它们是更复杂的数据结构和分析的基础。让我们进一步了解其中一些类型的向量。

### 数值向量

Aarya 可以使用数值向量来存储她在 Netflix 上观看的每部电影或电视节目的时长。例如，她可以创建一个名为 `movie_durations` 的数值向量，并将她观看的每部电影的时长分配给它。例如：

```r
# 创建观看电影时长的向量
movie_durations <- c(98, 109, 124, 138, 115, 149)

# 打印 movie_durations
movie_durations
## 98 109 124 138 115 149
```

这将创建一个名为 `movie_durations` 的数值向量，包含 6 个元素，分别代表她观看的每部电影的时长（以分钟为单位）。`c()` 用于创建向量或将两个或更多向量连接在一起。`c()` 函数代表 combine（合并）或 concatenate（连接），是 R 中最常用的函数之一。

### 字符向量

字符向量存储一系列字符值。字符值是您想要存储的任何文本，例如单词、句子或单个字符。您可以使用 `c()` 函数通过用引号括起值来创建字符向量。例如，Aarya 创建一个字符向量来存储她观看的电影：

```r
# 创建观看电影标题的向量
movie_titles <- c(“Rush Hour”, “Knight and Day”, “The Notebook”, “Shutter Island”, “Now you see me”, “The Da Vinci Code”)

# 打印 movie_titles
movie_titles
## “Rush Hour” “Knight and Day” “The Notebook”
## “Shutter Island” “Now you see me” “The Da Vinci Code”
```

> **注意：** 字符串是字符向量的单个组成部分。因此，如果您将数字用引号括起来，例如：`1`，它将仅被视为字符向量。任何被引号括起来的内容都被视为字符串。

现在，如果 Aarya 想知道她上个月看了多少部电影，她可以使用 `length()` 函数来确定该向量中有多少个元素，如以下示例所示：

```r
# 计算 movie_titles 中的元素数量
num_movie_titles <- length(movie_titles)

# 打印结果
cat(“Number of movies watched on Netflix last month:”, num_movie_titles)
## Number of movies watched on Netflix last month: 6
```

### 逻辑向量

R 形式的布尔数据是存储 `TRUE` 和 `FALSE` 的逻辑向量。指示 Aarya 在给定日期是否观看了电影的向量显示如下：

```r
# 创建逻辑向量 watched
watched <- c(TRUE, FALSE, TRUE, FALSE, TRUE, TRUE, FALSE)

# 打印 watched
watched
## TRUE FALSE TRUE FALSE TRUE TRUE FALSE
```

对于指示 Aarya 是否在给定类型中观看了电影的向量：

```r
# 创建向量 genre
genre <- c(“Action”, “Action”, “Romance”, “Thriller”, “Thriller”, “Thriller”)

# 检查电影是否属于 “Thriller”
watched_thriller <- genre == “Thriller”

# 打印 watched_thriller
watched_thriller
## FALSE FALSE FALSE TRUE TRUE TRUE
```

对于指示 Aarya 对电影或电视节目给出“赞”或“踩”评分的向量：

```r
# 创建向量 rating
rating <- c(“Thumbs Up”, “Thumbs Down”, “Thumbs Down”, “Thumbs Up”, “Thumbs Up”, “Thumbs Up”)

# 检查电影是否被评为 “Thumbs Up”
watched_good <- rating == “Thumbs Up”

# 打印 watched_good
watched_good
## TRUE FALSE FALSE TRUE TRUE TRUE
```

R 中最常用的逻辑运算符有：

| 运算符 | 含义 |
| :--- | :--- |
| `==` | 等于 |
| `!=` | 不等于 |
| `<` | 小于 |
| `>` | 大于 |
| `<=` | 小于或等于 |
| `>=` | 大于或等于 |
| `&` | 逻辑与 |
| `\|` | 逻辑或 |
| `!` | 逻辑非（取反） |

**表 2.2：R 语言中使用的逻辑运算符**

## 属性

属性是与 R 对象关联的附加信息。它们提供关于对象的元数据，例如名称、维度、类或描述其属性的其他信息。属性不影响对象的行为，但有助于组织和操作数据。

例如，当 Aarya 创建向量或矩阵时，她可以为对象分配属性来描述其属性。她可以使用 `names()` 为向量元素分配名称，使用 `dim()` 为矩阵分配维度，或使用 `class()` 函数为对象分配类，以指示其数据类型或结构。

通过使用属性，Aarya 可以跟踪数据的结构和属性，这有助于她更有效地操作和分析数据。属性在 R 编程中也起着至关重要的作用，因为许多函数和操作使用它们来确定如何处理或转换数据。下文将进一步讨论不同类型的属性。

### 名称

`names()` 函数为向量、列表或数组的元素分配或检索名称。它是组织数据并使其更易于理解的宝贵工具。

例如，让我们创建一个包含 Aarya 上周观看的所有电视节目及其各自观看时长的向量：

```r
# TV Shows watched
tv_shows_names <- c("Breaking Bad", "Money Heist", "The office", "Suits", "The Last Kingdom")

# time spent on watching each TV show in minutes
duration <- c(120, 142, 64, 90, 185)

# adding and accessing attributes
# assign names to duration
names(duration) <- tv_shows_names
```

现在，`duration` 拥有名称属性：

```r
# print names and attributes of the vector duration
names(duration)
## "Breaking Bad" "Money Heist" "The office" "Suits" "The Last Kingdom"

attributes(duration)
## $names
## "Breaking Bad" "Money Heist" "The office" "Suits" "The Last Kingdom"
```

每当我们打印 `duration` 向量时，R 都会在 `duration` 元素上方显示节目名称：

```r
# print duration
duration
## Breaking Bad Money Heist The office Suits The Last Kingdom 
## 120 142 64 90 185
```

### 维度

`dim()` 函数通过分配维度属性将向量转换为 n 维数组。为此，您可以将 `dim()` 设置为长度为 n 的向量，其中 n 是您希望数组拥有的维度数。这允许您重塑和操作存储在向量中的数据，以适应特定的矩阵或数组结构。

例如，Aarya 想要将她的 `duration` 向量转换为一个 5 X 1 矩阵（5 行 1 列）。她使用以下代码创建它：

```r
# set the dimension of the vector
dim(duration) <- c(5, 1)

# print duration vector
duration
##      [,1]
## [1,]  120
## [2,]  142
## [3,]   64
## [4,]   90
## [5,]  185
```

R 始终将 `dim` 中的第一个值视为行数，第二个值视为列数。在任何涉及行和列的 R 操作中，行总是排在第一位。

## 矩阵

矩阵是只能容纳同类数据的二维数组。您可以将矩阵视为一组长度相同、按矩形模式排列的向量。`matrix()` 方法用于构建矩阵。

您可以使用 `matrix()` 创建矩阵，并通过将 `nrow` 参数设置为数字来指定行数。然后 `matrix()` 会将您的向量组织成具有指定行数的矩阵。例如，让我们用一个数值向量创建一个矩阵并将 `nrow` 设置为 3：

```r
# create a matrix 
simple_matrix <- matrix(1:6, nrow = 3)

# print simple_matrix
simple_matrix
##      [,1] [,2]
## [1,]    1    4
## [2,]    2    5
## [3,]    3    6
```

假设 Aarya 记录了周六和周日观看不同电视剧的小时数。接下来，Aarya 创建一个矩阵来展示她的数据：

```r
# create a vector with the duration of TV shows in hours
tv_duration <- c(2, 1, 2, 3)

# create a matrix with a number of hours spent watching each TV shows
tv_matrix <- matrix(tv_duration, nrow = 2, ncol = 2, byrow = TRUE)

# assign row and column names
# setting the vector tv_shows_names vector which we created earlier as rownames
rownames(tv_matrix) <- c("Breaking Bad", "Money Heist")

# assign column names
colnames(tv_matrix) <- c("Saturday", "Sunday")

# print tv_matrix
tv_matrix
##         Saturday Sunday
## Breaking Bad      2      1
## Money Heist       2      3
```

默认情况下，`matrix()` 按列填充矩阵，如果您想按行填充，可以将参数 `byrow` 设置为 `TRUE`。现在 Aarya 可以使用 `dim()` 方法获取矩阵的维度：
