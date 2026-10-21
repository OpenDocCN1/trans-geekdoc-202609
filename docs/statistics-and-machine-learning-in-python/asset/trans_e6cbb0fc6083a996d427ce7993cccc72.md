

## 7.5 两两关联的非参数检验

### 7.5.1 Spearman秩相关（定量 ~ 定量）

Spearman相关是一种衡量两个数据集之间关系单调性的非参数度量。

何时使用？观察数据分布：
- 存在离群值
- 残差的分布不是高斯分布。

与其他相关系数一样，该系数的取值范围在-1到+1之间，0表示不相关。相关系数为-1或+1表示完全单调关系。正相关意味着随着x增大，y也增大；负相关意味着随着x增大，y减小。

```
import numpy as np
import scipy.stats as stats
import matplotlib.pyplot as plt

x = np.array([44.4, 45.9, 41.9, 53.3, 44.7, 44.1, 50.7, 45.2, 46, 47, 48, 60.1])
y = np.array([2.6, 3.1, 2.5, 5.0, 3.6, 4.0, 5.2, 2.8, 4, 4.1, 4.5, 3.8])

plt.plot(x, y, "bo")

# Non-Parametric Spearman
cor, pval = stats.spearmanr(x, y)
print("Non-Parametric Spearman cor test, cor: %.4f, pval: %.4f" % (cor, pval))

# Parametric Pearson cor test
cor, pval = stats.pearsonr(x, y)
print("Parametric Pearson cor test: cor: %.4f, pval: %.4f" % (cor, pval))
```

非参数Spearman相关检验，相关系数：0.7110，p值：0.0095
参数Pearson相关检验：相关系数：0.5263，p值：0.0788

![](img/c2ad4b400bf63af9804b2d44510f76a6_94_0.png)

### 7.5.2 Wilcoxon符号秩检验（定量 ~ 常数）

来源：https://en.wikipedia.org/wiki/Wilcoxon_signed-rank_test

Wilcoxon符号秩检验是一种非参数统计假设检验，用于比较两个相关样本、配对样本或对单个样本的重复测量，以评估它们的总体平均秩是否存在差异（即它是一种配对差异检验）。它等价于对配对样本差值进行单样本检验。

当总体不能假定为正态分布时，它可以用作配对Student t检验、配对t检验或依赖样本t检验的替代方法。

何时使用？观察数据分布：
- 存在离群值
- 残差的分布不是高斯分布

与t检验相比，它的敏感性较低。当样本量较小时使用可能会有问题。

零假设H0：配对之间的差值服从关于零对称的分布。

```
import scipy.stats as stats
n = 20
# Business Volume time 0
bv0 = np.random.normal(loc=3, scale=.1, size=n)
# Business Volume time 1
bv1 = bv0 + 0.1 + np.random.normal(loc=0, scale=.1, size=n)

# create an outlier
bv1[0] -= 10

# Paired t-test
print(stats.ttest_rel(bv0, bv1))

# Wilcoxon
print(stats.wilcoxon(bv0, bv1))
```

```
Ttest_relResult(statistic=0.7676263474825586, pvalue=0.4521440652558284)
WilcoxonResult(statistic=34.0, pvalue=0.0080344288555667)
```

### 7.5.3 Mann-Whitney U检验（定量 ~ 分类（2个水平））

在统计学中，Mann-Whitney U检验（也称为Mann-Whitney-Wilcoxon检验、Wilcoxon秩和检验或Wilcoxon-Mann-Whitney检验）是一种非参数检验，用于检验零假设：两个样本来自同一总体，对立假设是特别地某个总体往往比另一个总体有更大的值。

与只能应用于正态分布的t检验不同，它可以应用于未知分布，并且在正态分布上其效率几乎与t检验相当。

```
import scipy.stats as stats
n = 20
# Business Volume group 0
bv0 = np.random.normal(loc=1, scale=.1, size=n)

# Business Volume group 1
bv1 = np.random.normal(loc=1.2, scale=.1, size=n)
```

```
# create an outlier
bv1[0] = 10

# Two-samples t-test
print(stats.ttest_ind(bv0, bv1))

# Wilcoxon
print(stats.mannwhitneyu(bv0, bv1))
```

```
Ttest_indResult(statistic=0.602260825054143, pvalue=0.5505776381778786)
MannwhitneyuResult(statistic=51.0, pvalue=2.9479586089607507e-05)
```

## 7.6 线性模型

![](img/c2ad4b400bf63af9804b2d44510f76a6_96_0.png)

图7.3：线性模型

给定n个随机样本 (yᵢ, x₁ᵢ, …, xₚᵢ)，i = 1, …, n，线性回归将观测值yᵢ与自变量xᵢᵖ之间的关系建模为

yᵢ = β₀ + β₁x₁ᵢ + ⋯ + βₚxₚᵢ + εᵢ      i = 1, …, n

- β是模型参数，即回归系数。
- β₀是截距或偏置。
- εᵢ是残差。
- **自变量（IV）**。它是一个独立存在的变量，不会因你试图测量的其他变量而改变。例如，某人的年龄可能就是一个自变量。其他因素（如他们吃什么、上多少学、看多少电视）不会改变一个人的年龄。事实上，当你寻找变量之间的某种关系时，你是在试图观察自变量是否会引起其他变量（或因变量）的某种变化。在机器学习中，这些变量也被称为**预测变量**。
- **因变量**。它依赖于其他因素。例如，考试成绩可以是一个因变量，因为它可能随多个因素变化，比如你学习了多少、考试前夜睡了多久，甚至考试时有多饿。通常，当你寻找两件事之间的关系时，你是在试图找出是什么导致因变量如此变化。在机器学习中，这个变量被称为**目标变量**。

### 7.6.1 简单回归：检验两个定量变量之间的关联

使用数据集“salary”，探索因变量（如Salary）和自变量（如Experience是定量的）之间的关联。

```python
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline

url = 'https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/salary_table.csv'
salary = pd.read_csv(url)
```

### 1. 对数据建模

根据某个假设对数据建模，例如：工资是经验的线性函数。

salary_i = β experience_i + β0 + ε_i,

更一般地

y_i = β x_i + β0 + ε_i

- β：模型的斜率或系数或参数，
- β0：截距或偏置，是模型的第二个参数，
- ε_i：第i个误差或残差，其中ε ~ N(0, σ²)。

简单回归等价于Pearson相关。

### 2. 拟合：估计模型参数

目标是估计β、β0和σ²。

最小化均方误差（MSE）或误差平方和（SSE）。所谓的普通最小二乘法（OLS）找到使SSE = Σ_i ε_i²最小的β、β0。

SSE = Σ_i (y_i - β x_i - β0)²

根据微积分知识，极值点可以通过计算导数为零的位置找到，即为了找到截距，我们执行以下步骤：

∂SSE/∂β0 = Σ_i (y_i - β x_i - β0) = 0
Σ_i y_i = β Σ_i x_i + n β0
n ȳ = n β x̄ + n β0
β0 = ȳ - β x̄

为了找到回归系数，我们执行以下步骤：

∂SSE/∂β = Σ_i x_i (y_i - β x_i - β0) = 0

![](img/c2ad4b400bf63af9804b2d44510f76a6_99_0.png)

使用seaborn

![](img/c2ad4b400bf63af9804b2d44510f76a6_99_1.png)

### 3. F检验

### 3.1 拟合优度

统计模型的拟合优度描述了它拟合一组观测值的程度。拟合优度的度量通常概括了观测值与所讨论模型下预期值之间的差异。我们将考虑**解释方差**，也称为决定系数，记为$R^2$，读作**R平方**。

总平方和$SS_{tot}$是回归解释的平方和$SS_{reg}$加上回归未解释的残差平方和$SS_{res}$（也称为SSE）之和，即

$SS_{tot} = SS_{reg} + SS_{res}$

![](img/c2ad4b400bf63af9804b2d44510f76a6_100_0.png)

图7.4：标题

$y$的均值为

$\bar{y} = \frac{1}{n} \sum_{i} y_i.$

总平方和是$y$的均值偏差的平方和，即

$SS_{tot} = \sum_{i} (y_i - \bar{y})^2$

回归平方和，也称为解释平方和：

$SS_{reg} = \sum_{i} (\hat{y}_i - \bar{y})^2,$

其中$\hat{y}_i = \beta x_i + \beta_0$是给定经验值$x_i$时工资$\hat{y}_i$的估计值。

残差平方和，也称为残差平方和（RSS）为：

$SS_{res} = \sum_{i} (y_i - \hat{y}_i)^2.$

$R^2$是解释的误差平方和。它是回归解释的方差除以总方差，即

$R^2 = \frac{\text{explained SS}}{\text{total SS}} = \frac{SS_{reg}}{SS_{tot}} = 1 - \frac{SS_{res}}{SS_{tot}}.$

### 3.2 检验

令$\hat{\sigma}^2 = SS_{res}/(n - 2)$为$\epsilon$方差的估计量。分母中的2源于两个估计参数：截距和系数。

