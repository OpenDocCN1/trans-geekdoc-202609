
如果 `U` 和 `V` 的维度相同且等于 `n`，则线性变换 `T` 可以表示为一个 `nxn` 可逆矩阵（即它有逆矩阵）。如果 `V` 的维度小于 `U` 的维度，则线性变换 `T` 涉及一个 `投影`。如果 `V` 的维度大于 `U` 的维度，则变换 `T` 涉及一个 `嵌入`。

例如，如果 `T` 将二维欧几里得空间中向量的分量放大两倍，那么 `T` 可以用以下矩阵表示：

![image](images/585-01.jpg)

如果 `T` 将二维空间中向量的第一个分量减半，第二个分量三倍化，那么 `T` 可以用以下矩阵表示：

![image](images/585-02.jpg)

如果 `T` 将形如 `(x,y,z)` 的向量映射到形如 `(x,y,0)` 的向量，那么 `T` 是一个 `投影`，`T` 可以用以下矩阵表示：

![image](images/585-03.jpg)

根据本节开头关于线性变换定义的内容，`PCA` 是一个 `linear` 维度降低算法，而 `kernel PCA` 是一个 `non-linear` 维度降低算法。

`Linear` 维度降低涉及计算特征的线性组合或执行线性变换。例如，将一组基向量通过非奇异矩阵进行线性变换。具体来说，假设集合 `B` 中的向量集合 {`v1`, `v2`, . . . , `vn`} 是正交的，并且它们构成 `n` 维向量空间 `V` 的基底。此外，假设 `M` 是一个 `nxn` 非奇异矩阵（其行列式不为零）。那么 {`Mv1`, `Mv2`, `Mvn`} 是对基底 `B` 的线性变换，它同样跨越向量空间 `V`。

相比之下，`nonlinear (NL)` 维度降低技术执行非线性变换。然而，在许多情况下，`NL` 维度降低技术与线性方法相关，它们倾向于属于以下两类之一：

*   `NL` 技术提供高到低的映射（或反之亦然）

*   `NL` 技术提供可视化

`Mapping` 方法用于执行初始特征提取步骤，之后机器学习算法可以进行模式识别。然而，提供可视化的 `NL` 技术会涉及物体之间距离的计算。

## 距离度量类型

`Nonlinear` 维度降低技术也可以使用不同的距离度量。例如，`linear` 维度降低技术可以使用 `Euclidean` 距离度量（基于勾股定理）。但是，要测量球体或其他曲面上两个点之间的距离，需要使用不同的距离度量。在 `NLP` 的情况下，使用 `cosine similarity` 度量来测量词嵌入（即代表单词或 token 的浮点数向量）之间的距离。

`Distance` 度量用于测量物理距离，下面列出了一些常见的 `distance` 度量：

*   `Euclidean` 距离

*   `Manhattan` 距离

*   `Chebyshev` 距离

`Euclidean` 算法也满足 `triangle inequality`（三角不等式），即在欧几里得平面的任何三角形中，任意两边之和必须大于第三边的长度。

在球面几何中，可以定义两点之间的距离为经过这两点的大圆弧（当两点对应的弧不同长时，总是选择较短的那个弧）。

除了物理度量外，还有实现“编辑距离”（即字符串之间的距离）的算法，如下列出：

*   `Hamming` 距离

*   `Jaro–Winkler` 距离

*   `Lee` 距离

*   `Levenshtein` 距离

*   `Mahalanobis` 距离度量

*   `Wasserstein` 度量

`Mahalanobis` 度量基于一个有趣的想法：给定一个点 `P` 和一个概率分布 `D`，该度量衡量点 `P` 与分布 `D` 之间有多少个标准差。关于 `Mahalanobis` 的更多信息见：

*[https://en.wikipedia.org/wiki/Mahalanobis\_distance](https://en.wikipedia.org/wiki/Mahalanobis_distance)*

在拓扑学分支中，`metric space` 是一个集合，其中集合中所有成员之间的距离都被定义。根据拓扑类型，可使用多种度量（如 `Hausdorff` 度量）。

`Wasserstein` 度量衡量两个在度量空间 `X` 上的概率分布之间的距离。该度量也称为“earth mover’s metric”（地球移动距离），原因如下：给定两个单位土堆，它衡量将一个土堆移动到另一个土堆上的最小成本。

`KL` divergence（Kullback-Leibler 差异）在表面上与 `Wasserstein` 度量相似，但两者有重要区别。具体而言，`Wasserstein` 度量具有以下性质：

*   它是度量。

*   它是对称的。

*   它满足三角不等式。

然而，`KL` divergence 具有以下性质：

*   它不是度量（它是偏差）。

*   它不对称：`KL(P,Q) != KL(Q,P)`。

*   它不满足三角不等式。

注意，`JS`（Jenson-Shannon）偏差（基于 `KL` 偏差）是一个真正的度量，这使得它可以与其他度量（如 `Wasserstein` 度量）进行更有意义的比较。

## 其他著名距离度量

第 [9](#ch09.xhtml) 章节讨论了推荐系统，这些系统涉及在用户或项目之间找到相似性并进行推荐。可用的相似度量包括项目相似度量、基于用户的 Jaccard 相似度量以及用于比较数值向量的余弦相似度量。下面的子节介绍了这些相似度量。

另一个著名的距离度量是所谓的“出租车”度量，也称为 `Manhattan` 距离度量。给定在矩形网格中的两点 `A` 和 `B`，出租车度量计算从 `A` 到 `B` 必须经过的“块”数量（另一方向的出租车度量值相同）。例如，如果你需要先向北走两个块，然后向东走三个块，那么曼哈顿距离是 5。

事实上，还有许多其他度量可供查询，可通过搜索 Wikipedia 获取更多信息。在 `NLP` 中，最常用的距离度量是两个向量的余弦相似度，它来源于两个向量内积（dot product）的公式。

### Pearson Correlation Coefficient

*Pearson similarity* 是两个向量之间的 Pearson 系数。给定随机变量 `X` 和 `Y`，以及以下术语：

`std(X)` = `X` 的标准差  
`std(Y)` = `Y` 的标准差  
`cov(X,Y)` = `X` 与 `Y` 的协方差  

则 Pearson 相关系数 `rho(X,Y)` 定义如下：

![image](images/588-01.jpg)

请注意，Pearson 系数仅适用于同类型的项目。关于 Pearson 相关系数的更多信息见：

*[https://en.wikipedia.org/wiki/Pearson\_correlation\_coefficient](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient)*

### Jaccard Index (or Similarity)

`Jaccard similarity` 基于拥有评级的项目 `A` 和 `B` 的用户数量除以拥有评级的项目 `A` 或 `B` 的用户总数。`Jaccard` 相似度基于句子中唯一的单词，不受重复影响，而 `cosine` 相似度基于所有单词向量的长度（添加重复会改变长度）。是否重要取决于是否需要考虑单词重复。

下面的 Python 方法展示了如何计算两个句子的 Jaccard 相似度：

