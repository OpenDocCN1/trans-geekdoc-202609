

# 库

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```

# 数据提取
dataset = pd.read_csv("Network_Ads.csv")
X = dataset.iloc[:, [2, 3]].values
Y = dataset.iloc[:, [4]].values

# 数据划分
from sklearn.model_selection import train_test_split
X_train, X_test, Y_train, Y_train = train_test_split(X, Y, test_size=0.25, random_state=0)

# 特征缩放
from sklearn.preprocessing import StandardScaler
st = StandardScaler()
X_train = st.fit_transform(X_train)
X_test = st.transform(X_test)

# 应用 Kernel-PCA：无监督
from sklearn.decomposition import KernelPCA
kernel_pca = KernelPCA(n_components=2, kernel="rbf")
X_train = kernel_pca.fit_transform(X_train)
X_test = kernel_pca.transform(X_test)

# 将数据集拟合到逻辑回归
from sklearn.linear_model import LogisticRegression
classifier = LogisticRegression(random_state=0)
classifier.fit(X_train, Y_train)

# 预测
Y_pred = classifier.predict(X_test)

# 构建混淆矩阵
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(Y_test, Y_pred)

# 可视化结果
from matplotlib.pyplot import Listedormap
X_set, Y_set = X_test, Y_test
X1, X2 = np.meshgrid(np.arange(X_set[:, 0].min(), X_set[:, 0].max() + 0.01),
                     np.arange(Y_set[:, 1].min(), Y_set[:, 1].max() + 0.01))
plt.contourf(X1, X2, classifier.predict_proba(np.c_[X1.ravel(), X2.ravel()]).T, alpha=0.3, cmap=Listedormap)
plt.scatter(X_set[:, 0], X_set[:, 1])
plt.title("应用 kernel-PCA 的逻辑回归")
plt.xlabel("PC1 : kernel-PCA 后的年龄")
plt.ylabel("PC2 : kernel-PCA 后的估计薪资")
plt.legend()
plt.show()

for i, j in enumerate(np.unique(Y_pred)):
    plt.scatter(X_test[y == j], Y_test[y == j], c=Listedormap(['red', 'green'])[i], label=j)
plt.title('应用 Kernel-PCA 的逻辑回归（测试集）')
plt.xlabel('PC1: kernel-PCA 后的年龄')
plt.ylabel('PC2: kernel-PCA 后的估计薪资')
plt.show()
```

# python kernel_pca.py

- 因此，当我们处理某些线性不可分的数据时（例如原始数据集中被蓝点包围的红点），通过应用 Kernel-PCA，我们可以使其变得完全线性可分。
- **我们可以将 Kernel-PCA 视为：** 我们正在使用核技巧（kernel trick）将不可分的数据集映射到更高维，并找到一个平面/空间，使得我们的数据点的投影是线性可分的。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_343.png)

https://towardsdatascience.com/dimension-reduction-techniques-with-python

# 第11 章：第一部分

## 模型选择：K折交叉验证、网格搜索

### 11.1 评估与改进模型性能

- **模型参数与超参数**：在机器学习模型中，我们有两种参数：模型参数和超参数。
- **模型参数**：这些是模型通过运行来学习并找到最优值的参数。
- **超参数**：这类参数是由我们自己选择的参数。例如，核惩罚参数或某些正则化参数。

因此，模型仍有改进空间，因为我们仍然为这些参数选择最优值。在本章中，我们将做两件事：

- [1]. **评估我们的模型性能**：为了高效地评估模型，我们使用 K 折交叉验证（K-fold Cross-validation）而不是仅仅进行训练-测试集划分。然后为了调整超参数，我们将使用网格搜索（Grid Search）。
- [2]. **改进我们的模型性能**：我们将使用机器学习中最强大的算法 XGBoost。
- **改进模型性能**可以通过称为“模型选择”的技术来实现。它由选择你机器学习模型的最佳参数。
- **网格搜索**：由于模型参数是由模型学习的，因此我们需要找到一种为这些超参数选择最优值的方法。网格搜索是调用的强大技术之一。
- **K折交叉验证**：在开始网格搜索之前，我们需要优化评估模型的方法。之前，我们将数据集划分为训练集和测试集。我们在训练集上训练，并在测试集上测试其性能。这是评估模型性能的一种正确方法。
- 但这不是最好的，因为我们实际上存在方差问题。
- 方差问题可以解释为：我们拥有测试集上的准确率。如果我们再次运行模型并在另一个测试集上测试，将得到非常不同的准确率。
- 因此，仅根据一个测试集来判断模型性能实际上不是一个好主意。这不是评估模型性能最相关的方法。
- **K折交叉验证**：K 折交叉验证是一种通过将训练集划分为 K 折来解决方差问题的技术。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_344.png)

# 折数：大多数情况下 K = 10，我们对一个新折训练模型，并在剩余的折上进行测试。

迭代次数：由于我们有 10 折，我们可以组合出 10 种不同的组合来训练模型。一旦我们在所有训练和测试集的组合（10 次迭代）上训练并测试模型，我们就会得到 10 种不同的准确率。我们取这 10 种准确率的平均值，并计算标准差。这让我们能更好地了解模型的性能。

## 偏差-方差权衡 (Bias-Variance tradeoff)

最终，我们的分析将更相关性，我们将知道这些类别属于：
- 高准确率（低偏差）和低方差 - 左下角
- 高准确率和高方差 - 右下角
- 低准确率（高偏差）和方差 - 左上角
- 低准确率和高方差 - 右上角

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_344.png)

（注：后续部分文本内容大量重复且无意义，未予翻译）

