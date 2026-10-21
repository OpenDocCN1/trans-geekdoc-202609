

![](img/c2ad4b400bf63af9804b2d44510f76a6_169_0.png)

## 11.4 模型选择

### 11.4.1 贝叶斯信息准则

在统计学中，贝叶斯信息准则（BIC）是在有限模型集合中进行模型选择的准则；BIC 最低的模型更受青睐。它部分基于似然函数，并且与赤池信息准则（AIC）密切相关。

```
X = iris.data
 y_iris = iris.target

 bic = list()
 #print(X)

 ks = np.arange(1, 10)

 for k in ks:
     gmm = GaussianMixture(n_components=k, covariance_type='full')
     gmm.fit(X)
     bic.append(gmm.bic(X))

 k_chosen = ks[np.argmin(bic)]

 plt.plot(ks, bic)
 plt.xlabel("k")
 plt.ylabel("BIC")

 print("Choose k=", k_chosen)
```

选择 k= 2

![](img/c2ad4b400bf63af9804b2d44510f76a6_170_0.png)

## 11.5 练习

使用高斯混合模型，基于所有变量对鸢尾花数据集执行聚类。使用 PCA 可视化聚类结果。

## 回归的线性方法

## 12.1 普通最小二乘法

线性回归将**输出**或**目标**变量 $y \in \mathbb{R}$ 建模为 $(P-1)$ 维输入 $x \in \mathbb{R}^{(P-1)}$ 的线性组合。设 $\mathbf{X}$ 为 $N \times P$ 矩阵，每一行是一个输入向量（第一个位置为 1），类似地，设 $y$ 为**训练集**中输出的 $N$ 维向量，线性模型将根据**参数向量**或**权重向量** $\beta \in \mathbb{R}^P$ 使用如下公式预测给定 $\mathbf{X}$ 的 $\mathbf{y}$：

$$\mathbf{y} = \mathbf{X}\beta + \varepsilon,$$

其中 $\varepsilon \in \mathbb{R}^N$ 是**残差**，即预测的误差。通过最小化**目标函数**（即**损失函数** $\mathcal{L}(\beta)$，也就是在数据上测得的误差）来求解 $\beta$。该误差是**平方误差和（SSE）**损失。最小化 SSE 即为普通最小二乘（OLS）回归的目标函数。

$$\begin{aligned}
\text{OLS}(\beta) &= \mathcal{L}(\beta) && (12.1)\\
&= \text{SSE}(\beta) && (12.2)\\
&= \sum_{i}^{N}(y_i - \mathbf{x}_i^T \beta)^2 && (12.3)\\
&= (\mathbf{y} - \mathbf{X}\beta)^T (\mathbf{y} - \mathbf{X}\beta) && (12.4)\\
&= \|\mathbf{y} - \mathbf{X}\beta\|_2^2, && (12.5)
\end{aligned}$$

这是一个简单的**普通最小二乘（OLS）**最小化问题。

## 12.2 使用 scikit-learn 进行线性回归

Scikit-learn 为监督学习提供了许多模型，它们都遵循相同的应用程序编程接口（API），即：

```
model = Estimator()
model.fit(X, y)
predictions = model.predict(X)
```

```
%matplotlib inline
import warnings
warnings.filterwarnings(action='once')
```

```
from mpl_toolkits.mplot3d import Axes3D
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import sklearn.linear_model as lm
import sklearn.metrics as metrics
%matplotlib inline

# Fit Ordinary Least Squares: OLS
csv = pd.read_csv('https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/Advertising.csv', index_col=0)
X = csv[['TV', 'Radio']]
y = csv['Sales']

lr = lm.LinearRegression().fit(X, y)
y_pred = lr.predict(X)
print("R-squared =", metrics.r2_score(y, y_pred))

print("Coefficients =", lr.coef_)

# Plot
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

ax.scatter(csv['TV'], csv['Radio'], csv['Sales'], c='r', marker='o')

xx1, xx2 = np.meshgrid(
    np.linspace(csv['TV'].min(), csv['TV'].max(), num=10),
    np.linspace(csv['Radio'].min(), csv['Radio'].max(), num=10))

XX = np.column_stack([xx1.ravel(), xx2.ravel()])

yy = lr.predict(XX)
ax.plot_surface(xx1, xx2, yy.reshape(xx1.shape), color='None')
ax.set_xlabel('TV')
ax.set_ylabel('Radio')
_ = ax.set_zlabel('Sales')
```

/home/edouard/anaconda3/lib/python3.6/site-packages/_pytest/fixtures.py:844:
DeprecationWarning: The convert argument is deprecated in favor of converter.
It will be removed after 2019/01.
    params = attr.ib(convert=attr.converters.optional(tuple))

```
R-squared = 0.8971942610828956
Coefficients = [0.04575482 0.18799423]
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_174_0.png)

## 12.3 过拟合

在统计学和机器学习中，当过拟合发生时，统计模型描述的是随机误差或噪声，而非潜在的关联关系。过拟合通常发生在模型**过于复杂**时，例如**相对于观测数量参数过多**。发生过拟合的模型通常预测性能较差，因为它可能夸大数据中的细微波动。

学习算法使用某些训练样本进行训练。如果学习算法具有过拟合训练样本的能力，则在**训练样本集**上的表现会提高，而在未见过的**测试样本集**上的表现则会下降。

过拟合现象主要有三种解释：

- 模型过于复杂
- 多重共线性
- 高维性

### 12.3.1 模型复杂度

相对于观测数量而言参数过多的复杂学习器可能会过拟合训练数据集。

### 12.3.2 多重共线性

预测变量高度相关，意味着其中一个可以由其他预测变量线性预测。在这种情况下，多元回归的系数估计可能因模型或数据的微小变化而剧烈变动。多重共线性不会降低模型整体的预测能力或可靠性，至少在样本数据集内如此；它仅影响与单个预测变量相关的计算。也就是说，具有相关预测变量的多元回归模型可以表明整个预测变量组对结果变量的预测效果，但可能无法提供关于任何单个预测变量的有效结果，也无法说明哪些预测变量相对于其他变量是冗余的。在完全多重共线性的情况下，预测变量矩阵是奇异的，因此无法求逆。在这种情况下，对于一般线性模型 y = Xβ + ε，普通最小二乘估计量 β_OLS = (X^T X)^{-1} X^T y 不存在。

下面是一个相关预测变量可能产生不稳定模型的示例：

```
import numpy as np
from mpl_toolkits.mplot3d import Axes3D
import matplotlib.pyplot as plt

bv = np.array([10, 20, 30, 40, 50])            # business volume
tax  = .2 * bv                                 # Tax
bp = .1 * bv + np.array([-.1, .2, .1, -.2, .1]) # business potential

X = np.column_stack([bv, tax])
beta_star = np.array([.1, 0])  # true solution

'''
Since tax and bv are correlated, there is an infinite number of linear combinations
leading to the same prediction.
'''

# 10 times the bv then subtract it 9 times using the tax variable:
beta_medium = np.array([.1 * 10, -.1 * 9 * (1/.2)])
# 100 times the bv then subtract it 99 times using the tax variable:
beta_large = np.array([.1 * 100, -.1 * 99 * (1/.2)])

# Check that all model lead to the same result
assert np.all(np.dot(X, beta_star) == np.dot(X, beta_medium))
assert np.all(np.dot(X, beta_star) == np.dot(X, beta_large))
```

预测变量之间的多重共线性：业务量和税收会产生具有任意大系数的不稳定模型。

![](img/c2ad4b400bf63af9804b2d44510f76a6_176_0.png)

### 处理多重共线性

- 通过例如 ℓ₂ 收缩进行正则化：通过使 $(X^T X)^{-1}$ 非奇异来在解中引入偏差。参见 ℓ₂ 收缩。
- 特征选择：选择少量特征。参见：Isabelle Guyon 和 André Elisseeff *An introduction to variable and feature selection* The Journal of Machine Learning Research, 2003。
- 特征选择：使用 ℓ₁ 收缩选择少量特征。
- 使用例如主成分分析（PCA）、偏最小二乘回归（PLS-R）或能够将预测变量数量缩减为较少不相关成分的回归方法来提取少量独立（不相关）的特征。

### 12.3.3 高维性

高维度意味着大量输入特征。线性预测器为每个输入特征关联一个参数，因此高维情形（$P$，特征数量，很大）而样本数量 $N$ 相对较小（即所谓的大 $P$ 小 $N$ 情形）通常会导致对训练数据的过拟合。因此，向学习器中添加许多输入特征通常不是一个好主意。这种现象称为**维度灾难**。

在选择学习算法时，需要依据的最重要标准之一是 $P$ 和 $N$ 的相对大小。

- 请记住，线性模型中使用的“协方差”矩阵 $\mathbf{X}^T \mathbf{X}$ 是秩为 $\min(N, P)$ 的 $P \times P$ 矩阵。因此，如果 $P > N$，则方程组过度参数化，并且存在一个

