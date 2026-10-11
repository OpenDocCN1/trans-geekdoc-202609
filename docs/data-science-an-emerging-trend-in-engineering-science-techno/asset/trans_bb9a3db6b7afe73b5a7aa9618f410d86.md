
在 `print(results.summary())` 中

```
OLS 回归结果
==============================================================================
因变量:                      y   R-squared:                       0.178
模型:                            OLS   Adj. R-squared:                  0.161
方法:                 最小二乘法   F-statistic:                     10.51
日期:                Wed, 02 Nov 2022   Prob (F-statistic):           7.41e-05
时间:                        17:12:45   Log-Likelihood:                -20.926
观测数:                 100   AIC:                            47.85
残差自由度:                      97   BIC:                            55.67
模型自由度:                           2
协方差类型:            nonrobust
==============================================================================
                 coef    std err          t      P>|t|      [0.025      0.975]
------------------------------------------------------------------------------
const          1.4713      0.075     19.579      0.000       1.322       1.620
x1             0.1045      0.105      1.000      0.320      -0.103       0.312
x2             0.4831      0.107      4.503      0.000       0.270       0.696
==============================================================================
Omnibus:                       39.684   Durbin-Watson:                   1.848
Prob(Omnibus):                  0.000   Jarque-Bera (JB):                6.503
Skew:                           0.096   Prob(JB):                        0.0387
Kurtosis:                       1.766   Cond. No.                         5.09
==============================================================================
注释:
[1] 标准误假设误差的协方差矩阵已正确指定。
```

### 使用 Statsmodels 进行 Python 线性回归

线性回归分析是一种统计技术，用于根据一个变量（自变量）的值来预测另一个变量（因变量）的值。因变量是我们想要预测或预报的变量。在简单线性回归中，有一个自变量用于预测单个因变量。在多元线性回归的情况下，有不止一个自变量。自变量是你用来预测另一个变量值的变量。`statsmodels.regression.linear_model.OLS` 方法用于执行线性回归。线性方程的形式为：

$$y = mx + c$$
$$m = \text{斜率}$$
$$c = \text{常数}$$

**语法：** `statsmodels.regression.linear_model.OLS(endog, exog=None, missing='none', hasconst=None, **kwargs)`

**参数：**

*   `endog`: 类数组对象。
*   `exog`: 类数组对象。
*   `missing`: 字符串。可选项有 None、decrease 和 raise。如果值为 'none'，则不执行 nan 检测。如果选择 'drop'，则删除任何包含 nan 的观测值。如果使用 'raise'，则引发错误。'none' 为默认值。
*   `hasconst`: None 或布尔值。指示用户提供的常数是否包含在 RHS（方程右侧）中。如果为 True，则 k 常数设为 1，所有结果统计量的计算均假设存在常数。如果为 False，则 k 常数设为 0，且不验证常数。
*   `**kwargs`: 使用公式接口时，额外的参数被用于设置模型特性。

**返回：** 返回普通最小二乘法结果。

### 安装

```bash
pip install numpy
pip install pandas
pip install statsmodels
```

### 分步实现

#### 步骤 1：导入包

导入所需的包是建模的第一步。导入 pandas、NumPy 和 statsmodels 包。

```python
import numpy as np
import pandas as pd
import statsmodels.api as sm
```

#### 步骤 2：加载数据

点击[此处](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20220522225116/headbrain11.csv)访问 CSV 文件。使用 `pandas.read_csv()` 方法读取 CSV 文件。使用 `head()` 方法返回数据集的前五行（表头）。列为 Head size（头围大小）和 Brain weight（脑重量）。

```python
df = pd.read_csv('headbrain1.csv')
df.head()
```

数据框的表头如下所示：

![数据框表头](image_rsrc9WN.jpg)

#### 可视化数据

通过使用 `matplotlib` 和 seaborn 包，我们对数据进行可视化。`sns.regplot()` 函数帮助我们创建回归图。

```python
# 导入包
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('headbrain1.csv')
sns.regplot('Head Size(cm^3)', 'Brain Weight(grams)', data=df)
plt.show()
```

**输出：**

![使用 Statsmodels 进行 Python 线性回归](image_rsrc9WP.jpg)

**图 5.13 回归图**

#### 步骤 3：设定假设

*   **原假设 (H0)：** 头围大小与脑重量之间没有关系。
*   **备择假设 (Ha)：** 头围大小与脑重量之间存在关系。

#### 步骤 4：拟合模型

使用 `statsmodels.regression.linear_model.OLS()` 方法获取普通最小二乘法，并使用 `fit()` 方法拟合数据。`ols` 方法接收数据并执行线性回归。我们按以下格式提供因变量和自变量列：

`自变量列 ~ 因变量列`

`~` 运算符左侧包含自变量，右侧包含因变量的名称或预测列。

```python
df.columns = ['Head_size', 'Brain_weight']
model = smf.ols(formula='Head_size ~ Brain_weight', data=df).fit()
```

#### 步骤 5：模型摘要

线性回归模型的所有摘要统计量由 `model.summary()` 方法返回。通过此方法可知 p 值和许多其他值/统计量。通过 `model.summary()` 方法可得出关于数据的预测。

```python
print(model.summary())
```

### 代码实现

```python
# 导入包
import numpy as np
import pandas as pd
import statsmodels.formula.api as smf

# 加载 csv 文件
df = pd.read_csv('headbrain1.csv')
print(df.head())

# 拟合模型
df.columns = ['Head_size', 'Brain_weight']
model = smf.ols(formula='Head_size ~ Brain_weight', data=df).fit()

# 模型摘要
print(model.summary())
```

**输出：**

![模型摘要输出](image_rsrc9WR.jpg)

### 表中部分术语的说明

*   **R-squared 值：** R-squared 值范围在 0 和 1 之间。R-squared 为 100% 表示因变量的所有变化完全由自变量的变化解释。如果 R-squared 值为 1，意味着完美拟合。在我们的例子中，R-squared 值为 0.638。
*   **F-statistic：** F 统计量简单地比较所有变量的综合效应。简单来说，如果你的显著性水平大于 p 值，则拒绝原假设。
*   **coef：** 回归方程中自变量的系数。

### 我们的预测

如果我们将显著性水平 (alpha) 设为 0.05，由于 p < 0.05，我们拒绝原假设并接受备择假设。因此，我们可以得出结论：头围大小与脑重量之间存在关系。

### 5.14 使用 Matplotlib 和 Seaborn 进行 Python 数据可视化

