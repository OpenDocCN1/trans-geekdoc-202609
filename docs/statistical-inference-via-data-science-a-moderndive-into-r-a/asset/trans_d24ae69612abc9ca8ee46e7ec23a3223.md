

## 2.9 结论

先写数据（data）后写 `aes()` 映射，你可以省略参数名 `data` 和 `mapping` 的显式声明。

在本书的后续内容中，所有的 `ggplot()` 代码将采用第二种形式：即省略 `data =` 和 `mapping =` 的显式命名，并遵循参数的默认顺序。我们这样做是为了简洁；在审阅其他 R 用户的代码时，这种风格非常常见。

### 2.9.3 额外资源

所有学习检查（Learning checks）的答案都可以在书籍在线版的附录中找到。附录从 https://modernndive.com/v2/appendix 开始。

本章中使用的所有 R 代码的脚本文件可以在 https://www.modernndive.com/v2/scripts/02-visualization.R 获取。

如果你想解锁 RStudio 的“ggplot2 Data Visualization with ggplot2”速查表（cheatsheet），这份图表总结的内容比我们在本章讨论的要多。特别是，它展示了比本章涵盖的 5 个几何对象更多的对象，同时提供了快速且易读的视觉描述。对于所有的几何对象，它还列出了可以调整的所有可能的审美属性。在 2024 年中的当前的 RStudio 版本中，你可以通过 RStudio 菜单栏 -> Help -> Cheatsheets -> Data Visualization with ggplot2 访问此表。或者，你也可以通过此链接6 进入 ggplot2 的 Github 页面预览该表。

> 6https://github.com/rstudio/cheatsheets/blob/main/data-visualization-2.1.pdf

### 2.9.4 展望

回想第 2.3 节中的图 2.2，我们视觉化了 Envoy Air 航班的部门与延迟之间的关系，而不是所有航班。这些数据保存在 `modernndive` 包的 `envoy_flights` 数据框中。

实际上，`envoy_flights` 数据框只是 `nycflights3` 包中 `flights` 数据框的一个子集，由所有 2023 年从纽约出发的航班组成。我们使用以下代码通过 `dplyr` 包进行数据包装创建了 `envoy_flights`：

```r
library(dplyr)

envoy_flights <- flights |
  filter(carrier == "MQ")

ggplot(data = envoy_flights, mapping = aes(x = dep_delay, y = arr_delay)) + 
  geom_point()
```

## 2 数据可视化

这段代码获取了 `flights` 数据框并使用 `filter()` 仅返回 `carrier` 等于“MQ”（Envoy Air 的载运代码）的 357 行。（回想第 1.2 节，相等性测试使用 `==` 而不是 `!=`）。然后代码使用赋值运算符 `<-` 将输出结果循环写到一个新数据框 `envoy_flights` 中。

同样，回想第 2.4 节中的图 2.7，我们视觉化了纽瓦克机场（Newark airport）2023 年 1 月前 15 天的每小时风速记录。这些数据保存在 `modernverse` 包的 `early_january_2023_weather` 数据框中。

实际上，`early_january_2023_weather` 数据框只是 `nycflights3` 包中 `weather` 数据框的一个子集，包含了 2023 年纽约三个城市的所有每小时天气观测数据。我们使用以下 `dplyr` 代码创建了 `early_january_2023_weather`：

```r
early_january_2023_weather <- weather |
  filter(origin == "EWR" & month == 1 & day <= 15)

ggplot(data = early_january_2023_weather, aes(x = time_hour, y = temp)) + 
  geom_line()
```

这段代码将 `weather` 数据框解析为新的数据框 `early_january_2023_weather`，其中仅包含 `origin == "EWR"`、`month == 1` 且小于或等于 15 的每小时风速记录。

这两段代码是对第 3 章使用 `dplyr` 包进行数据清洗（data wrangling）的预览。数据清洗是转换和修改现有数据的过程，其目的是使其更符合分析目的。例如，这两段代码使用了 `filter()` 函数，通过选择现有数据框（`flights` 和 `weather`）的行子集创建了新的数据框（`envoy_flights` 和 `early_january_2023_weather`）。在下一章中，我们将正式介绍 `filter()` 和其他数据清洗函数，以及管道运算符 `|>`，后者允许你将多个数据清洗操作组合成单一的顺序操作链。进入第 3 章：数据清洗！

## 3 数据清洗

在目前为止旅程中，我们已经学习了如何在第 1 章中通过 `glimpse()` 和 `View()` 函数查看保存在数据框中的数据，以及如何在第 2 章中使用 `ggplot2` 包创建数据可视化。特别是，我们研究了我们所谓的“五种命名图表”（5NG）：

- 1. 通过 `geom_point()` 创建散点图
- 2. 通过 `geom_line()` 创建折线图
- 3. 通过 `geom_boxplot()` 创建箱线图
- 4. 通过 `geom_histogram()` 创建直方图
- 5. 通过 `geom_bar()` 或 `geom_col()` 创建柱状图

我们使用图形句法（grammar of graphics）创建了这些可视化内容，它将数据框中的变量映射到 5 个几何对象之一的审美属性。我们还可以控制几何对象的其他审美属性，例如图 2.1 中 Gapminder 数据示例中的大小和颜色。

在本章中，我们将引入来自 `dplyr` 包的一系列用于数据清洗的函数，它们允许你处理数据框以满足你的需求。函数包括：

- 1. `filter()` 筛选数据框的行以选出子集。例如，筛选 `alaska_flights` 数据框。
- 2. `summarize()` 对一个或多个列进行汇总统计。正如我们在第 2.7 节的箱线图中看到的分组统计数据。
- 3. `group_by()` 将行分组。例如，为每个机场分别计算 `dep_delay` 的平均值。
- 4. `mutate()` 根据现有列/变量创建新列。例如，将华氏温度转换为摄氏度。
- 5. `arrange()` 对行进行排序。例如，按 `temp` 排序天气数据。
- 6. `join()` 根据“键”变量与另一个数据框连接。换句话说，合并这两个数据框。

DOI: 10.12011/978103224546-3

注意我们如何使用 `computer_code` 字体来描述我们要对数据框执行的操作。这是因为用于数据清洗的 `dplyr` 包具有直观命名的函数，易于记忆。

学习使用 `dplyr` 进行数据清洗的进一步好处是它与数据库语言 SQL¹（读作 sequel 或字母拼写 S-Q-L，全称为结构化查询语言）相似，SQL 被广泛用于高效管理大量数据库。虽然 SQL 是书籍或数据库管理课程的主题，但请记住，学会了 dplyr，就能轻松学习 SQL。我们将讨论它们的相似之处。

## 需要的包

加载本章所需的包（假设你已经安装了它们）。如果需要，请阅读第 1.3 节关于如何安装和加载 R 包的信息。

```r
library(dplyr)
library(ggplot2)
library(nycflights)
```

## 3.1 管道运算符：|>

在开始数据清洗之前，让我们首先介绍一种自 2021 年 5 月起成为 R 的一部分的巧妙工具：管道运算符 `|>`；原生管道允许我们将 R 中的多个操作组合成单一的顺序操作链。在现代 R 中，原生管道运算符 `|>` 现在是函数链的默认方式，取代了以前随 `dplyr` 包加载的 tidyverse %>%。`|>` 在 R 4.1.0 中引入，为数据清洗和其他任务提供了更直观、易读的语法，消除了对额外包依赖的需求。

你可能会在旧脚本或在线搜索中看到使用 %>% 的 R 代码，但本书中我们将使用 `|>`。如果你在其他代码中看到它，请担心。

让我们从一个假设的示例开始。假设你想对一个假设的数据框 `x` 使用假设函数 `f()`、`g()` 和 `h()` 执行一组假设的操作序列：

