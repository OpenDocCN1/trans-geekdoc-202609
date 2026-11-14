
停止标准可以通过以下任一方式定义。当数据点重新分配到不同簇的数量为零或达到最小值时，我们可以停止迭代。我们也可以将停止标准定义为：质心没有变化（或变化最小），或者以误差形式定义为平方误差和（`SSE`）的最小减少量，这将在下一节定义。

### 9.11.3 评估 `k-Means` 簇

最常用的度量是平方误差和（`SSE`）。其定义如下：

对于每个点，误差是到最近簇的距离（公式 9.7），

$$
{SSE} = \sum\limits_{i = 1}^{N}\sum\limits_{x \in {CL}_{i}}\text{dist}\left( x,C_{i} \right)^{2}
$$

`CL[i]` 是第 `i` 个簇，`C[i]` 是簇 `CL[i]` 的质心（`CL[i]` 中所有数据点的均值向量），`dist(x, C[i])` 是数据点 `x` 与质心 `C[i]` 之间的距离。

给定两个聚类结果（聚类是形成的簇的集合），我们可以选择误差最小的那个。减少 `SSE` 的一个直接方法是增加 `N`，即簇的数量。

### 9.11.4 `k-Means` 的优缺点

`k-means` 的主要优点是易于理解和实现。`k-means` 被认为是一种线性时间算法。如果使用 `SSE`，它会在局部最优处终止。然而，寻找全局最优很复杂，这是它的弱点之一。

其他弱点包括：仅适用于可定义均值概念的数据、需要指定 `k` 的值、不同的初始化（质心选择）会产生不同的聚类结果、以及对异常值敏感。

## 9.12 簇有效性

簇验证对于比较聚类算法、确定簇的数量、比较两个簇、比较两组簇以及避免在噪声中发现模式非常重要。良好的聚类被定义为：类内相似性高、类间相似性低的聚类。聚类质量取决于待聚类实体的表示和所使用的相似度度量。

簇验证涉及使用外部指数评估聚类，方法是将聚类结果与 `ground truth`（外部已知结果）进行比较。仅使用数据而*不*参考外部信息来评估簇的质量，称为使用内部指数的评估。

### 9.12.1 与 `Ground Truth` 比较

只有给定 `ground truth` 时，才能使用 `precision` 和 `recall` 进行简单的聚类评估。[图 9.12](#ch9.xhtml#fig9_12) 展示了一个示例，其中总共有 7 只蝙蝠和 7 个球。聚类产生两个簇：簇 1 包含 7 只蝙蝠和 2 个球，簇 2 仅包含 5 个球。在此背景下，`precision` 和 `recall` 由公式 (9.8) 和 (9.9) 给出：

$$
\text{Precision} = \frac{\text{the number of items of a particular category obtained in the cluster}}{\text{total number of items in that cluster}}
$$

![图 9.12 聚类的精确率和召回率。](images/fig9_12_B.jpg)

[图 9.12 聚类的精确率和召回率。](#ch9.xhtml#R_fig9_12)

$$
\text{Recall} = \frac{\text{the number of items of a particular category obtained in the cluster}}{\text{total number of items in that category}}
$$

接下来讨论另一种方法，假设数据集有 `N` 个对象。令 `G` 为 “ground truth” 簇的集合，`C` 为从聚类算法获得的簇的集合。有两个 `N` × `N` 的对象矩阵，分别对应 `G` 簇和 `C` 簇。如果对应该条目的行和列对象在 `C` 中属于同一簇，则 `G` 矩阵中的条目为 1，否则为 0。任何一对数据对象都属于以下类别之一：`SS`，如果两个矩阵中的条目一致且为 1；`DD`，如果两个矩阵中的条目一致且为 0；`SD`，如果两个矩阵中的条目不一致，且 `C` 中为 1、`G` 中为 0；`DS`，如果两个矩阵中的条目不一致，且 `C` 中为 0、`G` 中为 1。基于这些矩阵定义了两个评估度量：`Rand index` 和 `Jaccard coefficient`（公式 9.10 和 9.11）。

$$
\text{Rand} = \frac{\mid \text{Agree} \mid}{\mid \text{Agree} \mid + \mid \text{Disagree} \mid} = \frac{\mid {SS} \mid + \mid {DD} \mid}{\mid {SS} \mid + \mid {SD} \mid + \mid {DS} \mid + \mid {DD} \mid}
$$

$$
\text{Jaccard coefficient} = \frac{\mid {SS} \mid}{\mid {SS} \mid + \mid {SD} \mid + \mid {DS} \mid}
$$

### 9.12.2 基于纯度的度量

接下来讨论另一种用于寻找外部指数的方法。[图 9.13](#ch9.xhtml#fig9_13) 给出了混淆矩阵。令 `n` = 数据点数量，`K` = 簇总数，`L` = “ground truth” 类总数，`m[i]` = 簇 `i` 中的点数，`c[j]` = 类 `j` 中的点数，`n[ij]` = 属于类 `j` 的簇 `i` 中的点数，`p[ij]` = `n[ij]`/`m[i]` = 簇 `i` 中的元素被分配到类 `j` 的概率。熵和纯度可以针对单个簇或聚类（完整的簇集合）进行度量。簇的熵基于簇 `i` 中的元素被分配到类 `j` 的概率 `p[ij]`（公式 9.12）。

![图 9.13 混淆矩阵。](images/fig9_13_B.jpg)

[图 9.13 混淆矩阵。](#ch9.xhtml#R_fig9_13)

$$
\text{Entropy of a cluster } i:e_{i} = - \sum\limits_{j = 1}^{L}p_{ij}\log p_{ij}.
$$

聚类的熵基于每个簇的平均熵以及数据集中对象的总数 `n`（公式 9.13）。

$$
\text{Entropy of a clustering}:e = \sum\limits_{i = 1}^{K}\frac{m_{i}}{n}e_{i}
$$

簇 `i` 的纯度是使概率 `p[ij]` 最大的类 `j`，即簇 `i` 中的元素被分配到类 `j` 的概率（公式 9.14）。

$$
\text{Purity of a cluster } i:p_{i} = \max\limits_{j}p_{ij}
$$

聚类 `C` 的纯度由公式 (9.15) 给出：

$$
\text{Purity of a clustering}:p\left( C \right) = \sum\limits_{i = 1}^{K}\frac{m_{i}}{n}p_{i}
$$

### 9.12.3 内部度量

如前所述，内部度量用于在不与外部信息比较的情况下评估聚类。基本上考虑两个方面：`cohesion`（凝聚度）度量簇内数据点的紧密程度，而 `separation`（分离度）度量簇间数据点的分离程度。

簇凝聚度由公式 (9.16) 给出：

$$
{WSS} = \sum\limits_{i}\sum\limits_{x \in C_{i}}\left( x - m_{i} \right)^{2}
$$

簇分离度按如下方式度量（公式 9.17）：

$$
{BSS} = \sum\limits_{i} \mid C_{i} \mid \left( m - m_{i} \right)^{2}
$$

其中 `|C[i]|` 是簇 `i` 的大小，`m` 是整个数据集的质心。

## 9.13 维度灾难
