
![](img/da419ed7447ef051ee9d00167b7274cf_285_0.png)

检查残差的时间序列中是否存在任何形式的自相关，也是一个好主意。如果存在自相关，则表明模型仍有机会去建模数据中的时间结构。下面的示例重新计算了残差并生成了 ACF（自相关函数）和 PACF（偏自相关函数）图，以检查是否存在显著的自相关。

```python
# ACF and PACF plots of forecast residual errors
from pandas import read_csv
from pandas import DataFrame
from statsmodels.tsa.arima_model import ARIMA
from statsmodels.graphics.tsaplots import plot_acf
from statsmodels.graphics.tsaplots import plot_pacf
from matplotlib import pyplot

# load data
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
# prepare data
X = series.values
X = X.astype('float32')
train_size = int(len(X) * 0.50)
train, test = X[0:train_size], X[train_size:]
# walk-forward validation
history = [x for x in train]
predictions = list()
for i in range(len(test)):
    # predict
    model = ARIMA(history, order=(0,1,2))
    model_fit = model.fit(disp=0)
    yhat = model_fit.forecast()[0]
    predictions.append(yhat)
    # observation
    obs = test[i]
    history.append(obs)
# errors
residuals = [test[i]-predictions[i] for i in range(len(test))]
residuals = DataFrame(residuals)

pyplot.figure()
pyplot.subplot(211)
plot_acf(residuals, lags=25, ax=pyplot.gca())
pyplot.subplot(212)
plot_pacf(residuals, lags=25, ax=pyplot.gca())
pyplot.show()
```

列表 30.22：波士顿抢劫案数据集中 ARIMA 模型残差的 ACF 和 PACF 图。

结果表明，时间序列中存在的少量自相关已经被模型捕获。

![](img/da419ed7447ef051ee9d00167b7274cf_287_0.png)

图 30.6：波士顿抢劫案数据集中 ARIMA 模型残差的 ACF 和 PACF 图。

## 30.6.4 Box-Cox 变换后的数据集

Box-Cox 变换是一种能够评估一系列幂变换的方法，包括但不限于对数据进行对数、平方根和倒数变换。下面的示例对数据执行了对数变换，并生成了一些图表来检查对时间序列的影响。

```python
# plots of box-cox transformed dataset
from pandas import read_csv
from scipy.stats import boxcox
from matplotlib import pyplot
from statsmodels.graphics.tsaplots import qqplot
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
X = series.values
transformed, lam = boxcox(X)
print('Lambda: %f' % lam)
pyplot.figure(1)
# line plot
pyplot.subplot(311)
pyplot.plot(transformed)
# histogram
pyplot.subplot(312)
pyplot.hist(transformed)
# q-q plot
pyplot.subplot(313)
qqplot(transformed, line='r', ax=pyplot.gca())
pyplot.show()
```

列表 30.23：波士顿抢劫案数据集的 Box-Cox 变换及绘图。

运行该示例会生成三个图表：变换后时间序列的折线图、显示变换值分布的直方图，以及显示值分布与理想高斯分布对比的 Q-Q 图。从这些图中可以得到以下观察结果：

- 时间序列折线图中的大幅波动已被消除。
- 直方图显示值的分布更加平坦或更均匀（行为更良好）。
- Q-Q 图看起来合理，但仍然不是对高斯分布的完美拟合。

![](img/da419ed7447ef051ee9d00167b7274cf_289_0.png)

![](img/da419ed7447ef051ee9d00167b7274cf_289_1.png)

毫无疑问，Box-Cox 变换对时间序列做了一些改变，并且可能很有用。在继续使用变换后的数据测试 ARIMA 模型之前，我们必须有一种方法来逆转该变换，以便将基于变换数据训练的模型所做的预测转换回原始尺度。示例中使用的 `boxcox()` 函数通过优化一个代价函数来寻找理想的 lambda 值。lambda 用于以下函数中变换数据：

$$
\begin{align}
& \text{transform} = \log(x), \quad \text{if } \lambda = 0 \\
& \text{transform} = \frac{x^{\lambda} - 1}{\lambda}, \quad \text{if } \lambda \neq 0
\end{align}
$$

(30.1)

该变换函数可以直接逆运算，如下所示：

$$
\begin{align}
& x = \exp(\text{transform}), \quad \text{if } \lambda = 0 \\
& x = \exp\left(\frac{\log(\lambda \times \text{transform} + 1)}{\lambda}\right), \quad \text{if } \lambda \neq 0
\end{align}
$$

(30.2)

这个逆 Box-Cox 变换函数可以用 Python 实现如下：

```python
# invert Box-Cox transform
from math import log
from math import exp

def boxcox_inverse(value, lam):
    if lam == 0:
        return exp(value)
    return exp(log(lam * value + 1) / lam)
```

列表 30.24：用于逆转 Box-Cox 变换的函数。

我们可以使用 Box-Cox 变换重新评估 **ARIMA(0,1,2)** 模型。这包括首先在拟合 ARIMA 模型之前对历史数据进行变换，然后在将预测值存储以供后续与期望值比较之前，对预测值进行逆变换。**boxcox()** 函数可能会失败。在实践中，我见过这种情况，其表现为返回的 **lambda** 值小于 -5。按照惯例，**lambda** 值在 -5 和 5 之间评估。

添加了对 **lambda** 值小于 -5 的检查，如果这种情况发生，则假设 **lambda** 值为 1，并使用原始历史数据来拟合模型。**lambda** 值为 1 等同于 **无变换**，因此逆变换没有效果。完整的示例列在下方。

```python
# evaluate ARIMA models with box-cox transformed time series
from pandas import read_csv
from sklearn.metrics import mean_squared_error
from statsmodels.tsa.arima_model import ARIMA
from math import sqrt
from math import log
from math import exp
from scipy.stats import boxcox

# invert box-cox transform
def boxcox_inverse(value, lam):
    if lam == 0:
        return exp(value)
    return exp(log(lam * value + 1) / lam)

# load data
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
# prepare data
X = series.values
X = X.astype('float32')
train_size = int(len(X) * 0.50)
train, test = X[0:train_size], X[train_size:]
# walk-forward validation
history = [x for x in train]
predictions = list()
for i in range(len(test)):
    # transform
    transformed, lam = boxcox(history)
    if lam < -5:
        transformed, lam = history, 1
    # predict
    model = ARIMA(transformed, order=(0,1,2))
    model_fit = model.fit(disp=0)
    yhat = model_fit.forecast()[0]
    # invert transformed prediction
    yhat = boxcox_inverse(yhat, lam)
    predictions.append(yhat)
    # observation
    obs = test[i]
    history.append(obs)
    print('>Predicted=%.3f, Expected=%.3f' % (yhat, obs))
# report performance
rmse = sqrt(mean_squared_error(test, predictions))
print('RMSE: %.3f' % rmse)
```

列表 30.25：波士顿抢劫案数据集 Box-Cox 变换版本的 ARIMA 模型。

运行该示例会在每次迭代中打印预测值和期望值。请注意，在使用 `boxcox()` 变换函数时，您可能会看到警告；例如：

```
RuntimeWarning: overflow encountered in square
llf -= N / 2.0 * np.log(np.sum((y - y_mean)**2. / N, axis=0))
```

列表 30.26：在对波士顿抢劫案数据集的 Box-Cox 变换版本进行建模时打印的示例错误。

这些警告目前可以忽略。模型在变换数据上的最终 RMSE 为 49.443。这与未变换数据上的 ARIMA 模型相比误差更小，但只是略微更小，而且它可能在统计上可能存在也可能不存在显著差异。

```
...
>Predicted=276.253, Expected=287
>Predicted=299.811, Expected=355
>Predicted=338.997, Expected=460
>Predicted=404.509, Expected=364
>Predicted=349.336, Expected=487
RMSE: 49.443
```

列表 30.27：波士顿抢劫案数据集 Box-Cox 变换版本的 ARIMA 模型示例输出。

我们将使用带有 Box-Cox 变换的该模型作为最终模型。

## 30.7 模型验证

在模型开发完成并选定最终模型后，必须对其进行验证和定稿。验证是该过程的可选部分，但它提供了最后一次检查，以确保我们
