
```
assert np.all(y_test_pred == y_test_pred_seq)
assert np.allclose(np.array(coefs_cv).squeeze(), np.array(coefs_seq).squeeze())
```

## 15.4 用于模型选择的交叉验证：设置超参数

需要注意的是，交叉验证（CV）可用于两个不同的目标：

- 1. 模型评估：在选定最终模型后，估计其在新数据上的预测误差（泛化误差）。
- 2. 模型选择：估计不同模型的性能以选择最佳模型。模型选择的一个特例是选择模型的超参数。确实请记住，大多数学习算法都有超参数（通常是正则化参数）需要设置。

通常我们必须同时解决这两个问题。对于这两个问题，通常的做法是将数据集随机分为三部分：训练集、验证集和测试集。

- 训练集（train）用于拟合模型；
- 验证集（val）用于估计模型选择的预测误差，或在可能的取值网格上确定超参数。
- 测试集（test）用于评估最终选定模型的泛化误差。

### 15.4.1 网格搜索流程

在可能的取值网格上进行最佳超参数的模型选择

对于超参数 α_k 的每个可能取值：

- 1. 在训练集上拟合学习器：f(X_train, y_train, α_k)
- 2. 在验证集上评估模型并保留使误差度量最小的参数
- α_* = arg min L(f(X_train), y_val, α_k)
- 3. 使用最佳超参数在所有训练集+验证集数据上重新拟合学习器：f* ≡ f(X_train ∪ val, y_train ∪ val, α_*)
- 4. ** 模型评估 ** f* 在测试集上的表现：L(f*(X_test), y_test)

### 15.4.2 用于模型选择和评估的嵌套交叉验证

大多数情况下，我们无法承受这种三向划分。因此，我们再次使用交叉验证，但在这种情况下我们需要两个嵌套的交叉验证。

一个外层交叉验证循环，用于模型评估。该交叉验证将数据集划分为 K 次训练加验证集（X_{-K}, y_{-K}）和测试集 X_K, y_K

一个内层交叉验证循环，用于模型选择。对于外层循环的每次运行，内层循环将数据集（X_{-K}, y_{-K}）划分为 L 次训练集：（X_{-K,-L}, y_{-K,-L}）和验证集：（X_{-K,L}, y_{-K,L}）。

### 15.4.3 使用 scikit-learn 的实现

请注意，内层交叉验证循环与学习器结合形成了一个具有自动模型（参数）选择过程的新学习器。该新学习器可使用 Scikit-learn 轻松构建。学习器被封装在 GridSearchCV 类中。

然后可以将该新学习器插入到经典的外层交叉验证循环中。

```
import numpy as np
from sklearn import datasets
import sklearn.linear_model as lm
from sklearn.model_selection import GridSearchCV
import sklearn.metrics as metrics
from sklearn.model_selection import KFold

# Dataset
noise_sd = 10
X, y, coef = datasets.make_regression(n_samples=50, n_features=100, noise=noise_sd,
                                      n_informative=2, random_state=42, coef=True)

# Use this to tune the noise parameter such that snr < 5
print("SNR:", np.std(np.dot(X, coef)) / noise_sd)

# param grid over alpha & l1_ratio
param_grid = {'alpha': 10. ** np.arange(-3, 3), 'l1_ratio':[.1, .5, .9]}

# Wrap
model = GridSearchCV(lm.ElasticNet(max_iter=10000), param_grid, cv=5)

# 1) Biased usage: fit on all data, omit outer CV loop
model.fit(X, y)
print("Train r2:%.2f" % metrics.r2_score(y, model.predict(X)))
print(model.best_params_)

# 2) User made outer CV, useful to extract specific information
cv = KFold(n_splits=5, random_state=42)
y_test_pred = np.zeros(len(y))
y_train_pred = np.zeros(len(y))
alphas = list()

for train, test in cv.split(X, y):
    X_train, X_test, y_train, y_test = X[train, :], X[test, :], y[train], y[test]
    model.fit(X_train, y_train)
    y_test_pred[test] = model.predict(X_test)
    y_train_pred[train] = model.predict(X_train)
    alphas.append(model.best_params_)

print("Train r2:%.2f" % metrics.r2_score(y, y_train_pred))
print("Test  r2:%.2f" % metrics.r2_score(y, y_test_pred))
print("Selected alphas:", alphas)
```

## 统计学与机器学习 in Python，发行版 0.2

```
# 3.) user-friendly sklearn for outer CV
from sklearn.model_selection import cross_val_score
scores = cross_val_score(estimator=model, X=X, y=y, cv=cv)
print("Test r2:%.2f" % scores.mean())
```

SNR: 2.6358469446381614
Train r2:0.96
{'alpha': 1.0, 'l1_ratio': 0.9}
Train r2:1.00
Test  r2:0.62
Selected alphas: [{'alpha': 0.001, 'l1_ratio': 0.9}, {'alpha': 0.001, 'l1_ratio': 0.9}, {'alpha': 0.001, 'l1_ratio': 0.9}, {'alpha': 0.01, 'l1_ratio': 0.9}, {'alpha': 0.001, 'l1_ratio': 0.9}]
Test r2:0.55

### 15.4.4 内置交叉验证的回归模型

Sklearn 会自动选择参数网格，大多数时候使用默认值。
n_jobs 是交叉验证期间使用的 CPU 数量。如果为 -1，则使用所有 CPU。

```
from sklearn import datasets
import sklearn.linear_model as lm
import sklearn.metrics as metrics
from sklearn.model_selection import cross_val_score

# Dataset
X, y, coef = datasets.make_regression(n_samples=50, n_features=100, noise=10,
 n_informative=2, random_state=42, coef=True)

print("== Ridge (L2 penalty) ==")
model = lm.RidgeCV(cv=3)
# Let sklearn select a list of alphas with default LOO-CV
scores = cross_val_score(estimator=model, X=X, y=y, cv=5)
print("Test r2:%.2f" % scores.mean())

print("== Lasso (L1 penalty) ==")
model = lm.LassoCV(n_jobs=-1, cv=3)
# Let sklearn select a list of alphas with default 3CV
scores = cross_val_score(estimator=model, X=X, y=y, cv=5)
print("Test r2:%.2f" % scores.mean())

print("== ElasticNet (L1 penalty) ==")
model = lm.ElasticNetCV(l1_ratio=[.1, .5, .9], n_jobs=-1, cv=3)
# Let sklearn select a list of alphas with default 3CV
scores = cross_val_score(estimator=model, X=X, y=y, cv=5)
print("Test r2:%.2f" % scores.mean())
```

```
== Ridge (L2 penalty) ==
Test r2:0.16

== Lasso (L1 penalty) ==
```

from True to False in version 0.22 and will be removed in 0.24. This will change numeric results when test-set sizes are unequal.
DeprecationWarning)
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/model_selection/_search.py:841: DeprecationWarning: The default of the iid parameter will change from True to False in version 0.22 and will be removed in 0.24. This will change numeric results when test-set sizes are unequal.
DeprecationWarning)
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/model_selection/_search.py:841: DeprecationWarning: The default of the iid parameter will change from True to False in version 0.22 and will be removed in 0.24. This will change numeric results when test-set sizes are unequal.
DeprecationWarning)
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/model_selection/_search.py:841: DeprecationWarning: The default of the iid parameter will change from True to False in version 0.22 and will be removed in 0.24. This will change numeric results when test-set sizes are unequal.
DeprecationWarning)
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/model_selection/_search.py:841: DeprecationWarning: The default of the iid parameter will change from True to False in version 0.22 and will be removed in 0.24. This will change numeric results when test-set sizes are unequal.
DeprecationWarning)

Test  r2:0.74
== ElasticNet (L1 penalty) ==
Test r2:0.58

### 15.4.5 内置交叉验证的分类模型

```python
from sklearn import datasets
import sklearn.linear_model as lm
import sklearn.metrics as metrics
from sklearn.model_selection import cross_val_score

X, y = datasets.make_classification(n_samples=100, n_features=100,
                                    n_informative=10, random_state=42)

# provide CV and score
def balanced_acc(estimator, X, y, **kwargs):
    """
    Balanced accuracy scorer
    """
    return metrics.recall_score(y, estimator.predict(X), average=None).mean()

print("== Logistic Ridge (L2 penalty) ==")
model = lm.LogisticRegressionCV(class_weight='balanced', scoring=balanced_acc, n_jobs=-1, cv=3)
# Let sklearn select a list of alphas with default LOO-CV
scores = cross_val_score(estimator=model, X=X, y=y, cv=5)
print("Test  ACC:%.2f" % scores.mean())
```
