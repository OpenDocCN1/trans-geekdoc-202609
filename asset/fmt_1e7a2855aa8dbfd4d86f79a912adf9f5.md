
```python
X_set, y_set = X_test, y_test

X1, X2 = np.meshgrid(np.arange(start=X_set[:,0].min-1, stop=X_set[:,0].max+1, step=0.01), 
np.arange(start=X_set[:,1].min-1, stop=X_set[:,1].max+1, step=0.01))

plt.contour(X1, X2, classifier.predict(np.array((X1.ravel(), X2.ravel())).reshape(X1.shape)), 
alpha=0.5, cmap=ListedColormap(['red', 'green']))

plt.xlim(X1.min(), X1.max())
plt.ylim(X2.min(), X2.max())

for i, j in enumerate(np.unique(y_set)):
    plt.scatter(X_set[y_set==j, 0], X_set[y_set==j, 1], label=ListedColormap(['red', 'green'])(i))

plt.title('KNN (测试集)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

`python prctc_knn.py`

# 第 3 章：部分 3
## 支持向量机

### 3.3.1 决策边界

在使用特定的分类算法在数据集上训练分类器时，需要定义一组超平面（Set Of Hyper-Plane），称为决策边界，它将数据点分为特定的类别，算法在此从一个类别切换到另一个类别。在决策边界的一侧，数据点更有可能归类为 A 类——在边界的另一侧，它更有可能归类为 B 类。

例如，在我们的逻辑回归示例中：我们有 $p = \frac{1}{1+e^{-y}}$ 和 $y = b_0 + b_1x$，这意味着：

$p = \frac{1}{1+e^{-(b_0+b_1x)}}$

因此，我们当前的预测函数返回一个 0 到 1 之间的概率分数。为了将其映射到离散类别（A/B），我们选择一个阈值或临界点，高于该值的值被归类为 A 类，低于该值的值被归类为 B 类。这个阈值通常用 p 表示。

- $p \ge 0.5$: 类别=A
- $p \le 0.5$: 类别=B

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_98_0.png)

- 如果我们的阈值是 .5，预测函数返回 .7，我们认为该观测值属于 A 类。如果我们的预测是 .2，我们认为该观测值属于 B 类。

为了将预测值映射到概率，我们使用 Sigmoid 函数。

**决策边界**：因此，具有 0.5 的即水平线 y = 0.5 被称为决策边界。

### 3.3.2 支持向量机

为了简单起见，考虑两个列特征 $x_1$ 和 $x_2$。观测值已经经过了分类。

#### 如何分离这些点？

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_98_1.png)
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_98_2.png)
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_98_3.png)
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_98_4.png)

所以，让我们来看看 SVM 实际上是如何寻找这条线（决策边界的）。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_99_0.png)

实际上，对角线有很多选择：

使用 SVM 的决策边界：实际上，这条决策边界线是通过最大间隔（maximum margin）来搜索的。基本上，它是分离这两个类别点的线，同时具有最大间隔。

- **最大间隔**：这意味着从绘制的线条到两侧的点的距离是等等的。因此，这两个距离之和（总间隔）必须最大化，以便使这条线成为 SVM 的结果（“最佳决策边界”）。

#### 支持向量

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_99_1.png)

- **支持向量**：最大间隔所依赖的（支撑的）最近的点被称为支持向量，因为它们字面上支撑了决策边界。在上面的图中，接触最大间隔的两个点实际上被称为支持向量。

- 这两个点支撑了整个算法。即使你去除了所有其他点，算法也将完全相同。

- 所以，其他点对算法结果没有贡献，只有这两个点有贡献，因此称它们为支持向量（你可以称它们为支持向量）。

- 支持向量：从这个意义上说，你可以认为它是一种更极端的算法，一种非常反叛的算法，因为它查看的是非常边界的极端情况。（注：此处原文存在大量重复文本，已按逻辑合并翻译）。

（此处省略原文中大量重复的 Support vectors描述，以保持文档简洁）

### 3.3.3 SVM 的特殊之处

将一个水果分类为苹果或橙子。假设你正在尝试教机器区分苹果和橙子。现在在我们的案例中，你可以看到右边有橙子，左边有苹果。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_100_0.png)

苹果类苹果 & 橙类橙子

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_100_1.png)

- 大多数机器学习算法会这样做，它们会查看**最苹果/最橙子**来匹配给定的“水果”（即给定的水果是否最像“苹果类：更像苹果的苹果”或“最橙类：更像橙子的橙子”）。最大化水果特征。

- 但 **SVM 反其道**，它查看的是边缘值（即橙类苹果：*更像橙子的苹果*或苹果橙子：*更像苹果的橙子*）。这些就是**支持向量**。你可以看到它们非常接近边界，使得“橙子/苹果水果特征非常接近”。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_100_2.png)

因此，支持向量机从这个意义上说你可以认为它是一种更极端的算法，一种非常反叛的算法，因为它查看的是非常接近边界的极端情况。

而这一点本身使得*支持向量机 [SVM] 算法*与大多数其他**机器学习算法**相比非常特殊且不同。

### 3.3.4 SVM算法的Python实现

```python
# 库
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```

```python
# 数据提取
dataset = pd.read_csv("Social_Network_Ads.csv")
X = dataset.iloc[:, 2,3].values
y = dataset.iloc[:, 4].values
```

```python
# 数据划分后的特征缩放
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

```python
# 特征缩放
from sklearn.preprocessing import StandardScaler
```

```python
st = StandardScaler()
X_train = st.fit_transform(X_train)
X_test = st.transform(X_test)
```

```python
# 训练集到模型分类器
from sklearn.svm import SVC
clsf = SVC(kernel="linear", random_state=0)
clsf.fit(X_train, y_train)
```

```python
# 预测
y_pred = clsf.predict(X_test)
```

```python
# 使用函数"confusion_matrix"创建混淆矩阵
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(true=y_test,
```

```python
# 可视化训练集
from matplotlib.colors import ListedColormap
X_set, y_set = X_train, y_train
X1, X2 = np.meshgrid(np.arange(start=X_set[:,0].min, stop=X_set[:,0].max+1, step=0.01), np.arange(start=y_set[:,1].min, stop=y_set[:,1].max+1, step=0.01))
```

```python
plt.contourf(X1, X2, clsf.predict(np.array([X1.ravel(), X2.ravel()]).T).reshape(X1.shape), alpha=0.5, cmap=ListedColormap(['red', 'green']))
plt.xlim(X1.min(), X1.max())
plt.ylim(X2.min(), X2.max())
plt.scatter(X_set[:,0], X_set[:,1], c=y_set, cmap=ListedColormap(['red', 'green']), label=y)
plt.title('Training set')
```

```python
# 可视化测试集
from matplotlib.colors import ListedColormap
X_set, y_set = X_test, y_test
X1, X2 = np.meshgrid(np.arange(start=X_set[:,0].min, stop=X_set[:,0].max+1, step=0.01), np.arange(start=y_set[:,1].min, stop=y_set[:,1].max+1, step=0.01))
```

```python
plt.contourf(X1, X2, clsf.predict(np.array([X1.ravel(), X2.ravel()]).T).reshape(X1.shape), alpha=0.5, cmap=ListedColormap(['red', 'green']))
plt.xlim(X1.min(), X1.max())
plt.ylim(X2.min(), X2.max())
plt.scatter(X_set[:,0], X_set[:,1], c=y_set, cmap=ListedColormap(['red', 'green']), label=y)
plt.title('Test set')
```

```python
# python prct_svm.py
```

## 数据预处理与之前的 KNN 示例相似。

分类器：我们使用 `kernel = "Linear"`。它是核 SVM 的一部分，默认值为 `rbf`（径向基函数核），或 RBF 核，这是一种在各种核化算法中常用的流行的核函数，大多数情况下是“高斯分布”。`kernel = "Linear"` 意味着我们不应用任何核技巧（Kernel-trick）。

```python
# 训练集到模型分类器
from sklearn.svm import SVC
clsF=SVC(kernel="linear", random_state=0)
clsF.fit(X_train, y_train) # 拟合数据集
```

预测和混淆矩阵：从以下数值中可以看出，结果与“之前的逻辑回归”几乎相同。在这里模型性能并没有得到很大提升。我们将在下一节使用核 SVM，然后性能将会提高。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_102_0.png)

数据可视化：与 KNN 算法部分相同

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_102_1.png)

## 测试集

### SVM (测试集)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_102_0.png)

## 核 SVM

### 核 SVM

### 核 SVM

在核 SVM 的情况下，我们有一组属于不同的类别

### SVM

### 关于这些点

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_104_0.png)

在第一种情况下，SVM 算法告诉我们找到边界。但它有一个假设，即数据是可分的。

- 线性可分
- 非线性可分

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_104_1.png)

## 线性可分

- 线性可分
- 非线性可分

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_104_1.png)

SVM 算法帮助我们找到那个边界并正确放置。

在非线性可分的情况下，支持向量机无法画出单一的边界。

### 3.4.2 处理非线性分离数据的技巧

1. **映射到高维**：首先，我们将探索一种“映射到高维”的方法。在这种情况下，我们使用数据集并向空间中添加一个额外的维度，我们正在处理的，使得数据是可分的。

2. **核技巧**：核技巧允许我们在不处理多个高维的情况下使数据变得可分。

最后，我们将讨论不同的核类型。

### 3.4.3 映射到高维

使用高维空间来使数据集变得可分。

- i. 我们可以将*非线性分离数据集*映射到高维并获得*线性可分数据集*。
- ii. 调用 SVM 算法为数据集构建*决策边界*并
- iii. 然后将所有内容投影回*原始维度*。

#### 投影回 2D 空间

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_106_1.png)

使用这种算法时，问题在于映射到高维空间可能是计算密集型的，因此它可能需要大量的计算和处理能力。数据集越大，产生的问题就越严重，因此这种方法并不是最好的，因为你可以想象你有一个数据集，然后将其映射到高维，在那里进行所有的计算，然后返回你的低维，这对于计算机来说会导致大量的延迟，会导致大量的回溯和问题。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_106_2.png)

### 3.4.4 技巧 (The Trick)

在这里我们得到了高斯/径向基函数（高斯 RBF 核）核。

#### 高斯 RBF 核

```
$K(\vec{x},\vec{l'}) = e^{-\frac{\|\vec{x}-\vec{l}'\|^2}{2\sigma^2}}$
```
