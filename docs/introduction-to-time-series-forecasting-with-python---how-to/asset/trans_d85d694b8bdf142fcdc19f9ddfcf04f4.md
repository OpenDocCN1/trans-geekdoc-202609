
## 31.6. ARIMA 模型

下一步的首要任务是选择自回归（AR）和移动平均（MA）参数的滞后阶数，分别为 **p** 和 **q**。我们可以通过查看自相关函数（ACF）和偏自相关函数（PACF）图来完成这一步。下面的示例为该时间序列创建了 ACF 和 PACF 图。

```python
# ACF and PACF plots of the time series
from pandas import read_csv
from statsmodels.graphics.tsaplots import plot_acf
from statsmodels.graphics.tsaplots import plot_pacf
from matplotlib import pyplot

series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)

pyplot.figure()
pyplot.subplot(211)
plot_acf(series, lags=20, ax=pyplot.gca())
pyplot.subplot(212)
plot_pacf(series, lags=20, ax=pyplot.gca())
pyplot.show()
```

列表 31.13：巴尔的摩用水量数据集的 ACF 和 PACF 图。

运行该示例并查看图表，以获取有关如何设置 ARIMA 模型中 p 和 q 变量的见解。以下是从图表中观察到的一些情况。

- ACF 显示在 4 个时间步长内有显著滞后。
- **PACF** 显示在 1 个时间步长内有显著滞后。

**p** 的一个良好起点是 4，**q** 是 1。

![](img/da419ed7447ef051ee9d00167b7274cf_309_0.png)
![](img/da419ed7447ef051ee9d00167b7274cf_309_1.png)

这种快速分析表明，在原始数据上使用 **ARIMA(4,1,1)** 可能是一个良好的起点。完整的手工 ARIMA 示例如下所示。

```python
# evaluate a manually configured ARIMA model
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
    model = ARIMA(history, order=(4, 1, 1))
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

列表 31.14：巴尔的摩用水量数据集上的手工 ARIMA 模型。

运行此示例的结果为 RMSE 31.097，这高于上述的持久性模型。

```
...
>Predicted=609.030, Expected=598
>Predicted=601.832, Expected=575
>Predicted=580.316, Expected=564
>Predicted=574.084, Expected=549
>Predicted=562.009, Expected=538
RMSE: 31.097
```

列表 31.15：巴尔的摩用水量数据集中手工 ARIMA 模型的示例输出。

### 31.6.2 网格搜索 ARIMA 超参数

ACF 和 PACF 图表明，对于这个数据集，我们可能无法做到比持久性模型更好。为了确认这一分析，我们可以网格搜索一系列 ARIMA 超参数，并检查是否没有任何模型能带来更好的样本外 RMSE 表现。在本节中，我们将搜索 p、d 和 q 的组合值（跳过那些未能收敛的情况），并找出性能最佳的组合。我们将使用网格搜索来探索一组整数值子集中的所有组合。具体来说，我们将搜索以下参数的所有组合：

- p：0 到 4。
- d：0 到 2。
- q：0 到 4。

这是 $(5 \times 3 \times 5)$，即测试框架的 300 种潜在运行方式，执行将花费一些时间。当调用 `fit()` 时，我们将通过设置 `trend` 参数为 `nc`（无常量）来禁用模型中趋势常量的自动添加。带有网格搜索版本测试框架的完整实际示例如下所示。

```python
# grid search ARIMA parameters for a time series
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
        # model_fit = model.fit(disp=0)
        model_fit = model.fit(trend='nc', disp=0)
        yhat = model_fit.forecast()[0]
        predictions.append(yhat)
        history.append(test[t])
    # calculate out of sample error
    rmse = sqrt(mean_squared_error(test, predictions))
    return rmse

# evaluate combinations of p, d and q values for an ARIMA model
def evaluate_models(dataset, p_values, d_values, q_values):
    dataset = dataset.astype('float32')
    best_score, best_cfg = float('inf'), None
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
p_values = range(0, 5)
d_values = range(0, 3)
q_values = range(0, 5)
warnings.filterwarnings('ignore')
evaluate_models(series.values, p_values, d_values, q_values)
```

列表 31.16：巴尔的摩用水量数据集上的网格搜索 ARIMA 模型。

运行示例会遍历所有组合，并报告那些无错误收敛的结果。该示例在现代硬件上运行仅需略多 2 分钟。结果显示，发现的最佳配置是 ARIMA(2,1,0)，其 RMSE 为 21.733，略低于之前测试的持久性模型，但可能并不存在显著差异。

```
ARIMA(4, 1, 0) RMSE=24.802
ARIMA(4, 1, 1) RMSE=25.103
ARIMA(4, 2, 0) RMSE=27.089
ARIMA(4, 2, 1) RMSE=25.932
ARIMA(4, 2, 2) RMSE=25.418
Best ARIMA(2, 1, 0) RMSE=21.733
```

列表 31.17：巴尔的摩用水量数据集中网格搜索 ARIMA 模型的示例输出。

我们将选择这个 ARIMA(2,1,0) 模型作为后续的基础。

### 31.6.3 检查残差误差

对模型良好的最终检查是查看残差预测误差。理想情况下，残差误差的分布应为均值为零的高斯分布。我们可以通过使用统计摘要和图表来调查 ARIMA(2,1,0) 模型的残差误差来检查这一点。下面的示例计算并总结了残差预测误差。

```python
# summarize residual errors for an ARIMA model
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
    model = ARIMA(history, order=(2,1,0))
    model_fit = model.fit(trend='nc', disp=0)
    yhat = model_fit.forecast()[0]
    predictions.append(yhat)
    # observation
    obs = test[i]
    history.append(obs)

# errors
residuals = [test[i]-predictions[i] for i in range(len(test))]
residuals = DataFrame(residuals)
print(residuals.describe())

pyplot.figure()
pyplot.subplot(211)
residuals.hist(ax=pyplot.gca())
pyplot.subplot(212)
residuals.plot(kind='kde', ax=pyplot.gca())
pyplot.show()
```

列表 31.18：巴尔的摩用水量数据集上 ARIMA 模型的误差绘图与汇总。

运行示例首先描述了残差的分布。我们可以看到分布向右偏斜，且均值为非零的 1.081624。这也许是预测存在偏差的迹象。

```
count 35.000000
mean 1.081624
std 22.022566
min -52.103811
25% -16.202283
50% -0.459801
75% 12.085091
max 51.284336
```

列表 31.19：巴尔的摩用水量数据集中 ARIMA 模型残差误差统计摘要的示例输出。

残差误差的分布也绘制出来了。图表显示出一种类似高斯分布的形态，但右侧尾部较长，这提供了进一步的证据，表明或许值得探索一下幂变换。

![](img/da419ed7447ef051ee9d00167b7274cf_313_0.png)

