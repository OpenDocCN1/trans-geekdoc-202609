
现在，由新直方图和箱线图表示的分布更加对称，尽管显然分布的两侧都有离群观测值。由于我们的目的是为了说明性，我们可以忽略原始分布并关注有意义的目标。例如，我们可以只保留低于 1,000 的价格值（见图 4.5）。在下面的代码段中，我们生成了一个只关注 1,000 以下价格值的直方图：

```python
data[["price"]][data.price <= 1000].hist(bins=20)
```

![](img/def89cc476fa39f4c54bd34e78d91674_126_0.png)

这里代表的分布仍然是右偏，但它类似于电子商务或其他具有长尾产品销售场景中常见的分布。此外，如果我们关注 50 到 200 之间的范围，分布将看起来更加均匀（见图 4.6）。在下面的代码段中，我们进一步将关注范围限制在 50 到 200 之间的价格，并绘制生成的直方图：

```python
data["price"][(data.price >= 50) & (data.price <= 200)].hist(bins=20)
```

![](img/def89cc476fa39f4c54bd34e78d91674_126_1.png)

因此，我们可以创建两个由布尔值掩码变量，可以帮助我们根据想要使用的算法类型过滤目标。`price_capped` 变量在演示某些机器学习算法如何轻松处理长尾时将非常有用：

```python
price_capped = data.price >= 1000
price_window = (data.price >= 50) & (data.price <= 200)
```

图 4.7 显示了相对于封顶价格的箱线图，它呈现出右侧离群值，但至少箱线图是可见的。

![](img/def89cc476fa39f4c54bd34e78d91674_127_0.png)

图 4.8 显示了相对于窗口价格的箱线图，没有任何离群值的迹象：

```python
data["price"] [price_window].boxplot()
```

![](img/def89cc476fa39f4c54bd34e78d91674_127_1.png)

在完成对预测变量和目标的探索后，我们准备了四个不同的目标将我们的示例：

```python
target_mean = (data["price"] > data["price"].mean()).astype(int)
target_median = (data["price"] > data["price"].median()).astype(int)
target_multiclass = pd.qcut(data["price"], q=5, labels=False)
target_regression = data["price"]
```

# 第 4 章 表格数据的经典算法

我们准备了两个二分类目标 `target_mean` 和 `target_median`，以及一个基于分位数具有五个不同类别的多分类目标用于分类。

特别重要的是，我们要注意到我们的 `target_median` 是一个平衡二分类目标。因此，我们可以安全地使用准确率（accuracy）作为良好的性能衡量。作为测试，如果你尝试计算这些值，你会得到正负类的案例数量几乎相等：

```python
target_median.value_counts()
```

你得到结果

```
0 24472
1 24423
```

相反，如果你对 `target_mean` 目标变量尝试相同的操作，你会得到

```python
target_mean.value_counts()
```

你将获得一个向负例倾斜的不平衡分布；也就是说，由于我们之前观察到的偏态分布，低于平均值的情况更多：

```
0 34016
1 14879
```

在这种情况下，评估机器学习分类器的结果时，我们倾向于使用受试者工作曲线下面积（ROC-AUC）或平均精确率（Average Precision）等指标。最后，对于多分类目标，计数显示它们也是平衡的：

```python
target_multiclass.value_counts()
```

该命令返回结果

```
0 10063
1 9835
2 9804
3 10809
4 8384
```

对于回归目标，`target_regression` 是原始转换的原始。然而，我们使用子集并根据我们将演示的机器学习算法对其转换。

在完成对预测变量、目标以及在下一节中基础特征选择的探索后，我们准备好了四个不同的目标。使用构建方法，我们将准备一些

## 探索并处理 Airbnb 数据集的特征

配合我们对表格数据机器学习选项发现的管道

## 4.2.2 管道准备

我们将使用之前过的 `Pipeline` 和 `ColumnTransformer` 类来准备管道。在构建块方法中，我们首先创建适用于数据类型的不同操作。

下面的代码定义了可以重复使用的三个过程：

- 类别特征独热编码——类别特征被转换为二进制特征。如果某个值从未出现过，它将被忽略。
- 数值透传——使用零填充数值值。
- 数值标准化——在填充缺失值后，通过减去平均值并除以标准差对数值进行缩放。

定义这些过程的代码如下所示：

| 列表 4.2 为表格学习管道设置构建块 |
| :--- |
| from sklearn.pipeline import Pipeline |
| sklearn.compose import ColumnTransformer |
| sklearn.preprocessing import OneHotEncoder |
| sklearn.preprocessing import OrdinalEncoder |
| sklearn.impute import SimpleImputer |
| sklearn.preprocessing import StandardScaler |

```python
categorical_onehot_encoding = OneHotEncoder(
    handle_unknown='ignore')
numeric_passsthrough = SimpleImputer(
    strategy='constant', fill_value=0)
numeric_standardization = Pipeline(
    ('imputation', SimpleImputer(strategy='median')),
    ('standardization', StandardScaler())
))
```

> 将类别特征转换为独热格式
> 将数值值替换为零
> 管道替换缺失值并标准化特征

此时，我们可以根据每个机器学习算法的需求组合转换管道。例如，在这个例例中，我们设置了一个管道，它会对类别特征进行编码，并对数值特征仅填充缺失值为零。这样的管道由 `ColumnTransformer` 函数创建，它是一个同时对不同特征集进行操作的胶水函数。对于大多数机器学习模型来说，这都是极佳的转换策略：

```python
column_transform = ColumnTransformer(
    ['categories',
```

# 第 4 章 针对表格数据的经典算法

```python
categorical_onehot_encoding,
low_card_categorical,
('numeric',
numeric_passthrough,
continuous),
),
remainder='drop',
verbose_names_out=False,
sparse_threshold=0.0
```

流水线的的第一步：对分类特征进行独热编码
流水线的第二步：处理数值特征
未被流水线处理的特征将从结果中删除。
特征名称将保持原样。
结果始终是一个稠密矩阵（即 NumPy 数组）。

我们可以立即运行这段代码，并检查此流水线是如何转换 Airbnb NYC 数据的：

```python
X = column_transform.fit_transform(data)
print(type(X), X.dtype, X.shape)
```

结果是输出为浮点数的 NumPy 数组，且形状增加到了 13 列。事实上，由于独热编码，分类特征中的每个值都已变成单个特征：

```
<class 'numpy.ndarray'> float64 (48895, 13)
```

接下来的章节将探索针对表格数据的主要机器学习技术。每种技术将配有一个相应的转换类，该类将集成到流水线模型中。

## 4.3 经典机器学习

为了解释针对表格数据的经典机器学习技术的不同模型，我们将首先介绍算法的核心特征，然后演示代码片段，观察其在我们的参考表格问题——Airbnb NYC 数据集上的运行。以下是我们在示例中使用的一些最佳实践，以确保不同方法的可重复性和可比性：

- 我们定义了一个结合了数据转换和建模的流水线。
- 我们设置了误差衡量标准，例如回归的均方根误差 (RMSE) 或分类的准确率 (accuracy)，并使用相同的交叉验证策略进行测量。
- 我们报告交叉验证估计误差的平均值和标准差——这对于判断模型在不同数据样本上是否具有恒定的性能至关重要。

在上一节中，我们介绍了 Scikit-learn 提供的构建集成特征处理和机器学习模型的数据流水线的各种工具。在本节中，我们将介绍推荐的评估标准，以及 Scikit-learn 的 `cross_validate` 命令的交叉验证估计的工作原理。

让我们先回顾评估指标。我们决定使用 RMSE、准确率，另一种在类别大小相相等的平衡二分类和多分类问题的标准衡量。在随后的章节中，我们还将使用适用于不平衡分类问题的指标，如 ROC-AUC 和平均精确率 (average precision)。

当你打算估计机器学习模型在任何与训练数据不同但分布相同的数据上的预期性能时，交叉验证是数据科学的事实标准。需要注意的是，你的数据在未来可能会变化，但不会发生根本性变化。为了正确运行，模型期望你将在未来使用这些特征，并且它们具有相同的值（如果是分类特征）、相似的分布（包括分类特征和数值特征），最重要的是，这些特征将与你的目标变量保持相同的关系。

数据分布在未来保持一致的假设通常是不成立的，因为世界上经济动态、消费者市场和政治局势变化非常快。在现实世界中，你的模型可能会遇到概念漂移（concept drift），即特征与目标之间的建模关系不再代表现实。因此，你的模型在处理新数据时表现将不佳。交叉验证是在模型创建时评估模型的最佳工具，因为它基于你当时的可用信息，而且如果设计得当，它不受机器学习模型过拟训练数据能力的影响。即使在将交叉验证结果与未来性能进行比较后，它的有用性依然存在，通常是因为底层数据分布发生了变化。此外，其他方法（如留一法 leave-one-out 或自助采样法 bootstrapping）以计算成本的增加为代价提供了更好的估计，而更简单的方法（如训练/划分 train/split）在估计方面的可靠性较低。

对我们有利的是，k 折交叉验证（在 Scikit-learn 中通过 `KFold` 函数实现：https://mg.bz/VVM0）基于将可用的训练数据分为 k 份，每次通过不同的 k-1 份组合构建 k 个版本的模型，然后在留下的部分（样本外性能）上进行测试。生成的 k 个分数的平均值和标准差提供了一个估计，以及对其不确定性水平的量化，用作未来数据预期性能的模型估计。4.9 展示了当 k 设置为 5 时的 k 折验证：每行代表每一折的数据划分。每一折的验证部分始终与其他部分不同，而训练部分的组成也总是不同的。

设置正确的 k 值取决于你拥有多少可用的训练数据、在这些数据上训练模型的计算成本有多高，以及你收到的样本是否捕获了你想要建模的数据分布的所有可能变化。

| Fold | validation | train |
| :--- | :--- | :--- |
| Fold 1 | | train |
| Fold 2 | train | validation | train |
| Fold 3 | train | validation | train |
| Fold 4 | | validation | train |
| Fold 5 | train | | validation |

**图 4.9** 在五折交叉验证中数据在训练和验证之间的分布

每一折的验证部分始终与其他部分不同，而训练部分的组成也总是不同的。设置正确的 k 值取决于你拥有多少可用的训练数据、在这些数据上训练模型的计算成本有多高，以及你收到的样本是否捕获了你想要建模的数据分布的所有可能变化。

### 4.3.1 线性与逻辑回归

在线性回归中，这是一种统计方法，通过对所有转换为数值并放入矩阵的特征拟合线性方程，对因变量与一个多个自变量之间的关系。算法的目标是最小化目标与预测值之间的残差平方和。

# 第 4 章 针对表格数据的经典算法

深入理解算法的内部机制，并使自己未来能够更有能力地解决相似模型的故障排除并优化其性能。在第 5 章中，我们将展示一些可以从零开始实现的算法，以供学习之。

我们将从一个应用于我们 Airbnb NYC 数据的线性回归模型示例开始。该示例遵循图 4.10 中提议的架构（schema），我们将为所介绍的每一个经典机器学习算法复制该架构，该架构基于 Scikit-learn 的流水线（pipelines）和交叉验证评估函数。

![](img/def89cc476fa39f4c54bd34e78d91674_134_0.png)

**图 4.10** 我们如何组织经典机器学习算法示例的架构

该架构是非常线性的。来自逗号分隔值文件的输入首先通过 `ColumnTransformer`，它构成了数据准备部分，能够根据列名对数据应用转换、丢弃数据或保持原样通过，然后进入机器学习模型。这两者都被封装在一个`pipeline`中，并由 `cross_validate` 函数进行测试，该函数执行交叉验证并记录训练模型的计算情况以及在多个折上的性能。最后，选择结果以展示模型是如何运行的。此外，我们可以通过通过流水线访问模型系数和权重，以便对算法的功能有更深入的洞察。

应用这种架构，我们在 4.3 中使用了原生的（vanilla）线性回归模型，因为这种算法通常不需要指定任何参数。对于与模型解释性相关的特殊应用，你可以指定 `fit_intercept` 为 `false` 以从模型中移除截距，并仅根据特征推导出所有预测；或者将正数参数设为 `true` 以仅获取正系数。

## 列表 4.3 线性回归

```python
from sklearn.linear import LinearRegression
from sklearn.metrics import make_scorer, mean_squared_error
from sklearn.model_selection import KFold
from sklearn.model_selection import cross_validate
```

```python
column_transform = ColumnTransformer(
    (['categories', categorical_onehot_encoding, low_card_categorical),
    ['numeric', numeric_passthrough, continuous]),
    remainder='drop',
    verbose_feature_names_out=False,
    sparse_threshold=0.0
)
```

```python
model = Pipeline(
    (['processing', column_transform),
    ('modeling', model)
)
```

ColumnTransformer，将数据转换为数值特征并填充缺失数据。原生线性回归模型。组装 ColumnTransformer 和模型的 Pipeline。

```python
cv = KFold(5, shuffle=True, random_state=0)
rmse = make_scorer(mean_squared_error,
                   squared=False)
c_scores = cross_validate(estimator=model_pipeline,
                           X_data[price_window],
                           y_target_regression[price_window],
                           scoring=rmse,
                           cv=cv,
                           return_train=True,
                           return_estimator=True)
```

基于五折和随机抽样的交叉验证策略。从均方误差派生的评估指标的函数。自动化的交叉验证过程。

```python
mean_cv = np.mean(c_scores['test_score'])
std_cv = np.std(c_scores['test_score'])
fit_time = np.mean(c_scores['fit_time'])
score_time = np.mean(c_scores['score_time'])
print(f"mean_cv:{mean_cv:.3f}, {std_cv:.3f}")
print(f"fit_time:{fit_time:.2f}")
print(f"secs pred: {score_time:.2f} secs")
```

关于评估指标、标准差、拟合和预测时间的报告。

运行列表代码生成了以下 RMSE：

33.949 (0.274) fit: 0.06 secs pred: 0.01 secs
