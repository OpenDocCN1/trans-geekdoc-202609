

# 避免命名空间冲突

如果您使用来自多个包且名称相同的函数，可能会遇到命名空间冲突。为避免这种情况，您可以使用 `::` 运算符来指定要使用哪个包的函数。例如，不使用 `summarize()`，而是可以使用 `dplyr::summarize()` 来指定要使用 `dplyr` 包中的 `summarize()` 函数。

# 工作目录

使用 R 时，保持文件井然有序至关重要。这意味着为您正在处理的每个项目创建一个文件夹，并将相关文件保留在该文件夹中。R 工作目录是 R 默认启动时所在的文件夹。

R 使用您计算机上的一个指定文件夹（称为工作目录）来定位与特定项目相关的文件。在这里，R 查找要加载的文件并保存文件。在不同的计算机上，您的工作目录位置可能不同，并且一次只能打开一个工作目录。要确定当前工作目录，可以运行以下代码：

```
# 查看当前工作目录
getwd()
## “C:/Users/Hp/Documents”
```

在整理数据集时，您有两个选择：第一，将文件放入您的工作目录中；第二，将工作目录更改为存储文件的文件夹。您可以使用函数 `setwd()` 并指定新工作目录的文件路径，将工作目录修改为计算机上的任意文件夹。请看以下示例：

```
# 设置工作目录
setwd(“E:/Book_Project”)
```

从菜单栏，您可以点击 **Session | Set Working Directory | Choose Directory**（会话 | 设置工作目录 | 选择目录）来更改工作目录。要查看工作目录中的文件，可以使用函数 `list.files()`。

在 R 中读写文件时，注意您的工作目录至关重要。如果您不在正确的文件夹中工作，可能会遇到错误或覆盖现有文件。保持文件井然有序并适当设置工作目录，可确保您的 R 代码具有可复现性，且易于与他人共享。

# 对象

让我们回到 Aarya 的例子。为了分析她的 Netflix 使用情况，Aarya 首先必须理解 R 中对象的概念。对象是一种通过将数据存储在指定名称内来保存数据的方式，该名称可用于调用存储的数据。所有数据都存储在对象中，范围从简单的数字或字符串到复杂的结构，如统计分析摘要和绘图。

为了继续她的分析，Aarya 创建了三个不同的 R 对象，分别称为 `hours_watched_movies`、`hours_watched_tv` 和 `total_hours_watched`，以分别保存她观看电影、电视节目以及观看 Netflix 总共花费的小时数。有了这些对象，Aarya 可以执行许多操作来高效地分析她的数据。要将名称分配给数字，您可以使用赋值运算符：`<-`（`<` 和 `-` 之间无空格）。请看以下示例：

```
# 定义 hours_watched_movies
hours_watched_movies <- 6

# 存储观看电视节目所花费的时间（小时）
hours_watched_tv <- 12

# 将总花费时间（小时）保存到 total_hours_watched
total_hours_watched <- 18
```

要检查 `total_hours_watched` 对象中存储的内容，Aarya 只需在 R 控制台中输入其名称 `total_hours_watched`，它将在下一行显示对象值：

```
# 显示存储在 total_hours_watched 中的值
total_hours_watched
## 18
```

> **注意：** 全书中，R 代码的输出将后跟 `##`。

现在，让我们看看 Aarya 如何创建各种 R 对象并为它们赋值，以高效地分析她的数据。

# 向量

向量是相同数据类型元素的集合。向量可以包含数字、字符或逻辑值，但不能包含这些数据类型的混合。向量是 R 最基本的数据结构，用于许多不同的目的，例如存储数据或执行数学运算。向量可以被视为一维数组，向量中的每个元素都有一个索引或位置。理解如何创建和操作向量至关重要，因为它们是更复杂的数据结构和分析的基础。让我们进一步了解其中一些类型的向量。

## 数值向量

Aarya 可以使用数值向量来存储她在 Netflix 上观看的每部电影或电视节目的时长。例如，她可以创建一个名为 `movie_durations` 的数值向量，并将她观看的每部电影的时长分配给它。例如：

```
# 创建观看电影时长的向量
movie_durations <- c(98, 109, 124, 138, 115, 149)

# 打印 movie_durations
movie_durations
## 98 109 124 138 115 149
```

这将创建一个名为 `movie_durations` 的数值向量，包含 6 个元素，分别代表她观看的每部电影的时长（以分钟为单位）。`c()` 用于创建向量或将两个或更多向量连接在一起。`c()` 函数代表 combine（合并）或 concatenate（连接），是 R 中最常用的函数之一。

## 字符向量

字符向量存储一系列字符值。字符值是您想要存储的任何文本，例如单词、句子或单个字符。您可以使用 `c()` 函数通过用引号括起值来创建字符向量。例如，Aarya 创建一个字符向量来存储她观看的电影：

```
# 创建观看电影标题的向量
movie_titles <- c(“Rush Hour”, “Knight and Day”, “The Notebook”, “Shutter Island”, “Now you see me”, “The Da Vinci Code”)

# 打印 movie_titles
movie_titles
## “Rush Hour” “Knight and Day” “The Notebook”
## “Shutter Island” “Now you see me” “The Da Vinci Code”
```

> **注意：** 字符串是字符向量的单个组成部分。因此，如果您将数字用引号括起来，例如：`1`，它将仅被视为字符向量。任何被引号括起来的内容都被视为字符串。

现在，如果 Aarya 想知道她上个月看了多少部电影，她可以使用 `length()` 函数来确定该向量中有多少个元素，如以下示例所示：

```
# 计算 movie_titles 中的元素数量
num_movie_titles <- length(movie_titles)

# 打印结果
cat(“Number of movies watched on Netflix last month:”, num_movie_titles)
## Number of movies watched on Netflix last month: 6
```

## 逻辑向量

R 形式的布尔数据是存储 `TRUE` 和 `FALSE` 的逻辑向量。指示 Aarya 在给定日期是否观看了电影的向量显示如下：

```
# 创建逻辑向量 watched
watched <- c(TRUE, FALSE, TRUE, FALSE, TRUE, TRUE, FALSE)

# 打印 watched
watched
## TRUE FALSE TRUE FALSE TRUE TRUE FALSE
```

对于指示 Aarya 是否在给定类型中观看了电影的向量：

```
# 创建向量 genre
genre <- c(“Action”, “Action”, “Romance”, “Thriller”, “Thriller”, “Thriller”)

# 检查电影是否属于 “Thriller”
watched_thriller <- genre == “Thriller”

# 打印 watched_thriller
watched_thriller
## FALSE FALSE FALSE TRUE TRUE TRUE
```

对于指示 Aarya 对电影或电视节目给出“赞”或“踩”评分的向量：

```
# 创建向量 rating
rating <- c(“Thumbs Up”, “Thumbs Down”, “Thumbs Down”, “Thumbs Up”, “Thumbs Up”, “Thumbs Up”)

# 检查电影是否被评为 “Thumbs Up”
watched_good <- rating == “Thumbs Up”

# 打印 watched_good
watched_good
## TRUE FALSE FALSE TRUE TRUE TRUE
```

R 中最常用的逻辑运算符有：

| Operators | Description |
| --- | --- |

