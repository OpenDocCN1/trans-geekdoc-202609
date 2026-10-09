
## 14.3. 使用差分法进行季节调整

![](img/da419ed7447ef051ee9d00167b7274cf_134_0.png)

图 14.1：使用差分法对去季节化后的最低日温度数据集绘制的折线图。

我们的数据集中有两个闰年（1984 年和 1988 年）。我们没有显式处理这些问题；这意味着从 1984 年 3 月起，观测数据的偏移量误差为一天，而在 1988 年 3 月之后，偏移量误差为两天。一种选择是更新代码示例，使其支持闰日。

另一种选择是认为一年中任何特定时段内的温度可能保持稳定。也许是在几周内。我们可以简化这个想法，认为日历月份内的所有温度都是稳定的。一个改进的模型可能是减去前一年同一日历月份的平均温度，而不是同一天。我们可以开始将数据集重采样为月度平均最低温度。

```python
# calculate and plot monthly average
from pandas import read_csv
from matplotlib import pyplot
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
resample = series.resample('M')
monthly_mean = resample.mean()
print(monthly_mean.head(13))
monthly_mean.plot()
pyplot.show()
```

清单 14.2：将最低日温度数据集重采样为月度。

运行此示例将打印出前 13 个月的月平均最低温度。

```text
Date
1981-01-31  17.712903
1981-02-28  17.678571
1981-03-31  13.500000
1981-04-30  12.356667
1981-05-31   9.490323
1981-06-30   7.306667
1981-07-31   7.577419
1981-08-31   7.238710
1981-09-30  10.143333
1981-10-31  10.087097
1981-11-30  11.890000
1981-12-31  13.680645
1982-01-31  16.567742
```

清单 14.3：重采样后的最低日温度数据集前 13 个月的示例输出。

它还绘制了月度数据，清晰地显示了数据集的季节性。

![](img/da419ed7447ef051ee9d00167b7274cf_135_0.png)

我们可以在月度数据上测试相同的差分方法，并确认去季节化的数据集确实去除了年度周期。

```python
# deseasonalize monthly data by differencing
from pandas import read_csv
from matplotlib import pyplot
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
resample = series.resample('M')
monthly_mean = resample.mean()
X = series.values
diff = list()
months_in_year = 12
for i in range(months_in_year, len(monthly_mean)):
    value = monthly_mean[i] - monthly_mean[i - months_in_year]
    diff.append(value)
pyplot.plot(diff)
pyplot.show()
```

清单 14.4：使用差分法对去季节化的月度最低日温度数据集。

运行该示例会创建一个新的季节调整后的月度最低温度数据集，并跳过第一年的数据以创建调整值。然后绘制调整后的数据集。

![](img/da419ed7447ef051ee9d00167b7274cf_136_0.png)

图 14.3：去季节化的月度最低日温度数据集的折线图。

接下来，我们可以使用前一年同月的月平均最低温度来调整日最低温度数据集。同样，我们只是跳过第一年的数据，但使用月度而非每日数据进行校正可能是一种更稳定的方法。

```python
# deseasonalize a time series using month-based differencing
from pandas import read_csv
from matplotlib import pyplot
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
X = series.values
diff = list()
days_in_year = 365
for i in range(days_in_year, len(X)):
    month_str = str(series.index[i].year-1)+'-'+str(series.index[i].month)
    month_mean_last_year = series[month_str].mean()
    value = X[i] - month_mean_last_year
    diff.append(value)
pyplot.plot(diff)
pyplot.show()
```

清单 14.5：使用月级差分法对最低日温度数据集进行去季节化。

再次运行该示例将创建季节调整后的数据集并绘制结果。此示例对前一年的每日波动以及因闰年 2 月 29 日导致的偏移误差具有鲁棒性。

![](img/da419ed7447ef051ee9d00167b7274cf_138_0.png)

图 14.4：使用月度数据对最低日温度数据集进行去季节化的折线图。

日历月份的边缘提供了一个硬边界，这对于温度数据可能没有意义。更灵活的方法可能是取前一年相同日期前后各一周的平均值，这可能是一种更好的方法。此外，温度数据在多个尺度上可能存在季节性，可以通过直接或间接的方式进行校正，例如：

-   天级。
-   多天级别，例如一周或数周。
-   多周级别，例如一个月。
-   多月级别，例如一个季度或季节。

## 14.4 使用建模方法进行季节调整

我们可以直接对季节分量建模，然后将其从观测值中减去。给定时间序列中的季节分量很可能是具有固定周期和振幅的正弦波。这可以使用曲线拟合方法轻松近似。可以构造一个数据集，以正弦波的时间索引作为输入（或 x 轴），观测值作为输出（或 y 轴）。例如：

| 时间索引 | 观测值 |
| :--- | :--- |
| 1 | obs1 |
| 2 | obs2 |
| 3 | obs3 |
| 4 | obs4 |
| 5 | obs5 |

清单 14.6：时间索引作为特征的示例。

拟合完成后，模型可以用于计算任何时间索引的季节分量。对于温度数据，时间索引将为一年中的天数。然后我们可以估算任何历史观测值或未来任何新观测值的一年中某天的季节分量。该曲线可以作为新的输入用于监督学习算法的建模，或者从观测值中减去以创建季节调整后的序列。

让我们开始对最低日温度数据集拟合一条曲线。NumPy 库提供了 `polyfit()` 函数 [^1]，可用于将选定阶数的多项式拟合到数据集。首先，我们可以创建一个从时间索引（在这种情况下为天数）到观测值的数据集。我们可以取一年的数据或所有年的数据。理想情况下，我们会尝试两者并查看哪种模型产生更好的拟合。我们还可以使用中心于每个值的移动平均线来平滑观测值。这也可能产生拟合更好的模型。

准备好数据集后，我们可以通过调用 `polyfit()` 函数来创建拟合，传入 x 轴值（整数天数）、y 轴值（温度观测值）以及多项式的阶数。阶数控制项的数量，进而控制用于拟合数据的曲线的复杂性。理想情况下，我们希望使用能够描述数据集季节性的最简单曲线。对于一致的正弦波状季节性，4 阶或 5 阶多项式就足够了。在这种情况下，我通过试错选择了 4 阶。所得模型的形式为：

$$y = (x^{4} \times b1) + (x^{3} \times b2) + (x^{2} \times b3) + (x^{1} \times b4) + b5 \quad (14.1)$$

其中 $y$ 是拟合值，$x$ 是时间索引（一年中的天数），$b1$ 到 $b5$ 是由曲线拟合优化算法找到的系数。拟合完成后，我们将拥有一组代表我们模型的系数。然后我们可以使用此模型来计算一个观测值、一年观测值或整个数据集的曲线。完整示例如下所示。

```python
# model seasonality with a polynomial model
from pandas import read_csv
from matplotlib import pyplot
from numpy import polyfit
series = read_csv('daily-minimum-temperatures.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
# fit polynomial: x^2*b1 + x*b2 + ... + bn
X = [i%365 for i in range(0, len(series))]
y = series.values
degree = 4
coef = polyfit(X, y, degree)
print('Coefficients: %s' % coef)
```

[^1]: https://docs.scipy.org/doc/numpy/reference/generated/numpy.polyfit.html

