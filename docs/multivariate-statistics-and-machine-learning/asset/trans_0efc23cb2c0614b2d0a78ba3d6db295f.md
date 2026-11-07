
我们看到上面计算得到的度量（0.89）与我们的手工计算相符。如果在聚类之前已知真实标签，那么在本例中聚类纯度就很容易概念化，它本质上是在评估被正确聚类到其真实分类中的案例的总比例。例如，如果 *setosa* 有 50 个案例，并且所有这些案例都被聚类到“*setosa*”，那么这就构成了 *setosa* 的完美聚类纯度。*versicolor* 的聚类纯度就没有那么好了，因为本应进入 *versicolor* 的 50 个案例中，只有 48 个被归类到该类别。*Virginica* 的聚类纯度最差，只有 50 个中的 36 个。总体聚类纯度有效地汇总了这些类别特定的纯度比率。

我们还可以绘制最优聚类数目的组内平方和（代码取自 [Boehmke & Greenwell, 2020](#ref.xhtml#re_CIT000033)，第 409 页），如图 [图 14.2](#c14.xhtml#f14.2) 所示。函数 `fviz_nbclust()` 有助于可视化并确定最优聚类数目，其中 `get_dist` 计算距离函数，在本例中基于 `spearman` 的相关方法（其他选项包括 `pearson` 和 `kendall`、`minkowski` 等）；有关详情请参阅包 `factoextra`（[Kassambara & Mundt, 2017,](#ref.xhtml#re_CIT000182)）：

![图 14.2 随着聚类数目变化的组内平方和，有助于确定应保留的最优聚类数目。返回文本。⏎](images/fig14.2.jpg)

*图 14.2* 随着聚类数目变化的组内平方和，有助于确定应保留的最优聚类数目。[返回文本。⏎](#c14.xhtml#re_f14.2)

```
> library(factoextra)
> fviz_nbclust(iris.data,
+ kmeans,
+ k.max = 3,
+ method = “wss”,
+ diss = get_dist(iris.data, method = “spearman”))
```

从图中可以看出，理想的聚类数目是 2 或 3，其中 3 产生最低的组内平方和（`method = "wss"`）：

## 14.9 稀疏和纵向 `K`-均值

`k`-均值聚类有许多变体。例如，在 *稀疏聚类分析* 中，可以获得数据的排列，使得排列后数据集中特征彼此不相关 517with each other。在 R 中，稀疏聚类分析可使用 `KMeansSparseCluster()` 执行。纵向 `k`-均值也是可能的，其中聚类可以在连续时间点上进行追踪。R 中的 `kml` 包（[Genolini et al., 2024](#ref.xhtml#re_CIT000125)）可以在纵向数据上执行 `k`-均值。包 `longitudinalData`（[Genolini et al., 2024](#ref.xhtml#re_CIT000125)）也很实用，因为 `kml` 依赖于它。

## 14.10 层次聚类

如我们所见，在 `k`-族或 `k`-代表聚类中，聚类数目是 *a priori* 指定的。诸如 `k`-均值及其变体等方法依赖于距离矩阵来执行聚类。聚类的另一种方法是 *层次聚类*，其中聚类数目不是 *a priori* 请求的，而是算法会构建一棵树，即 *dendrogram*，该树显示了算法从单个案例到受某种最小化准则约束的案例融合集合的过程中所做的历史连接。可以采用多种连接方法来定义案例相似性，我们稍后会对其进行调查。层次聚类可以是凝聚的或分裂的。*凝聚聚类* 从单个案例开始，将案例融合在一起构建树状图。*分裂聚类* 从一个大簇开始，在每一步中将其分离成更小的簇。我们在这里只讨论凝聚情况，因为它是最常见的。

[图 14.3](#c14.xhtml#f14.3) 是一个简单树状图的示例，我们可以轻松地从下往上可视化案例在树状图中的合并历史。我们看到案例 2 和 3 最先被合并，随后这些案例与案例 4 合并。最后，由案例 2、3 和 4 组成的这个簇与案例 1 合并，形成了最大的簇。

![图 14.3 聚类分析树状图的示例，揭示了从下往上的连接历史。返回文本。⏎](images/fig14.3.jpg)

*图 14.3* 聚类分析树状图的示例，揭示了从下往上的连接历史。[返回文本。⏎](#c14.xhtml#re_f14.3)

如前所述，在融合案例和簇时可以使用竞争性的连接方法，包括 `complete`、`single`、`average` 和 `centroid` 方法，每种方法都有其优缺点。在单链接（文献中也称为 `MIN`）中，案例之间的最小距离被用作融合的标准，而在完全链接（文献中也称为 `MAX`）中，则采用案例之间最大最远距离。平均链接不出所料，取组间距离的平均值。单链接和完全链接中的树状图在成对不相似性的单调变换下是不变的，然而平均链接则不然（[Izenman, 2008](#ref.xhtml#re_CIT000167)）。这些并不是唯一可能的连接方法，但是最常见的。

有关层次聚类中使用的连接方法的良好讨论，请参阅 [Johnson and Wichern (2007)](#ref.xhtml#re_CIT000173)。目前的关键点是认识到采用不同的连接方法可能会导致不同的解决方案。

层次聚类在计算上可能很昂贵，因为它操作的是可能相当大的不相似性指数。层次聚类速度较慢可以被视为这种方法的缺点，也是凝聚方法更一般地被视为缺点，因为它们 518can be quite expensive since they require entire distance matrices as inputs。层次方法的另一个缺点是，与 `k`-代表聚类相反，最终解决方案中通常没有明确的单一优化标准或目标被优化（[Murphy, 2022](#ref.xhtml#re_CIT000259)）。此外，一旦案例被融合，就无法 *unfused*。相反，用户通常必须主要依靠实质理论来确定聚类解决方案是否成功。

### 14.10.1 Python 中的凝聚聚类

我们演示了在 iris 数据上使用 Python 的简单凝聚聚类例程：

```
import seaborn as sns
iris = sns.load_dataset(“iris”)
df = iris[[‘sepal_length’, ‘sepal_width’, ‘petal_length’, ‘petal_width’]]
iris.drop([‘species’], axis=1, inplace=True)
iris
```

我们生成变量之间的散点图系列（[图 14.4](#c14.xhtml#f14.4)）。

![图 14.4 鸢尾花数据特征的双变量散点图。此类图有助于可视化数据中暂定的双变量分组，虽然本身不是聚类分析，但在描述性层面上仍可能有助于预测聚类分离。鉴于对物种的先验知识，很容易清楚地看出 setosa 已经很好地从 virginica 和 versicolor 中分离出来。返回文本。⏎](images/fig14.4.jpg)

*图 14.4* 鸢尾花数据特征的双变量散点图。此类图有助于可视化数据中暂定的双变量分组，虽然本身不是聚类分析，但在描述性层面上仍可能有助于预测聚类分离。鉴于 *a priori* 知识，很容易清楚地看出 *setosa* 已经很好地从 *virginica* 和 *versicolor* 中分离出来。[返回文本。⏎](#c14.xhtml#re_f14.4)

```
import seaborn as sns
sns.pairplot(iris)
```

我们现在使用欧几里得距离执行单链接聚类分析：519

```
from sklearn.cluster import AgglomerativeClustering
groups = AgglomerativeClustering(n_clusters=3,
affinity=’euclidean’, linkage=’single’)
groups.fit_predict(iris)
```
