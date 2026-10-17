
WCSS = \sum_{P_i \in Cluster 1} distance(P_i, C_1)^2 + \sum_{P_i \in Cluster 2} distance(P_i, C_2)^2 + \sum_{P_i \in Cluster 3} distance(P_i, C_3)^2

其中 `$P_i$` 是`聚类`中的数据点，`$C_1, C_2, C_3$` 是质心。在上述公式中，`WCSS` 是每个数据点与其质心之间的平方和，其他项同理。为了测量数据点与质心之间的`距离`，可以使用任何方法，如*欧几里距离*或*曼哈顿距离*。

### 寻找聚类的最佳值，肘部法遵循以下步骤：

- [1]。在给定数据集上执行 `K-means` 聚类（K 值范围为 1-10）。
- [2]。对于每个 k 值，计算 `WCSS`。
- [3]。绘制 `WCSS` 值与`聚类数量`之间的曲线。
- [4]。图中像手臂一样的****转拐点**，该点被认为是 K 的最佳值。

由于图形显示出像肘部的尖角，因此被称为肘部法。肘部法的图右侧所示：

**最大聚类数量**：我们可以选择聚类数量等于给定数据点。如果聚类数量等于数据点，则 `WCSS` 的值变为零，这将是图表的端点。实际上，我们可以看到 `WCSS` 迅速下降，在某个数量后不再变化。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_146_0.png)

**WCSS 值是一个指标**：我们需要一个指标来理解或评估不同的聚类数量（最好是量化的）。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_146_1.png)

`WCSS` = $\sum_{P_i \in Cluster 1} distance(P_i, C_1)^2 \sum_{P_i \in Cluster 2} distance(P_i, C_2)^2 \sum_{P_i \in Cluster 3} distance(P_i, C_3)^2$

实际上，对于理解不同 `K-means` 聚类的拟合程度，这是一个很好的指标。让我们看看随着`增加聚类数量`，`WCSS` 将如何变化。如果我们在中间使用一个质心，每个数据点的距离都很大，平方距离将非常大。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_146_2.png)

如果我们有 2 个聚类，则平方距离会减少。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_147_0.png)

对于 3 个聚类，我们得到了减少的 `WCSS`。对于 4 或 5 个，质心越多，距离下降得越快（但在下降）。`WCSS` 随着 K 达到数据点数量趋于稳定。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_147_1.png)

`WCSS` = `distance(P1, C1)^2` + `distance(P1, C2)^2` + `distance(P1, C3)^2`

肘部法是一种帮助你决定 k（聚类数量）的方法。最后取决于你的决定。

## 4.1.5 Python 实现 K-means 聚类

**问题描述：** 我们有一个 `Mall_Customers` 数据集，是访问商场的数据。数据集中有 `Customer_Id`、`Gender`、`Age`、`Annual Income ($)` 和 `Spending Score`（在商场花费的计算值；花费得越多）。从这个数据集中，我们需要计算这种模式，因为它是一种无监督方法，所以我们不知道具体要计算什么。

### 聚类内误差和

### K-means 聚类

### 库

```python
import pandas as pd

import numpy as np

import matplotlib.pyplot as plt
```

### 导入数据

```python
dataset = pd.read_csv('Mall_Customers.csv')

X = dataset.iloc[:, [3, 4]].values
```

## 聚类没有 y

```python
# 使用肘部法寻找最佳聚类数量：WCSS
from sklearn.cluster import KMeans

wcss = []

for i in range(1, 11):
    #为聚类器设置参数
    cluster_elbow = KMeans(n_clusters=i, init='k-means++', random_state=0, max_iter=300, n_init=10)
    cluster_elbow.inertia_ = cluster_elbow.fit(X) # 拟合独立数据
    wcss.append(cluster_elbow.inertia_) # 捕捉每个 wcss 数据

# 惯性：到最近聚类中心的距离平方和。它实际上是 "wcss"
```

```python
# 可视化肘部
plt.plot(range(1, 11), wcss)
plt.title("The Elbow Method")
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.show()

# 从肘部图中获取最佳聚类数量
kmeans = KMeans(n_clusters=5, init='k-means++', random_state=0, max_iter=300, n_init=10)
y_kmeans = kmeans.fit_predict(X)

# 绘制聚类
plt.scatter(X[:, 0], X[:, 1], c=y_kmeans, s=50, cmap='viridis')
plt.scatter(kmeans.cluster_centers_[:, 0], kmeans.cluster_centers_[:, 1], s=300, c='red', label='Centroids')
plt.title("Clusters")
plt.xlabel("Annual income")
plt.ylabel("Spending score (1-100)")
plt.legend()
plt.show()
```

手肘法（The Elbow technique）：对于包含一个 1 到 10 个簇的循环，并计算每个簇的 `WCSS`（簇内误差和）。在创建 `WCSS` 值列表后，我们绘制手肘图（Elbow diagram），然后选择最佳的簇数量。

```python
# finding optimal number of clusters using elbow method : WCSS
from sklearn.cluster import KMeans

wcss = []

for i in range(1, 11):
    # setting cluster for cluster generator
    cluster_generator_elbow = KMeans(n_clusters=i, init='k-means', random_state=0, max_iter=300, n_init=10)
    cluster_generator_elbow.fit(data) # capturing inertia for each cluster i
    wcss.append(cluster_generator_elbow.inertia_)
    # Inertia : Sum of squared distances of samples to their closest cluster. Is actually "wcss"

plt.plot(range(1, 11), wcss, marker='o')
plt.title("The Elbow Method")
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.show()
```

我们创建该对象：

```
KMeans(n_clusters=i, init='k-means', random_state=0, max_iter=300, n_init=10)
```

`n_clusters`：要形成的簇数量以及生成的质心数量。对于手肘法，这是一个我们将使用的最终簇数量，我们将使用固定数量的簇。

- `init = 'k-means'`：是一种初始化方法。`k-means++` 以智能的方式为 `k-means` 聚类选择初始簇，以加速收敛。
- `n_init`：`k-means` 算法使用不同的质心种子运行的次数。最终结果将是 `n_init` 次连续运行中惯惯性（`inertia`）的最优输出。
- `max_iter`：单次运行中 `k-means` 算法的最大迭代次数。

在拟合（fitting）之后，我们使用以下代码提取 `WCSS` 值：

```python
cluster_generator_elbow.inertia_
```

`inertia_` : 样本到其最近簇的距离平方和。这实际上就是 "`wcss`"。

最佳簇数量：从手肘图中我们可以，如果簇的数量超过 5，`WCSS` 不会发生快速变化。因此这就是最佳簇数量。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_149_0.png)

从上面的图中，我们可以看到手肘点位于 5。因此，这里的簇数量将是 5。

## 使用最佳“n clusters”创建聚类

我们对 5 个簇对数据进行分析。我们可以使用 `fit_predict()` 来找到这些值。

由于我们已经有了簇的数量，现在我们可以在数据集上训练模型了。为了训练模型，我们将使用与上面部分相同的代码行，但不再使用 `i`，而是使用 `5`，因为我们知道需要形成 5 个簇。

```python
# creating cluster with optimal "clusters". From elbow-plot we get 5 the optimal number of clusters
k_mean_cluster = KMeans(n_clusters=5, init='k-means++', random_state=0, max_iter=300, n_init=10)
y_mean_cluster = k_mean_cluster.fit_predict(X)
```

- 第一行与上面 `KMeans` 类的其他部分相同。
在第二行代码中，我们创建了因变量 `y_mean_cluster`（我们也可以将其命名为 `y_predict`）来训练模型。通过执行上述代码行，我们将得到 `y_mean_cluster` 变量。我们可以在 Spyder IDE 的变量资源器中检查该变量。我们现在可以将 `y_mean_cluster` 的值与我们的原始数据集进行比较。请参考下面的图片。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_150_0.png)

- 从上面的图像，我们现在可以意识到 `CustomerID` 1 属于簇 3（索引从 0 开始），因此 2 将被视为 3，并属于簇 4，而不属于其他任何簇。

可视化聚类：在接下来的代码行中，我们为 1 到 5 的每个簇编写了代码。第一个 `plt.scatter`，即 `[X, y_k_mean_cluster == 0, 0]` 包含了特征匹配的 x 值以及范围从 0 到 4 的 `y_k_mean_cluster` 值。

```python
# clusters
plt.scatter(X[y_k_mean_cluster == 0, 0], X[y_k_mean_cluster == 0, 1], s=100, c='red', label='cluster 4')
plt.scatter(X[y_k_mean_cluster == 1, 0], X[y_k_mean_cluster == 1, 1], s=100, c='blue', label='cluster 2')
plt.scatter(X[y_k_mean_cluster == 2, 0], X[y_k_mean_cluster == 2, 1], s=100, c='green', label='cluster 3')
plt.scatter(X[y_k_mean_cluster == 3, 0], X[y_k_mean_cluster == 3, 1], s=100, c='cyan', label='cluster 4')
plt.scatter(X[y_k_mean_cluster == 4, 0], X[y_k_mean_cluster == 4, 1], s=100, c='pink', label='cluster 5')
```

```python
# centroids
plt.scatter(k_mean_cluster.cluster_centers[:, 0], k_mean_cluster.cluster_centers[:, 1], s=300, c='black', label='centroids')
```

```python
plt.title('Annual Income ($)')
plt.legend()
plt.show()
```
