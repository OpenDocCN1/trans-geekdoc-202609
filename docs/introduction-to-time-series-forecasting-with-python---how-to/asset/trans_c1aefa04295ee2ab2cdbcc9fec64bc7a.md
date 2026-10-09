
## A.3. *月度太阳黑子数据集*

该数据集归功于 Andrews & Herzberg (1985)。 以下代码加载了月度太阳黑子数据集，打印了数据的前 5 行，并以线图形式绘制了数据。

```python
# load the sunspots dataset
from matplotlib import pyplot
from pandas import read_csv
series = read_csv('sunspots.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
print(series.head())
series.plot()
pyplot.show()
```

列表 A.5：创建月度太阳黑子数据集的线图。

以下是加载数据集的前 5 行示例。

| 月份 | 值 |
|---|---|
| 1949-01-01 | 58.0 |
| 1949-02-01 | 62.6 |
| 1949-03-01 | 70.0 |
| 1949-04-01 | 55.7 |
| 1949-05-01 | 85.0 |

列表 A.6：打印月度太阳黑子数据集前 5 行的示例输出。

以下是整个数据集的线图。

![](img/da419ed7447ef051ee9d00167b7274cf_357_0.png)

图 A.3：月度太阳黑子数据集的线图。

## A.4 每日女婴出生数数据集

该数据集描述了 1959 年加利福尼亚州每日女婴的出生数量。 单位是计数，共有 365 个观测值。 该数据集的来源归功于 Newton (1988)。 以下代码加载了每日女婴出生数数据集，打印了数据的前 5 行，并以线图形式绘制了数据。

```python
# load the female births dataset
from matplotlib import pyplot
from pandas import read_csv
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True,
                  squeeze=True)
print(series.head())
series.plot()
pyplot.show()
```

列表 A.7：创建每日女婴出生数数据集的线图。

以下是加载数据集的前 5 行示例。

```
Date
1959-01-01  35
1959-01-02  32
1959-01-03  30
1959-01-04  31
1959-01-05  44
```

列表 A.8：打印每日女婴出生数数据集前 5 行的示例输出。

以下是整个数据集的线图。

![](img/da419ed7447ef051ee9d00167b7274cf_359_0.png)

## A.5 航空乘客数据集

该数据集描述了航空乘客总数随时间的变化。 单位是航空乘客数量的计数（以千为单位）。 从 1949 年到 1960 年共有 144 个月的观测值。 以下代码加载了航空乘客数据集，打印了数据的前 5 行，并以线图形式绘制了数据。

```python
# load the airline passengers dataset
from matplotlib import pyplot
from pandas import read_csv
series = read_csv('airline-passengers.csv', header=0, index_col=0, parse_dates=True,
                   squeeze=True)
print(type(series))
print(series.head())
series.plot()
pyplot.show()
```

列表 A.9：创建航空乘客数据集的线图。

以下是加载数据集的前 5 行示例。

```
Month
1949-01-01 112
1949-02-01  118
1949-03-01  132
1949-04-01  129
1949-05-01  121
```

列表 A.10：打印航空乘客数据集前 5 行的示例输出。

以下是整个数据集的线图。

![](img/da419ed7447ef051ee9d00167b7274cf_360_0.png)

图 A.5：航空乘客数据集的线图。

## 附录 B

### 保存 ARIMA 模型的变通方法

自回归积分滑动平均模型，或称 ARIMA，是时间序列分析和预测中一种流行的线性模型。 Statsmodels 库提供了 Python 中使用的 ARIMA 实现。 可以将 ARIMA 模型保存到文件中，以便日后用于对新数据进行预测。 当前版本的 Statsmodels 库中存在一个 bug，导致无法加载已保存的模型。 在本教程中，你将发现如何诊断并解决此问题。 让我们开始吧。

#### B.1 每日女婴出生数数据集

在本课中，我们将使用每日女婴出生数数据集作为示例。 该数据集描述了 1959 年加利福尼亚州每日女婴的出生数量。 你可以在附录 A.4 中了解有关该数据集的更多信息。 将该数据集放入当前工作目录，文件名为 *daily-total-female-births.csv*。

#### B.2 Python 环境

确认你正在使用最新版本的 Statsmodels 库。 你可以通过运行以下脚本来做到这一点：

```python
# check the version of statsmodels
import statsmodels
print('statsmodels: %s' % statsmodels.__version__)
```

列表 B.1：检查 Statsmodels 版本。

运行脚本应该会显示 Statsmodels 0.6.1 或 0.8.0 的结果。

```
statsmodels: 0.8.0
```

列表 B.2：检查 Statsmodels 版本的示例输出。

你可以使用 Python 2 或 3。

#### B.3 ARIMA 模型保存 Bug

我们可以轻松地在每日女婴出生数数据集上训练一个 ARIMA 模型。 下面的代码片段在该数据集上训练了 ARIMA(1,1,1)。 model.fit() 函数返回一个 ARIMAResults 对象，我们可以调用 save() 将模型保存到文件，并调用 load() 稍后加载它。

```python
# save and load an ARIMA model that causes an error
from pandas import read_csv
from statsmodels.tsa.arima_model import ARIMA
from statsmodels.tsa.arima_model import ARIMAResults
# load data
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
# prepare data
X = series.values
X = X.astype('float32')
# fit model
model = ARIMA(X, order=(1,1,1))
model_fit = model.fit()
# save model
model_fit.save('model.pkl')
# load model
loaded = ARIMAResults.load('model.pkl')
```

列表 B.3：保存并加载导致错误的 ARIMA 模型。

运行此示例将训练模型并将其保存到文件，而不会出现问题。 当你尝试从文件加载模型时，会报告一个错误。

```
Traceback (most recent call last):
  File "...", line 16, in <module>
    loaded = ARIMAResults.load('model.pkl')
  File ".../site-packages/statsmodels/base/model.py", line 1529, in load
    return load_pickle(fname)
  File ".../site-packages/statsmodels/iolib/smpickle.py", line 41, in load_pickle
    return cPickle.load(fin)
TypeError: __new__() takes at least 3 arguments (1 given)
```

列表 B.4：加载 ARIMA 模型时的示例错误消息。

具体来说，请注意这一行：

```
TypeError: __new__() takes at least 3 arguments (1 given)
```

列表 B.5：加载 ARIMA 模型时的具体错误。

或者，如果你运行的是较新版本的 Statsmodels，例如 0.8.0，你可能会遇到诸如以下的错误消息：

```
AttributeError: 'ARIMA' object has no attribute 'dates'
```

列表 B.6：加载 ARIMA 模型时的另一种错误。

到目前为止还不错，那么我们如何修复它呢？

#### B.4 ARIMA 模型保存 Bug 的变通方法

Zae Myung Kim 在 2016 年 9 月发现了这个 bug 并报告了故障。 你可以在此处阅读所有相关信息：

- BUG: Implemented `__getnewargs__()` method for unpickling.  
  https://github.com/statsmodels/statsmodels/pull/3217

该 bug 的发生原因是，pickle（用于序列化 Python 对象的库）所需的一个函数未在 Statsmodels 中定义。 必须在保存前在 ARIMA 模型中定义函数 `__getnewargs__`[^1]，该函数定义构建对象所需的参数。 我们可以变通解决此问题。 修复方法涉及两件事：

1.  定义一个适用于 ARIMA 对象的 `__getnewargs__()` 函数的实现。
2.  将新函数添加到 ARIMA。

幸运的是，Zae Myung Kim 在他的 bug 报告中提供了该函数的一个示例，因此我们可以直接使用该函数：

```python
def __getnewargs__(self):
    return ((self.endog),(self.k_lags, self.k_diff, self.k_ma))
```

列表 B.7：定义缺失的 pickle 函数的示例。

Python 允许我们对对象进行猴子补丁（monkey patch），即使是来自 Statsmodels 等库的对象。 我们可以使用赋值在现有对象上定义新函数。 我们可以对 ARIMA 对象的 `__getnewargs__()` 函数这样做，如下所示：

```python
ARIMA.__getnewargs__ = __getnewargs__
```

列表 B.8：将缺失的函数添加到 ARIMA 类的示例。

使用猴子补丁在 Python 中训练、保存和加载 ARIMA 模型的完整示例如下：

```python
# save and load an ARIMA model with a workaround
from pandas import read_csv
from statsmodels.tsa.arima_model import ARIMA
from statsmodels.tsa.arima_model import ARIMAResults

# monkey patch around bug in ARIMA class
def __getnewargs__(self):
    return ((self.endog),(self.k_lags, self.k_diff, self.k_ma))
ARIMA.__getnewargs__ = __getnewargs__

# load data
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True,
                  squeeze=True)
# prepare data
X = series.values
X = X.astype('float32')
```

[^1]: https://docs.python.org/2/library/pickle.html#object.__getnewargs__

