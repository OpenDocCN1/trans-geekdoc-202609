
这次我们指定了聚类的位置，并将中心（x 和 y 值）作为 2D 数组传递，且点数等于聚类的数量。我们可以使用 `scatter()` 散图来查看数据

```python
In [3]: X1 = dt[:,0]
X2 = dt[:,1]
pyplot.scatter(X1,X2)
```

Out[3]: <matplotlib.collections.PathCollection at 0x1dbd820e

![](img/d75fea3635f5553f1cb0585b399b1b4b_181_0.png)

现在我们可以使用 MeanShift 算法创建一个聚类模型，并传递我们的 `dt` 数据

```python
In [4]: Clstr = MeanShift()
Clstr.fit(dt)
```

```
Out[4]: MeanShift()
```

我们创建了 `MeanShift` 类的 `Clstr` 对象，并通过 `fit()` 方法传递了数据。你可能注意到，我们并没有像使用 K-Means 算法那样在数据集中指定聚类的数量。现在，让我们找到算法预测的聚类数量，并绘制由我们的 MeanShift 算法分类的聚类

```python
In [5]: labels = Clstr.labels_
cen = Clstr.cluster_centers_
n_clusters = len(numpy.unique(labels))
print("Estimated No. of Clusters:", n_clusters)
colors = 10*['r', 'g', 'b']
for i in range(len(dt)):
    pyplot.plot(dt[i][0], dt[i], colors[labels[i]])
    plt.scatter(cen[i,0],cen[i,1], marker='x',color='k',s=100,zorder=10)
```

Estimated No. of Clusters: 3

Out[5]: <matplotlib.collections.PathCollection at 0x1dbd92972

![](img/d75fea3635f5553f1cb0585b399b1b4b_182_0.png)

如所示，`Clstr` 在我们的数据集中预测了 3 个聚类，即这是正确的。我们通过 `labels_` 属性提取了每个数据点的标签，并用它来绘制聚类。然后我们通过 `Clstr` 类的 `cluster_centers_` 属性找到了聚类中心或质心，即它们的 x 和 y 值。聚类的长度（x 和 y 值，即 2D 数组）代表了 `Clstr` 预测的聚类数量。接着，使用 for 循环绘制了聚类（注意使用 `labels` 为不同聚类的不同数据点着色），我们还使用 `scatter()` 图绘制了聚类中心，并指定 `zorder` 为 10 以将其绘制在最前面

那么，尽管我们没有预先指定聚类的数量，MeanShift 算法是如何找到聚类的呢？

首先，它将每个数据点分配到自己的类中。然后算法将计算质心并改变新质心的位置。

这个过程将不断迭代并移动到高密度区域，直到质心达到无法进一步移动的位置。

# 层次聚类

顾如名，层次聚类是聚类的一种形式，将数据集像树一样分为若干组或类别，可以是单个数据点，也可以是单个聚类

层次聚类分为以下两种：

- 凝聚法（Agglomerative）：层次聚类的一种类型，其中每个单独的数据点被视为一个聚类，然后合并或汇合成 2 个、4 个、8 个聚类，反之亦然，直到形成包含整个数据集的聚类

![](img/d75fea3635f5553f1cb0585b399b1b4b_183_0.png)

- 划分法（Divisive）：凝聚法的相反，将整个数据集视为一个聚类，然后将其分为单个数据点。

# 整个数据集聚类形状

![](img/d75fea3635f5553f1cb0585b399b1b4b_184_0.png)

分裂法是凝聚法的相反，将数据集视为一个聚类，然后将其分为单个数据点。让我们创建一个层次模型来观察它的运行。我们将使用用于决策树分类算法（第145页）的 `flavours.csv` 数据集。

进入你的 Jupyter notebook 并导入以下模块

```python
In [1]: import pandas
import numpy
from sklearn.cluster import AgglomerativeClustering
from matplotlib.pyplot as plt
from scipy.cluster.hierarchy import dendrogram
from sklearn.preprocessing import LabelEncoder
```

在创建模型之前，我们需要使用 `LabelEncoder` 对口味标签进行编码。我们将导入数据并对其编码

| In [2]: |
| :--- |
| `dt = pandas.read_csv('flavour.csv')` |
| `Enc = LabelEncoder().fit(dt['Flavour'])` |
| `dt['Flavour'] = Enc.transform(dt['Flavour'])` |

现在我们可以创建我们的凝聚式层次聚类 `Clstr` 模型。我们将使用年龄和口味数据。

| In [3]: |
| :--- |
| `X = dt.drop(columns='Gender')` |
| `Clstr = AgglomerativeClustering(distance_threshold=0, n_clusters=None)` |
| `Clstr.fit(X)` |

| Out[3]: AgglomerativeClustering |
