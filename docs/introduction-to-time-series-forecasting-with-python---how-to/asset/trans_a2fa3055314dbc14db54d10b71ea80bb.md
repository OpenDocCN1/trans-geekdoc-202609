
5, 20.7, 17.9, 18.8

**清单 5.16**：手动滚动均值特征的示例。

这意味着我们预计至少要到第5行（数组索引 4）之前无法获得可用数据。

```python
# create rolling statistics features
from pandas import read_csv
from pandas import DataFrame
from pandas import concat
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
temps = DataFrame(series.values)
width = 3
shifted = temps.shift(width - 1)
window = shifted.rolling(window=width)
dataframe = concat([window.min(), window.mean(), window.max(), temps], axis=1)
dataframe.columns = ['min', 'mean', 'max', 't+1']
print(dataframe.head(5))
```

**清单 5.17**：在最低日温度数据集上计算滚动统计特征的示例。

运行该代码会打印新数据集的前5行。我们可以抽查第5行（数组索引 4）数值的正确性。我们可以看到，[20.7, 17.9, 18.8] 窗口内的最小值确实是 17.9，最大值是 20.7。

|   |   min |    mean |   max |   t+1 |
|---:|------:|--------:|------:|------:|
| 0 | NaN |   NaN  | NaN  | 20.7 |
| 1 | NaN |   NaN  | NaN  | 17.9 |
| 2 | NaN |   NaN  | NaN  | 18.8 |
| 3 | NaN |   NaN  | NaN  | 14.6 |
| 4 | 17.9| 19.13333| 20.7 | 15.8 |

**清单 5.18**：在最低日温度数据集上计算滚动统计特征输出的示例。

## 5.7 扩展窗口统计

另一种可能有用的窗口类型包含序列中所有之前的数据。这被称为扩展窗口，有助于跟踪可观测数据的边界。类似于 DataFrame 的 `rolling()` 函数，Pandas 提供了 `expanding()` 函数[4]，它收集每个时间步之前的所有值集合。

这些先前的数值列表可以进行汇总并作为新特征包含进来。例如，以下是序列前5个时间步中扩展窗口的数值列表：

```python
#, Window Values
1, 20.7
2, 20.7, 17.9,
3, 20.7, 17.9, 18.8
4, 20.7, 17.9, 18.8, 14.6
5, 20.7, 17.9, 18.8, 14.6, 15.8
```

**清单 5.19**：手动扩展窗口的示例。

[4] http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.expanding.html

再次说明，我们必须将序列向后移动一个时间步，以确保我们希望预测的输出值不包含在这些窗口值中。因此，输入窗口如下所示：

```python
#, Window Values
1, NaN
2, NaN, 20.7
3, NaN, 20.7, 17.9,
4, NaN, 20.7, 17.9, 18.8
5, NaN, 20.7, 17.9, 18.8, 14.6
```

**清单 5.20**：带偏移的手动扩展窗口示例。

幸运的是，统计计算会排除扩展窗口中的 NaN 值，这意味着不需要进一步的修改。下面是在每日温度数据集上计算扩展窗口最小值、均值和最大值的示例。

```python
# create expanding window features
from pandas import read_csv
from pandas import DataFrame
from pandas import concat
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
temps = DataFrame(series.values)
window = temps.expanding()
dataframe = concat([window.min(), window.mean(), window.max(), temps.shift(-1)], axis=1)
dataframe.columns = ['min', 'mean', 'max', 't+1']
print(dataframe.head(5))
```

**清单 5.21**：在最低日温度数据集上计算扩展统计特征的示例。

运行该示例会打印数据集的前5行。抽查扩展最小值、均值和最大值表明该示例产生了预期的效果。

|   |   min |   mean |   max |   t+1 |
|---:|------:|-------:|------:|------:|
|  0 | 20.7  | 20.7   | 20.7  | 17.9  |
|  1 | 17.9  | 19.3   | 20.7  | 18.8  |
|  2 | 17.9  | 19.133 | 20.7  | 14.6  |
|  3 | 14.6  | 18.0   | 20.7  | 15.8  |
|  4 | 14.6  | 17.56  | 20.7  | 15.8  |

**清单 5.22**：在最低日温度数据集上计算扩展统计特征输出的示例。

## 5.8 总结

在本教程中，你发现了如何使用特征工程将时间序列数据集转换为用于机器学习的监督学习数据集。具体来说，你学习了：

- 时间序列数据特征工程的重要性和目标。
- 如何开发基于日期时间和滞后特征的特征。
- 如何开发滑动窗口和扩展窗口的汇总统计特征。

### 5.8.1 下一步

在下一课中，你将发现如何使用一系列不同的图表来可视化时间序列数据。

# 第 6 章

# 数据可视化

时间序列天然适合可视化。随时间变化的观测值线图很受欢迎，但你可以使用一系列其他图表来更深入地了解你的问题。你对数据了解得越多，你就越有可能开发出更好的预测模型。在本教程中，你将发现6种你可以用来用 Python 可视化时间序列数据的图表类型。具体来说，完成本教程后，你将知道：

- 如何使用线图、滞后图和自相关图来探索时间序列的时间结构。
- 如何使用直方图和密度图来理解观测值的分布。
- 如何使用箱须图（box and whisker plots）和热力图来揭示分布随区间的变化。

让我们开始吧。

## 6.1 时间序列可视化

可视化在时间序列分析和预测中起着重要作用。原始样本数据的图表可以提供有价值的诊断信息，以识别可能影响模型选择的时间结构，如趋势、周期和季节性。一个问题是，时间序列预测领域的新手往往止步于线图。在本教程中，我们将看看你可以用于自己时间序列数据的6种不同类型的可视化。它们是：

1. 线图（Line Plots）。
2. 直方图和密度图（Histograms and Density Plots）。
3. 箱须图（Box and Whisker Plots）。
4. 热力图（Heat Maps）。
5. 滞后图或散点图（Lag Plots or Scatter Plots）。
6. 自相关图（Autocorrelation Plots）。

重点是一元时间序列，但这些技术同样适用于多元时间序列，即当每个时间步都有多个观测值时。接下来，让我们看看我们将用于在本教程中演示时间序列可视化的数据集。

## 6.2 最低日温度数据集

在本课中，我们将使用最低日温度数据集作为一个例子。该数据集描述了澳大利亚墨尔本10年（1981-1990）的每日最低温度。你可以在附录 A.2 中了解有关该数据集的更多信息。请将数据集放在当前工作目录中，文件名为 `daily-minimum-temperatures.csv`。

## 6.3 线图

第一种，也是最流行的时间序列可视化方式是线图。在此图中，时间显示在 x 轴上，观测值沿 y 轴分布。以下是直接将 Pandas `Series` 的最低日温度数据集可视化为线图的一个示例。

```python
# create a line plot
from pandas import read_csv
from matplotlib import pyplot
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
series.plot()
pyplot.show()
```

**清单 6.1**：最低日温度数据集中线图示例。

运行该示例会创建一个线图。

![](img/da419ed7447ef051ee9d00167b7274cf_50_0.png)

**图 6.1**：最低日温度数据集的线图。

线图相当密集。有时改变线图的样式会有帮助；例如，使用虚线或点。下面是改变线条样式为黑色点而不是连接线（`style='k,'` 参数）的示例。我们可以通过将 style 设置为 `'k-'` 来改变该示例使用虚线。

```python
# create a dot plot
from pandas import read_csv
from matplotlib import pyplot
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
series.plot(style='k,')
pyplot.show()
```

**清单 6.2**：最低日温度数据集中点线图示例。

运行该示例会以点代替连接线，重新创建相同的线图。

