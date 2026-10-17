
`Out[16]`: `(-5.0, 5.0)`

![](img/d75fea3635f5553f1cb0585b399b1b4b_166_0.png)

如你所示，我们在线条周围绘制了间隔以寻找最近的支持向量。间隔非常宽，因为数据簇之间较远。

我们采取的方法与之前相同，绘制了包含数据簇、分离线的图表，然后使用 `fill_between()` 函数创建了这些间隔。我们传递了其中一个 X 轴和两个 Y 轴的值来填充它们，以表示间隔。我们不需要 `edgecolor`，填充颜色设为黑色，`alpha` 为 0.4（透明度）。

现在我们可以从 `sklearn.svm` 导入 `SVC` 支持向量分类器来创建我们的模型。

```
In [36]: from sklearn.svm import SVC
SVC(kernel='linear')
fit(X, y)
[36]: SVC(kernel='linear')
```

让我们创建一个函数，使用我们的模型来绘制最大间隔超平面和支持向量。

```
In [40]: def MMH(model, ax=None, plot_support=True):
## 2-D 图绘制
if ax is None:
 ax = ax.gca()
xlim = ax.get_xlim()
ylim = ax.get_ylim()
### 创建网格
x = numpy.linspace(xlim[0], xlim[1], 30)
y = numpy.linspace(ylim[0], ylim[1], 30)
Y, X = numpy.meshgrid(x, y)
xy = np.vstack([X.ravel(), Y.ravel()]).T
P = model.decision_function(xy).reshape(X.shape)
### 绘制边界和间隔
ax.contour(X, Y, P, colors='k',
           levels=[-1, 0, 1], alpha=0.5,
           linestyles=['--', '-', ':', '--'])
### 绘制支持向量
if plot_support:
 ax.scatter(model.support_vectors_[:, 0],
            model.support_vectors_[:, 1])
```

## 支持向量机

```
In [5]: Z = SvcModel.predict(X_plot)
z = Z.reshape(xx.shape)
plt.figure(figsize=(15, 5))
plt.subplot(121)
plt.contour(xx, yy, Z, alpha=0.3)
plt.scatter(X[:, 0], X[:, 1], c=y)
plt.xlim(xx.min(), xx.max())
```

`Out[5]`: `(3.3, 8.88272727272751)`

![](img/d75fea3635f5553f1cb0585b39b1b4b_171.png)

同样，我们可以使用径向基函数内核创建 `SVC`。

```
In [10]: RbfSvc = svm.Svc(kernel='rbf', C=1.0).fit(X, y)

Z = RbfSvc.predict(X_plot)

z = Z.reshape(xx.shape)

plt.figure(figsize=(15, 5))

plt.subplot(121)

plt.contour(xx, yy, Z, alpha=0.3)

plt.scatter(X[:, 0], X[:, 1], c=y)

plt.xlim(xx.min(), xx.max())
```

你可以观察线性和 rbf 的两张图表，并注意到线条和曲线之间明显的差异

```
Out[10]: (3.3, 8.88272727272751)
```

![](img/d75fea3635f5553f1cb0585b39b1b4b_172.png)

## 聚类算法

- K-Means
- 均值偏移 `Mean shift`
- 层次聚类 `Hierarchical`

![](img/d75fea3635f5553f1cb0585b39b1b4b_173.png)

## 聚类

聚类是无监督机器学习的一种。聚类算法学习数据中的关系，并根据是否提供了组数量将其分为不同的组。

![](img/d75fea3635f5553f1cb0585b39b1b4b_174.png)

发现的结果是不同类型的聚类：

- 基于密度的：聚类作为稠密区域形成。这些算法具有良好的准确率和合并两个聚类的能力。带噪声的基于密度的空间聚类 `DBSCAN`、用于识别聚类的点排序 `OPTICS`。
- 基于层次的：聚类在层次树中形成，具有凝聚性聚类（自下而上的方法）和分裂性聚类（自上而下的方法）。使用代表点进行聚类 `CURE`、基于层次结构的平衡迭代聚类 `BIRCH`。
- 划分的：聚类通过将对象划分为 k 份形成，聚类的数量将等于划分数量。`K-Means`。
- 网格的：聚类以网格形式形成。这种方法速度快，且与对象的数量无关。统计信息网格 `STING`、聚类 `CLIQUE`。

到为止，我们已经通过预测值和实际值计算了监督学习的准确率，那么当我们处理无标记数据时，如何对无监督学习这样做呢？

有一些指标可以根据聚类的变化来评估不同无监督学习算法的性能或质量。轮廓分析 `Silhouette analysis` 用于通过衡量聚类之间的距离来检查聚类模型的质量。它基本上为我们提供了一种通过轮廓系数评估聚类数量等参数的方法。

轮廓系数的范围从 -1 到 1。不同的数字代表以下：

- 1 表示聚类远离其相邻聚类的情况。
- 0 表示聚类非常接近或本身位于决策边界上，即分离了聚类。
- -1 表示聚类没有正确形成的情况。

可以使用以下公式计算轮廓系数：

`Silhouette Score = p - q / max(p, q)`

其中 `p` 是到最近聚类中点的平均距离，`q` 是到所有点的类内平均距离。

接下来，我们可以使用 Davis-Bouldin 指数来判断聚类之间的间距是否良好以及聚类的密度。我们可以使用以下公式计算 DB 指数：

![](img/d75fea3635f5553f1cb0585b39b1b4b_175.png)

## 聚类

`$DB = \frac{1}{n} \max_{j\neq i} \left(\frac{\sigma_i + \sigma_j}{d(c_i, c_j)}\right)$`

`n` 是聚类的数量，`$\sigma^i$` 是聚类 `i` 中所有点到聚类中心 `c_i` 的平均距离。

较低的值表示性能良好，其中 `$\theta$` 是最小值。

Dunn 指数是另一个用于评估聚类算法性能的指标。它与 DB 指数相似，区别在于：

- 它只考虑相邻的聚类，而 DB 指数考虑所有的聚类。
- Dunn 指数越低性能越差，DB 指数越高性能越好。

Dunn 指数可以使用以下公式计算：

`$D = \frac{\min_{i \neq j} P(i,j)}{\max_{k} q(k)}$`

`i,j,n` 是类的索引，`P` 是类间距离，`q` 是类内距离。

Dunn 指数随着聚类算法的提高而增加。

我们可以通过以下指标评估不同聚类算法（而不是单一算法）的性能：

- 轮廓系数
- Davis-Bouldin 指数
- Dunn 指数

让我们看看聚类的效果。我们使用 `make_blobs` 函数。

```python
from sklearn.cluster import KMeans
from sklearn.datasets import make_blobs
from matplotlib import pyplot
```

`dt, y = make_blobs(n_samples=240, centers=4, std=0.6)`

```python
kmeans = KMeans(n_clusters=4)
kmeans.fit(dt)
pred = kmeans.predict(dt)
centers = kmeans.cluster_centers()
```

```python
plt.figure(figsize=(15, 5))
plt.subplot(121)
plt.scatter(dt[:,0], dt[:,1], c=pred, s=30)
plt.plot(centers[:,0], centers[:,1], c='x', s=100)
plt.show()
```

```python
plt.figure(figsize=(15, 5))
plt.subplot(121)
plt.contour(xx, yy, Z, alpha=0.3)
plt.scatter(X[:, 0], X[:, 1], c=y)
plt.xlim(xx.min(), xx.max())
```

```python
pred = kmeans.predict(dt)
centers = kmeans.cluster_centers()
```

```python
plt.scatter(dt[:,0], dt[:,1], c=pred, s=30)
plt.plot(centers[:,0], centers[:,1], c='x', s=100)
```

这次我们指定了聚类的位置，并将中心（x 和 y 值）作为 2D 数组传递，且点数等于聚类的数量。我们可以使用 `scatter()` 散图来查看数据

```python
In [3]: X1 = dt[:,0]
X2 = dt[:,1]
pyplot.scatter(X1,X2)
```

`Out[3]`: `<matplotlib.collections.PathCollection at 0x1dbd820e`

![](img/d75fea3635f5553f1cb0585b399b1b4b_181_0.png)

现在我们可以使用 `MeanShift` 算法创建一个聚类模型，并传递我们的 `dt` 数据

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

`Estimated No. of Clusters: 3`

`Out[5]`: `<matplotlib.collections.PathCollection at 0x1dbd92972`

![](img/d75fea3635f5553f1cb0585b399b1b4b_182_0.png)

如所示，`Clstr` 在我们的数据集中预测了 3 个聚类，即这是正确的。我们通过 `labels_` 属性提取了每个数据点的标签，并用它来绘制聚类。然后我们通过 `Clstr` 类的 `cluster_centers_` 属性找到了聚类中心或质心，即它们的 x 和 y 值。聚类的长度（x 和 y 值，即 2D 数组）代表了 `Clstr` 预测的聚类数量。接着，使用 for 循环绘制了聚类（注意使用 `labels` 为不同聚类的不同数据点着色），我们还使用 `scatter()` 图绘制了聚类中心，并指定 `zorder` 为 10 以将其绘制在最前面

那么，尽管我们没有预先指定聚类的数量，MeanShift 算法是如何找到聚类的呢？

首先，它将每个数据点分配到自己的类中。然后算法将计算质心并改变新质心的位置。

这个过程将不断迭代并移动到高密度区域，直到质心达到无法进一步移动的位置。

### 层次聚类

顾如名，层次聚类是聚类的一种形式，将数据集像树一样分为若干组或类别，可以是单个数据点，也可以是单个聚类

层次聚类分为以下两种：

- 凝聚法 `Agglomerative`：层次聚类的一种类型，其中每个单独的数据点被视为一个聚类，然后合并或汇合成 2 个、4 个、8 个聚类，反之亦然，直到形成包含整个数据集的聚类

![](img/d75fea3635f5553f1cb0585b399b1b4b_183_0.png)

- 划分法 `Divisive`：凝聚法的相反，将整个数据集视为一个聚类，然后将其分为单个数据点。

### 整个数据集聚类形状

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

现在根据上面计算的距离值对它们进行升序排序

最后，根据最近的数据点为该点分配一个类别或值

![](img/d75fea3635f5553f1cb0585b399b1b4b_190_0.png)

### 使用 KNN 回归

我们将使用 KNN 算法进行回归，创建一个模型，在提供身高作为输入时预测一个人的体重，这与在线性回归模型（第 130 页）中解决的是相同的问题。

我们可以从导入必要的模块和数据集 `height_and_weight.csv` 开始。

```python
import pandas
from sklearn.neighbors import KNeighborsRegressor
from sklearn.model_selection import train_test_split
```

### KNN 算法

```
In [1]: import pandas
from sklearn.neighbors import KNeighborsRegressor
from sklearn.model_selection import train_test_split
dt = pandas.read_csv('height_and_weight.csv')
dt
```

```
Out[1]:
| Index | Height | Weight(lbs) |
|---|---|---|
| 0 | 1 | 65.78 | 112.99 |
| 1 | 2 | 71.52 | 136.49 |
| 2 | 3 | 69.40 | 153.03 |
| 3 | 4 | 68.22 | 142.34 |
| 4 | 5 | 67.79 | 144.30 |
| ... | ... | ... |
| 195 | 196 | 65.80 | 120.84 |
| 196 | 197 | 66.11 | 115.78 |
| 197 | 198 | 68.24 | 128.30 |
| 198 | 199 | 68.02 | 127.47 |
| 199 | 200 | 71.39 | 127.88 |
200 rows × 3 columns
```

我们可以将数据集拆分为训练集和测试集。

```python
In [2]: X = dt.drop(columns=['Index','Weight(lbs)'])
y = dt.drop(columns=['Index','Height(In)'])
inp_X, tst_X, out_y, tst_y = train_test_split(X,y, test_size=0.1)
```

我们的数据准备准备绪，现在来创建 KNN 模型并对其进行训练。

```python
In [3]: KNN = KNeighborsRegressor()
KNN.fit(inp_X,out_y)
```
