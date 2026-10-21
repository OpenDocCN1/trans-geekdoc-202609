

## 7.4.1 皮尔逊相关检验：检验两个定量变量之间的关联

检验两个定量变量的相关系数。该检验计算皮尔逊相关系数和用于检验不相关的 p 值。

设 x 和 y 是两个定量变量，观测到 n 个样本。线性相关系数定义为：

r = \frac{\sum_{i=1}^{n}(x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum_{i=1}^{n}(x_i - \bar{x})^2 \sqrt{\sum_{i=1}^{n}(y_i - \bar{y})^2}}.

在原假设 H0 下，检验统计量 t = \sqrt{n-2} \frac{r}{\sqrt{1-r^2}} 服从自由度为 n - 2 的学生分布。

```
import numpy as np
import scipy.stats as stats
n = 50
x = np.random.normal(size=n)
y = 2 * x + np.random.normal(size=n)

# Compute with scipy
cor, pval = stats.pearsonr(x, y)
```

## 7.4.2 双样本（学生）t 检验：比较两个均值

双样本 t 检验（Snedecor 和 Cochran，1989）用于确定两个总体均值是否相等。该检验有若干变体。如果数据是配对的（例如对每个个体在处理前后进行两次测量），则使用差值的单样本 t 检验。两个样本的方差可以被假定为相等（即方差齐性）或不相等（即方差不齐）。

### 1. 数据建模

假设两个随机变量服从正态分布：x ~ N(μx, σx)，y ~ N(μy, σy)。

### 2. 拟合：估计模型参数

估计均值和方差：\bar{x}, s_x^2, \bar{y}, s_y^2。

### 3. t 检验

如果我们假设方差相等，用于检验均值是否不同的 t 统计量为：

t = \frac{\bar{x} - \bar{y}}{s \cdot \sqrt{\frac{1}{n_x} + \frac{1}{n_y}}},

其中，\bar{x} 和 \bar{y} 分别是组 1 和组 2 的样本均值，并且

$s = \sqrt{\frac{s_x^2(n_x - 1) + s_y^2(n_y - 1)}{n_x + n_y - 2}}$

是两个样本共同标准差的估计量：这样定义是为了使其平方无论总体均值是否相同，都是共同方差的无偏估计量。

![](img/c2ad4b400bf63af9804b2d44510f76a6_90_0.png)

图 7.2：双样本 t 检验

### 样本量相等或不等、方差不相等（Welch's t 检验）

Welch's t 检验将 t 统计量定义为

$t = \frac{\bar{x} - \bar{y}}{\sqrt{\frac{\sigma_x^2}{n_x} + \frac{\sigma_y^2}{n_y}}}$

要计算 p 值，需要与该方差估计相关的自由度。它通过 Welch–Satterthwaite 方程近似得到：

$\nu \approx \frac{\left(\frac{\sigma_x^2}{n_x} + \frac{\sigma_y^2}{n_y}\right)^2}{\frac{\sigma_x^4}{n_x^2(n_x - 1)} + \frac{\sigma_y^4}{n_y^2(n_y - 1)}}$

### 示例

给定以下两个样本，使用标准 t 检验（假设方差相等）检验它们的均值是否相等。

```
import scipy.stats as stats
height = np.array([ 1.83,  1.83,  1.73,  1.82,  1.83,  1.73,  1.99,  1.85,  1.68,  1.87,
1.66, 1.71, 1.73, 1.64, 1.70, 1.60, 1.79, 1.73, 1.62, 1.77])
grp = np.array(["M"] * 10 + ["F"] * 10)
# Compute with scipy
print(stats.ttest_ind(height[grp == "M"], height[grp == "F"], equal_var=True))
```

```
Ttest_indResult(statistic=3.5511519888466885, pvalue=0.00228208937112721)
```

## 7.4.3 方差分析 F 检验（定量 ~ 分类（>2 个水平））

方差分析（ANOVA）提供了检验多个组的均值是否相等的统计方法，因此它将 t 检验推广到两个以上的组。ANOVA 可用于比较（检验）三个或更多均值（组或变量）的统计显著性。它在概念上类似于多个双样本 t 检验，但没那么保守。

这里我们将考虑一个自变量（即单因素方差分析）的单因素 ANOVA。

### 1. 数据建模

一家公司为了增加业务量，对三组客户样本分别采用了三种营销策略。营销部门想知道这些策略是否导致了不同的业务量增长。设 y1、y2 和 y3 为业务量增长的三个样本。

这里我们假设这三个总体分别来自三个服从正态分布的随机变量。即 Y1 ~ N(μ1, σ1)，Y2 ~ N(μ2, σ2)，Y3 ~ N(μ3, σ3)。

### 2. 拟合：估计模型参数

对 ∀i ∈ {1, 2, 3}，估计均值和方差：ȳi, σi。

### 3. F 检验

来源：https://en.wikipedia.org/wiki/F-test

ANOVA F 检验可用于评估任一策略是否在平均意义上优于或劣于其他策略，其原假设为所有四种策略产生相同的均值响应（业务量增长）。这是“综合”（omnibus）检验的一个例子，意味着通过一次检验来检测若干种可能差异中的任何一种。或者，我们可以在策略之间进行两两检验。ANOVA F 检验的优点是，我们无需预先指定要比较哪些策略，也无需为多重比较进行调整。其缺点是，如果我们拒绝原假设，我们无法知道哪些策略可以认为与其他策略有显著差异。

单因素 ANOVA F 检验统计量的公式为

F = 已解释方差 / 未解释方差

或

$F = \frac{\text{between-group variability}}{\text{within-group variability}}.$

“已解释方差”，即“组间变异性”，为

$\sum_{i} n_{i}(\bar{Y}_{i.} - \bar{Y})^{2}/(K - 1),$

其中 $\bar{Y}_{i.}$ 表示第 $i$ 组的样本均值，$n_{i}$ 是第 $i$ 组的观测数，$\bar{Y}$ 表示数据的总体均值，$K$ 表示组数。

“未解释方差”，即“组内变异性”，为

$\sum_{ij}(Y_{ij} - \bar{Y}_{i.})^{2}/(N - K),$

其中 $Y_{ij}$ 是 $K$ 组中第 $i$ 组的第 $j$ 个观测值，$N$ 是总样本量。在原假设下，该 $F$ 统计量服从自由度为 $K - 1$ 和 $N - K$ 的 $F$ 分布。如果组间变异性相对于组内变异性较大，则统计量会很大；而当各组总体均值都相同时，这种情况不太可能发生。

注意，当单因素 ANOVA F 检验只有两组时，$F = t^{2}$，其中 $t$ 是学生 $t$ 统计量。

## 7.4.4 卡方检验（$\chi^{2}$）（分类 ~ 分类）

计算卡方（$\chi^{2}$）统计量和 $p$ 值，用于检验观测列联表（交叉表）中频率的独立性原假设。将观测频率与期望列联表进行比较，期望列联表是在独立性假设下根据边际合计计算期望频率而得到的。

示例：20 名参与者：10 名接触过某种化学产品，10 名未接触（exposed = 1 或 0）。在这 20 名参与者中，10 人患癌症，10 人未患（cancer = 1 或 0）。$\chi^{2}$ 检验这两个变量之间的关联。

```
import numpy as np
import pandas as pd
import scipy.stats as stats

# Dataset:
# 15 samples:
# 10 first exposed
exposed = np.array([1] * 10 + [0] * 10)
# 8 first with cancer, 10 without, the last two with.
cancer = np.array([1] * 8 + [0] * 10 + [1] * 2)

crosstab = pd.crosstab(exposed, cancer, rownames=['exposed'],
                       colnames=['cancer'])
print("Observed table:")
print("---------------")
print(crosstab)

chi2, pval, dof, expected = stats.chi2_contingency(crosstab)
```

## Python 中的统计与机器学习，版本 0.2

```
print("Statistics:")
print("----------")
print("Chi2 = %f, pval = %f" % (chi2, pval))
print("Expected table:")
print("---------------")
print(expected)
```

观测表：
---------------

| 暴露 | 癌症 0 | 癌症 1 |
|---|---|---|
| 0 | 8 | 2 |
| 1 | 2 | 8 |

统计量：
----------
Chi2 = 5.000000, pval = 0.025347
期望表：
----------------
[[5. 5.]
 [5. 5.]]

### 计算期望交叉表

```
# Compute expected cross-table based on proportion
exposed_marg = crosstab.sum(axis=0)
exposed_freq = exposed_marg / exposed_marg.sum()

cancer_marg = crosstab.sum(axis=1)
cancer_freq = cancer_marg / cancer_marg.sum()

print('Exposed frequency? Yes: %.2f' % exposed_freq[0],
    'No: %.2f' % exposed_freq[1])
print('Cancer frequency? Yes: %.2f' % cancer_freq[0],
    'No: %.2f' % cancer_freq[1])

print('Expected frequencies:')
print(np.outer(exposed_freq, cancer_freq))

print('Expected cross-table (frequencies * N): ')
print(np.outer(exposed_freq, cancer_freq) * len(exposed))
```

暴露频率？是：0.50 否：0.50
癌症频率？是：0.50 否：0.50
期望频率：
[[0.25 0.25]
 [0.25 0.25]]
期望交叉表（频率 × N）：
[[5. 5.]
 [5. 5.]]

