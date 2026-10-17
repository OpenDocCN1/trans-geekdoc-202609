
# 3.5.2 贝叶斯分类器

- 它是一种概率分类器，用于高维数据数据集的分类。
- 它主要用于文档分类，这意味着将特定的文档归为体育、政治、教育等类别。分类器使用单词频率作为预测因子。

## 为什么叫它贝叶斯？

- 这样命名是因为因为它依赖于贝斯定理。
- 被识别为颜色、形状和味道，然后水果是苹果。

## 贝叶斯分类器的优点：

- 贝叶斯是最快且最高效的算法之一。
- 它可以用于二分类，也可以用于多分类。
- 在多分类中它的性能优于其他算法。
- 它是文本分类中最受欢迎的选择。

## 贝叶斯分类器的缺点：

- 贝叶斯假设特征是独立的，因此它无法学习特征之间的关系。

## 贝叶斯分类器的应用：

- 它用于信用评分。
- 它用于医学数据分类。
- 它可以实时预测，因为贝叶斯分类器是一个主动学习者（eager learner）。
- 它用于文本分类，如垃圾过滤和情感分析。

## 贝叶斯模型的类型：下面是三种贝叶斯模型：

- 高斯（Gaussian）：高斯模型假设数据遵循正态分布。其中预测变量采用连续变量而不是离散变量，模型假设这些值是从高斯分布中抽样的。
- 多项（Multinomial）：当数据呈多项分布时使用多项贝叶斯分类器。它主要用于文档分类，这意味着将特定的文档归为体育、政治、教育等类别。分类器使用单词频率作为预测因子。
- 伯努利（Bernoulli）：伯努利分类器的工作与多项分类器类似，但预测变量是独立的布尔变量。取决于特定单词是否出现在文档中。该分类器也因文档分类任务而闻名。

## 工作原理：

i. 在此例中应用贝斯定理，我们用它根据特征（数据点的年龄和工资）找到人步行的概率。计算贝斯定理中每个组件的概率。
ii. 再次应用定理，在这种情况下将是根据新数据集的特征（年龄和工资）找到驾驶概率。
iii. 比较两者并为数据集分配一个类别。

我们得到了一个数据集。它有两个特征 `x1`（工资）和 `x2`（年龄）。并且有两个类别：类别 1 是红色（步行上班），类别 2 是绿色（开车上班）。

机器学习（ML）问题是对一个新的数据点进行分类；即如果我们在集中添加一个新的观测数据点，会发生什么。

因此，这是一个监督学习机器学习算法，因为我们是根据之前已知的类别（Classes）对事物进行分类。

这里朴素贝叶斯（Naive Bayes）将帮助我们解决这个挑战。

### 贝斯定理

我们将采用贝斯定理并应用两次。

**[1] 步骤 1：** 首先，我们将应用它来找到某*人（新数据点）*在给定其特征 `X`（例如年龄和薪水作为特征）的情况下走路的概率。

```
P(Walks|X) = \frac{P(X|Walks)P(Walks)}{P(X)}
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_118_0.png)

**[2] 步骤 2：** 我们将根据在我们**新数据点**中看到的特征，计算某人驾驶的概率。[某*人（新数据点）*在给定其特征 `X`（例如年龄和薪水作为特征）的情况下驾驶的概率]

```
P(Drives|X) = \frac{P(X|Drives)P(Drives)}{P(X)}
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_118_1.png)

```
P(Walks|X) = \frac{P(X|Walks)P(Walks)}{P(X)}
```

**[3] 步骤 3：** 最后，我们将比较某人在给定特征下走路的概率与某人在给定特征 `X` 下驾驶的概率。然后我们将决定将该新数据点归入哪类。

```
P(Walks|X) v. P(Drives|X)
```

你可以看到，朴素贝叶斯分类器是一种概率型分类器，因为我们首先计算概率，并根据概率将其分配给一类。

步骤 1 `$P(Walks|X) = \frac{P(X|Walks)P(Walks)}{P(X)}$` **我们将每次计算分为 4 个步骤：**

**计算先验概率（Prior Probability）：** 我们将计算某人走路的概率。即我们将向数据集中添加一个新的观测值，但我们不知道他们的年龄和薪水（在未知特征的情况下）。

我们关注的这个人的概率是：

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_118_2.png)

我们计算已观测的数量（即实际走路的人数为 10 人），并除以总观测数（即 30）。

这里的先验概率是：`$P(Walks) = \frac{\text{实际走路的人数}}{\text{总观测数}}$`

**计算边缘似然（Marginal Likelihood）：** 在数据点周围选择一个半径。`P(X)` 是任何给定点落在所选半径内的概率。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_119_0.png)

## 2. `P(X)`

`$P(X) = \frac{\text{相似观测数}}{\text{总观测数}}$` `$P(X) = \frac{4}{30}$`

我们将选择一个半径，并在观测值周围画一个圆。现在这个半径需要由你自己选择并由你决定。

我们将移除我们的新数据点 `DOT`，这以防产生混淆。

然后我们回到圆圈内的所有点，并认为它们在特征上与我们的新数据点（年龄 25 岁，年薪 `$30,000`）相似。

假设年龄在 20 到 30 岁之间，薪水在 `$25000` 到 `$35000` 之间是圆圈区域的特征。任何落在圆内的人都被认为与我们添加到数据集中的新数据点相似。

> 边缘似然（Marginal Likelihood）：`X` 的概率 `P(X)` 是我们添加到数据集中的新点与我们正在添加的特征相似的概率。基本上，它是我们添加的新点（或任何随机点）落入这个圆的概率。

`P(X)` 告诉我们我们添加到此数据集的任何随机变量落在圆内的似然（概率）是多少，`P(X)` 的计算方式为：

`$P(X) = \frac{\text{相似观测数}}{\text{总观测数}}$`

圆内有 3 个红点和 1 个绿点。即 `$P(X) = \frac{4}{30}$`

- 似然（Likelihood）：相同的半径。`P(X | Walks)` 在给定数据点走路的情况下，该数据点位于此圆内的概率。

- 某人走路表现出特征 `X` 的似然是多少？我们将反复画出同一个圆，落在圆内的点被认为与我们正在添加的点相似。

- 所以，一个随机选择的数据点由一个走路的人落入这个圆的似然是多少。

- 另一种思考方式是，我们只处理走路上班的人。所以我们只处理代表走路上班的人的红点。让我们忘记绿点。

- 所以，问题是：“在我们仅只处理红点的情况下，从红点中随机选择一个数据点落入这个圆内（即表现出与我们添加到数据集中的点相似的特征）的似然是多少。”

## 3. `P(X|Walks)`

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_120_0.png)

| 相似观测数 | 在走路的人中 | 走路的人总数 |
|---|---|---|
| `$P(X|Walks) = \frac{P(X|Walks)}{3}$` | | |

- D. 计算后验概率（Posterior Probability）：

`$后验概率，$P(Walks|X) = \frac{P(Walks) \times P(X|Walks)}{P(X)}$`

- [1] 先验概率：`P(Walks)`。我们将计算某人走路的概率。即我们将向数据集中添加一个新的观测值，但我们不知道他们的年龄和薪水（在未知特征的情况下）。

- [2] 计算边缘似然：在数据点周围选择一个半径。`P(X)` 是任何给定点落在所选半径内的概率。（任何给定点落在所选半径内的概率）。

- [3] 似然：相同的半径。`P(X | Walks)` 在给定数据点走路的情况下，该数据位于位于圆内的概率。

- [4] 计算后验概率：后验概率，`$P(Walks|X) = \frac{P(Walks) \times P(X|Walks)}{P(X)}$`

# ------ 朴贝叶斯模型

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# # 提取数据
dataset = pd.read_csv('Social_Network_Ads.csv')
X = dataset.iloc[:, [2, 3]].values
y = dataset.iloc[:, 4].values

# # 数据分割后的特征缩放
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25, random_state=0)

# # 特征缩放
from sklearn.preprocessing import StandardScaler
st = StandardScaler()
X_train = st.fit_transform(X_train)
X_test = st.transform(X_test)

# # 训练集到朴贝叶斯分类器：不需要参数
from sklearn.naive_bayes import GaussianNB
classifier = GaussianNB()
classifier.fit(X_train, y_train)

# # 预测
y_pred = classifier.predict(X_test)

# # 使用函数 "confusion_matrix" 生成混淆矩阵
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_test, y_pred)
# cm 的参数：y_true, y_pred 真实值，y_pred: 预测值

# # 可视化训练结果
from matplotlib.colors import ListedColormap
X_set, y_set = X_train, y_train
X1, X2 = np.meshgrid(np.arange(start=X_set[:, 0].min(), stop=X_set[:, 0].max() + 1, step=0.01), np.arange(start=X_set[:, 1].min(), stop=X_set[:, 1].max() + 1, step=0.01))
plt.contour(X1, X2, classifier.predict(np.c_[X1.ravel(), X2.ravel()]), cmap=ListedColormap(['red', 'green']), alpha=0.25)
plt.xticks(X_set[:, 0])
plt.yticks(X_set[:, 1])
for i, j in enumerate(np.unique(y_set)):
    plt.scatter(X_set[y_set == j, 0], X_set[y_set == j, 1], c=j, cmap=ListedColormap(['red', 'green']), label=j)
plt.title('朴贝叶斯（训练集)')
plt.xlabel('年龄')
plt.ylabel('估计薪资')
plt.legend()
plt.show()

# # 可视化测试结果
from matplotlib.colors import ListedColormap
X_set, y_set = X_test, y_test
X1, X2 = np.meshgrid(np.arange(start=X_set[:, 0].min(), stop=X_set[:, 0].max() + 1, step=0.01), np.arange(start=X_set[:, 1].min(), stop=X_set[:, 1].max() + 1, step=0.01))
plt.contour(X1, X2, classifier.predict(np.c_[X1.ravel(), X2.ravel()]), cmap=ListedColormap(['red', 'green']), alpha=0.25)
plt.xticks(X_set[:, 0])
plt.yticks(X_set[:, 1])
for i, j in enumerate(np.unique(y_set)):
    plt.scatter(X_set[y_set == j, 0], X_set[y_set == j, 1], c=j, cmap=ListedColormap(['red', 'green']), label=j)
plt.title('朴贝叶斯（测试集)')
plt.xlabel('年龄')
plt.ylabel('估计薪资')
plt.legend()
plt.show()

# # python predict_ntc.py
```

*朴素*

## # 训练数据集绘图

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_123_0.png)

## # 测试数据集绘图

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_123_1.png)

# 第 3 章：第 6 部分

# 决策树分类

### 3.6.1 决策树回归算法

决策树回归算法的目标是将数据分为相似的组。该算法使用了被称为“信息熵”（Information Entropy）的东西（这是一个非常复杂的数学过程）。

- 该算法的原理是以这种方式分割数据：通过增加信息，并在当无法向数据集中添加更多信息时停止分割数据。

- 在回归章节中，我们说“决策树回归”预测的是数值数据。分类树帮助我们对数据进行分类，例如类别变量如男性或女性、苹果或橙子、不同颜色类型和变体。而回归树旨在帮助你预测可以是实数的结果，例如人的薪资或将要呈现的温度。

- 在分类树中，我们对数据进行分类并预测类别。在这一部分，我们将观察与决策树回归几乎相同的方法。

- 在这里我们看到一个具有跨类别分割的图表。决策树的分割方式将最大化每类中的点数量并最小化熵。用通俗的话说，就是让每个类别尽可能纯净。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_123.png)

```python
plt.show()

from matplotlib.pyplot as plt

from matplotlib import ListedColormap

x_set, y_set = np.meshgrid(np.arange(x_set[:,0].min(), x_set[:,0].max() + 0.01, step=0.01),
                                np.arange(x_set[:,1].min(), x_set[:,1].max() + 0.01, step=0.01))

Z1, Z2 = clf.predict(np.c_[x_set.ravel(), y_set.ravel()])

Z1, Z2 = Z1.reshape(x_set.shape)

plt.contour(x_set, y_set, Z1, cmap=ListedColormap(['red', 'green']))

plt.scatter(x_set[:,0], x_set[:,1])

plt.scatter(y_set[:,0], y_set[:,1])

for i, j in enumerate(y_set):
    plt.scatter(x_set[j], y_set[j], c=ListedColormap(['red', 'green'])(i), label=j)

plt.title('Decision Tree (Test set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

```python
# python prcts_DTC.py
```
