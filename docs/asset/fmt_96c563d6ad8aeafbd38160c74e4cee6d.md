
```python
# summarize residual errors from bias corrected forecasts
from pandas import read_csv
from pandas import DataFrame
from sklearn.metrics import mean_squared_error
from statsmodels.tsa.arima_model import ARIMA
from math import sqrt
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
bias = 1.081624

for i in range(len(test)):
    # predict
    model = ARIMA(history, order=(2,1,0))
    model_fit = model.fit(trend='nc', disp=0)
    yhat = bias + float(model_fit.forecast()[0])
    predictions.append(yhat)
    # observation
    obs = test[i]
    history.append(obs)

# report performance
rmse = sqrt(mean_squared_error(test, predictions))
print('RMSE: %.3f' % rmse)

# summarize residual errors
residuals = [test[i]-predictions[i] for i in range(len(test))]
residuals = DataFrame(residuals)
print(residuals.describe())

# plot residual errors
pyplot.figure()
pyplot.subplot(211)
residuals.hist(ax=pyplot.gca())
pyplot.subplot(212)
residuals.plot(kind='kde', ax=pyplot.gca())
pyplot.show()
```

### 列表 31.20：绘制并总结 ARIMA 模型在巴尔的摩用水量数据集上的偏差校正误差。

预测性能从 21.733 略微提升到 21.706，这可能具有显著性，也可能不具有。预测残差误差的摘要显示，平均值确实移动到了非常接近零的值。

```
RMSE: 21.706

           0
count  3.500000e+01
mean  -3.537544e-07
std   2.202257e+01
min  -5.318543e+01
25%  -1.728391e+01
50%  -1.541425e+00
75%   1.100347e+01
max   5.020271e+01
```

列表 31.21：在巴尔的摩用水量数据集上对偏差校正 ARIMA 模型残差误差的摘要统计量的示例输出。

最后，残差误差的密度图确实显示了向零的小幅偏移。

![](img/da419ed7447ef051ee9d00167b7274cf_315_0.png)

图 31.7：巴尔的摩用水量数据集上偏差校正模型残差误差的密度图。

这种偏差校正是否值得商榷，但我们暂时会使用它。

## 31.7 模型验证

在模型开发完毕并选定最终模型后，必须对其进行验证并最终确定。验证是过程中的可选部分，但提供了最后一次检查，以确保我们没有被欺骗或误导。本节包括以下步骤：

- **确定模型**：训练并保存最终模型。
- **进行预测**：加载已确定的模型并进行预测。
- **验证模型**：加载并验证最终模型。

### 31.7.1 确定模型

确定模型涉及在整个数据集上拟合 `ARIMA` 模型，在本例中，是在整个数据集的转换版本上拟合。一旦拟合完成，模型可以保存到文件以供日后使用。下面的示例在数据集上训练一个 **ARIMA(2,1,0)** 模型，并将整个拟合对象和偏差保存到文件。当前版本的 Statsmodels 库中存在一个 bug，导致尝试从文件加载保存的 `ARIMA` 模型时会出现错误。请在附录 B 中了解有关此 bug 及其变通办法的更多信息。下面的示例将正确状态的拟合模型保存到文件，以便稍后能够成功加载。

```python
# save finalized model to file
from pandas import read_csv
from statsmodels.tsa.arima_model import ARIMA
import numpy

# monkey patch around bug in ARIMA class
def __getnewargs__(self):
    return ((self.endog), (self.k_lags, self.k_diff, self.k_ma))

ARIMA.__getnewargs__ = __getnewargs__

# load data
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)

# prepare data
X = series.values
X = X.astype('float32')

# fit model
model = ARIMA(X, order=(2,1,0))
model_fit = model.fit(trend='nc', disp=0)

# bias_constant, could be calculated from in-sample mean residual
bias = 1.081624

# save model
model_fit.save('model.pkl')
numpy.save('model_bias.npy', [bias])
```

列表 31.22：为巴尔的摩用水量数据集保存已确定的 `ARIMA` 模型到文件。运行该示例会创建两个本地文件：

- **`model.pkl`**：这是调用 **`ARIMA.fit()`** 返回的 **`ARIMAResult`** 对象。其中包括系数以及拟合模型时返回的所有其他内部数据。
- **`model_bias.npy`**：这是存储为一行一列 NumPy 数组的偏差值。

### 31.7.2 进行预测

一种自然的情况是加载模型并进行单次预测。这相对简单，涉及恢复保存的模型和偏差，并调用 **`forecast()`** 函数。下面的示例加载模型，对下一个时间步进行预测，并打印该预测值。

```python
# load finalized model and make a prediction
from statsmodels.tsa.arima_model import ARIMAResults
import numpy

model_fit = ARIMAResults.load('model.pkl')
bias = numpy.load('model_bias.npy')
yhat = bias + float(model_fit.forecast()[0])
print('Predicted: %.3f' % yhat)
```

列表 31.23：加载已确定的 `ARIMA` 模型并在巴尔的摩用水量数据集上进行预测。

运行该示例打印出约为 540 的预测值。

```
Predicted: 540.013
```

列表 31.24：在巴尔的摩用水量数据集上加载 `ARIMA` 模型并进行单次预测的示例输出。

如果我们查看 `validation.csv`，我们可以看到下一时间段的下一行值为 568。预测值在正确的范围内。

### 31.7.3 验证模型

我们可以加载模型，并以模拟操作方式使用它。在测试框架部分，我们将原始数据集的最后 10 年数据保存到单独的文件中，以验证最终模型。我们现在可以加载这个 `validation.csv` 文件，并使用它来查看我们的模型在未见过数据上的实际表现。我们可能有两种前进方式：

- 加载模型并预测接下来 10 年。超出第一或两年的预测会迅速开始降低精度。
- 加载模型并以滚动预测方式使用，在每个时间步更新转换和模型。这是首选方法，因为这是在实际中如何使用该模型，并且它会获得最佳性能。

与前几节中的模型评估一样，我们将以滚动预测方式进行预测。这意味着我们将遍历验证数据集中的提前量，并将观察值作为对历史的更新。

```python
# load and evaluate the finalized model on the validation dataset
from pandas import read_csv
from matplotlib import pyplot
from statsmodels.tsa.arima_model import ARIMA
from statsmodels.tsa.arima_model import ARIMAResults
from sklearn.metrics import mean_squared_error
from math import sqrt
import numpy

# load and prepare datasets
dataset = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
X = dataset.values.astype('float32')
history = [x for x in X]

validation = read_csv('validation.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
y = validation.values.astype('float32')

# load model
model_fit = ARIMAResults.load('model.pkl')
bias = numpy.load('model_bias.npy')

# make first prediction
predictions = list()
yhat = bias + float(model_fit.forecast()[0])
predictions.append(yhat)
history.append(y[0])
print('Predicted=%.3f, Expected=%.3f' % (yhat, y[0]))

# rolling forecasts
for i in range(1, len(y)):
    # predict
    model = ARIMA(history, order=(2,1,0))
    model_fit = model.fit(trend='nc', disp=0)
    yhat = bias + float(model_fit.forecast()[0])
    predictions.append(yhat)
    # observation
    obs = y[i]
    history.append(obs)
    print('Predicted=%.3f, Expected=%.3f' % (yhat, obs))

# report performance
rmse = sqrt(mean_squared_error(y, predictions))
print('RMSE: %.3f' % rmse)
pyplot.plot(y)
pyplot.plot(predictions, color='red')
pyplot.show()
```

列表 31.25：在巴尔的摩用水量数据集上加载并验证已确定的模型。

运行该示例会打印验证数据集中每个时间步的预测值和期望值。验证期的最终 RMSE 预测为每人每天 16 升。这与预期的误差 21 相差不大，但我预计它与一个简单的持续性模型也相差不大。

```
>Predicted=540.013, Expected=568
>Predicted=571.589, Expected=575
>Predicted=573.289, Expected=579
>Predicted=579.561, Expected=587
>Predicted=588.063, Expected=602
>Predicted=603.022, Expected=594
>Predicted=593.178, Expected=587
>Predicted=588.558, Expected=587
>Predicted=588.797, Expected=625
>Predicted=627.941, Expected=613
RMSE: 16.532
```

列表 31.26：在巴尔的摩用水量数据集上加载并验证已确定模型的示例输出。

还提供了预测值与验证数据集的比较图。预测确实具有持续性预测的特征。这表明，尽管该时间序列具有明显的趋势，它仍然是一个相当困难的问题。

![](img/da419ed7447ef051ee9d00167b7274cf_319_0.png)

图 31.8：验证数据集中期望值（蓝色）和预测值（红色）的折线图。

## 31.8 总结

在本教程中，你了解了使用 Python 进行时间序列预测项目的步骤和工具。本教程涵盖了许多内容；具体来说：

- 如何开发一个带有性能指标和评估方法的测试框架，以及如何快速开发一个基线预测和技能。
- 如何使用时间序列分析来提出最佳建模预测问题的思路。
- 如何开发 `ARIMA` 模型，保存它，并在以后加载它以对新数据进行预测。

### 31.8.1 下一步

在下一个项目中，你将开发模型来预测法国香波酒的月度销售额。

## 第 32 章

## 项目：法国香波酒的月度销售额

时间序列预测是一个过程，获得良好预测的唯一方法就是练习这个过程。在本教程中，你将发现如何使用 Python 预测法国香波酒的月度销售额。通过完成本教程，你将获得一个用于解决自己时间序列预测问题的步骤和工具的框架。完成本教程后，你将知道：

- 如何确认你的 Python 环境并仔细定义时间序列预测问题。
- 如何创建用于评估模型的测试框架，开发基线预测，并更好地使用时间序列分析工具理解你的问题。
- 如何开发自回归积分滑动平均模型（`ARIMA`），将其保存到文件，并在以后加载它以对新的时间步长进行预测。

让我们开始吧。

## 32.1 概述

在本教程中，我们将端到端地完成一个时间序列预测项目，从下载数据集和定义问题，到训练最终模型并进行预测。该项目并非详尽无遗，但它展示了如何通过系统地解决时间序列预测问题来快速获得良好的结果。

我们将要完成的项目步骤如下。

1. 问题描述。
2. 测试框架。
3. 持久性（Persistence）。
4. 数据分析。
5. `ARIMA` 模型。
6. 模型验证。

这将提供一个解决时间序列预测问题的模板，你可以将其用于自己的数据集。

## 32.2 问题描述

问题是预测 Perrin Freres 标签（以法国的一个地区命名）的香波酒月销售数量。数据集提供了从 1964 年 1 月到 1972 年 9 月的香波酒月销售数量，也就是不到 10 年的数据。数值是销售百万次的计数，共有 105 个观测值。该数据集归功于 Makridakis 和 Wheelwright，1989 年。以下是数据集前几行的样本。

```
"Month", "Sales"
"1964-01", 2815
"1964-02", 2672
"1964-03", 2755
"1964-04", 2721
"1964-05", 2946
```

列表 32.1：数据集前几行的样本。

下载该数据集作为 CSV 文件，并将其放在当前工作目录中，文件名为 `champagne.csv`。

## 32.3 测试框架

我们必须开发一个测试框架来调查数据并评估候选模型。这涉及两个步骤：

1. 定义验证数据集。
2. 开发一种模型评估方法。

### 32.3.1 验证数据集

该数据集不是最新的。这意味着我们无法轻松收集更新的数据来验证模型。因此，我们将假装现在是 1971 年 9 月，并从分析和模型选择中保留最后一年数据。最后一年的数据将用于验证最终模型。下面的代码将数据集加载为 Pandas 序列并分为两部分，一部分用于模型开发（`dataset.csv`），另一部分用于验证（`validation.csv`）。

```python
# separate out a validation dataset
from pandas import read_csv
series = read_csv('champagne.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
split_point = len(series) - 12
dataset, validation = series[0:split_point], series[split_point:]
print('Dataset %d, Validation %d' % (len(dataset), len(validation)))
dataset.to_csv('dataset.csv', header=False)
validation.to_csv('validation.csv', header=False)
```

列表 32.2：将原始数据划分为训练数据集和验证数据集。
