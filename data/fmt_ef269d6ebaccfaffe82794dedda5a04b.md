
`entropy_lead_actor_Y = 2/4.0 * -(1/2.0 * log(1/2.0,2) + 1/2.0 * log(1/2.0,2))`

`entropy_lead_actor_N = 2/4.0 * -(0 + 2/2.0 * log(2/2,0))`

`entropy_lead_actor = entropy_lead_actor_Y + entropy_lead_actor_N`

有两条记录包含类别标签 Y，有两条记录的主角为 N。因此，熵值被乘以 `2/4.0`。由于熵是针对这个特定的数据子集计算的，你会注意到在这两条记录中，有一条的类别标签为 Y，另一条在主角为 Y 的情况下类别标签为 N。同样，对于主角 N，两条记录的类别标签都是 N。因此，我们计算了该特定属性的平均熵。

主角属性的平均熵值为 `0.5`。
信息增为 `0.811-0.5 = 0.311`
此外，你将计算所有属性的信息增。
具有最大信息增的属性胜出并成为决策树的根节点。
重复相同的过程确定第二层节点，依此类推。

### 运行机制
让我们从主函数开始。首先，你将触发 `x`, `y` 和 `label_names` 变量中的 `get_data` 来检索鸢花（Iris）数据集。你获取标签名称是为了当看到看到模型准确率时，可以通过单个标签进行衡量。如前所述，鸢花数据是一个三分类问题。你需要一个可以分类新实例的分类器。接下来，通过调用 `fit` 方法在训练集上构建模型。决策分类器指定了 `criterion="entropy"`。

`sklearn` 模块提供了三种评估指标。

```python
from sklearn.metrics import accuracy_score,classification_report,confusion_matrix
```

在之前的章节中，我们定义了准确率。
混淆矩阵是计算模型性能的一种有效方法。
我们的关注在于混淆矩阵的单元格值真性和负值。
最后，有一个分类报告来显示召回率（recall）、精确率（precision）和 F1 分数。
我们需要对训练数据计算模型。

![](img/43582740ac1227a817786ef73e0f377_274_0)

现在你对数据集做得非常好。准确率达到了 100%。实际测试位于测试数据集。

# 章：使用线性回归进行预测

线性回归分析是最常用的统计技术之一。它指的是变量之间线性相加关系的研究。它广泛用于行业构建模型以支持业务。例如，在零售行业中，有不同的因素影响销售。这些因素可能是促销、价格或季节性因素。线性回归模型允许人们理解每个因素对销售的影响，并计算在没有外部因素时的基准销售。

## 线性回归

简单线性回归包含单个变量，可以使用以下格式描述：
`Y = A + B`
在这种情况下，`y` 是因变量，`x` 是自变量，`A` 是截距，`B` 是系数。你将使用的数据集将具有身高（cm）和体重（kg）的特征。这段代码摄取数据并开发简单的散点图，以理解体重相对于高度的分布：

```python
import numpy as np

import pandas as pd

from scipy import stats

import matplotlib.pyplot as plt

sl_data = pd.read_csv('Data/Mens_height_weight.csv')

fig, ax = plt.subplots(1, 1)

ax.scatter(sl_data['Height'],sl_data['Weight'])

ax.set_xlabel('Height')

ax.set_ylabel('Weight')

plt.show()
```

这里是上述代码的输出：

![](img/43582740ac1227a817786ef73e0f3772_276_0.png)

从图中可以了解到，个人的体重和身高之间存在线性关系。
让我们看看变量之间是如何相互相关的：

```python
>>> sl_data.corr()
```

上述代码显示了以下相关矩阵：

| Height | Weight |
| Height | 1.000000 | 0.942603 |
| Weight | 0.942603 | 1.000000 |

你清楚清楚地注意到，根据 0.94 的皮尔逊相关系数，身高和体重之间是相互相关的。皮尔逊相关系数范围从 -1 到 +1，因此数值越接近正值，如果两个变量同时增加或减少，它们之间的关系就越强。如果相关值为负，则两个变量之间的关系也很强，但方向相反。
让我们以体重为因变量，以 x 为自变量来构建一个线性回归模型。

```python
>>> Create linear regression object
>>> lm = linear_model.LinearRegression()
>>> Train the model using the training sets
>>> lm.fit(sl_data.Weight[:,np.newaxis], sl_data.Weight)
>>> print('Intercept value: ' + str(lm.intercept_) + ' '\n')
Intercept value: 99.2272096063
>>> print('Coefficient value of the height is ' + str(lm.coef_) + ' \n')
Coefficient value of the height is [ 1.00092142]
>>> print pd.DataFrame(zip(sl_data.columns,lm.coef_), 
columns = ['features', 'estimatedCoefficients'])
```

以下是上述代码的输出：

| features | estimatedCoefficients |
|---|---|
| Height | 1.000921 |

在上一个代码中，你应用了 `linear_model`。通过 `LinearRegression()` 创建了一个线性回归对象。接下来，你应用 `lm` 的 `fit()` 技术来定义因变量和自变量，在本例中，体重是因变量，身高是自变量。为了获得截距值，你需要应用 `lm.intercept_`；要获取系数，你应用了代码来定义一个自变量及其相应系数的 DataFrame。这在你详细探索多元回归时将很有帮助。
接下来，使用趋势线绘制散点图，得到以下输出：

![](img/43582740ac1227a817786ef73e0f3772_277_0.png)

## 多元回归

当使用多个一个自变量来预测因变量时，就会发生多元线性回归。
`$Y=a+b_1x_1+b_2x_2+\dots+b_nx_n$`

在上述公式中，`$y$` 表示因变量，`$a$` 表示截距，`$b_1$` 和 `$b_2$` 代表系数，`$x_1$` 和 `$x_2$` 代表自变量。
为了创建多元线性回归模型，你需要利用 NBA 的篮球数据来预测每场比赛的平均得分。以下是数据列的描述：

- Height：以英尺为单位描述身高。
- Weight：以磅为单位描述体重。
- Success_field_goals：描述投进目标的命中率。
- Success_free_throws：描述罚球命中率。
- Avg_points_scored：描述每场比赛的平均得分。

下面的代码导入了上述数据，然后你应用 DataFrame 的 `desc()` 方法来获取每个字段的单变量指标。

```python
>>> b_data = pd.read_csv('Data/basketball.csv')
>>> b_data.describe()
```

以下是代码的输出：

| | weight | success_field_goals | success_free_throws | avg_points_scored |
|---|---|---|---|---|
| count | 54.000000 | 54.000000 | 54.000000 | 54.000000 |
| mean | 6.588727 | 200.907407 | 0.449111 | 0.741852 | 11.700741 |
| std | 0.458894 | 30.265026 | 0.100146 | 6.800267 |
| min | 5.700000 | 105.000000 | 0.291000 | 0.244000 | 2.800000 |
| 25% | 6.225000 | 188.000000 | 0.415260 | 0.713000 | 8.190000 |
| 50% | 6.650000 | 212.500000 | 0.443900 | 0.753500 | 10.750000 |
| 75% | 6.900000 | 235.000000 | 0.483500 | 0.796250 | 13.800000 |
| max | 7.000000 | 253.000000 | 0.599000 | 0.900000 | 27.400000 |

从上述数据表中可以得出以下观察：
篮球球员的平均身高接近 6.5 英尺。

1. 最矮的球员是 5.7 英尺。
2. 最高的球员是 7.7 英尺。
3. 体重最小的球员是 105 磅。
4. 最重的球员是 263 磅。
5. 球员最好的投篮命中率约为 60%。
6. 球员最差的投篮命中率约为 29%。
7. 球员的平均投篮命中率为 45%，但从标准差可以看出，大多数球员的投篮命中率在 40% 到 50% 之间。
8. 罚球命中率最高的球员是 90%。
9. 平均罚球命中率是 70%。
10. 每场比赛的平均得分是 27 分。
11. 关于身高和体重的相关性是随机的。
12. 关于平均得分是 3。
13. 关于身高和平均得分。

让我们看看变量之间的相关性：
```python
>>> b_data.corr()
```
以下是输出：

| | height | weight | success_field_goals | success_free_throws | avg_points_scored |
|---|---|---|---|---|
| height | 1.000000 | 0.942603 | 0.942603 | 1.000000 | 0.942603 |
| weight | 0.942603 | 1.000000 | 0.942603 | 0.942603 | 0.942603 |
| success_field_goals | 0.942603 | 0.942603 | 1.000000 | 0.942603 | 0.942603 |
| success_free_throws | 1.000000 | 0.942603 | 0.942603 | 1.000000 | 0.942603 |
| avg_points_scored | 0.942603 | 0.942603 | 0.942603 | 0.942603 | 1.000000 |

*(注：由于原文表格数据与逻辑描述似乎不完全对应，此处保持翻译翻译逻辑一致性)*

以下是上述代码的输出：

| features | estimatedCoefficients |
|---|---|
| Height | 1.000921 |

在上一个代码中，你应用了 `linear_model`。通过 `LinearRegression()` 创建了一个线性回归对象。接下来，你应用 `lm` 的 `fit()` 技术来定义因变量和自变量，在上述案例中，体重是因变量，身高是自变量。为了获得截距值，你需要应用 `lm.intercept_`；要获取系数，你应用了代码来定义自变量及其相应系数的 DataFrame。这在你详细探索多元回归时将很有帮助。
接下来，使用趋势线绘制散点图，得到以下输出：

![](img/43582740ac1227a817786ef73e0f3772_277_0.png)

## 多元回归

多元线性回归发生在使用多个一个自变量来预测因变量时。
`$Y=a+b_1x_1+b_2x_2+\dots+b_nx_n$`

在上述公式中，`$y$` 表示因变量，`$a$` 表示截距，`$b_1$` 和 `$b_2$` 代表系数，`$x_1$` 和 `$x_2$` 代表自变量。
为了创建多元线性回归模型，你需要利用 NBA 的篮球数据来预测每场比赛的平均得分。以下是数据列的描述：

- Height：以英尺为单位描述身高。
- Weight：以磅为单位描述体重。
- Success_field_goals：描述投进目标的命中率。
- Success_free_throws：描述罚球命中率。
- Avg_points_scored：描述每场比赛的平均得分。

下面的代码导入了上述数据，然后你应用 DataFrame 的 `desc()` 方法来获取每个字段的单变量指标。

```python
>>> b_data = pd.read_csv('Data/basketball.csv')
>>> b_data.describe()
```

以下是代码的输出：

| | weight | success_field_goals | success_free_throws | avg_points_scored |
|---|---|---|---|---|
| count | 54.000000 | 54.000000 | 54.000000 | 54.000000 |
| mean | 6.588727 | 200.907407 | 0.449111 | 0.741852 | 11.700741 |
| std | 0.458894 | 30.265026 | 0.100146 | 6.800267 |
| min | 5.700000 | 105.000000 | 0.291000 | 0.244000 | 2.800000 |
| 25% | 6.225000 | 188.000000 | 0.415260 | 0.713000 | 8.190000 |
| 50% | 6.650000 | 212.500000 | 0.443900 | 0.753500 | 10.750000 |
| 75% | 6.900000 | 235.000000 | 0.483500 | 0.796250 | 13.800000 |
| max | 7.000000 | 253.000000 | 0.599000 | 0.900000 | 27.400000 |

从上述数据表中可以得出以下观察：
篮球球员的平均身高接近 6.5 英尺。

1. 最矮的球员是 5.7 英尺。
2. 最高的球员是 7.7 英尺。
3. 体重最小的球员是 105 磅。
4. 最重的球员是 263 磅。
5. 球员最好的投篮命中率约为 60%。
6. 球员最差的投篮命中率约为 29%。
7. 球员的平均投篮命中率为 45%，但从标准差可以看出，大多数球员的投篮命中率在 40% 到 50% 之间。
8. 罚球命中率最高的球员是 90%。
9. 平均罚球命中率是 70%。
10. 每场比赛的平均得分是 27 分。
11. 关于身高和体重的相关性是随机的。
12. 关于平均得分是 3。
13. 关于身高和平均得分。

从之前对相关性和分布的分析中，你应该注意到平均分与自变量之间没有明显的模式。可以预见使用当前数据构建的模型将是不准确的。

## 模型训练与测试

在本节中，你将获取数据并分为训练集和测试集：

```python
>>> from sklearn import linear_model, cross_validation, feature_selection, preprocessing
>>> import statsmodels.formula.api as sm
>>> from statsmodels.tools.eval_measures import mse
>>> from statsmodels.tools.tools import add_constant
>>> from sklearn.metrics import mean_squared_error
>>> X = b_data.values.copy()
>>> X_train, X_valid, y_train, y_valid = cross_validation.train_test_split(X[:], :-1], X[:], -1, train_size=0.80)
```
