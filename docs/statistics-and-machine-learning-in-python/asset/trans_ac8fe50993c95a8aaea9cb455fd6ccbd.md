
- 未解释方差：\(\frac{SS_{\text{res}}}{\sigma^2} \sim \chi^2_{n-2}\)
- 解释方差：\(\frac{SS_{\text{reg}}}{\sigma^2} \sim \chi^2_1\)。单一自由度来自 \(\frac{SS_{\text{tot}}}{\sigma^2} (\sim \chi^2_{n-1})\) 与 \(\frac{SS_{\text{res}}}{\sigma^2} (\sim \chi^2_{n-2})\) 之间的差值，即 \((n-1) - (n-2)\) 自由度。

两个方差比率的 Fisher 统计量：

\[
F = \frac{\text{Explained variance}}{\text{Unexplained variance}} = \frac{SS_{\text{reg}}/1}{SS_{\text{res}}/(n-2)} \sim F(1, n-2)
\]

使用 \(F\) 分布，计算在 \(H_0\) 下观察到大于 \(F\) 的值的概率，即 \(P(x > F \mid H_0)\)，即给定 \(F\) 分布在 \(x\) 处的生存函数（\(1 - \text{CDF}\)）。

## 7.6.2 多元回归

### 理论

多元线性回归是最基本的监督学习算法。

给定：一组训练数据 \(\{x_1, \dots, x_N\}\) 与对应的目标 \(\{y_1, \dots, y_N\}\)。

在线性回归中，我们假设生成数据的模型仅涉及输入变量的线性组合，即

\[
y(x_i, \beta) = \beta_0 + \beta_1 x_i^1 + \dots + \beta_P x_i^P,
\]

或，简化为

\[
y(x_i, \beta) = \beta_0 + \sum_{j=1}^{P} \beta_j x_i^j.
\]

通过为每个样本扩展截距，\(x_i := [1, x_i] \in \mathbb{R}^{P+1}\) 允许我们使用基于线性代数的更一般记号并将其写成简单的点积：

\[
y(x_i, \beta) = x_i^T \beta,
\]

其中 \(\beta \in \mathbb{R}^{P+1}\) 是定义模型 \(P+1\) 个参数的权重向量。从现在起我们有 \(P\) 个回归量 + 截距。

最小化均方误差（MSE）损失：

\[
MSE(\beta) = \frac{1}{N} \sum_{i=1}^N (y_i - y(x_i, \beta))^2 = \frac{1}{N} \sum_{i=1}^N (y_i - x_i^T \beta)^2
\]

设 \(X = [x_1^T, \dots, x_N^T]\) 为 \(N \times (P+1)\) 矩阵，包含 \(N\) 个样本的 \(P\) 个输入特征并带有一列全为 1，且设 \(y = [y_1, \dots, y_N]\) 为 \(N\) 个目标的向量。那么，利用线性代数，均方误差（MSE）损失可以重写为：

\[
MSE(\beta) = \frac{1}{N} \|y - X\beta\|_2^2.
\]

使 MSE 最小的 \(\beta\) 可以通过以下方式求得：

\[
\begin{aligned}
\nabla_\beta \left( \frac{1}{N} \|y - X\beta\|_2^2 \right) &= 0 \tag{7.6}\\
\frac{1}{N} \nabla_\beta (y - X\beta)^T (y - X\beta) &= 0 \tag{7.7}\\
\frac{1}{N} \nabla_\beta (y^T y - 2\beta^T X^T y + \beta^T X^T X \beta) &= 0 \tag{7.8}\\
-2 X^T y + 2 X^T X \beta &= 0 \tag{7.9}\\
X^T X \beta &= X^T y \tag{7.10}\\
\beta &= (X^T X)^{-1} X^T y, \tag{7.11}
\end{aligned}
\]

其中 \((X^T X)^{-1} X^T\) 是 \(X\) 的伪逆。

### 使用 NumPy 拟合

```python
import numpy as np
from scipy import linalg
np.random.seed(seed=42)  # make the example reproducible

# Dataset
N, P = 50, 4
X = np.random.normal(size=N * P).reshape((N, P))
# Our model needs an intercept so we add a column of 1s:
X[:, 0] = 1
print(X[:5, :])

betastar = np.array([10, 1., .5, 0.1])
e = np.random.normal(size=N)
y = np.dot(X, betastar) + e

# Estimate the parameters
Xpinv = linalg.pinv2(X)
betahat = np.dot(Xpinv, y)
print("Estimated beta:\n", betahat)
```

```text
[[ 1.         -0.1382643   0.64768854  1.52302986]
 [ 1.         -0.23413696  1.57921282  0.76743473]
 [ 1.          0.54256004 -0.46341769 -0.46572975]
 [ 1.        -1.91328024 -1.72491783 -0.56228753]
 [ 1.          0.31424733 -0.90802408 -1.4123037 ]]
Estimated beta:
[10.14742501  0.57938106  0.51654653  0.17862194]
```

## 7.7 使用 statsmodels 的线性模型

来源：http://statsmodels.sourceforge.net/devel/examples/

### 7.7.1 多元回归

#### 与 NumPy 的接口

```python
import statsmodels.api as sm

# Fit and summary:
model = sm.OLS(y, X).fit()
print(model.summary())

# prediction of new values
ypred = model.predict(X)

# residuals + prediction == true values
assert np.all(ypred + model.resid == y)
```

```text
----------------------------------------------------------------
ModuleNotFoundError Traceback (most recent call last)
~/anaconda3/lib/python3.6/site-packages/statsmodels/compat/pandas.py in <module>()
     52 try:
---> 53     import pandas.tseries.tools as datetools
     54     import pandas.tseries.frequencies as frequencies

ModuleNotFoundError: No module named 'pandas.tseries.tools'

During handling of the above exception, another exception occurred:

ImportError Traceback (most recent call last)
<ipython-input-46-ddfb08c06bd1> in <module>()
---> 1 import statsmodels.api as sm
      2
      3 # Fit and summary:
      4 model = sm.OLS(y, X).fit()
      5 print(model.summary())

~/anaconda3/lib/python3.6/site-packages/statsmodels/api.py in <module>()
      5 from . import regression
      6 from .regression.linear_model import OLS, GLS, WLS, GLSAR
---> 7 from .regression.recursive_ls import RecursiveLS
      8 from .regression.quantile_regression import QuantReg
      9 from .regression.mixed_linear_model import MixedLM

~/anaconda3/lib/python3.6/site-packages/statsmodels/regression/recursive_ls.py in <module>()
     14 from statsmodels.regression.linear_model import OLS
     15 from statsmodels.tools.data import _is_using_pandas
---> 16 from statsmodels.tsa.statespace.mlemodel import (
     17     MLEModel, MLEResults, MLEResultsWrapper)
     18 from statsmodels.tools.tools import Bunch

~/anaconda3/lib/python3.6/site-packages/statsmodels/tsa/statespace/mlemodel.py in <module>()
     15 from .kalman_filter import (KalmanFilter, FilterResults, INVERT_UNIVARIATE,
     16                             SOLVE_LU)
---> 17 import statsmodels.tsa.base.tsa_model as tsbase
     18 import statsmodels.base.wrapper as wrap
     19 from statsmodels.tools.numdiff import (_get_epsilon, approx_hess_cs,

~/anaconda3/lib/python3.6/site-packages/statsmodels/tsa/base/tsa_model.py in <module>()
      1 from statsmodels.compat.python import lrange, long
---> 2 from statsmodels.compat.pandas import is_numeric_dtype
      3
      4 import datetime
      5

~/anaconda3/lib/python3.6/site-packages/statsmodels/compat/pandas.py in <module>()
     54     import pandas.tseries.frequencies as frequencies
     55 except ImportError:
---> 56     from pandas.core import datetools
     57     frequencies = datetools

ImportError: cannot import name 'datetools'
```

#### 与 Pandas 的接口

使用 R 语言语法表示数据框。对于加性模型：\(y_i = \beta_0 + x_i^1\beta_1 + x_i^2\beta_2 + \epsilon_i \equiv y \sim x1 + x2\)。

```python
import statsmodels.formula.api as smf

df = pd.DataFrame(np.column_stack([X, y]), columns=['inter', 'x1', 'x2', 'x3', 'y'])

# Build a model excluding the intercept, it is implicit
model = smf.ols("y ~ x1 + x2 + x3", df).fit()
print(model.summary())
```

### 7.7.2 具有分类自变量或因子的多元回归：协方差分析（ANCOVA）

协方差分析（ANCOVA）是一种融合 ANOVA 和线性回归的线性模型。ANCOVA 评估因变量（DV）在分类自变量（IV）通常称为处理的各水平上的总体均值是否相等，同时对其他非主要兴趣的定量或连续变量即协变量（CV）的影响进行统计控制。

```python
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline

try:
    salary = pd.read_csv("../datasets/salary_table.csv")
except:
    url = 'https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/salary_table.csv'
    salary = pd.read_csv(url)
```

#### 单向 AN(C)OVA

- ANOVA：一个分类自变量，即一个因子。
- ANCOVA：带有所协变量的 ANOVA。

```python
import statsmodels.formula.api as smf

oneway = smf.ols('salary ~ management + experience', salary).fit()
print(oneway.summary())
aov = sm.stats.anova_lm(oneway, typ=2)  # Type 2 ANOVA DataFrame
print(aov)
```

#### 双向 AN(C)OVA

具有两个分类自变量的 ANCOVA，即两个因子。

```python
import statsmodels.formula.api as smf

twoway = smf.ols('salary ~ education + management + experience', salary).fit()
print(twoway.summary())
aov = sm.stats.anova_lm(twoway, typ=2)  # Type 2 ANOVA DataFrame
print(aov)
```

#### 比较两个嵌套模型

`oneway` 嵌套在 `twoway` 中。比较两个嵌套模型可以告诉我们完整模型的额外预测变量即 `education` 是否显著降低残差。这种比较可以使用残差的 F 检验进行：

```python
print(twoway.compare_f_test(oneway))  # return F, pval, df
```

#### 因子编码

参见 http://statsmodels.sourceforge.net/devel/contrasts.html

默认情况下 Pandas 使用“哑编码”。探索：

```python
print(twoway.model.data.param_names)
print(twoway.model.data.exog[:10, :])
```
