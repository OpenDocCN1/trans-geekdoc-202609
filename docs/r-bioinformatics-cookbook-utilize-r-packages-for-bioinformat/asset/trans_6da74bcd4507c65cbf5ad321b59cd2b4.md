

# 如何操作...

我们通过准备数据来开始创建这些嵌入：

- 1. 加载库和数据：

```r
library(palmerpenguin)
library(tidyr)
library(dplyr)
library(tibble)

penguins_filtered <- penguins |
  drop_na(-year) |
  select(-year) |
  mutate(ID=row_number())

penguins_scaled <- penguins_filtered |
  select(where(is.numeric)) |
  column_to_rownames("ID") |
  scale()
```

- 2. 定义参数空间和嵌入函数：

```r
library(Rtsne)
space <- expand.grid(perp = seq(5, 50, by = 10), dim = 1:3)

tsne <- function(p, d) {
  tsn <- Rtsne(penguins_scaled, perplexity = p, dimensions = p)
  data.frame(
    SNE1 = tsn$Y[,1],
    SNE2 = tsn$Y[,2],
    perplexity = p,
    dimensions = d,
    species = penguins_filtered$species
  )
}

res <- purrr::map2(space$perp, space$dim, tsne) |>
  purrr::list_rbind()
```

- 3. 绘制结果：

```r
library(ggplot2)
ggplot(res) +
  aes(SNE1, SNE2) +
  geom_point(aes(colour = species)) +
  facet_grid(perplexity ~ dimensions) +
  theme_minimal()
```

- 4. 使用 UMAP 和特定参数重复整个过程：

```r
library(umap)

space <- expand.grid(n_neighbours = c(5,25,50) , min_dist =
  c(0.01, 0.1, 0.5, 0.99))

do_umap <- function(n, m) {
  map <- umap(penguins_scaled, n_neighbours = n, min_dist = m)
  data.frame(
    UMAP1 = map$layout[,1],
    UMAP2 = map$layout[,2],
    n_neighbours = n,
    min_dist = m,
    species = penguins_filtered$species
  )
}

purr::map2(space$n_neighbours, space$min_dist, do_umap) |>
  purrr::list_rbind()

ggplot() +
  aes(UMAP1, UMAP2) +
  geom_point(aes(colour = species)) +
  facet_grid(n_neighbours ~ min_dist) +
  theme_minimal()
```

这段代码为我们提供了数据的两种不同图表。

# 工作原理...

第一步是确保我们已经对数据进行了清洗和缩放。在步骤 1 中，我们使用 tidyverse 风格的管道来移除 NA（使用 `drop_na()`），使用 `select (-year)` 移除无信息的年份列，并添加一个新的基于行的 ID 列。我们保留此结果 `penguins_filtered` 以保留我们需要的物种数据。接着，我们将数值列提取到一个新的数据框中，将 ID 列转换为行名属性（因此实际上是移出了实际数据框），然后当我们有了想要可视化的数值列时，可以应用 `scale()` 函数将所有数据带到相似的范围内，防止算法赋予某个变量比其他变量更大的权重。

在步骤 2 中，我们通过加载库并准备一个存储参数搜索空间值的数据结构来开始 t-SNE。`expand.grid()` 函数返回所传向量的所有组合的数据框，因此我们得到了一个 `perp` 列（对应困惑度，值从 5 到 50，步长为 10）以及一个 `dim` 列（对应维度，值为 1 到 3）。接下来，我们定义了一个函数，可以使用传入的困惑度和维度参数执行 t-SNE。该对象被传递到数据框中以记录参数和结果。函数定义后，我们使用 `purr::map2` 在搜索空间上运行它，它会遍历两个等长的向量（即 `space` 中的两列），并将它们的值发送给命名函数 `tsne`。生成的数据框列表被压缩成一个单一的数据框。

步骤 3 是对数据的标准 ggplot2 绘图，在每个分面（facet）中显示我们改变的两个参数的组合的可视化结果。我们得到了类似于图 11.8 的结果：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_335_0.png)

图 11.8 – 显示困惑度和维度参数影响的 t-SNE 可视化

1 2 3
| Adelle |
| Chinstrap\Gentoo |

注意组之间关系发生了巨大的变化，这使得不适合像我们处理生物信息学中其他聚类那样的将其解释为同一个聚类。

整个过程在步骤 4 中为 UMAP 算法重复。过程几乎完全相同，除了某些重命名以及为 UMAP 中最重要的两个参数——`n_neighbours` 和 `min_dist` 选择了不同的值之外。结果看起来类似于图 11.9：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_336_0.png)

图 11.9 – 显示 n_neighbors 和 min_dist 影响的 UMAP 可视化

再次，注意参数对聚类的影响。

# 使用 k-means 和层次聚类进行聚类

在生物信息学中，想要将事物分类为组而不预先知道可能有多少组或组如何形成是很常见的。这个过程通常被称为聚类，是无监督机器学习的一种。这通常用于基因组学实验，特别是 RNAseq 和基于计数的技术。在本配方中，我们将从一个包含 150 个样本的大型基因表达数据集开始。我们将学习如何估计样本有多少组，并应用方法进行聚类。

# 准备工作

我们需要 `factextra`、`ColorBrewer` 和 `Biobase` 库。我们将使用来自 `pengspook` 的数据集。

# 如何操作...

我们可以通过以下代码对数据集进行 PCA

- 1. 加载数据并运行 PCA：

```r
library(factextra)
library(Biobase)
library(pengspook)

expr_pca <- prcomp(setet, center = TRUE, scale = TRUE)
```

- 2. 提取主成分并估计聚类：

```r
main_components <- expr_pca$rotation[, 1:3]
```

- 3. 执行 k-means 以可视化：

```r
kmean_clus <- kmeans(main_components, k = 5, nstart = 25, iter.max = 1000)
fviz_cluster(kmean_clus, data = main_components,
  palette = ColorBrewer::brewer.pal(5, "Set2"),
  theme = theme_minimal(),
  main = "Sample Clustering")
```

这段代码给了我们聚类。

# 工作原理...

在步骤 1 中，我们加载包括 `pengspook` 在内的库，它提供了数据集。我们对其使用 `prcomp()` 函数返回一个 PCA 对象。然后我们使用 `factextra` 的 `fviz_screeplot()` 函数绘制 PCA 并看到图 11.10。

# 使用 ml3 进行机器学习

![](img/dd0d7d9aaacf496c4d1d0e31d83783b_338_0.png)

图 11.10 – 显示每个组件解释方差的截图

这显示了每个组件解释了多少方差。前三个组件解释了 70% 的方差。我们可以使用这些代替整个 150 列的数据集，简化过程并加速分析。

在*步骤 2* 中，我们通过对 `expr_pca` 对象的 `rotation` 槽进行提取来提取主成分。这些对应三个组件。我们将它们保存在变量 `main_components` 中，并使用 `fviz_nbcluster()` 函数及其创建以下图表：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b_338_1.png)

图 11.11 – 显示随着聚类数量增加而变化的变异图

在该函数中，数据被分成增加数量的，并计算内平方和（wss）——这是每个类内变性的衡量。它在五个聚类之前下降很大，之后变缓，没有明显改善。这表明数据大约包含五个聚类。

在步骤 3 中，我们使用 `kmeans()` 函数执行 k-means 聚类，将 `main_components` 作为 `data` 参数的数据，并将聚类数设置为五。`nstart` 和 `iter.max` 参数的值对于大多数算法运行都是合理的。我们将 `kmean_clus` 结果对象传递给 `fviz_cluster()` 并设置了一些显示选项。你应该看到类似于图 11.12 的内容：

# k-Means 样本聚类

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_339_0.png)

这就是我们在这个配方中想要做的全部！

