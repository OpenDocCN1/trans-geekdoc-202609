
然后，我们必须应用 `MinMaxScaler` 来缩放转置后的值。为了在一个数组中获得结果，我们可以将转置后的结果转回原始形式：

```python
preprocessing.MinMaxScaler(feature_range=(0,1))
.fit_transform(values_to_scale)
.transpose()
```

输出如下：

```
array([[9.999900e-06, 2.999999e-04, 4.499999e-04, ..., 1.499999e-04, 1.499999e-04, 1.999990e-05]])
```

这些值看起来很奇怪，因为 Kickstarter 上有一些很高的目标，可能使用了七位数的数值。除了线性的 Minmax 缩放，还可以使用对数来对数量级进行缩放，计算目标价格有多少个数字。这是另一种可能降低分类练习复杂性的转换。

一如既往，你必须将结果放在 `DataFrame` 的相应列中，以利用这些转换后的值。

我们在此停止预处理。希望现在这些不同方法的用法已经很清楚了，你将来将能够熟练地使用这些预处理方法。

### 识别特征和标签

与回归类似，在分类中，我们也必须分离特征和标签。继续原始示例，我们的特征是除最后一列以外的所有列，最后一列包含信用评分的结果。我们唯一的标签是信用评分列。

我们将使用 `NumPy` 数组来存储特征和标签：

```python
import numpy as np

features = np.array(data_frame.drop(['CreditScore'], 1))
label = np.array(data_frame['CreditScore'])
```

现在我们已经准备好了特征和标签，可以使用这些数据进行交叉验证了。

### 使用 scikit-learn 进行交叉验证

关于回归的另一个相关点是，我们可以使用交叉验证来训练和测试模型。这个过程与回归问题的情况完全相同：

```python
from sklearn import model_selection

features_train, features_test, label_train, label_test = \
model_selection.train_test_split(
    features,
    label,
    test_size=0.1
)
```

`train_test_split` 方法会打乱并将我们的特征和标签拆分为训练数据集和测试数据集。我们可以指定测试数据集的大小为 `0` 到 `1` 之间的数字。`test_size` 为 `0.1` 意味着 `10%` 的数据将进入测试数据集。

### 活动 7：为分类准备信用数据

在本节中，我们将讨论如何为分类器准备数据。我们将使用来自 [`archive.ics.uci.edu/ml/machine-learning-databases/statlog/german/`](https://archive.ics.uci.edu/ml/machine-learning-databases/statlog/german/) 的 `german.data` 作为示例，并为训练和测试分类器准备数据。确保所有的标签都是数值型的，并且值已经为分类准备好。使用 80% 的数据点作为训练数据：

1. 从 [`archive.ics.uci.edu/ml/machine-learning-databases/statlog/german/`](https://archive.ics.uci.edu/ml/machine-learning-databases/statlog/german/) 下载 `german.data` 并使用 Sublime Text 或 Atom 等文本编辑器打开它。为其添加表头。
2. 使用 `pandas` 导入数据文件并将 NA 值替换为离群值值。
3. 执行标签编码。将数据框中的所有标签转换为整数。
4. 分离特征和标签。我们可以应用与理论章节中看到的相同的方法。
5. 联合对训练和测试数据进行缩放。使用 Scikit Preprocessing 库中的 `MinMaxScaler`。
6. 最后一步是交叉验证。打乱我们的数据，并将 80% 用于训练，20% 用于测试。

#### 注意事项

此活动的解决方案见第 276 页。

### k-最近邻分类器

我们将从上次过的地方继续。在引入 K-最近邻算法后，我们将使用 scikit-learn 进行分类。

#### 介绍 K-最近邻算法

分类算法的目标是对数据进行划分，以便我们确定属于哪一类。假设有一组分类点。我们的任务是确定一个数据点属于哪个类。

k-最近邻分类器接收具有给定特征值的类别。分类基于接近性。接近性被定义为欧几里得距离。如果 A 与 B 之间的欧几里得距离比 A 与 C 之间的距离短，则 A 更接近 B。

#### 距离函数

许多距离量都可以 k-最近邻算法。我们现在计算两个数据点的欧几里得距离和曼哈顿距离。欧几里得距离是我们在平面或三维空间中计算两点距离方法的推广。

点 `A = (a1, a2, …, an)` 和 `B=(b1, b2, …, bn)` 之间的距离是连接这两点的线段长度：

![图 4.1 点 A 和 B 之间的距离](img/Image0043.jpg)

###### 图 4.2：点 A 和 B 之间的距离

技术上讲，当我们寻找最近邻居时，不需要计算平方根，因为平方根是一个单调函数。

由于我们将在本书中使用欧几里得距离，让我们来看看如何通过单次 scikit-learn 函数调用计算多个点之间的距离。我们需要从 `sklearn.metrics.pairwise` 导入 `euclidean_distances`。该函数接受两组点，并返回一个矩阵，其中包含第一组与第二组中每个点之间的两对距离：

```python
from sklearn.metrics.pairwise import euclidean_distances

points = [[2,3], [3,7], [1,6]]

euclidean_distances([[4,4]], points)
```

输出如下：

```python
array([[2.23606798, 3.16227766, 3.60555128]])
```

例如，(4,4) 和 (3,7) 之间的距离约为 3.162。

我们也可以计算同一组点之间的欧几里得距离：

```python
euclidean_distances(points)
```

```
array([[0. , 4.12310563, 3.16227766],
 [4.12310563, 0. , 2.23606798],
 [3.16227766, 2.23606798, 0.]])
```

#### 曼哈顿/汉明距离

汉明和曼哈顿距离代表相同的公式。

曼哈顿距离依赖于计算数据点坐标差的绝对值：

![图 4.2 曼哈顿与汉明距离](img/Image00044.jpg)

#### 图 4.3：曼哈顿与汉明距离

欧几里得距离是距离更准确的推广，而曼哈顿距离计算更容易。

### 练习 12：演示 K-最近邻分类算法

假设我们有一份员工数据列表。我们的特征是每周工作小时和年薪。我们的标签表示员工是否在我们公司工作了两年以上。如果工作时间小于两年，则用 0 表示；如果大于等于两年，则用 1 表示。

我们想创建一个 3-最近邻分类器，来判断员工是否会在我们公司工作至少两年。

然后，我们想使用这个分类器来预测一个要求每周工作 32 小时且年薪 52,000 美元的员工是否会留在公司工作两年。

数据集如下：

```python
employees = [
 [20, 50000, 0],
 [24, 45000, 0],
 [32, 48000, 0],
 [24, 55000, 0],
 [40, 50000, 0],
 [40, 62000, 1],
 [40, 48000, 1],
 [32, 55000, 1],
 [40, 72000, 1],
 [32, 60000, 1]
]
```

1. 缩放特征：

```python
import matplotlib.pyplot as plot
from sklearn import preprocessing
import numpy as np
from sklearn.preprocessing import MinMaxScaler

scaled_employees = preprocessing.MinMaxScaler(feature_range=(0,1))\
    .fit_transform(employees)
```

缩放结果如下：

```python
array([[0. , 0.18518519, 0. ],
 [0.2 , 0. , 0. ],
 [0.6 , 0.11111111, 0. ],
 [0.2 , 0.37037037, 0. ],
 [1. , 0.18518519, 0. ],
 [1. , 0.62962963, 1. ],
 [1. , 0.11111111, 1. ],
 [0.6 , 0.37037037, 1. ],
 [1. , 1. , 1. ],
 [0.6 , 0.55555556, 1.]])
```

此时对我们请求的员工进行缩放也是合理的：`[32, 52000]` 变为 `[(32-24)/(40 - 24), (52000-45000)/(72000 - 45000)] = [0.5, 0.25925925925925924]`。

2. 在二维平面上绘制这些点，其中前两个坐标代表平面上的一个点，第三个坐标决定点的点的颜色：

```python
import matplotlib.pyplot as plot

plot.scatter(x[0], x[1], color = 'g' if x[2] > 0.5 else 'r')

for x in scaled_employees:
    plot.scatter(0.5, 0.25925925925925924, color='b')
```

输出如下：

![图 4.3 绘制在二维平面上的点](img/Image00045.jpg)

#### 图 4.4：绘制在二维平面上的点

3. 为了计算蓝色点和其他所有点的距离，我们将应用 `transpose` 函数。如果转置 `scaled_employees`，我们将得到十个数组。特征值在前两个数组中。我们可以简单地使用 `[:2]` 来保留它们。然后将其转置回原始形式，得到特征数组：

```python
scaled_employee_features = scaled_employees.transpose()[:2]
scaled_employee_features
```

输出为：

```python
array([[0. , 0.18518519],
 [0.2 , 0. ],
 [0.6 , 0.11111111],
 [0.2 , 0.37037037],
 [1. , 0.18518519],
 [1. , 0.62962963],
 [1. , 0.11111111],
 [0.6 , 0.37037037],
 [1. , 1. ],
 [0.6 , 0.55555556]])
```

4. 使用以下代码计算欧几里得距离：

```python
from sklearn.metrics.pairwise import euclidean_distances

euclidean_distances([[0.5,0.25925925925925924]], scaled_employee_features)
```

输出为：

```python
array([[0.50545719, 0.39650393, 0.17873968, 0.31991511, 0.50545719,
 0.62223325, 0.52148622, 0.14948471, 0.89369841, 0.31271632]])
```

最短距离如下：
- 点 `[0.6, 0.37037037, 1]` 的距离为 `0.14948471`。
- 点 `[0.6, 0.11111111, 0]` 的距离为 `0.17873968`。
- 点 `[0.6, 0.55555556, 1]` 的距离为 `0.31271632`。

由于三个点中有两个标签为 1，我们找到了两个绿点和一个红点。这意味着我们的 3-最近邻分类器认为该员工更有可能留在公司工作两年。

##### 注意
第四个点仅以非常微小的差距错过了前三名。事实上，如果有两个不同颜色的点到目标的距离相等，我们的算法将出现平局。不过，这是一个边缘情况，在现实问题中几乎不会发生。

### 练习 13：scikit-learn 中的 k-最近邻分类

1. 将我们的数据分为四类：`training` 和 `testing` 集、特征以及标签：

```python
from sklearn import model_selection
import pandas
import numpy as np
from sklearn import preprocessing

features_train, features_test, label_train, label_test = model_selection.train_test_split(
    scaled_features,
    label,
    test_size=0.2
)
```

2. 创建一个 `KNeighborsClassifier` 分类器来执行此分类：

```python
from sklearn import neighbors

classifier = neighbors.KNeighborsClassifier()
classifier.fit(features_train, label_train)
```

由于我们没有提到 `K` 的值，默认值为 `5`。

3. 检查我们的分类器在测试数据上的表现：

```python
classifier.score(features_test, label_test)
```

输出为 `0.665`。

你可能会在其他数据集上找到更高的评分，但可以理解，20 多个特征可能很容易包含随机噪声，导致数据难以分类。

### 练习 14：使用 k-最近邻分类器进行预测

此代码基于上一个练习的代码。

1. 我们将通过取第 `i` 个测试数据点的第 `i` 个元素来创建一个分类的数据点：

```python
data_point = [None] * 20
for i in range(20):
    data_point[i] = features_test[i][i]
data_point = np.array(data_point)
```

2. 我们有一个一维数组。分类器期望一个包含数据点数组的数组。因此，我们必须将数据点重塑为数据点数组：

```python
data_point = data_point.reshape(1, -1)
```

3. 通过此，我们创建了一个完全随机的人格，我们对他们是否被归类为信用良好：

```python
credit_rating = classifier.predict(data_point)
```

现在，我们可以安全地使用预测来确定数据点的信用评分：

```python
classifier.predict(data_point)
```

输出如下：

```python
array([1], dtype=int64)
```

我们已根据输入数据成功对新用户进行了评分。

#### scikit-learn 中 k-近邻分类器的参数化

你可以在此处访问 k-近邻分类器的文档：[`scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html`](http://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html)。

分类器的参数化可能会微调你分类器的准确性。由于我们还没有学习过 k-近邻的所有可能变体，我们将专注于你已经根据此主题理解的参数上。

- `n_neighbors`: 这是 k-近邻算法的 k 值。默认值为 5。
- `metric`: 在创建分类器时，你会看到一个奇怪的名字——“Minkowski”（闵可夫斯）。不要担心这个名字——你已经学习过一阶和二阶度量。这种度量有一个幂。当 `p=1` 时，`Minkowski` 度量等于 `Manhattan`（曼哈顿）距离。当 `p=2` 时，`Minkowski` 度量等于 `Euclidean`（欧几里得）距离。
- `p`: 这是 `Minkowski` 量的幂。默认值为 2。

一旦创建分类器，你就必须指定这些参数：

```python
classifier = neighbors.KNeighborsClassifier(n_neighbors=50)
```
