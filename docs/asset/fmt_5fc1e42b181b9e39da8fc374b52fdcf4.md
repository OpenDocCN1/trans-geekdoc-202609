
## Box-Cox 变换与逆变换

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

我们可以使用 Box-Cox 变换重新评估 `ARIMA(0,1,2)` 模型。这包括首先在拟合 ARIMA 模型之前对历史数据进行变换，然后在将预测值存储以供后续与期望值比较之前，对预测值进行逆变换。`boxcox()` 函数可能会失败。在实践中，我见过这种情况，其表现为返回的 `lambda` 值小于 -5。按照惯例，`lambda` 值在 -5 和 5 之间评估。

添加了对 `lambda` 值小于 -5 的检查，如果这种情况发生，则假设 `lambda` 值为 1，并使用原始历史数据来拟合模型。`lambda` 值为 1 等同于 `无变换`，因此逆变换没有效果。完整的示例列在下方。

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

## 30.7 操作模型

在本节中，我们假设我们没有自欺欺人。本节包含以下步骤：

- `最终确定模型`：训练并保存最终模型。
- `进行预测`：加载已确定的模型并进行预测。
- `验证模型`：加载并验证最终模型。

### 30.7.1 最终确定模型

最终确定模型涉及在整个数据集上拟合一个 ARIMA 模型，在本例中，是在整个数据集的转换版本上拟合。拟合完成后，可以将模型保存到文件中以便日后使用。由于对数据还执行了 Box-Cox 变换，我们需要知道选定的 `lambda`，以便将模型的任何预测值转换回原始未变换的尺度。下面的示例在 Box-Cox 转换后的数据集上拟合一个 `ARIMA(0,1,2)` 模型，并将完整的拟合对象和 `lambda` 值保存到文件中。

`statsmodels` 库的当前版本存在一个 bug，当您尝试从文件加载保存的 ARIMA 模型时会导致错误。有关此 bug 及其变通办法的更多信息，请参见附录 B。下面的示例将拟合后的模型以正确的状态保存到文件中，以便之后可以成功加载。

```python
# finalize model and save to file with workaround
from pandas import read_csv
from statsmodels.tsa.arima_model import ARIMA
from scipy.stats import boxcox
import numpy

# monkey patch around bug in ARIMA class
def __getnewargs___(self):
    return ((self.endog),(self.k_lags, self.k_diff, self.k_ma))

ARIMA.__getnewargs__ = __getnewargs__

# load data
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
# prepare data
X = series.values
X = X.astype('float32')
# transform data
transformed, lam = boxcox(X)
# fit model
model = ARIMA(transformed, order=(0,1,2))
model_fit = model.fit(disp=0)
# save model
model_fit.save('model.pkl')
numpy.save('model_lambda.npy', [lam])
```

Listing 30.28: 使用变通方法保存最终确定的 ARIMA 模型。

运行该示例会创建两个本地文件：

- `model.pkl`：这是调用 `ARIMA.fit()` 返回的 ARIMAresult 对象。它包括系数以及拟合模型时返回的所有其他内部数据。
- `model_lambda.npy`：这是存储为一行一列 NumPy 数组的 lambda 值。

这可能有些过度了，实际上操作使用真正需要的只是模型中的 AR 和 MA 系数、表示差分次数的 d 参数，可能还有滞后观测值和模型残差，以及用于变换的 lambda 值。

### 30.7.2 进行预测

一个自然的案例可能是加载模型并进行单次预测。这相对简单，涉及恢复保存的模型和 lambda，并调用 `forecast()` 函数。下面的示例加载模型，预测下一个时间步，反转 Box-Cox 变换，并打印预测值。

```python
# load the finalized model and make a prediction
from statsmodels.tsa.arima_model import ARIMAResults
from math import exp
from math import log
import numpy

# invert box-cox transform
def boxcox_inverse(value, lam):
    if lam == 0:
        return exp(value)
    return exp(log(lam * value + 1) / lam)

model_fit = ARIMAResults.load('model.pkl')
lam = numpy.load('model_lambda.npy')
yhat = model_fit.forecast()[0]
yhat = boxcox_inverse(yhat, lam)
print('Predicted: %.3f' % yhat)
```

Listing 30.29: 加载最终确定的 ARIMA 模型并进行预测。

运行该示例会打印出约为 452 的预测值。如果我们查看 `validation.csv`，可以看到下一个时间周期第一行的值是 452。模型完全正确，这令人印象深刻（或者说是运气好）。

```
Predicted: 452.043
```

Listing 30.30: 加载最终确定的 ARIMA 模型并进行一次预测的输出示例。

### 30.7.3 验证模型

我们可以加载模型，并以模拟操作的方式使用它。在测试框架部分，我们将原始数据集的最后 12 个月保存到一个单独的文件中，以验证最终模型。我们现在可以加载这个 `validation.csv` 文件，并查看我们的模型在未见数据上的实际表现。我们可能采用的两种方式如下：

- 加载模型并预测接下来的 12 个月。第一个或第二个月份之后的预测精度会迅速下降。
- 加载模型，以滚动预测的方式使用，并在每个时间步更新变换和模型。这是首选方法，因为这是实际中如何使用该模型的方式，它能取得最佳性能。

与前面章节中的模型评估一样，我们将以滚动预测的方式进行预测。这意味着我们将遍历验证数据集中的提前期，并将观测值作为历史的更新。

```python
# evaluate the finalized model on the validation dataset
from pandas import read_csv
from matplotlib import pyplot
from statsmodels.tsa.arima_model import ARIMA
from statsmodels.tsa.arima_model import ARIMAResults
from scipy.stats import boxcox
from sklearn.metrics import mean_squared_error
from math import sqrt
from math import exp
from math import log
import numpy

# invert box-cox transform
def boxcox_inverse(value, lam):
    if lam == 0:
        return exp(value)
    return exp(log(lam * value + 1) / lam)

# load and prepare datasets
dataset = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
X = dataset.values.astype('float32')
history = [x for x in X]
validation = read_csv('validation.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
y = validation.values.astype('float32')
# load model
model_fit = ARIMAResults.load('model.pkl')
lam = numpy.load('model_lambda.npy')
# make first prediction
predictions = list()
yhat = model_fit.forecast()[0]
yhat = boxcox_inverse(yhat, lam)
predictions.append(yhat)
history.append(y[0])
print('>Predicted=%.3f, Expected=%.3f' % (yhat, y[0]))
# rolling forecasts
for i in range(1, len(y)):
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
    obs = y[i]
    history.append(obs)
    print('>Predicted=%.3f, Expected=%.3f' % (yhat, obs))
# report performance
rmse = sqrt(mean_squared_error(y, predictions))
print('RMSE: %.3f' % rmse)
pyplot.plot(y)
pyplot.plot(predictions, color='red')
pyplot.show()
```

Listing 30.31: 加载并验证最终确定的模型。

运行该示例会打印验证数据集中每个时间步的预测值和期望值。验证期间的最终 RMSE 预测为 53 起抢劫案。这与 49 的预期误差不太不同，但我预计这与简单的持久性模型也不太不同。
