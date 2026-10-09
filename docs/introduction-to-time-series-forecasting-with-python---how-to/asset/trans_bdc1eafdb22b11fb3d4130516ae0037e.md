
具有时间依赖的结构。

```
ADF Statistic: -7.134898
p-value: 0.000000
Critical Values:
5%: -2.898
1%: -3.515
10%: -2.586
```

列表 32.13：对差分后的香槟销售数据集进行统计检验的示例输出。

作为参考，可以通过加上前一年同一月份的观测值来反转季节性差分操作。当使用在季节性差分数据上拟合的模型进行预测时，需要执行此操作。出于完整性考虑，下方列出了用于反转季节性差分操作的函数。

```
# 反转差分后的值
def inverse_difference(history, yhat, interval=1):
    return yhat + history[-interval]
```

列表 32.14：反转差分的函数。

还绘制了差分数据集的图表。该图表没有显示出明显的季节性或趋势，这表明季节性差分数据集是建模的良好起点。我们将使用此数据集作为 ARIMA 模型的输入。这也表明可能不需要进一步的差分，d 参数可能设置为 0。

![](img/da419ed7447ef051ee9d00167b7274cf_332_0.png)

接下来的第一步是选择自回归（AR）和移动平均（MA）参数的滞后值，即 p 和 q。我们可以通过查看自相关函数（ACF）和部分自相关函数（PACF）图表来做到这一点。请注意，我们现在使用的是季节性差分的 stationary.csv 作为数据集。这是因为手动执行的季节性差分与 ARIMA 模型中由 d 参数执行的 lag=1 差分不同。下例为序列创建了 ACF 和 PACF 图表。

```
# 时间序列的 ACF 和 PACF 图表
from pandas import read_csv
from statsmodels.graphics.tsaplots import plot_acf
from statsmodels.graphics.tsaplots import plot_pacf
from matplotlib import pyplot
series = read_csv('stationary.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
pyplot.figure()
pyplot.subplot(211)
plot_acf(series, lags=25, ax=pyplot.gca())
pyplot.subplot(212)
plot_pacf(series, lags=25, ax=pyplot.gca())
pyplot.show()
```

列表 32.15：香槟销售数据集的 ACF 和 PACF 图表。

运行示例并查看图表，以获得有关如何设置 ARIMA 模型中 **p** 和 **q** 变量的见解。以下是从图表中得出的一些观察结果：

-   ACF 显示 1 个月存在显著滞后。
-   PACF 显示 1 个月存在显著滞后，或许在 12 和 13 个月处也存在一些显著滞后。
-   ACF 和 PACF 都在同一点出现下降，这可能暗示 AR 和 MA 的混合。

**p** 和 **q** 值的一个良好起点也是 1。PACF 图还表明差分数据中仍然存在一些季节性。我们可以考虑一种更好的季节性模型，例如直接建模并从模型中显式移除季节性，而不是进行季节性差分。

![](img/da419ed7447ef051ee9d00167b7274cf_333_0.png)

这种快速分析表明，在平稳数据上使用 ARIMA(1, 0, 1) 可能是一个良好的起点。历史观测值将在拟合每个 ARIMA 模型之前进行季节性差分。为了使预测值能够直接与原始销售计数单位下的预期观测值进行比较，将对所有预测进行差分反转。实验表明，这种配置的 ARIMA 模型不收敛，并导致底层库出错。进一步的实验表明，对平稳数据增加一层差分使模型更加稳定。该模型可以扩展为 ARIMA(1,1,1)。

我们还将通过在调用 `fit()` 时将 `trend` 参数设置为 `nc`（表示无常数）来禁用模型中自动添加的趋势常数。通过实验，我发现这在某些问题上可以获得更好的预测性能。下例演示了该 ARIMA 模型在测试框架上的表现。

```python
# 评估手动配置的 ARIMA 模型
from pandas import read_csv
from sklearn.metrics import mean_squared_error
from statsmodels.tsa.arima_model import ARIMA
from math import sqrt

# 创建一个差分序列
def difference(dataset, interval=1):
  diff = list()
  for i in range(interval, len(dataset)):
    value = dataset[i] - dataset[i - interval]
    diff.append(value)
  return diff

# 反转差分后的值
def inverse_difference(history, yhat, interval=1):
  return yhat + history[-interval]

# 加载数据
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
# 准备数据
X = series.values
X = X.astype('float32')
train_size = int(len(X) * 0.50)
train, test = X[0:train_size], X[train_size:]
# 向前验证（walk-forward validation）
history = [x for x in train]
predictions = list()
for i in range(len(test)):
  # 差分数据
  months_in_year = 12
  diff = difference(history, months_in_year)
  # 预测
  model = ARIMA(diff, order=(1,1,1))
  model_fit = model.fit(trend='nc', disp=0)
  yhat = model_fit.forecast()[0]
  yhat = inverse_difference(history, yhat, months_in_year)
  predictions.append(yhat)
  # 观测值
  obs = test[i]
  history.append(obs)
  print('>Predicted=%.3f, Expected=%.3f' % (yhat, obs))
# 报告性能
rmse = sqrt(mean_squared_error(test, predictions))
print('RMSE: %.3f' % rmse)
```

列表 32.16：香槟销售数据集上的手动 ARIMA 模型。

请注意，你可能会看到来自底层线性代数库的警告信息；目前可以忽略此信息。运行此示例得到的 RMSE 为 956.942，这比持续性方法的 RMSE 3186.501 好得多。

```text
...
>Predicted=3157.018, Expected=5010
>Predicted=4615.082, Expected=4874
>Predicted=4624.998, Expected=4633
>Predicted=2044.097, Expected=1659
>Predicted=5404.428, Expected=5951
RMSE: 956.942
```

列表 32.17：香槟销售数据集上手动的 ARIMA 模型的示例输出。

这是一个很好的开端，但通过配置更好的 ARIMA 模型，我们可能会获得改进的结果。

## 32.6.2 网格搜索 ARIMA 超参数

ACF 和 PACF 图表表明，ARIMA(1, 0, 1) 或类似模型可能是我们能做到的最好水平。为了确认这一分析，我们可以对一套 ARIMA 超参数进行网格搜索，并检查是否没有模型能获得更好的样本外 RMSE 性能。在本节中，我们将搜索 p、d 和 q 值的组合（跳过那些无法收敛的组合），并找到在测试集上表现最佳的组合。我们将使用网格搜索来探索整数值的子集中的所有组合。具体来说，我们将搜索以下参数组合：

-   p：0 到 6。
-   d：0 到 2。
-   q：0 到 6。

这是 (7 × 3 × 7)，即 147，潜在的运行测试，执行将花费一些时间。评估滞后为 12 或 13 的 MA 模型可能很有趣，因为我们在查看 ACF 和 PACF 图表时注意到这些可能很有趣。实验表明，这些模型可能不稳定，导致底层数学库出错。带有网格搜索版本测试框架的完整示例如下所示。

```python
# 对时间序列进行 ARIMA 参数网格搜索
import warnings
from pandas import read_csv
from statsmodels.tsa.arima_model import ARIMA
from sklearn.metrics import mean_squared_error
from math import sqrt
import numpy

# 创建一个差分序列
def difference(dataset, interval=1):
    diff = list()
    for i in range(interval, len(dataset)):
        value = dataset[i] - dataset[i - interval]
        diff.append(value)
    return numpy.array(diff)

# 反转差分后的值
def inverse_difference(history, yhat, interval=1):
    return yhat + history[-interval]

# 评估给定阶数 (p,d,q) 的 ARIMA 模型并返回 RMSE
def evaluate_arima_model(X, arima_order):
    # 准备训练数据集
    X = X.astype('float32')
    train_size = int(len(X) * 0.50)
    train, test = X[0:train_size], X[train_size:]
    history = [x for x in train]
    # 进行预测
    predictions = list()
    for t in range(len(test)):
        # 差分数据
        months_in_year = 12
        diff = difference(history, months_in_year)
        model = ARIMA(diff, order=arima_order)
        model_fit = model.fit(trend='nc', disp=0)
        yhat = model_fit.forecast([0])
        yhat = inverse_difference(history, yhat, months_in_year)
        predictions.append(yhat)
        history.append(test[t])
    # 计算样本外误差
    rmse = sqrt(mean_squared_error(test, predictions))
    return rmse

# 评估 ARIMA 模型中 p, d 和 q 值组合
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

# 加载数据集
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
# 评估参数
p_values = range(0, 7)
d_values = range(0, 3)
q_values = range(0, 7)
warnings.filterwarnings("ignore")
evaluate_models(series.values, p_values, d_values, q_values)
```

列表 32.18：香槟销售数据集上的网格搜索 ARIMA 模型。

