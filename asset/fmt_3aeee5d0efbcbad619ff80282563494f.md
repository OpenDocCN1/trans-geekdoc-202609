
| :--- | :--- |

| 计数 (count) | 125.000000 |

| 平均值 (mean) | 0.064000 |

| 标准差 (std) | 9.187776 |

| 最小值 (min) | -28.000000 |

| 25% 分位数 | -6.000000 |

| 50% 分位数 | -1.000000 |

| 75% 分位数 | 5.000000 |

| 最大值 (max) | 30.000000 |

列表 19.9：每日女性出生数据集的残差误差汇总统计量的示例输出。

接下来，我们将超越汇总统计量，查看可视化残差误差分布的方法。

## 19.6 残差直方图和密度图

图表可用于更好地理解超出汇总统计量的误差分布。我们期望预测误差围绕零均值呈正态分布。图表可以帮助发现该分布中的偏斜。我们可以使用直方图和密度图来更好地理解残差误差的分布。下面是一个创建这两种图表各一个的示例。

```python
# density plots of residual errors
from pandas import read_csv
from pandas import DataFrame
from pandas import concat
from matplotlib import pyplot
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
# create lagged dataset
values = DataFrame(series.values)
dataframe = concat([values.shift(1), values], axis=1)
dataframe.columns = ['t', 't+1']
# split into train and test sets
X = dataframe.values
train_size = int(len(X) * 0.66)
train, test = X[1:train_size], X[train_size:]
train_X, train_y = train[:,0], train[:,1]
test_X, test_y = test[:,0], test[:,1]
# persistence model
predictions = [x for x in test_X]
# calculate residuals
residuals = [test_y[i]-predictions[i] for i in range(len(predictions))]
residuals = DataFrame(residuals)
# histogram plot
residuals.hist()
pyplot.show()
# density plot
residuals.plot(kind='kde')
pyplot.show()
```

列表 19.10：创建每日女性出生数据集的残差误差密度图。

我们可以看到分布确实具有高斯分布的外观，但可能更尖锐，显示出带有某些不对称性的指数分布。如果图表显示了一个明显非高斯的分布，这可能会表明建模过程中做出的假设可能是不正确的，并且可能需要采用不同的建模方法。较大的偏斜可能表明有机会在建模之前对数据进行转换，例如取对数或平方根。

![](img/da419ed7447ef051ee9d00167b7274cf_182_0.png)

图 19.2：每日女性出生数据集的预测残差误差直方图。

![](img/da419ed7447ef051ee9d00167b7274cf_183_0.png)

图 19.3：每日女性出生数据集的预测残差误差密度图。

接下来，我们将查看另一种快速且可能更可靠的方法来检查残差分布是否为高斯分布。

## 19.7 残差 Q-Q 图

Q-Q 图，或分位数图，比较两种分布，可用于观察它们的相似程度或差异程度。我们可以使用 Statsmodels 库中的 `qqplot()` 函数创建 Q-Q 图。

Q-Q 图可用于快速检查残差误差分布的正态性。数值被排序并与理想的高斯分布进行比较。比较结果显示为散点图（x 轴为理论值，y 轴为观测值），其中两种分布的匹配显示为从图表左下角到右上角的对角线。

该图有助于发现对此预期的明显偏离。下面是残差误差 Q-Q 图的一个示例。x 轴显示理论分位数，y 轴显示样本分位数。

## 19.8 残差自相关图

自相关计算了观测值与之前时间步观测值之间关系的强度。我们可以计算残差误差时间序列的自相关并绘制结果，这就是自相关图。我们不会期望残差之间存在任何相关性。这表现为自相关得分低于显著性阈值（图上的虚线和点线水平线）。

残差图中显著的自相关表明，模型可以更有效地利用观测值与滞后观测值（称为自回归）之间的关系。Pandas 提供了一个用于计算自相关图的内建函数，称为 `autocorrelation_plot()`。

下面是一个可视化残差误差自相关的示例。x 轴显示滞后阶数，y 轴显示观测值与滞后变量之间的相关性，其中负相关和正相关的相关性值分别位于 -1 和 1 之间。

```python
from pandas import read_csv
from pandas import DataFrame
from pandas import concat
from matplotlib import pyplot
from pandas.plotting import autocorrelation_plot
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
# create lagged dataset
values = DataFrame(series.values)
datframe = concat([values.shift(1), values], axis=1)
datframe.columns = ['t', 't+1']
# split into train and test sets
X = datframe.values
train_size = int(len(X) * 0.66)
train, test = X[1:train_size], X[train_size:]
train_X, train_y = train[:,0], train[:,1]
test_X, test_y = test[:,0], test[:,1]
# persistence model
predictions = [x for x in test_X]
# calculate residuals
residuals = [test_y[i]-predictions[i] for i in range(len(predictions))]
residuals = DataFrame(residuals)
autocorrelation_plot(residuals)
pyplot.show()
```

列表 19.12：为每日女性出生数据集创建残差误差的 ACF 图。

运行该示例会为残差误差创建自回归图。我们在图中没有看到明显的自相关趋势。在滞后 7 阶处可能存在一些值得进一步研究的正自相关，因为它看起来具有显著性。

![](img/da419ed7447ef051ee9d00167b7274cf_187_0.png)

图 19.5：每日女性出生数据集的预测残差误差的 ACF 图。

## 19.9 摘要

在本教程中，你学习了如何使用 Python 探索残差预测误差的时间序列。具体来说，你学会了：

- 如何绘制预测残差误差时间序列的折线图。
- 如何使用统计量、密度图和 Q-Q 图探索残差误差的分布。
- 如何检查残差时间序列的自相关性。

### 19.9.1 下一步

在下一课中，你将了解如何将时间序列预测问题重构为分类或回归问题。

# 第 20 章

## 重构时间序列预测问题

你不必原封不动地对时间序列预测问题进行建模。有很多方法可以重构你的预测问题，这既可以简化预测问题，又可能暴露出更多或不同的信息以供建模。重构最终可以带来更好和/或更稳健的预测。在本教程中，你将了解如何使用 Python 重构你的时间序列预测问题。完成本教程后，你将了解：

- 如何将时间序列预测问题重构为另一种回归问题。
- 如何将时间序列预测问题重构为分类预测问题。
- 如何以不同的时间地平线重构时间序列预测问题。

让我们开始吧。

## 20.1 重构问题的好处

重构问题意味着探索对预测目标的替代视角。探索时间序列预测问题的替代重构框架有两个潜在好处：

- 简化你的问题。
- 为集成预测提供基础。

这两种好处最终都会导致更高技能和/或更稳健的预测。

### 20.1.1 简化问题

预测项目中最大的收获可能来自对问题的重构。这是因为预测问题的结构和类型比数据转换的选择、模型的选择或模型超参数的选择具有更大的影响。这是项目中最大的杠杆，必须仔细考虑。

### 20.1.2 集成预测

除了改变你正在处理的问题外，重构还发挥着另一个作用：它可以提供一组不同但高度相关的问题供你建模。这样做的好处是，这些重构框架可能足够不同，从而要求不同的数据准备和建模方法。

对同一问题持有不同视角的模型可能从输入中捕获不同的信息，并因此以不同的方式产生高技能预测。这些预测可以结合在集成中以产生更高技能或更稳健的预测。在本教程中，我们将探讨你可能考虑的三种重构时间序列预测问题的方法。在我们深入探讨之前，让我们先看一下一个简单的一元时间序列问题——预测每日最低温度，以作为讨论的背景。

## 20.2 每日最低温度数据集

在本课中，我们将使用每日最低温度数据集作为示例。该数据集描述了澳大利亚墨尔本 10 年（1981-1990）的每日最低温度。你可以在附录 A.2 中了解有关该数据集的更多信息。请将数据集以文件名 `daily-minimum-temperatures.csv` 放入当前工作目录中。

## 20.3 朴素时间序列预测

朴素的方法是原封不动地预测问题。作为参考，我们将这称为朴素时间序列预测。在这种情况下，可以去除季节信息以使序列具有季节平稳性。然后，时间序列可以基于滞后观测值的某个函数进行建模。例如：

$$Temp(t + 1) = B0 + (B1 \times Temp(t)) + (B2 \times Temp(t - 1)) ... (Bn \times Temp(t - n))$$  (20.1)

其中 `Temp(t+1)` 是序列中要预测的下一个温度，`B0` 到 `Bn` 是从训练数据中学习的系数，`Temp(t)` 到 `Temp(t-n)` 是当前和滞后观测值。这对许多问题来说可能已经足够，甚至可能是必需的。风险在于，对如何构建问题的预设观念影响了数据收集，进而可能限制了结果。

## 20.4 回归重构

大多数时间序列预测问题是回归问题，需要预测实数输出值。以下是将该预测问题重新表述为替代回归问题的 5 种不同方法：

- 预测与前一日相比最低温度的变化。
- 预测相对于过去 14 天平均值的最低温度。
- 预测相对于去年同月平均值的最低温度。
- 预测最低温度，四舍五入到最接近的5摄氏度。
- 预测未来7天的平均最低温度。

将温度相对化是一种线性变换，这可能不会让问题变得更简单或更容易预测，但它可能会激发新的想法，甚至发现新的数据源供你参考。它还可以帮助你更清晰地思考预测结果的具体用途，以及对预测值的硬性要求究竟是什么。

改变预测问题的粒度确实会改变问题的难度，如果问题的要求允许这种重新定义，这可能会非常有用。下面是一个示例，展示了如何将“每日最低温度”预测问题重构为预测四舍五入到最接近5摄氏度的每日温度。

```python
# reframe precision of regression forecast
from pandas import read_csv
from pandas import DataFrame
from pandas import concat

# load data
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)

# create lagged dataset
values = DataFrame(series.values)
dataframe = concat([values.shift(1), values], axis=1)
dataframe.columns = ['t', 't+1']

# round forecast to nearest 5
for i in range(len(dataframe['t+1'])):
    dataframe['t+1'][i] = int(dataframe['t+1'][i] / 5) * 5.0

print(dataframe.head(5))
```

Listing 20.1: “每日最低温度”数据集的回归重构。

运行该示例会输出重构后问题的前5行。该问题定义为：给定前一天以摄氏度为单位的最低温度，预测四舍五入到最接近5摄氏度的最低温度。

| t | t+1 |
|---|---|
| 0 | NaN | 20.0 |
| 1 | 20.7 | 15.0 |
| 2 | 17.9 | 15.0 |
| 3 | 18.8 | 10.0 |
| 4 | 14.6 | 15.0 |

Listing 20.2: “每日最低温度”数据集回归重构的示例输出。

## 20.5 分类框架

分类涉及预测类别或标签输出（如 `hot` 和 `cold`）。以下是将此预测问题重构为分类问题的5种不同方法：

- 预测最低温度将是寒冷、温和还是温暖。
- 预测最低温度的变化将是小的还是大的。
- 预测最低温度是否为月度最低值。
- 预测最低温度是否高于或低于上一年同期的最低温度。
- 预测未来7天内最低温度是上升还是下降。

转向分类可以简化预测问题。这种方法开放了关于标签以及二元分类框架的想法。

输出变量的原始回归表示意味着大多数分类框架可能会保留序数结构（例如：寒冷、温和、炎热）。这意味着被预测的类别之间存在有序关系，而在预测如狗和猫这样的标签时，情况可能并非如此。

序数关系既允许进行硬分类问题，也允许进行整数预测问题，后者可以事后舍入到特定类别。下面是一个示例，展示了如何将“每日最低温度”预测问题转换为一个分类问题，其中每个温度值都是寒冷、温和或炎热的序数值。这些标签被映射为整数值，定义如下：

- 0 (cold)：低于10摄氏度。
- 1 (moderate)：大于等于10且小于25摄氏度。
- 2 (hot)：大于等于25摄氏度。

```python
# reframe regression as classification

from pandas import read_csv
from pandas import DataFrame
from pandas import concat

# load data
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)

# Create lagged dataset
values = DataFrame(series.values)
dataframe = concat([values.shift(1), values], axis=1)
dataframe.columns = ['t', 't+1']

# make discrete
for i in range(len(dataframe['t+1'])):
    value = dataframe['t+1'][i]
    if value < 10.0:
        dataframe['t+1'][i] = 0
    elif value >= 25.0:
        dataframe['t+1'][i] = 2
    else:
        dataframe['t+1'][i] = 1

print(dataframe.head(5))
```

Listing 20.3: “每日最低温度”数据集的分类重构。

运行该示例会输出重构后问题的前5行。给定前一天以摄氏度为单位的最低温度，目标是预测温度为寒冷、温和或炎热（分别对应 0, 1, 2）。

![](img/da419ed7447ef051ee9d00167b7274cf_192_0.png)

Listing 20.4: “每日最低温度”数据集分类重构的示例输出。

## 20.6 时间视野框架

另一个可以变化的轴是时间视野。时间视野是指预测未来多少时间步长。以下是将此预测问题重构为不同时间视野的5种不同方法：

- 预测未来7天的最低温度。
- 预测30天后的最低温度。
- 预测下个月的平均最低温度。
- 预测下周哪一天的最低温度最低。
- 预测一年的最低温度值。

很容易陷入认为你需要单步预测的想法中。专注于围绕时间视野重构问题会迫使你去思考单点预测与多步预测的区别，以及需要考虑到多远的未来。

你可能能够预测很长的未来，但技能水平可能会随预测距离的延伸而逐渐降低。在思考预测视野时，也要考虑预测的可接受最低性能。下面的示例将“每日最低温度”预测问题转换为预测未来7天的最低温度。
