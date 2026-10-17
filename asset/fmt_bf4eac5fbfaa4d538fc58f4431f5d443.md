
- 所以 `K` 代表核（kernel），它是作用于两个向量 $\vec{x}, \vec{l}'$ 的函数。
- 在我们的数据集中存在某些点，被称为标记点（Landmark）。
- $\vec{l}'$ 意味着可能存在多个标记点。
- 双垂直线表示 $\vec{x}$ 与标记点 $\vec{l}'$ 之间的距离。
- Sigma（$\sigma$）的作用类似于半径（方差）。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_107_0.png)

在上方图中，这个观测值的顶点正位于中间，当我们将其投影到 xy 平面时，我们就得到了标记点的位置。它是我们测量距离的起点。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_107_1.png)

假设是平面上某处的两个点。绿色的靠近标记点，红色的远离标记点。

- 红色点距离标记点非常远。因此距离很大，导致 $\frac{\|\vec{x}-\vec{l}'\|^2}{2\sigma^2}$ 也很大。这使得 `K(\vec{x},\vec{l}') \to 0`。
- 对于靠近标记点的点（绿色点），距离 $\|\vec{x}-\vec{l}'\|$ 较小，因此 $\frac{\|\vec{x}-\vec{l}'\|^2}{2\sigma^2}$ 也较小。这使得 `K(\vec{x},\vec{l}') \to 1`。这就是机器学习算法寻找这些标记点最优放置位置的方法。

在 2D 空间中发生了什么？我们将使用这个核函数来划分我们的数据集以构建决策边界。让我们来看看这是我们的 2D 维度空间。

回到 `X_1, X_2` 平面。现在我们将取一个标记点并将其放在数据集的某个地方。

## 2D 空间

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_108_0.png)

标记点放置后，算法设置为使用 `sigma` 寻找最优圆周/非线性边界。当 `sigma` 增加时，边界扩散；当 `sigma` 减小时，边界收缩。核函数实际上在这里投影到了我们的数据集上。

所有在该圆周内的点都被赋予了零以上的 (0,1) 区间值。在该圆周之外的任何东西（基本上是这些红点）将获得 0 值。在 3D 空间中，圆周内的点位于标记点上，而圆周之外的点非常接近于零，位于蓝色平面上。

因此，基于这个函数，只要我们选择正确的 Sigma `sigma`，就可以将绿色和红色两个类分离开。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_108_1.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_108_2.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_109_0.png)

所以基本上，通过**寻找正确的 sigma**，你可以为你所有**不希望**出现在分类中的点设置 D 值，并为你**想要**出现在分类中的点设置**零以上**的值。这将允许你**区分这两个类**。允许你将它们中的每一个进行分类。本质上，这就是核技巧（kernel trick）。

- 因此，我们实际上创建了一个进入高维空间的**决策边界**，而不需要投影回 2D 空间。
- 这里使用了高维空间，但我们仍然在低维空间进行计算。
- 是的，我们有这种涉及高维空间的视觉表示，但同时如果你看我们刚才在 2D 中计算这个公式的部分。

## 3.4.5 多个标记点的核技巧

假设突然你无法调整决策边界，而且是非线性的，此外你发现自己能够解决更难、更复杂的问题，例如：

```
$$K(\vec{x},\vec{l}^1) + K(\vec{x},\vec{l}^2)$$
```
(简化公式)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_109_1.png)

这里有一个非常简化的公式：

```
$$K(\vec{x},\vec{l}^1) + K(\vec{x},\vec{l}^2)$$
```

- 如果你取**两个核函数**并仅将它们**相加**（在实际上你需要一些系数）。**远离一个标记点**且**靠近**另一个标记点**的点将具有非零值。远离**两个标记点**的点为 0 值。就是这样。
- 公式当该方程**大于零**时，点被分配给**绿色类**；当该方程**等于零**时，点被分配给**红色类**。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_110_0.png)

`K(\vec{x},\vec{l}^1) + K(\vec{x},\vec{l}^2)`
(简化公式)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_110_1.png)

`K(\vec{x},\vec{l}^1) + K(\vec{x},\vec{l}^2)`
(简化公式)

- 绿色：`K(\vec{x},\vec{l}^1) + K(\vec{x},\vec{l}^2) > 0`
- 红色：`K(\vec{x},\vec{l}^1) + K(\vec{x},\vec{l}^2) = 0`

## 3.4.6 不同类型的核函数

你需要了解 SVM 的径向基函数（也称为高斯函数）不是唯一使用的核函数。让我们看看：

### 核的类型

| 核名称 | 公式 |
| :--- | :--- |
| 高斯 RBF 核 | $K(\vec{x},\vec{l}) = e^{-\frac{\|\vec{x}-\vec{l}\|^2}{2\sigma^2}}$ |
| Sigmoid 核 | $K(X,Y) = \tanh(y \cdot X)$ |
| 多项式核 | $K(X,Y) = (y \cdot X)^d, y > 0$ |

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_110_2.png)
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_111_0.png)
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_111_1.png)
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_111_2.png)
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_111_3.png)

### 更多核

- 卡方平方核 (Chi-Squared Kernel)
- Sigmoid 核
- 拉普拉斯核 (Laplacian Kernel)
- 高斯核
- 多项式核
- 周期核 (Periodic Kernel)

## 3.4.7 核的 Python 实现

所有代码与之前的算法相同。我们只需要将“核”改为 `kernel="rbf"` 而不是 `kernel="linear"`。

```python
# 库
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# 数据提取
dataset = pd.read_csv("Social_Network_Ads.csv")
X = dataset.iloc[:, [2, 3]].values
y = dataset.iloc[:, 4].values

# 数据划分后的标准化
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25, random_state=0)

# 标准化
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)

# 训练核 SVM 分类器
from sklearn.svm import SVC
classifier = SVC(kernel="rbf", random_state=0)
classifier.fit(X_train, y_train)

# 预测
y_pred = classifier.predict(X_test)

# 使用 "confusion_matrix" 函数制作混淆矩阵
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_test, y_pred)
```

## 训练数据可视化

### 核函数SVM (训练集)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_114_0.png)

## 测试数据可视化

### 核函数SVM (测试集)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_114_1.png)

# 第3 章：第 5 部分

## 朴素贝叶斯

贝斯定理，朴素贝叶斯算法

### 3.5.1 贝斯定理

**贝叶斯定理：**贝斯定理也被称为贝叶斯法则或贝斯律，用于根据根据先验知识确定*假设的概率*。它依赖于*条件概率*。贝斯定理的公式如下：

```
P(A|B) = \frac{P(B|A)P(A)}{P(B)}
```

在给定 *B* 的情况下 *A* 发生的概率 `P(A|B)`。贝斯定理是一种寻找在某事*刚刚发生 (B)* 的情况下，某事*发生的概率 (A)* 的方法。

- `P(A|B)` 是后验概率概率：在观测到事件 B 的情况下，假设 A 的概率。在 B 发生时 A 发生的频率。
- `P(B|A)` 是似然概率：在假设假设 A 为真的情况下，证据出现的概率。在 A 发生时 B 发生的频率。
- `P(A)` 是先验概率：在观察到证据之前假设的概率。A 是独立存在的。
- `P(B)` 是边缘概率：证据的概率。B 是独立存在的。

其中 *A* 和 *B* 是事件，$P(B) \neq 0$ 且 *B* 必须是*不同的事件*。
- `P(A|B)` 是条件概率：在 B 为真的情况下，事件 A 发生的概率。它也被称为给定 B 的*后验概率*。
- `P(B|A)` 也是条件概率：在 A 为真的情况下，事件 B 发生的概率。它也可以解释为在固定 B 的情况下 A 的似然 `P(B|A) = L(A|B)`。
- `P(A)` 和 `P(B)` 分别是观测 A 和 B 的概率，被称为*边缘概率或先验概率*。

*示例：* 假设 `P(Fire|Smoke)` 表示火灾发生的频率，`P(Smoke)` 表示我们看到烟的频率；

`P(Fire|Smoke)` 意味着当我们看到*烟*时，*火灾*发生的频率
`P(Fire|Smoke)` 意味着当发生*火灾*时，我们看到*烟*的频率

所以公式告诉我们在知道“反向” `P(Smoke|Fire)` 时预测“向前”的 `P(Fire|Smoke)`。

- 危险火灾很罕见 (1%)，
- 但由于烧烤，烟相当常见 (10%)，`P(Smoke)`，且 90% 的危险火灾会产生烟，`P(Smoke|Fire)`

我们就可以发现在有烟时危险火灾的概率：

```
$P(Fire|Smoke) = \frac{P(Smoke)P(Fire)}{P(Smoke)} = \frac{10\% \times 90\%}{100\%} = 9\%$
```

所以为了确保万无，检查一下烟还是值的。

# 扳手制造机：两台机器生产扳手。我们知道：

- 机器 1：每小时生产 30 把扳手
- 机器 2：每小时生产 20 把扳手
- 所有扳手中有 1% 是次品，其中机器 1 的缺陷扳手占 50%，机器 2 占 50%。

问题：机器2 生产的零件是次品的概率是多少？

- 扳手来自机器 M1 的总概率 = 30/50 = 0.6
- `P(M1)` = 来自机器 M1 的概率
- `P(M2)` = 来自机器 M2 的概率 = 20/50 = 0.4
- `P(D)` = 次品的概率 = 0.01
- `P(M1 | D)` = 在缺陷扳手中来自机器 M1 的概率 = 0.5
- `P(M2 | D)` = 在缺陷扳手中来自机器 M2 的概率 = 0.5
- `P(D | M2)` = 机器2 生产的扳手是次品的概率？？

根据贝斯定理，

```
$P(M_2|D) = \frac{P(M_2)P(D|M_2)}{P(D)}$
```

# 它是直观的！

```
$P(Defect | Mach2) = \frac{P(Mach2)P(Defect|Mach2)}{P(Defect)}$
```

让我们来看一个例子：

- 危险火灾很罕见 (1%)，
- 但由于烧烤，烟相当常见 (10%)，`P(Smoke)`，且 90% 的危险火灾会产生烟，`P(Smoke|Fire)`

我们就可以发现在有烟时危险火灾的概率：

```
$P(Fire|Smoke) = \frac{P(Smoke)P(Fire)}{P(Smoke)} = \frac{10\% \times 90\%}{100\%} = 9\%$
```
