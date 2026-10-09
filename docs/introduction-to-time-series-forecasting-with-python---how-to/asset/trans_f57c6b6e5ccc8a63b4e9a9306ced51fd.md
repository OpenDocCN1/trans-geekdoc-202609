
## 26.2 评估 ARIMA 模型

我们可以通过在训练数据集上准备模型，并在测试数据集上评估预测来评估 ARIMA 模型。该方法包括以下步骤：

- 1. 将数据集划分为训练集和测试集。
- 2. 遍历测试数据集中的时间步。
    - (a) 训练一个 ARIMA 模型。
    - (b) 进行单步预测。
    - (c) 存储预测值；获取并存储实际观测值。
- 3. 计算预测值与期望值的误差分数。

我们可以使用 Python 实现一个名为 `evaluate_arima_model()` 的新独立函数，该函数接受时间序列数据集作为输入，以及一个包含待评估模型 p、d 和 q 参数的元组。数据集被分为两部分：66% 用于初始训练数据集，剩余的 34% 用于测试数据集。

测试集的每个时间步都会进行迭代。仅进行一次迭代即可提供一个你可以用来对新数据进行预测的模型。这种迭代方法允许在每个时间步训练一个新的 ARIMA 模型。每次迭代都会做出一个预测并存储在列表中。这样做是为了在测试集结束时，可以将所有预测值与期望值列表进行比较，并计算误差分数。在这种情况下，计算并返回均方根误差分数。完整的函数如下所示。

```python
# evaluate an ARIMA model for a given order (p,d,q)
def evaluate_arima_model(X, arima_order):
    # prepare training dataset
    train_size = int(len(X) * 0.66)
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
    # calculate out-of-sample error
    rmse = sqrt(mean_squared_error(test, predictions))
    return rmse
```

列表 26.1：使用样本外误差评估 ARIMA 模型的函数。

既然我们知道如何评估一组 ARIMA 超参数，让我们看看如何重复调用此函数来评估参数网格。

## 26.3 迭代 ARIMA 参数

评估一组参数相对简单。用户必须指定 p、d 和 q ARIMA 参数网格进行迭代。为每个参数创建一个模型，并通过调用上一节中描述的 `evaluate_arima_model()` 函数来评估其性能。该函数必须跟踪观察到的最低误差分数以及导致该分数的配置。这可以在函数末尾通过打印到标准输出进行总结。

我们可以将名为 `evaluate_models()` 的此函数实现为四个循环的系列。还有两个额外的考虑因素。首先是确保输入数据是浮点值（而不是整数或字符串），因为这会导致 ARIMA 过程失败。其次，Statsmodels ARIMA 过程内部使用数值优化过程来查找模型的一组系数。这些过程可能会失败，从而引发异常。我们必须捕获这些异常并跳过导致问题的配置。这种情况发生的频率比你想象的要高。此外，建议忽略此代码中的警告，以避免运行过程时产生大量噪声。可以按以下方式操作：

```python
import warnings
warnings.filterwarnings("ignore")
```

列表 26.2：禁用 Python 警告。

最后，即使有了所有这些保护措施，底层代码库仍可能向标准输出报告警告，例如：

```text
** On entry to DLASCL, parameter number 4 had an illegal value
```

列表 26.3：来自底层库的错误消息示例。

为了简明起见，这些内容已从本教程报告的RESULTS中删除。评估 ARIMA 超参数网格的完整过程如下所示。

```python
# evaluate combinations of p, d and q values for an ARIMA model
def evaluate_models(dataset, p_values, d_values, q_values):
    dataset = dataset.astype('float32')
    best_score, best_cfg = float("inf"), None
    for p in p_values:
        for d in d_values:
            for q in q_values:
                order = (p,d,q)
                try:
                    rms = evaluate_arima_model(dataset, order)
                    if rmse < best_score:
                        best_score, best_cfg = rmse, order
                        print('ARIMA%s RMSE=%.3f' % (order,rmse))
                except:
                    continue
    print('Best ARIMA%s RMSE=%.3f' % (best_cfg, best_score))
```

列表 26.4：网格搜索 ARIMA 模型配置的函数。

既然我们有了一个网格搜索 ARIMA 超参数的过程，让我们在两个单变量时间序列问题上测试该过程。我们将从洗发水销售数据集开始。

## 26.4 洗发水销售案例研究

在本节中，我们将使用洗发水销售数据集作为示例。该数据集描述了 3 年期间洗发水的月度销售数量。你可以在附录 A.1 中了解有关该数据集的更多信息。将数据集放入当前工作目录，文件名为 `shampoo-sales.csv`。时间序列中的时间戳不包含绝对年份组件。我们可以在加载数据时使用自定义日期解析函数，并将年份基准设为 1900，如下所示：

```python
# load dataset
def parser(x):
    return datetime.strptime('190'+x, '%Y-%m')
series = read_csv('shampoo-sales.csv', header=0, parse_dates=[0], index_col=0, squeeze=True, date_parser=parser)
```

列表 26.5：加载洗发水销售数据集。

加载完成后，我们可以指定 p、d 和 q 值的搜索集，并将它们传递给 `evaluate_models()` 函数。我们将尝试一组滞后值 (p)、少数几个差分迭代 (d) 和残差误差滞后值 (q)。

```python
# evaluate parameters
p_values = [0, 1, 2, 4, 6, 8, 10]
d_values = range(0, 3)
q_values = range(0, 3)
warnings.filterwarnings("ignore")
evaluate_models(series.values, p_values, d_values, q_values)
```

列表 26.6：在洗发水销售数据集上进行网格搜索的 ARIMA 配置。

将这一切与上一节定义的通用过程结合起来，我们可以在洗发水销售数据集上对 ARIMA 超参数进行网格搜索。完整的代码示例如下所示。

```python
# grid search ARIMA parameters for time series
import warnings
from math import sqrt
from pandas import read_csv
from pandas import datetime
from statsmodels.tsa.arima_model import ARIMA
from sklearn.metrics import mean_squared_error

# evaluate an ARIMA model for a given order (p,d,q)
def evaluate_arima_model(X, arima_order):
    # prepare training dataset
    train_size = int(len(X) * 0.66)
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
def parser(x):
    return datetime.strptime('190'+x, '%Y-%m')
series = read_csv('shampoo-sales.csv', header=0, index_col=0, parse_dates=True, squeeze=True, date_parser=parser)

# evaluate parameters
p_values = [0, 1, 2, 4, 6, 8, 10]
d_values = range(0, 3)
q_values = range(0, 3)
warnings.filterwarnings("ignore")
evaluate_models(series.values, p_values, d_values, q_values)
```

列表 26.7：在洗发水销售数据集上网格搜索 ARIMA 配置。

运行该示例会打印每次成功评估完成的 ARIMA 参数和 RMSE。运行结束时报告最佳参数为 ARIMA(4,2,1)，其均方根误差为 68.519 销售单位。

```text
ARIMA(0, 0, 0) RMSE=228.966
ARIMA(0, 0, 1) RMSE=195.308
ARIMA(0, 0, 2) RMSE=154.886
ARIMA(0, 1, 0) RMSE=134.176
ARIMA(0, 1, 1) RMSE=97.767
ARIMA(0, 2, 0) RMSE=259.499
ARIMA(0, 2, 1) RMSE=135.363
ARIMA(1, 0, 0) RMSE=152.029
ARIMA(1, 1, 0) RMSE=84.388
ARIMA(1, 1, 1) RMSE=83.688
ARIMA(1, 2, 0) RMSE=136.411
ARIMA(2, 1, 0) RMSE=75.432
ARIMA(2, 1, 1) RMSE=88.089
ARIMA(2, 2, 0) RMSE=99.302
ARIMA(4, 1, 0) RMSE=81.545
ARIMA(4, 1, 1) RMSE=82.440
ARIMA(4, 2, 0) RMSE=87.157
```
