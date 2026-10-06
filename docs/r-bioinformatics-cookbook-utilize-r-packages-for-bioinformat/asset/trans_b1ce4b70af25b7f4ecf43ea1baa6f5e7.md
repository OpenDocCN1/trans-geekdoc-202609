

- 3. 在多列上分组并汇总：

```r
genes_df |>
  group_by(chromosome_id, strand) |>
  summarise(
  num_genes = n(),
  avg_length = mean(length)
)
```

- 4. 对嵌套数据框（nested dataframe）操作：

```r
# 创建一个嵌套数据框
chromosome_id <- c(1,1,1,2,2,3,3)
gene_id <- c("A1","A2","A3","B1","B2","C1","C2","C3")
strand <- c("forward","reverse","forward","forward","reverse",
"forward","reverse","reverse")
length <- c(2000,1500,3000,2500,2000,1000,3000)
genes_df <- data.frame(chromosome_id, gene_id, strand, length)
```

```r
genes_df$samples <- list(data.frame(sample_id=1:2,
expression=c(2,3)),
data.frame(sample_id=1:3,
expression=c(3,4,5)),
data.frame(sample_id=1:2,
expression=c(4,5)),
data.frame(sample_id=1:3,
expression=c(5,6,7)),
data.frame(sample_id=1:2,
expression=c(6,7)),
data.frame(sample_id=1:2,
expression=c(1,2)),
data.frame(sample_id=1:2,
expression=c(2,3)),
data.frame(sample_id=1:2,
expression=c(3,4)))
```

```r
genes_df |>
  tidyr::unnest() |>
  group_by(chromosome_id, strand) |>
  summarise(mean_expression = mean(expression))
```

这些是在 dplyr 中使用“拆分-应用-合并”（split-apply-combine）的广泛示例。

# 工作原理……

第 1 步显式地创建一个数据框；我们这样做是为了能够方便地理解它的结构。

在第 2 步中，我们使用了最简单的方法：`group_by()` 函数用于根据 `chromosome_id` 对数据框的行进行分组，我们使用 `summarise()` 返回汇总数据框。第 3 步类似，但展示了如何使用分组列来创建更细粒度的分组，以及如何应用多个汇总函数。

第 4 步较为复杂；新的数据框是一个嵌套数据框，样本列表列在每个单元格中包含一个表达的数据框。在嵌套数据框上使用 `group_by()` 函数时，你首先需要使用 `tidyr::unnest()` 函数访问嵌套数据，然后像往常一样分组。注意，当使用 `tidyr::unnest()` 时，新数据框的每个基因、每个样本会有多行，因此通过感兴趣的列对数据框进行分组非常重要。

# 使用 datapasta 从复制的数据创建 R 对象

将数据粘贴到源代码文档中出于各种原因非常有用，其中最重要的是它允许创建一个可重复的示例，也称为 reprodex——一个演示问题或概念的最小化、自包含的示例。通过将数据包含在源代码中，其他人可以运行代码并亲眼看到结果，从而更容易理解和复制结果。

R 的 datapasta 包可以方便地将数据粘贴到 R 源代码文档中。它提供了一系列将数据转换为 R 定义的函数，在代码示例、测试或共享时创建静态对象时非常有用。在本教程中，你将学习如何使用 datapasta 将外部数据带入你的源代码文档中，而不是通过长期输入。

# 准备工作

我们将使用 `datapasta` 包，尽管它是非标准的。使用此命令：

```r
renv::install("datapasta", repos = c(mm = "https://ilesmcbain.universe.dev",), getOption("repos"))
```

这应该使用 `renv` 安装该包并让我们准备就绪。如果你还没有 `renv`，请按通常方式安装它。

# 如何操作……

datapasta 工具是以 RStudio 插件（add-in）的形式实现的，因此我们首先进行该设置：

- 1. 使用 RStudio 的 **Tools（工具） | Addins（插件） | Browse Addins（浏览插件）** 菜单，然后选择 **Keyboard Shortcuts（快捷键）**。你可以选择想要用于粘贴的组合键。

- 2. 点击操作旁边的中间列（如下截图所示），并按下你想要的按键。*图 2.1* 中的组合是一个不错的选择：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_63_0.png)

图 2.1 – 选择快捷键

- 3. 获取一个网页表格——例如，访问 **Wikipedia（维基百科）** 此页面：`https://en.wikipedia.org/wiki/Tab-separated_values`——使用浏览右键 **Copy（复制）** 功能复制整个文本示例表格。这会将文本表格放入你的剪贴板缓冲区中。它看起来应该像*图 2.2 所示：*：

# 示例 [编辑]

iris 数据集的头部可以使用以下纯文本存储为 TSV（注意，HTML 渲染可能会将制表符转换为空格）：

| Sepal length | Sepal width | Petal length | Petal width | Species |
|---|---|---|---|---|
| 5.1 | 3.5 | 1.4 | 0.2 | I. setosa |
| 4.9 | 3.0 | 1.4 | 0.2 | I. setosa |
| 4.7 | 3.2 | 1.3 | 0.2 | I. setosa |
| 4.6 | 3.1 | 1.5 | 0.2 | I. setosa |
| 5.0 | 3.6 | 1.4 | 0.2 | I. setosa |

上面的 TSV 纯文本对应于以下表格：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_64_0.png)

- 4. 将剪贴板中的新行粘贴到 R 源代码文档中。在合适的位置放置输入光标。

