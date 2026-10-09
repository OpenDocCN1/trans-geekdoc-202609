

这表明至少需要执行一次差分。我们 ARIMA 模型中的 `d` 参数至少应为 1。下一步是选择自回归（AR）和移动平均（MA）参数的滞后值，即分别为 `p` 和 `q`。我们可以通过查看自相关函数（ACF）和偏自相关函数（PACF）图来完成这一步。下面的示例创建了对该序列的 ACF 和 PACF 图。

```python
# ACF and PACF plots of time series
from pandas import read_csv
from statsmodels.graphics.tsaplots import plot_acf
from statsmodels.graphics.tsaplots import plot_pacf
from matplotlib import pyplot
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
pyplot.figure()
pyplot.subplot(211)
plot_acf(series, lags=50, ax=pyplot.gca())
pyplot.subplot(212)
plot_pacf(series, lags=50, ax=pyplot.gca())
pyplot.show()
```

Listing 30.16: 创建波士顿抢劫案数据集的 ACF 和 PACF 图。

运行该示例并查看图表，以了解如何设置 ARIMA 模型中的 `p` 和 `q` 变量。以下是从图表中得出的一些观察结果。

- ACF 显示 10-11 个月有显著的滞后。
- PACF 显示大约 2 个月有显著的滞后。
- ACF 和 PACF 都在同一点出现下降，这可能暗示需要混合使用 AR 和 MA。

`p` 和 `q` 值的一个良好起点分别是 11 和 2。

![](img/da419ed7447ef051ee9d00167b7274cf_281_0.png)

这种快速分析表明，在原始数据上使用 ARIMA(11,1,2) 可能是一个良好的起点。实验表明，这种 ARIMA 配置无法收敛，并导致底层库报错，同样较大的 AR 值也是如此。一些实验显示，模型似乎不稳定，因为同时定义了非零的 AR 和 MA 阶数。模型可以简化为 ARIMA(0,1,2)。下面的示例演示了该 ARIMA 模型在测试框架上的性能。

```python
# evaluate manually configured ARIMA model
from pandas import read_csv
from sklearn.metrics import mean_squared_error
from statsmodels.tsa.arima_model import ARIMA
from math import sqrt
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
    print('>Predicted=%.3f, Expected=%.3f' % (yhat, obs))
# report performance
rmse = sqrt(mean_squared_error(test, predictions))
print('RMSE: %.3f' % rmse)
```

Listing 30.17: 波士顿抢劫案数据集的手动 ARIMA 模型。

运行此示例得到的 RMSE 为 49.821，低于持续性模型。

```
...
>Predicted=280.614, Expected=287
>Predicted=302.079, Expected=355
>Predicted=340.210, Expected=460
>Predicted=405.172, Expected=364
>Predicted=333.755, Expected=487
RMSE: 49.821
```

Listing 30.18: 波士顿抢劫案数据集的手动 ARIMA 模型示例输出。

这是一个良好的开始，但我们可能能够通过更好地配置的 ARIMA 模型获得改进的结果。

### 30.6.2 网格搜索 ARIMA 超参数

许多 ARIMA 配置在此数据集上不稳定，但可能存在其他能产生高性能模型的超参数。在本节中，我们将搜索 `p`、`d` 和 `q` 的值，寻找那些不会导致错误的组合，并找出性能最佳的那个组合。我们将使用网格搜索来探索一组整数值范围内的所有组合。具体来说，我们将搜索以下参数的所有组合：

- `p`: 0 到 12。
- `d`: 0 到 3。
- `q`: 0 到 12。

这是 $(13 \times 4 \times 13)$，即 676 次测试框架的运行，执行需要一些时间。下面是包含网格搜索版本测试框架的完整示例。

```python
# grid search ARIMA parameters for time series
import warnings
from pandas import read_csv
from statsmodels.tsa.arima_model import ARIMA
from sklearn.metrics import mean_squared_error
from math import sqrt

# evaluate an ARIMA model for a given order (p,d,q) and return RMSE
def evaluate_arima_model(X, arima_order):
    # prepare training dataset
    X = X.astype('float32')
    train_size = int(len(X) * 0.50)
    train, test = X[0:train_size], X[train_size:]
    history = [x for x in train]
    # make predictions
    predictions = list()
    for t in range(len(test)):
        model = ARIMA(history, order=arima_order)
        model_fit = model.fit(disp=0)
        yhat = model_fit.forecast()[0]
        predictions.append(yhat)
        history.append(test[t])
    # calculate out of sample error
    rmse = sqrt(mean_squared_error(test, predictions))
    return rmse

# evaluate combinations of p, d and q values for an ARIMA model
def evaluate_models(dataset, p_values, d_values, q_values):
    dataset = dataset.astype('float32')
    best_score, best_cfg = float("inf"), None
    for p in p_values:
        for d in d_values:
            for q in q_values:
                order = (p,d,q)
                try:
                    rmse = evaluate_arima_model(dataset, order)
                    if rmse < best_score:
                        best_score, best_cfg = rmse, order
                        print('ARIMA%s RMSE=%.3f' % (order,rmse))
                except:
                    continue
    print('Best ARIMA%s RMSE=%.3f' % (best_cfg, best_score))

# load dataset
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
# evaluate parameters
p_values = range(0,13)
d_values = range(0, 4)
q_values = range(0, 13)
warnings.filterwarnings("ignore")
evaluate_models(series.values, p_values, d_values, q_values)
```

Listing 30.19: 波士顿抢劫案数据集的网格搜索 ARIMA 模型。

运行该示例会遍历所有组合，并报告那些无错误收敛的结果。在现代化硬件上，该示例运行时间不到 2 小时。结果显示，发现的最佳配置是 ARIMA(0,1,2)；巧合的是，这在前一节中已被证明是有效的。

```
...
ARIMA(6, 1, 0) RMSE=52.437
ARIMA(6, 2, 0) RMSE=58.307
ARIMA(7, 1, 0) RMSE=51.104
ARIMA(7, 1, 1) RMSE=52.340
ARIMA(8, 1, 0) RMSE=51.759
Best ARIMA(0, 1, 2) RMSE=49.821
```

Listing 30.20: 波士顿抢劫案数据集网格搜索 ARIMA 模型的示例输出。

### 30.6.3 审查残差误差

对模型进行良好的最终检查是审查残差预测误差。理想情况下，残差误差的分布应为一个零均值的正态分布。我们可以通过绘制残差的直方图和密度图来检查这一点。下面的示例计算了测试集预测的残差误差，并显示了这些密度图。

```python
# plot residual errors for ARIMA model
from pandas import read_csv
from pandas import DataFrame
from statsmodels.tsa.arima_model import ARIMA
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
residuals.hist(ax=pyplot.gca())
pyplot.subplot(212)
residuals.plot(kind='kde', ax=pyplot.gca())
pyplot.show()
```

Listing 30.21: 绘制波士顿抢劫案数据集中 ARIMA 模型残差误差的密度。

运行该示例生成两个图表。这些图表暗示了一种类似正态的分布，但具有较长的右尾。这可能是一个迹象，表明预测存在偏差，在这种情况下，在建模前对原始数据进行基于幂的变换可能有用。

