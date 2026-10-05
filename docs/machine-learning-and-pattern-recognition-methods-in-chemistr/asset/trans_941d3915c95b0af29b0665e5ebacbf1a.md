

# Python 简介

（由组合、转换和分布特征组成），联合三元准序列序序列序列（包含顺序耦合数和准序列序描述符），以及伪氨基酸组成（由伪氨基酸组成和伪氨基酸特征组成）。此外，它还为小分子计算了13组特征组，包括组成、拓扑、连接性、E-state、kappa、负载、信息、自相关、电荷、属性、MOE 类型和指纹。此外，分别有三种和两种方法构建蛋白质-蛋白质和蛋白质-配体作用网络的交互描述符。

# 4. pyMCR

Camp Jr (2019) 引入了一个用于交替回归多元曲线解析的 Python库，称为 pyMCR。该软件库用 Python 编写，允许用户执行多元曲线解析（MCR）分析，允许用户选择用于最小化的误差函数、约束条件和回归器。

# 5. DeepChem

DeepChem 是一个开源框架，最早由斯坦福大学的 Bharath Ramsdumar 创建。现在，它由一组开发者维护；然而，任何人都可以加入并贡献。该项目使用 TensorFlow 创建深度学习模型。它的开发目的是方便研究人员在药物发现、生物学和生命科学领域开发新的基于深度学习的算法。DeepChem 提供了许多用于算法开发的 API。这些 API 包括：

(1) data（处理数据）
(2) features：从输入数据中提取特征以供机器学习模型使用。DeepChem 同时提供数据驱动（如图卷积特征）和非数据驱动的方法（如 CircularFingerprint、PubChemFingerprint、Mol2Fingerprint 和 RDKDescriptors）。
(3) Scikit-learn 模型，
(4) Keras 模型，
(5) PyTorch 模型，
(6) Transformers：提供 transformer 对象，通过对输入数据的每个部分进行加权以强调重要部分，
(7) 超参数调优，以及
(8) 强化学习：强化学习是机器学习中一种强大的技术：DeepChem 提供了一个实用的框架用它解决计算生物学问题。此外，还有许多有用的 API 以及相应的文档可以在 https://deepchem.readdocs.io/en/latest/ 中找到。

# 6. Scikit-learn

Scikit-learn 是 Python 中的一个机器学习包，它是开源的，并在 BSD 许可证下可以商业化使用。该包包含许多有用对象，包括预处理、分类、回归、降维、聚类和模型选择。该包的最后一个版本是 scikit-learn 1.0.1，于 2021 年 10 月发布。它基于 NumPy、SciPy 和 matplotlib 构建，并提供了许多用于数据可视化工具。

# 7. 示例

在本节中，使用“sklearn”包提供了三个示例（降维、部分最小二乘 (PLS) 和聚类分析）。

# 7.1 降维

在本节中解释了使用主成分分析（PCA）进行降维。在降维中，主要目标是将输入数据投影到一个低维的新空间中，以保留输入数据最重要的知识。降维方法分为两类：特征选择和特征投影（即特征提取）。有许多算法。在本节中，实际解释了特征投影类中的 PCA。最后，选择了一个玩具数据集，然后解释了如何将 PCA 应用于其以减少的步骤。

在 Python 中，第一步，你应该导入运行代码所需的库。在这里，我们需要“numpy”、“sklearn”（用于使用 PCA 和加载一个机器学习玩具数据集）以及“matplotlib”（用于显示结果）库。

```python
import numpy as np
from sklearn import datasets
from sklearn.decomposition import PCA
import matplotlib.pyplot as plt
```

在下一步，选择你想要应用 PCA 的玩具数据集。在本节中，我们选择了 IRIS 数据集，它包含三类 150 个样本，具有四个特征。

```python
from sklearn.datasets import load_iris
data = load_iris()
```

接下来，创建一个 PCA 对象，并通过以下命令对数据进行拟合：

```python
from sklearn.decomposition import PCA
pca = PCA(n_components=2)
data_reduced = pca.fit_transform(data.data)
```

需要注意的是，PCA 类接收一个参数 "n_components"，它决定了新数据空间的维度。现在，为了评估在数据上的执行情况，通过“matplotlib”包对投影数据进行可视化。

```python
import matplotlib.pyplot as plt
idx = np.arg.where(data.target==0)
plt.scatter(data_reduced[idx,0],data_reduced[idx,1],color='blue')
idx = np.arg.where(data.target==1)
plt.scatter(data_reduced[idx,0],data_reduced[idx,1],color='red')
idx = np.arg.where(data.target==2)
plt.scatter(data_reduced[idx,0],data_reduced[idx,1],color='purple')
plt.gca().set(title="PCA on IRIS Dataset",xlabel='Feature1', ylabel='Feature2')
plt.legend()
plt.show()
```

通过运行这段代码，出现了图 A.1。

![](img/1aed977a858463e62fc6af1793e4677c_183_0.png)
图 A.1 IRIS 数据集上的 PCA。

# 7.2 部分最小二乘

部分最小二乘（PLS）是回归中当相关变量数量较高时的一种已知技术。在本节中，给出了 PLS 的示例。要使用它，我们需要下载并读取数据。在第一步，应该按所示导入必要的库：

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.preprocessing import scale
from sklearn.model_selection import RepeatedFold
from sklearn.decomposition import PLSRegression
```

接下来，读取数据：

```python
data_url = "https://archive.ics.uci.edu/ml/databases/026/CASP.csv"
raw_df = pd.read_csv(data_url, header=None)
data = raw_df.values[1::10]
data = data.astype(float)
target = raw_df.values[1::0]
target = target.astype(float)
```

在这种情况下，“data”变量是一个 45730 × 9 的矩阵，而“target”变量是一个 45730 × 1 的矩阵，其中 45730 是实例数量。九预测变量（分别为总表面积、非极暴露面积、残基面积、分子质量权重暴露面积、与标准的偏差、二级结构惩罚、空间分布约束）。

确定 PLS 组件的数量。为此，对于不同数量的 PLS 组件，拟合模型，然后计算其 MSE。这样做使用了以下代码部分：

```python
cv = KFold(n_splits=5) # 注意：原文为 RepeatedFold，可能是 KFold 或 RepeatedKFold
cv = RepeatedKFold(n_splits=5)
mse=[]
for i in np.arange(1, 9):
    pls = PLSRegression(n_components=i)
    score = -1*model_selection.cross_val_score(pls, scale(data), target, cv=cv, scoring='neg_mean_squared_error').mean()
    mse.append(score)
#绘制 PLS 组件数量与 MSE 的图
plt.plot(mse)
plt.xlabel('Number of PLS Components')
plt.ylabel('MSE')
```

上述代码的输出见图 A.2。

![](img/1aed977a858463e62fc6af1793e4677c_185_0.png)
图 A.2 PLS 组件数量对蛋白质物理化学性质的影响。

# 7.3 聚类分析

在聚类分析中，将无标签数据分为若干组，使得每组内的样本相互相似。在文献中，有很多聚类算法（Mouton, Ferreira, & Helberg, 2020; Xu & Tian, 2015）。在本节中，给出了聚类的示例并使用 k-means 作为聚类算法。因此，需要一个无标签数据集来拟合

