

[5] 随着重新分配的完成，我们将再次回到步骤 4，即寻找新的质心或 K 点。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_143_0.png)

[6] 我们将通过寻找质心的重心来重复这一过程，因此新的质心如右侧图像所示：

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_143_1.png)

[7] 当我们获得新的质心后，将再次绘制中位线并重新分配数据点。因此，图像如下：

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_143_2.png)

[8] 我们可以从上面的图中看到，在线的两侧都没有不相似的数据点，这意味着我们的模型已经形成。考虑下图：

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_143_3.png)

[9] 我们的模型已经就绪，现在现在可以移除假设的质心，最终的两个聚类如下所示：

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_143_4.png)

## 4.1.3 K-Means 随机初始化陷阱

考虑以下散点图。我们有两个由 **x** 和 **y** 坐标表示变量。假设我们要选择聚类。看起来你在这里可以很容易识别出它们。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_144_0.png)

如果我们选择 K = 3 个聚类...

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_144_1.png)

- 所以，如果我们在**正确的位置**选择了**正确的随机初始化**，这就是最终结果。

- 然而，如果我们选择**不同位置**的**质心**，我们将得到不同的结果。遵循算法的步骤，我们将得到如下结果：

步骤 1：选择聚类数量 K：K = 3

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_144_2.png)

- [1] 绘制中位线
- [2] 对点分组

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_144_3.png)

- [3] 寻找新的质心
- [4] 然后将质心分配到新位置：
  步骤 4：计算并放置每个聚类的新质心

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_144_4.png)

## 真实聚类
## 错误聚类

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_145_0.png)

你可以看到这三个聚类是不同的，因此，在算法开始时对质心的选择可能会决定算法的结果。这不是一件好事，因为质心是随机选择的。

**K-means++**：这是对 **K-means 算法**的一种改进，它允许你正确地选择质心，并被称为 **K-means++**。

**Python Scikit-learn 库可以自动处理这一点：** 从上面我们可以看出这显然是一个陷阱。但我们不需要担心这个，因为 Python 对这种 k-means 算法的实现可以自动处理这种“陷阱”情况。好消息是，**K-means++** 算法会在 R、Python 或你使用的任何工具的后台运行，你[不需要]实际去实现它。

## 4.1.4 肘部法（Elbow-Method）：选择 K（正确的聚类数量）

k-means 聚类算法的性能高度取决于它所形成的聚类的效率。但*选择最佳聚类数量*是一项巨大的任务。有许多不同的寻找*最佳聚类数量*的方法，但在这里我们讨论的是寻找聚类数量或值的最合适方法。该方法如下：

**肘部法：**肘部法是寻找*最佳聚类数量*最流行的方法之一。这种方法使用了 **WCSS** 的概念。**WCSS 是聚类内误差和**，它定义了聚类内的*总变异*。计算 **WCSS（针对 k 个聚类）**值的方法如下：

```
WCSS = \sum_{P_i \in Cluster 1} distance(P_i, C_1)^2 + \sum_{P_i \in Cluster 2} distance(P_i, C_2)^2 + \sum_{P_i \in Cluster 3} distance(P_i, C_3)^2
```

其中 $P_i$ 是**聚类**中的数据点，$C_1, C_2, C_3$ 是质心。在上述公式中，WCSS 是每个数据点与其质心之间的平方和，其他项同理。为了测量数据点与质心之间的**距离**，可以使用任何方法，如*欧几里距离*或*曼哈顿距离*。

寻找聚类的最佳值，肘部法遵循以下步骤：

- [1]。在给定数据集上执行 **K-means** 聚类（K 值范围为 1-10）。
- [2]。对于每个 k 值，计算 WCSS。
- [3]。绘制 WCSS 值与**聚类数量**之间的曲线。
- [4]。图中像手臂一样的****转拐点**，该点被认为是 K 的最佳值。

由于图形显示出像肘部的尖角，因此被称为肘部法。肘部法的图右侧所示：

**最大聚类数量**：我们可以选择聚类数量等于给定数据点。如果聚类数量等于数据点，则 WCSS 的值变为零，这将是图表的端点。实际上，我们可以看到 WCSS 迅速下降，在某个数量后不再变化。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_146_0.png)

**WCSS 值是一个指标**：我们需要一个指标来理解或评估不同的聚类数量（最好是量化的）。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_146_1.png)

WCSS = $\sum_{P_i \in Cluster 1} distance(P_i, C_1)^2 \sum_{P_i \in Cluster 2} distance(P_i, C_2)^2 \sum_{P_i \in Cluster 3} distance(P_i, C_3)^2$

实际上，对于理解不同 K-means 聚类的拟合程度，这是一个很好的指标。让我们看看随着**增加聚类数量**，WCSS 将如何变化。如果我们在中间使用一个质心，每个数据点的距离都很大，平方距离将非常大。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_146_2.png)

如果我们有 2 个聚类，则平方距离会减少。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_147_0.png)

对于 3 个聚类，我们得到了减少的 WCSS。对于 4 或 5 个，质心越多，距离下降得越快（但在下降）。WCSS 随着 K 达到数据点数量趋于稳定。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_147_1.png)

WCSS = distance(P1, C1)^2 + distance(P1, C2)^2 + distance(P1, C3)^2

肘部法是一种帮助你决定 k（聚类数量）的方法。最后取决于你的决定。

## 4.1.5 Python 实现 K-means 聚类

**问题描述：** 我们有一个 Mall_Customers 数据集，是访问商场的数据。数据集中有 Customer_Id、Gender、Age、Annual Income ($）和 Spending Score（在商场花费的计算值；花费得越多）。从这个数据集中，我们需要计算这种模式，因为它是一种无监督方法，所以我们不知道具体要计算什么。

```python
# 聚类内误差和
# K-means 聚类

# 库
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# 导入数据
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

