
## Python 中的统计学与机器学习，版本 0.2

```
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/linear_model/logistic.py:1926: ChangedBehaviorWarning: The long-standing behavior to use the accuracy score has changed. The scoring parameter is now used. This warning will disappear in version 0.22.
ChangedBehaviorWarning
```

```
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/linear_model/logistic.py:1926: ChangedBehaviorWarning: The long-standing behavior to use the accuracy score has changed. The scoring parameter is now used. This warning will disappear in version 0.22.
ChangedBehaviorWarning
```

测试 ACC:0.77

```
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/linear_model/logistic.py:1926: ChangedBehaviorWarning: The long-standing behavior to use the accuracy score has changed. The scoring parameter is now used. This warning will disappear in version 0.22.
ChangedBehaviorWarning
```

置换检验是一种非参数随机化检验，其中检验统计量的零分布是通过随机置换观测值来估计的。

置换检验非常有吸引力，因为它们除了假设在零假设下观测值独立同分布外，不做其他假设。

- 1. 在数据上计算观测统计量 t_obs。
- 2. 使用随机化计算零假设下 t 的分布：对数据进行 N 次随机置换。对于每次置换后的样本，计算统计量 t_i。该过程提供了零假设 H0 下 t 的分布：P(t|H0)
- 3. 计算 p 值 = P(t > t_obs | H0) | {t_i > t_obs}，其中 t_i 包含 t_obs。

统计量为相关系数。

```python
import numpy as np
import scipy.stats as stats
import matplotlib.pyplot as plt as plt
import seaborn as sns
%matplotlib inline
%matplotlib qt
np.random.seed(42)
x = np.random.normal(loc=10, scale=1, size=100)
y = x + np.random.normal(loc=-3, scale=3, size=100) # snr = 1/2
# Permutation: simulate the null hypothesis
nperm = 10000
perms = np.zeros(nperm + 1)
perms[0] = np.corrcoef(x, y)[0, 1]
for i in range(1, nperm):
    perms[i] = np.corrcoef(np.random.permutation(x), y)[0, 1]
# Plot
# Re-weight
weights = np.ones(perms.shape[0]) / perms.shape[0]
plt.hist([perms[perms >= perms[0]], perms], histtype='stepfilled',
         bins=100, label=["t>t obs (p-value)", "t<t obs"],
         weights=[weights[perms >= perms[0]], weights])
plt.xlabel("Statistic distribution under null hypothesis")
plt.axvline(x=perms[0], color='blue', linewidth=1, label="observed statistic")
_ = plt.legend(loc="upper left")
# One-tailed empirical p-value
pval_perm = np.sum(perms >= perms[0]) / perms.shape[0]
# Compare with Pearson's correlation test
_, pval_test = stats.pearsonr(x, y)
print("Permutation two tailed p-value=%.5f. Pearson test p-value=%.5f" % (2*pval_perm, pval_test))
```

RuntimeWarning: numpy.dtype 大小已更改，可能表示二进制不兼容。预期 96，得到 88

ImportWarning: 无法从 __spec__ 或 __package__ 解析包，回退到 __name__ 和 __path__ return f(*args, **kwargs)

置换双尾 p 值=0.06959。Pearson 检验 p 值=0.07355

![](img/c2ad4b400bf63af9804b2d44510f76a6_219_0.png)

## 15.5.2 练习

给定上述 logistic 回归及其在 5 折交叉验证下的验证。

- 1. 使用置换检验计算与预测准确率相关的 p 值。
- 2. 使用参数检验计算与预测准确率相关的 p 值。

## 15.6 自助法

自助法是一种有放回的随机抽样策略，提供了一种非参数方法来评估性能分数的变异性，例如标准误差或置信区间。

自助法的巨大优势在于其简单性。它是为复杂分布的复杂参数的复杂估计量导出标准误差和置信区间估计的直接方法，例如百分位点、比例、优势比和相关系数。

- 1. 对数据集进行 B 次有放回抽样。
- 2. 对每个样本 i 拟合模型并计算分数。
- 3. 使用 B 次重采样数据集上获得的分数评估分数的标准误差和置信区间。

```python
import numpy as np
from sklearn import datasets
import sklearn.linear_model as lm
import sklearn.metrics as metrics
import pandas as pd

# Regression dataset
```

```python
n_features = 5
n_features_info = 2
n_samples = 100
X = np.random.randn(n_samples, n_features)
beta = np.zeros(n_features)
beta[:n_features_info] = 1
Xbeta = np.dot(X, beta)
eps = np.random.randn(n_samples)
y = Xbeta + eps

# Fit model on all data (!! risk of overfit)
model = lm.RidgeCV()
model.fit(X, y)
print("Coefficients on all data:")
print(model.coef_)

# Bootstrap loop
nboot = 100  # !! Should be at least 1000
scores_names = ["r2"]
scores_boot = np.zeros((nboot, len(scores_names)))
coefs_boot = np.zeros((nboot, X.shape[1]))

orig_all = np.arange(X.shape[0])
for boot_i in range(nboot):
    boot_tr = np.random.choice(orig_all, size=len(orig_all), replace=True)
    boot_te = np.setdiff1d(orig_all, boot_tr, assume_unique=False)
    Xtr, ytr = X[boot_tr, :], y[boot_tr]
    Xte, yte = X[boot_te, :], y[boot_te]
    model.fit(Xtr, ytr)
    y_pred = model.predict(Xte).ravel()
    scores_boot[boot_i, :] = metrics.r2_score(yte, y_pred)
    coefs_boot[boot_i, :] = model.coef_

# Compute Mean, SE, CI
scores_boot = pd.DataFrame(scores_boot, columns=scores_names)
scores_stat = scores_boot.describe(percentiles=[.99, .95, .5, .1, .05, 0.01])

print("r-squared: Mean=%.2f, SE=%.2f, CI=(%.2f %.2f)" %\
      tuple(scores_stat.loc[["mean", "std", "5%", "95%"], "r2")))

coefs_boot = pd.DataFrame(coefs_boot)
coefs_stat = coefs_boot.describe(percentiles=[.99, .95, .5, .1, .05, 0.01])
print("Coefficients distribution")
print(coefs_stat)
```

全数据上的系数：
[ 1.01094082  0.92410534 -0.07588245  0.13848944  0.19659906]
r-squared：均值=0.59，标准误差=0.11，置信区间=(0.39 0.74)
系数分布

|  | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| 计数 | 100.000000 | 100.000000 | 100.000000 | 100.000000 | 100.000000 |
| 均值 | 1.007552 | 0.927999 | -0.072079 | 0.166443 | 0.188892 |
| 标准差 | 0.105309 | 0.118476 | 0.092189 | 0.109172 | 0.089533 |
| 最小值 | 0.710004 | 0.676758 | -0.331354 | -0.059170 | -0.043120 |
| 1% | 0.787546 | 0.695238 | -0.261349 | -0.058613 | 0.001962 |
| 5% | 0.835648 | 0.741149 | -0.219243 | 0.009053 | 0.050575 |
| 10% | 0.878441 | 0.775851 | -0.202235 | 0.042002 | 0.079449 |
| 50% | 1.013152 | 0.921445 | -0.083346 | 0.167349 | 0.190600 |
| 95% | 1.211640 | 1.108971 | 0.052410 | 0.352416 | 0.345560 |
| 99% | 1.254097 | 1.180027 | 0.150143 | 0.383904 | 0.399238 |
| 最大值 | 1.290094 | 1.264742 | 0.153999 | 0.511701 | 0.401858 |

## 第十六章

## 索引和表格

- 通用索引
- 模块索引
- 搜索
