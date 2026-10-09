
## 15.6.1 每日出生数据集

由于我们要考察均值和方差，我们假设数据符合高斯分布（也称为钟形曲线或正态分布）。我们也可以通过直观地观察观察值的直方图来快速验证这一点。

```python
# 绘制时间序列的直方图
from pandas import read_csv
from matplotlib import pyplot
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
series.hist()
pyplot.show()
```

列表 15.3：创建每日女性出生数据集的直方图。

运行该示例会绘制时间序列值值的直方图。我们可以清楚地看到高斯分布的钟形曲线形状，也许右尾稍长。

![](img/da419ed7447ef051ee9d00167b7274cf_147_0.png)

图 15.3：每日女性出生数据集的直方图。

接下来，我们可以将时间序列拆分为两个连续的序列。然后，我们可以计算每组数字的均值和方差，并比较这些值。

```python
# 计算分区时间序列数据的统计信息
from pandas import read_csv
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True,
squeeze=True)
X = series.values
split = int(len(X) / 2)
X1, X2 = X[0:split], X[split:]
mean1, mean2 = X1.mean(), X2.mean()
var1, var2 = X1.var(), X2.var()
print('mean1=%f, mean2=%f' % (mean1, mean2))
print('variance1=%f, variance2=%f' % (var1, var2))
```

列表 15.4：每日女性出生数据集的汇总统计信息。

运行此示例显示均值和方差值不同，但在同一量级范围内。

```
mean1=39.763736, mean2=44.185792
variance1=49.213410, variance2=48.708651
```

列表 15.5：每日女性出生数据集汇总统计信息的示例输出。

接下来，让我们对航空乘客数据集尝试同样的技巧。

## 15.6.2 航空乘客数据集

直奔主题，我们可以拆分数据集并计算每组的均值和方差。

```python
# 计算分区时间序列数据的统计信息
from pandas import read_csv
series = read_csv('airline-passengers.csv', header=0, index_col=0, parse_dates=True,
squeeze=True)
X = series.values
split = int(len(X) / 2)
X1, X2 = X[0:split], X[split:]
mean1, mean2 = X1.mean(), X2.mean()
var1, var2 = X1.var(), X2.var()
print('mean1=%f, mean2=%f' % (mean1, mean2))
print('variance1=%f, variance2=%f' % (var1, var2))
```

列表 15.6：航空乘客数据集的汇总统计信息。

运行该示例，我们可以看到均值和方差看起来非常不同。这是一个非平稳时间序列。

```
mean1=182.902778, mean2=377.694444
variance1=2244.087770, variance2=7367.962191
```

列表 15.7：航空乘客数据集汇总统计信息的示例输出。

好吧，也许吧。让我们退后一步，通过绘制时间序列值的直方图来检查在这种情况下假设高斯分布是否合理。

```python
series.hist()
pyplot.show()
```

列表 15.8：创建航空乘客数据集的直方图。

运行该示例表明，值的分布确实不像高斯分布，因此均值和方差值的意义不大。观察值这种压缩的分布可能是非平稳时间序列的另一个指标。

![](img/da419ed7447ef051ee9d00167b7274cf_149_0.png)

图 15.4：航空乘客数据集的直方图。

再次回顾时间序列的绘图，我们可以看到存在明显的季节性成分，而且季节性成分似乎在增长。这可能暗示着季节间的指数增长。可以使用对数变换将指数变化拉回线性关系，从而压平变化。下面是同一时间序列经过对数变换后的直方图。

```python
# 对数变换时间序列的直方图和折线图
from pandas import read_csv
from matplotlib import pyplot
from numpy import log
series = read_csv('airline-passengers.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
X = series.values
X = log(X)
pyplot.hist(X)
pyplot.show()
pyplot.plot(X)
pyplot.show()
```

列表 15.9：创建对数变换后的航空乘客数据集的直方图。

运行该示例，我们可以看到值呈现出更熟悉的类高斯分布或类均匀分布。

![](img/da419ed7447ef051ee9d00167b7274cf_150_0.png)

图 15.5：对数变换后的航空乘客数据集的直方图。

我们还创建了数据对数变换后的折线图，可以看到指数增长似乎有所减弱（与附录中该数据集的折线图相比），但我们仍有趋势和季节性要素。

![](img/da419ed7447ef051ee9d00167b7274cf_151_0.png)

图 15.6：对数变换后的航空乘客数据集的折线图。

我们现在可以计算对数变换数据集值的均值和标准差。

```python
# 计算分区对数变换时间序列数据的统计信息
from pandas import read_csv
from numpy import log
series = read_csv('airline-passengers.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
X = series.values
X = log(X)
split = int(len(X) / 2)
X1, X2 = X[0:split], X[split:]
mean1, mean2 = X1.mean(), X2.mean()
var1, var2 = X1.var(), X2.var()
print('mean1=%f, mean2=%f' % (mean1, mean2))
print('variance1=%f, variance2=%f' % (var1, var2))
```

列表 15.10：对数变换后的航空乘客数据集的汇总统计信息。

运行示例显示每组再次相似但并非完全相同的均值和标准差值。或许仅凭这些数字，我们会说该时间序列是平稳的，但从回顾折线图来看，我们坚信事实并非如此。

```
mean1=5.175146, mean2=5.909206
variance1=0.068375, variance2=0.049264
```

列表 15.11：对数变换后的航空乘客数据集汇总统计信息的示例输出。

这是一种快速且粗略的方法，很容易被误导。我们可以使用统计检验来检查两个高斯随机变量样本之间的差异是真实的还是统计上的偶然。我们可以探索统计显著性检验，如 Student’s t-test，但由于值之间的序列相关性，情况变得棘手。在下一节中，我们将使用一种专门用于评论单变量时间序列是否平稳的统计检验。

## 15.7 增广迪基-富勒检验

统计检验对数据做出了强烈的假设。它们只能用于告知在多大程度上可以拒绝（或无法拒绝）原假设。为了使结果有意义，必须针对特定问题进行解读。尽管如此，它们可以提供快速检查和确认性证据，以表明你的时间序列是平稳的还是非平稳的。

增广迪基-富勒检验（Augmented Dickey-Fuller test）是一种称为单位根检验<sup>1</sup>的统计检验。单位根检验背后的直觉在于，它确定时间序列在多大程度上由趋势定义。

有许多种单位根检验，增广迪基-富勒检验可能是其中使用最广泛的之一。它使用自回归模型并针对多个不同的滞后值优化信息准则。该检验的原假设是时间序列可以用单位根表示，即它不是平稳的（具有某种时间依赖结构）。备择假设（拒绝原假设）是时间序列是平稳的。

- **原假设 (H0)：** 无法拒绝，表明时间序列存在单位根，意味着它是非平稳的。它具有某种时间依赖结构。
- **备择假设 (H1)：** 拒绝原假设；表明时间序列不存在单位根，意味着它是平稳的。它不具有时间依赖结构。

我们使用该检验的 p 值来解读这一结果。低于阈值（如 5% 或 1%）的 p 值表明我们拒绝原假设（平稳），否则高于阈值的 p 值表明我们无法拒绝原假设（非平稳）。

- **p 值 > 0.05：** 无法拒绝原假设 (H0)，数据存在单位根且是非平稳的。
- **p 值 ≤ 0.05：** 拒绝原假设 (H0)，数据不存在单位根且是平稳的。

下面是一个在每日女性出生数据集上计算增广迪基-富勒检验的示例。Statsmodels 库提供了实现该检验的 adfuller() 函数<sup>2</sup>。
