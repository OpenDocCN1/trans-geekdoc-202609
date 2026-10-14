
PCA 用于特征工程，旨在将高维数据集转换为低维数据集，同时尽可能保留更多信息（方差）。在下图中，整个数据集[19](#chap06.xhtml#footnote-102) 经过 PCA 变换[20](#chap06.xhtml#footnote-101) 后被压缩并投影到二维空间：

![](images/fig-6-11.png)

在图中，显示的两个类别（黄点和紫点）分别对应正收益类和负收益类（上涨和下跌）。虽然存在某些区域主要由单一类别占据，显示出同质性，但这些类别仍然在很大程度上是交织混合的。

这一发现并不质疑 PCA 生成特征的实用性。明确地说，目标并非仅凭这种新的特征表示就完全解决分类问题。相反，我们的目标是通过引入原始数据集中不明显的信息，来辅助分类算法。

这些新的 PCA 特征随后可作为机器学习模型的输入，提供原始数据的一种降维且信息丰富的表示。在处理多重共线性[21](#chap06.xhtml#footnote-100) 或试图因高维度而提升算法性能时，这特别有用。

PCA 寻找原始特征的简单（线性）组合，因此如果类别在原始特征空间中不是线性可分的，PCA 可能无法实现清晰的分离。复杂金融数据通常就是这种情况。在这种情况下，各类别的点不会聚集在分离的区域中，但 UMAP 等方法可能会有所帮助。

### 基于 UMAP 的特征

与 PCA 通过简单变换捕捉全局数据结构不同，统一流形逼近与投影（UMAP）擅长同时保留数据的局部和全局结构，这使其特别适用于检测数据的潜在结构，如下图所示：

![](images/fig-6-12.png)

正如图中所示，UMAP 允许识别出某一类别占主导而另一类别缺失的明显区域。这种显著的分离符合 UMAP 明确展示类别间清晰区别的目标。因此，配备这种数据表示的分类算法将更容易完成分离任务。这种为便于算法处理而增强数据的做法，正是特征工程的核心作用。

UMAP 是一种复杂的技术，但我们可以依赖一个优雅简洁的 API[22](#chap06.xhtml#footnote-099) 来实现该算法：

```python
from umap import umap_ as UMAP

clusterable_embedding = UMAP.UMAP(n_neighbors=30, min_dist=0.0, n_components=8).fit_transform(vct_bin)

plt.scatter(clusterable_embedding[:, 0], clusterable_embedding[:, 1], c=y_test, s=20, cmap='viridis', alpha=0.4)

plt.legend(['-1', '1'])
```

只需这些代码行即可执行计算并展示结果。要集成 UMAP 特征，我们只需遵循前面为熵特征和 PCA 特征概述的流程。

让我们继续探索基于机器学习的特征创建。

### 基于决策树叶节点的特征

决策树叶节点索引提供了一种独特的特征提取方式，通过利用模型做决策时所走的路径。这种方法捕捉决策树处理数据的方式，将其内部决策过程转化为有用的数值表示。

下图展示了一棵经过训练[23](#chap06.xhtml#footnote-098) 用于分类 SPY 日收益率的决策树：

![](images/fig-6-13.png)

思路很简单：我们首先在数据集上训练一棵决策树。训练完成后，每个数据点通过从树根移动到叶节点、在每一步遵循决策规则来进行分类。关键洞见在于，数据点落入的特定叶节点包含关于其特征的宝贵信息。

要将其转化为特征，我们为每个叶节点分配一个唯一索引。然后为每个数据点创建一个新特征，指示其所属的叶节点。这种方法有效地将树结构转换为可作为其他机器学习模型输入的格式，增加了超越传统特征的新预测信息层。

Sklearn API 为实现这种特征工程方法提供了实用途径。训练好树后，我们只需使用 `apply` 方法，它方便地提供了我们想要的输出：从根节点通向决策叶节点的叶索引序列：

```python
# Get the leaf indices for each sample
leaf_indices_train = clf.apply(X_train)
leaf_indices_test = clf.apply(X_test)

# merge leaf indexes with other features
X_train = pd.DataFrame(np.hstack([X_train, pd.DataFrame(leaf_indices_train)]))
X_test = pd.DataFrame(np.hstack([X_test, pd.DataFrame(leaf_indices_test)]))

# Train a new model on the combined dataset
clf = RandomForestClassifier(max_depth=15)
clf.fit(X_train, y_train)
```

我们现已完成对特征工程的深入探索，展示了突破特征分析与处理边界的前沿方法（UMAP、分数阶差分等）。在构建并计算出数千个新特征后，下一步是减少特征数量。实现这一减少的各种技术是本章最后一节的主题。

## 特征选择

特征选择是识别并选择对模型最相关特征的过程。这有助于将输入变量减少到对预测最有用的那些，从而提高模型效率。

减少特征数量的重要性怎么强调都不为过。在高维数据集中，特征数量远超观测样本数量时，模型可能遭受过拟合和维度灾难。该术语描述了这样一种现象：特征空间变得如此之大，以至于可用数据变得稀疏。这种稀疏性使得模型难以有效学习。结果，模型过度贴合训练数据，在未见数据上表现不佳。

相反，特征过少可能导致欠拟合，即模型无法有效学习数据中的潜在模式。

找到正确的平衡是关键。一个常用的启发式规则是特征数量应显著少于观测样本数量。

虽然没有铁律，但观测样本数量是特征数量的 5-10 倍这一准则可以作为起点。

现在，让我们看看如何减少特征数量。

### 互信息作为特征选择方法

互信息统计量可以捕捉变量间任何类型的统计依赖关系。当且仅当两个随机变量相互独立时，它等于零；值越高意味着依赖性越强。

通过计算每个特征与目标变量之间的互信息统计量[24](#chap06.xhtml#footnote-097)，可以判断该特征是否包含足够的信息来预测结果。如果包含，则保留该特征；否则丢弃。

使用以下代码，针对该分类问题，我们根据互信息准则选择最优的 pct%（5%）特征：

```python
from sklearn.feature_selection import mutual_info_classif, RFE, SelectKBest

pct = 5

# Assuming you want to select pct% best features
k_best = int(pct / 100 * len(X_train.columns))

# Initialize SelectKBest with mutual information
sel2 = SelectKBest(mutual_info_classif, k=k_best)
sel2.fit(X_train, y_train)

# Get the boolean mask of selected features
```
