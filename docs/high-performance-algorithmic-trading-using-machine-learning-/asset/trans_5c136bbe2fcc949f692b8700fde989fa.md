

## 应用

现在，您可以将这个训练并验证过的模型应用于新的、未见过的数据，以预测归一化收盘价。这种能力可以成为预测未来价格走势和制定战略决策的有力工具。

通过从分类转向回归，我们超越了仅识别价格是否落在正常范围内的层面，转而预测其偏离的幅度。这种方法提供了关于价格走势相对于市场波动率的详细且可操作的理解，从而支持更精准的交易决策。

## LASSO 方法

由于我们已经在“使用 Boosting 实现高准确率”一节中完成了分类任务的步骤 1 到 4，因此这些步骤将大幅简略。

我们首先按如下方式缩放特征：

```python
from sklearn.preprocessing import StandardScaler

scl = StandardScaler().set_output(transform="pandas")

X_train = scl.fit_transform(X_train)
X_test = scl.transform(X_test)
```

接下来，调用 Sklearn 导入所需模型：

```python
from sklearn.linear_model import Lasso, Ridge
```

在以下代码中，我们微调回归模型，以实现量化波动率范围内价格偏差的目标：

```python
# 超参数搜索空间
space = {
    'alpha': Real(0.001, 10, prior='log-uniform'), 
    # 正则化参数使用对数刻度
}

opt = BayesSearchCV(
    Lasso(),
    space,
    n_iter=30,
    cv=5,
    scoring="neg_mean_squared_error",
    n_jobs=-1,
    verbose=0
)

# 优化超参数
opt.fit(X_train, y_train) 
print("best params: ")
pprint(opt.best_params_)
```

输出：
```text
best params: 
OrderedDict([('alpha', 0.001)])
```

让我们记录下最佳模型以便当前使用：

```python
rgr = opt.best_estimator_
```

下图展示了优化后的模型在测试集上的预测结果，以及价差数值的真实值（归一化收盘价）：

![](images/fig-7-6.png)

我们通过预测值与实际值的散点图来检验拟合优度。数据点与对角虚线的接近程度衡量了模型的准确性。点越接近这条线，模型越准确：

![](images/fig-7-7.png)

在本例中，数据点聚集在对角线附近，表明优化后的模型提供了良好的拟合。为了量化这一观察结果，在以下代码中，我们计算归一化在 `[-1, 1]` 之间的回归得分，并获得 0.8 的分数。

该分数越接近最大值 1，表明模型具有很强的预测性能，如下所示：

```python
print(rgr.score(X_test, y_test))
```

输出：
```text
0.8
```

正如简介中提到的，LASSO 通过将不太相关特征的系数设为零，具有很强的特征选择能力。要确定 LASSO 认为哪些特征对我们的模型显著，我们可以检查（通过变量 `rgr.coef_`）模型训练后分配的非零系数：

```python
lst_coef = np.argwhere(rgr.coef_ != 0).reshape(1, -1)[0]
print("columns of interest :", list(X_test.iloc[:, lst_coef].columns))
```

输出：
```text
columns of interest : ['Close_diff_frac_0.2_4', 'Close_diff_frac_0.25_4', 'Close_diff_frac_0.3_4', 'Close_diff_frac_0.35_1', 'Close_diff_frac_0.35_2', 'Close_diff_frac_0.35_3', 'Close_diff_frac_0.35_4', 'Close_diff_frac_0.35_5', 'Volatility', 'Closing_Position', 'Gap_Previous_Close', 'Normalized_High', 'Relative_Change_Open_Close', 'High_Low_Clustering', 'SMA_30', 'SMA_35', 'MACD', 'MACD_Histogram', 'RSI', 'STOCHk_14_3_3', 'STOCHd_14_3_3', 'CCI', 'BBB_20_2.0', 'BBP_20_2.0', 'ATR', 'TR']
```

在提供给 LASSO 模型的数百个特征中，它仅选择了这份相关特征列表。

分配给这些特征中的每一个的系数，为我们提供了关于该特征对预测影响的信息。

这非常重要，如下所示：

```python
print("coef values :")
dict(zip(list(X_test.iloc[:, lst_coef].columns), rgr.coef_[lst_coef]))
```

输出：
```text
coef values :
{'Close_diff_frac_0.2_4': 0.0017052507726205356,
 'Close_diff_frac_0.25_4': 0.03357515414777998,
 'Close_diff_frac_0.3_4': 0.013239358125294583,
 'Close_diff_frac_0.35_1': 0.08641385813114096,
 …
 'CCI': -0.055638867385273676,
 'BBB_20_2.0': 0.06799642558179593,
 'BBP_20_2.0': 0.34890179044959546,
 'ATR': -0.008401739981565862,
 'TR': -0.1300218401488396}
```

应用岭回归方法可得到接近的结果。作为一个很好的练习，您可以使用 Scikit-Learn API 中的岭回归实现轻松验证这一说法：

```python
from sklearn.linear_model import Ridge
```

使用这种岭回归方法，我们获得了 0.7 的回归分数，虽然不如之前的 LASSO 方法好，但仍然是正确的。

现在，转向核方法，以探究这种非线性方法是否能改进 LASSO 给出的结果。

## 核方法

核方法允许我们发现线性不可分数据中的模式——即无法画一条直线来分离不同类别的情况。它依赖于一种技巧[^1]，将数据转换到一个更高维的空间，在那里这些类别可以用一个超平面分开。这就像通过一组新的透镜观察数据，揭示了在原始维度中不可见的结构，从而实现准确的分类。

既然已经完成了数据准备和特征工程这些繁重的任务，我们现在可以直接着手优化模型的超参数，以微调其性能：

```python
from sklearn.kernel_ridge import KernelRidge

# 超参数搜索空间
space = {
    # 正则化强度使用对数刻度
    'alpha': Real(0.001, 10, prior='log-uniform'), 
    'kernel': Categorical(['linear', 'rbf', 'polynomial', 'sigmoid']), 
    # 核系数
    'gamma': Real(0.001, 10, prior='log-uniform'), 
    # 'polynomial' 核的扩展度范围
    'degree': Integer(2, 10), 
    # 'coef0'，'polynomial' 和 'sigmoid' 核的参数
    'coef0': Real(0, 10, prior='uniform'),
}
```

接下来，我们打印优化结果（模型特征、核的选择和系数）：

```python
print("best params: ")
pprint(opt.best_params_)
```

输出：
```text
best params: 
OrderedDict([('alpha', 1.3324499412363422),
 ('coef0', 10.0),
 ('degree', 2),
 ('gamma', 0.0016201598106302523),
 ('kernel', 'polynomial')])
```

```python
best_model = opt.best_estimator_
accuracy = best_model.score(X_test, y_test)
print(f"score:", accuracy * 100.0)
```

输出：
```text
score: 80.30608312013042
```

经过超参数优化后，非线性核方法和 LASSO 产生了相似的结果，这表明计算归一化价差从根本上可能是一个线性问题。这意味着特征与目标变量之间的潜在关系可以通过线性模型有效捕捉，而 LASSO 正是专门为此设计的。

本章的最后一部分探讨在线学习，这是一种专门开发用于将机器学习技术应用于流式数据的方法。这种方法随着新数据的到来增量式地更新模型，使其成为在存储或重新处理大量数据不切实际的情况下的理想选择。

## 在线学习方法

在线机器学习是一种自适应策略，模型以增量方式训练，随着数据可用，按顺序处理单个样本或小批量数据。在数据持续生成、导致无法每次有新信息就从头重新训练模型的环境中，这种方法特别有用。

[^1]: 参考原文脚注 17。

