

# 第一步：选择邻居数量 K：K = 5

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_92_0.png)

# 第二步：根据欧几里得距离找到新数据点的 K=5 个最近邻居

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_92_1.png)

# 第三步：在这些 K 个邻居中，统计每个类别中的数据点数量

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_92_2.png)

# 第四步：将新数据点分配到邻居数量最多的类别

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_92_3.png)

**如何在 K-NN 算法中选择 K 的值？** 以下是在选择 K-NN 算法中 K 值时需要记住的几点。

- ****没有特定的方法**来确定 "K" 的最佳值，因此我们需要**尝试一些值**来找到其中最佳的一个。K 的**首选**值是 5。
- K 值过小（例如 K=1 或 K=2）可能会产生**噪声**，并导致模型中受到**离群值**的影响。
- K 的值较大是好的，但可能会遇到一些困难。

# **K-NN 算法的优点：**

- 实现简单。
- 对噪声训练数据具有鲁棒性。
- 如果训练数据量很大，效果可能更有效。

# **K-NN 算法的缺点：**

- 总是需要确定 K 值，这可能有些复杂。
- 由于需要计算所有训练样本数据点之间的距离，计算成本很高。

备注：

- K-近邻（K-Nearest）是基于**监督学习**技术的最简单的机器学习算法之一。

- K-NN 假设**新案例/数据**与可用案例之间存在**相似性**，并将新案例放入与**可用类别**最相似的**类别**中。
- K-NN 算法存储所有可用数据并根据**相似性**对新数据点进行分类。这意味着当新数据出现时，可以使用 K-NN 算法轻松将其归类为**良好的类别**。

- K-NN 既可以用于**回归**也可以用于**分类**，但它主要用于**分类**问题。

**参数算法：** K-NN 是一种**非参数算法**，这意味着它**对底层数据不做任何假设**。

懒惰学习（Lazy learner）：它也是一种懒惰学习器，因为它不会立即从训练集中学习，而是存储数据集，并在分类时对数据集执行操作。

KNN 算法在训练阶段仅存储数据集，当获得新数据时，它会将数据分类到与新数据非常相似的类别中。

示例：假设我们有一张看起来像猫和狗的生物图像，但我们想知道它是猫还是狗。因此，对于这种识别，我们可以使用 KNN 算法，因为它基于相似性度量。我们的 KNN 模型将找到新数据集与猫狗图像的相似特征，基于它在猫或狗类别中找到的最相似特征。

# KNN 分类器

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_93_0.png)

# 3.2.2 KNN算法的 Python 实现

为了完成 K-NN 算法的实现，我们将使用在逻辑回归中使用过的相同问题和数据集。但我们将提高模型的能力。以下是问题描述：

- K-NN 算法问题：有一家汽车制造商制造了一款新 SUV。公司想向对购买 SUV 感兴趣的用户投放广告。对于这个问题，我们有一个通过社交网络包含多个用户信息的数据集。该数据集包含大量信息，但预估薪资（Estimated Salary）、学位（degree）和购买（Purchased）变量是因变量。

| User ID | Gender | Age | EstimatedSalary | Purchased |
|---|---|---|---|---|
| 16245100 | Male | 15 | 19000 | 0 |
| 1580944 | Male | 35 | 25000 | 0 |
| 1568675 | Female | 26 | 43000 | 0 |
| 1603246 | Female | 27 | 57000 | 0 |
| 1580402 | Male | 19 | 76000 | 0 |
| 1572377 | Male | 27 | 58000 | 0 |
| 1598044 | Female | 27 | 84000 | 0 |
| 1694929 | Female | 32 | 150000 | 1 |
| 1540715 | Male | 25 | 33000 | 0 |
| 1572111 | Female | 26 | 80000 | 0 |
| 1558044 | Female | 35 | 65000 | 0 |
| 1570769 | Female | 26 | 52000 | 0 |
| 1560274 | Female | 31 | 20000 | 0 |
| 1575367 | Male | 32 | 18000 | 0 |
| 1562892 | Male | 18 | 82000 | 0 |
| 1567986 | Male | 29 | 80000 | 0 |
| 1571383 | Male | 45 | 25000 | 1 |
| 1561822 | Male | 46 | 26000 | 1 |
| 1570453 | Female | 48 | 28000 | 1 |
| 15621083 | Male | 45 | 22000 | 1 |
| 15623987 | Female | 47 | 49000 | 1 |

- 实现 KNN算法的步骤：
  i. 数据预处理步骤
  ii. 在训练集上拟合 K-NN 算法
  iii. 预测测试结果
  iv. 测试准确率（混淆矩阵）
  v. 可视化测试结果

- 数据预处理步骤：处理步骤与逻辑回归相同。

```python
# 库
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# 数据提取
dataSet = pd.read_csv("Social_Network_Ads.csv")
X = dataSet.iloc[:, [2, 3]]
y = dataSet.iloc[:, 4]
```

```python
from sklearn.model_selection import train_test_split
# 测试集占1/4
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25, random_state=0)
```

```python
# 特征缩放
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_94_0.png)

在训练数据上拟合 KNN分类器：我们将从 sklearn 库导入 KNeighborsClassifier。导入该类后，我们将创建该类的对象。该类的参数为：
- n_neighbors：定义算法所需的数量。
- metric='euclidean'：这是默认参数，决定点之间的距离。
- p=2：等同于标准距离。

然后我们将分类器拟合到训练数据。以下是代码：

```python
# 在训练集上拟合 K-NN 分类器
from sklearn.neighbors import KNeighborsClassifier
cls = KNeighborsClassifier(p=2, metric='euclidean', n_neighbors=5)
cls.fit(X_train, y_train)
```

预测测试结果：为了预测测试结果，我们将像逻辑回归一样获取 y_pred 向量。以下是代码：

```python
# 预测测试集
y_pred = cls.predict(X_test)
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_94_1.png)

```python
# 创建混淆矩阵：在下面，我们将导入 confusion_matrix 并使用变量调用它。
# 使用 "confusion_matrix" 函数创建混淆矩阵
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_test, y_pred)
# cm 的参数：y_true 真实值，y_pred 预测值
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_94_2.png)

我们可以看到 64+29=93 次正确预测，3+4=7 次错误预测，而在逻辑回归中，有 11 次错误预测。因此，我们可以说使用 K-NN 算法改进了模型的性能。

可视化训练集结果：现在，我们将使用 K-NN 模型对训练集可视化。代码与逻辑回归相同，除了代码名称外。以下代码用于：

```python
# 可视化训练集
from matplotlib.colors import ListedColormap
X_set, y_train = X_train, y_train
X1, X2 = np.meshgrid(np.arange(start=X_set[:,0].min() - 1, stop=X_set[:,0].max() + 1, step=0.01), np.arange(start=X_set[:,1].min() - 1, stop=X_set[:,1].max() + 1, step=0.01))
plt.contour(X1, X2, cls.predict(np.c_[X1.ravel(), X2.ravel()]).reshape(X1.shape), cmap=ListedColormap(('red', 'green')), alpha=0.35)
plt.xlim(X1.min(), X1.max())
plt.ylim(X2.min(), X2.max())
for i, j in enumerate(np.unique(y_train)):
    plt.scatter(X_set[:,0]==j, X_set[:,1]==j, c=ListedColormap(('red', 'green'))(i), label=j)
plt.title('KNN (Training set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

可视化测试集结果：训练完成后，我们现在使用新数据集（即测试集）来测试结果。代码与逻辑回归相同，仅此处：x_test 和 y_train 将替换为 x_test 和 y_test。

```python
# 可视化测试集结果
from matplotlib.colors import ListedColormap
X_set, y_test = X_test, y_test
X1, X2 = np.meshgrid(np.arange(start=X_set[:,0].min() - 1, stop=X_set[:,0].max() + 1, step=0.01), np.arange(start=X_set[:,1].min() - 1, stop=X_set[:,1].max() + 1, step=0.01))
plt.contour(X1, X2, cls.predict(np.c_[X1.ravel(), X2.ravel()]).reshape(X1.shape), cmap=ListedColormap(('red', 'green')), alpha=0.35)
plt.xlim(X1.min(), X1.max())
plt.ylim(X2.min(), X2.max())
for i, j in enumerate(np.unique(y_test)):
    plt.scatter(X_set[:,0]==j, X_set[:,1]==j, c=ListedColormap(('red', 'green'))(i), label=j)
plt.title('KNN (Test set)')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

