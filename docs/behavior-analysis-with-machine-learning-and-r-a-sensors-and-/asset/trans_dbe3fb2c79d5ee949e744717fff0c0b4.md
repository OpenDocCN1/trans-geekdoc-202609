

## 手势 1

![](img/91c149cc24c3e5af2971580c9dda9d8b_225_0.png)

图 7.9：手势 1 的 x 轴。

```r
library(heatmap)
heatmap(res$D, main="Distance matrix of gesture 1", cluster_row = FALSE,
cluster_col = FALSE,
legend = F,
color = colorRampPalette(c("white", "black"))(50)
```

从图 7.10 中我们可以看到对角线都是白色的。这些代表值为 0，即一个点与其自身之间的距离。除此之外，没有其他直观的模式可以寻找。现在，让我们绘制存储在 `res$RP` 中的复性图（recurrence plot）。

```r
heatmap(res$RP, main="RP with threshold = 0.5", cluster_row = FALSE,
cluster_col = FALSE,
legend = F,
color = colorRampPalette(c("white", "black"))(50)
```

## 手势 1 的距离矩阵

![](img/91c149cc24c3e5af2971580c9dda9d8b_226_0.png)

图 7.10：手势 1 的距离矩阵。

在这里，我们可以看到这是距离矩阵的一种倒置版本。现在，对角线是黑色的，因为小的距离被编码为1。还有一些点簇以及垂直水平线模式。如果我们想构建一个分类器，就不需要解释外星图像。我们只需要将每个距离矩阵或 RP 视为图像，并将它们直接输入到 CNN 中（CNN 将在第8章中介绍）。

最后，我们可以尝试看看改变阈值会发生什么。图 7.12 显示了两个 RP。在左图中，使用了 0.01 的小阈值。在这里，许多细节丢失了，并且出现了非常微小的距离。在右侧图中，使用了 1.5 的大阈值。在这里，图中堆满了黑色像素，使得很难观察到任何模式。另一方面，无论选择什么阈值，距离矩阵将保持不变。

```r
shiny_rp.R 这个 shiny 应用允许你选择手势，绘制它们对应的距离矩阵和复性图，并查看阈值如何影响最终结果。
```

## 阈值 = 0.5 的 RP

![](img/91c149cc24c3e5af2971580c9dda9d8b_227_0.png)

图 7.11：阈值为 0.5 的手势 1 的 RP。

![](img/91c149cc24c3e5af2971580c9dda9d8b_227_1.png)

## 第 7 章：行为数据编码

### 7.6 词袋（Bag-of-Words）

词袋（BoW）编码的主要思想是将复杂的实体表示为其组成部分的集合。它被称为“词袋”是因为它最早的应用之一是自然语言处理。假设有一组关于医学、艺术、工程等不同主题的文档，你想根据这些词汇自动对它们进行分类。在 BoW 中，每份文档都表示为一个表格，该表格包含所有文档中的唯一单词以及它们在每份文档中的相应计数。通过这种表示方法，可能会发现关于医学的文档中，“治疗（treatment）”、“诊断（diagnosis）”、“健康（health）等词的计数高于关于艺术或工程的文档。图 7.13 和 7.14 分别显示了概念视图和表格。

通过这些表示，现在构建文档分类器变得很容易。词频表可以作为输入特征向量。也就是说，特征向量中的每个位置代表一个单词，其值是代表该单词总数的整数。

> 注意，在实践中文档的长度各不相同，因此使用百分比而不是总计数是一个好主意。这可以通过将每个单词计数除以总计数来实现。还要注意，像 'the'、'is'、'it' 这样的频率词可能会引起问题，因此需要额外的预处理。这是一个简单的例子，但如果你对更高级的文本处理技术感兴趣，我推荐参考 Silge 和 Robinson (2017) 的《Text Mining with R: A Tidy Approach》一书。

BoW 也可以用于复杂场景下的图像分类。例如处理教室、公园、商店、街道等复合场景。首先，场景

![](img/91c149cc24c3e5af2971580c9dda9d8b_228_0.png)

图 7.13：两个文档作为 BoW 的概念视图。

| 单词 | 计数 |
|---|---|
| body | 1 |
| colors | 0 |
| diagnosis | 2 |
| health | 1 |
| hospital | 1 |
| idea | 0 |
| music | 0 |
| painting | 1 |
| patient | 0 |
| style | 0 |
| treatment | 2 |

| 单词 | 计数 |
|---|---|
| body | 1 |
| colors | 2 |
| diagnosis | 0 |
| health | 0 |
| hospital | 1 |
| idea | 1 |
| music | 1 |
| painting | 2 |
| patient | 0 |
| style | 1 |
| treatment | 0 |

图 7.14：两个文档作为 BoW 的表格。

