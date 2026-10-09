

运行该示例会遍历所有组合，并报告那些无错误收敛的结果。该示例在现代硬件上运行时间略多于 2 分钟。结果显示，发现的最佳配置为 `ARIMA(0,0,1)`，其 RMSE 为 939.464，略低于上一节中手动配置的 ARIMA 模型。这种差异是否具有统计显著性尚不确定。

```
ARIMA(5, 1, 2) RMSE=1003.200
ARIMA(5, 2, 1) RMSE=1053.728
ARIMA(6, 0, 0) RMSE=996.466
ARIMA(6, 1, 0) RMSE=1018.211
ARIMA(6, 1, 1) RMSE=1023.762
Best ARIMA(0, 0, 1) RMSE=939.464
```

列表 32.19：在香槟销售数据集上对 ARIMA 模型进行网格搜索的示例输出。

我们将选择这个 `ARIMA(0,0,1)` 模型用于后续步骤。

### 32.6.3 检查残差误差

对模型进行良好的最终检查是审查残差预测误差。理想情况下，残差误差的分布应为一个均值为零的高斯分布。我们可以通过使用统计摘要和图表来研究 `ARIMA(0,0,1)` 模型的残差误差以检查这一点。以下示例计算并总结了残差预测误差。

```python
# summarize ARIMA forecast residuals
from pandas import read_csv
from pandas import DataFrame
from statsmodels.tsa.arima_model import ARIMA
from matplotlib import pyplot

# create a differenced series
def difference(dataset, interval=1):
    diff = list()
    for i in range(interval, len(dataset)):
        value = dataset[i] - dataset[i - interval]
        diff.append(value)
    return diff

# invert differenced value
def inverse_difference(history, yhat, interval=1):
    return yhat + history[-interval]

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
    # difference data
    months_in_year = 12
    diff = difference(history, months_in_year)
    # predict
    model = ARIMA(diff, order=(0,0,1))
    model_fit = model.fit(trend='nc', disp=0)
    yhat = model_fit.forecast()[0]
    yhat = inverse_difference(history, yhat, months_in_year)
    predictions.append(yhat)
    # observation
    obs = test[i]
    history.append(obs)
# errors
residuals = [test[i]-predictions[i] for i in range(len(test))]
residuals = DataFrame(residuals)
print(residuals.describe())
# plot
pyplot.figure()
pyplot.subplot(211)
residuals.hist(ax=pyplot.gca())
pyplot.subplot(212)
residuals.plot(kind='kde', ax=pyplot.gca())
pyplot.show()
```

列表 32.20：在香槟销售数据集上绘制并总结 ARIMA 模型误差。

运行该示例首先描述了残差的分布。我们可以看到分布向右偏移，且均值非零，为 165.904728。这可能表明预测存在偏差。

| 计数 | 47.000000 |
| :--- | :--- |
| 均值 | 165.904728 |
| 标准差 | 934.696199 |
| 最小值 | -2164.247449 |
| 25% 分位数 | -289.651596 |
| 50% 分位数 | 191.759548 |
| 75% 分位数 | 732.992187 |
| 最大值 | 2367.304748 |

列表 32.21：在香槟销售数据集上对 ARIMA 模型残差误差的统计摘要示例输出。

残差误差的分布也被绘制出来。图表显示这是一种类似高斯的分布，左侧尾部有波动，这提供了进一步的证据，表明可能值得探索幂变换。

![](img/da419ed7447ef051ee9d00167b7274cf_339_0.png)

我们可以利用此信息通过在每个预测值中加入平均残差误差 165.904728 来对预测进行偏差校正。以下示例执行了此偏差校正。

```python
# plots of residual errors of bias corrected forecasts
from pandas import read_csv
from pandas import DataFrame
from statsmodels.tsa.arima_model import ARIMA
from matplotlib import pyplot
from sklearn.metrics import mean_squared_error
from math import sqrt

# create a differenced series
def difference(dataset, interval=1):
    diff = list()
    for i in range(interval, len(dataset)):
        value = dataset[i] - dataset[i - interval]
        diff.append(value)
    return diff

# invert differenced value
def inverse_difference(history, yhat, interval=1):
    return yhat + history[-interval]

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
bias = 165.904728
for i in range(len(test)):
    # difference data
    months_in_year = 12
    diff = difference(history, months_in_year)
    # predict
    model = ARIMA(diff, order=(0,0,1))
    model_fit = model.fit(trend='nc', disp=0)
    yhat = model_fit.forecast()[0]
    yhat = bias + inverse_difference(history, yhat, months_in_year)
    predictions.append(yhat)
    # observation
    obs = test[i]
    history.append(obs)
# report performance
rmse = sqrt(mean_squared_error(test, predictions))
print('RMSE: %.3f' % rmse)
# errors
residuals = [test[i]-predictions[i] for i in range(len(test))]
residuals = DataFrame(residuals)
print(residuals.describe())
# plot
pyplot.figure()
pyplot.subplot(211)
residuals.hist(ax=pyplot.gca())
pyplot.subplot(212)
residuals.plot(kind='kde', ax=pyplot.gca())
pyplot.show()
```

列表 32.22：在香槟销售数据集上绘制并总结 ARIMA 模型偏差校正后的误差。

预测性能从 939.464 略微提升至 924.699，这种提升可能具有也可能不具有显著性。预测残差误差的摘要显示，均值确实被移动到了非常接近零的值。

```
RMSE: 924.699

              0
count 4.700000e+01
mean  4.965016e-07
std   9.346962e+02
min  -2.330152e+03
25%  -4.555563e+02
50%   2.585482e+01
75%   5.670875e+02
max   2.201400e+03
```

列表 32.23：在香槟销售数据集上对偏差校正的 ARIMA 模型残差误差统计摘要的示例输出。

最后，残差误差的密度图确实显示出向零的微小偏移。这种偏差校正是否值得尚存争议，但我们暂时会使用它。

![](img/da419ed7447ef051ee9d00167b7274cf_341_0.png)

![](img/da419ed7447ef051ee9d00167b7274cf_341_1.png)

图 32.8：香槟销售数据集上偏差校正模型残差误差的密度图。

检查残差误差的时间序列是否存在某种自相关性也是一个好主意。如果存在自相关性，则表明模型还有更多机会对数据中的时间结构进行建模。以下示例重新计算残差误差，并创建 ACF 和 PACF 图以检查是否存在显著的自相关性。

```python
# ACF and PACF plots of residual errors of bias corrected forecasts
from pandas import read_csv
from pandas import DataFrame
from statsmodels.tsa.arima_model import ARIMA
from matplotlib import pyplot
from statsmodels.graphics.tsaplots import plot_acf
from statsmodels.graphics.tsaplots import plot_pacf

# create a differenced series
def difference(dataset, interval=1):
    diff = list()
    for i in range(interval, len(dataset)):
        value = dataset[i] - dataset[i - interval]
        diff.append(value)
    return diff

# invert differenced value
def inverse_difference(history, yhat, interval=1):
    return yhat + history[-interval]

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
    # difference data
    months_in_year = 12
    diff = difference(history, months_in_year)
    # predict
    model = ARIMA(diff, order=(0,0,1))
    model_fit = model.fit(trend='nc', disp=0)
    yhat = model_fit.forecast()[0]
    yhat = inverse_difference(history, yhat, months_in_year)
    predictions.append(yhat)
    # observation
    obs = test[i]
    history.append(obs)
# errors
residuals = [test[i]-predictions[i] for i in range(len(test))]
residuals = DataFrame(residuals)
print(residuals.describe())
# plot
pyplot.figure()
pyplot.subplot(211)
plot_acf(residuals, ax=pyplot.gca())
pyplot.subplot(212)
plot_pacf(residuals, ax=pyplot.gca())
pyplot.show()
```

列表 32.24：香槟销售数据集上偏差校正 ARIMA 模型预测残差的 ACF 和 PACF 图。

结果表明，时间序列中存在的少量自相关性已被模型捕获。

