
清单 23.18：计算每个示例的交叉熵的示例。

最后，我们可以计算数据集中交叉熵的平均值，并将其报告为模型在该数据集上的交叉熵损失。

```
...
# calculate the average cross-entropy
mean_ce = mean(results)
print('Average Cross Entropy: %.3f nats' % mean_ce)
```

清单 23.19：计算平均交叉熵的示例。

将所有内容结合起来，完整的示例列在下面。

```
# calculate cross entropy for classification problem
from math import log
from numpy import mean

# calculate cross entropy
def cross_entropy(p, q):
    return -sum([p[i]*log(q[i]) for i in range(len(p))])

# define classification data
p = [1, 1, 1, 1, 1, 0, 0, 0, 0, 0]
q = [0.8, 0.9, 0.9, 0.6, 0.8, 0.1, 0.4, 0.2, 0.1, 0.3]
# calculate cross entropy for each example
results = list()
for i in range(len(p)):
    # create the distribution for each event {0, 1}
    expected = [1.0 - p[i], p[i]]
    predicted = [1.0 - q[i], q[i]]
    # calculate cross entropy for the two events
    ce = cross_entropy(expected, predicted)
    print('> [y=%.1f, yhat=%.1f] ce: %.3f nats' % (p[i], q[i], ce))
    results.append(ce)

# calculate the average cross entropy
mean_ce = mean(results)
print('Average Cross Entropy: %.3f nats' % mean_ce)
```

清单 23.20：计算期望概率与预测概率之间平均交叉熵的示例。

运行该示例会打印每个示例的实际概率和预测概率以及以纳特为单位的交叉熵。在这种情况下，所有示例的最终平均交叉熵损失报告为 0.247 纳特。

```
>[y=1.0, yhat=0.8] ce: 0.223 nats
>[y=1.0, yhat=0.9] ce: 0.105 nats
>[y=1.0, yhat=0.9] ce: 0.105 nats
>[y=1.0, yhat=0.6] ce: 0.511 nats
>[y=1.0, yhat=0.8] ce: 0.223 nats
>[y=0.0, yhat=0.1] ce: 0.105 nats
>[y=0.0, yhat=0.4] ce: 0.511 nats
>[y=0.0, yhat=0.2] ce: 0.223 nats
>[y=0.0, yhat=0.1] ce: 0.105 nats
>[y=0.0, yhat=0.3] ce: 0.357 nats
Average Cross Entropy: 0.247 nats
```

清单 23.21：期望概率与预测概率之间交叉熵的示例输出。

这就是在交叉熵损失函数下优化逻辑回归模型或神经网络模型时计算交叉熵损失的方法。

## 23.5.3 使用 Keras 计算交叉熵

我们可以通过使用 Keras 深度学习 API 中的 `binary_crossentropy()` 函数来确认相同的计算，以计算我们的小数据集的交叉熵损失。完整的示例列在下面。请注意，本示例假定您已安装 Keras 库并使用 TensorFlow 等后端库进行配置。如果没有，可以跳过运行此示例。

```python
# calculate cross entropy with keras
from numpy import asarray
from keras import backend
from keras.losses import binary_crossentropy
# prepare classification data
p = asarray([1, 1, 1, 1, 1, 0, 0, 0, 0, 0])
q = asarray([0.8, 0.9, 0.9, 0.6, 0.8, 0.1, 0.4, 0.2, 0.1, 0.3])
# convert to keras variables
y_true = backend.variable(p)
y_pred = backend.variable(q)
# calculate the average cross-entropy
mean_ce = backend.eval(binary_crossentropy(y_true, y_pred))
print('Average Cross Entropy: %.3f nats' % mean_ce)
```

清单 23.22：使用 Keras 计算期望概率与预测概率之间平均交叉熵的示例。

运行示例，我们可以看到报告了相同的 0.247 纳特的平均交叉熵损失。这证实了交叉熵的手动计算是正确的。

```text
Average Cross Entropy: 0.247 nats
```

清单 23.23：使用 Keras 计算期望概率与预测概率之间平均交叉熵的示例输出。

我们可以看到，我们同样可以最小化 KL 散度作为损失函数，而不是交叉熵。具体数值会不同，但效果是相同的，因为这两个值彼此成比例（例如减去 P 的熵的常数）。

最小化该 KL 散度与最小化分布之间的交叉熵完全对应。

> — 第 132 页，*Deep Learning*，2016 年。

## 23.6 交叉熵与对数损失之间的区别

交叉熵不是对数损失，但在作为二元分类问题（第 13 章介绍）的损失函数使用时，它们计算的是相同的量。

### 23.6.1 对数损失是负对数似然

Logistic loss 指的是通常用于优化逻辑回归模型的损失函数。它也可能被称为 logarithmic loss（这令人困惑）或简单地称为 log loss。许多模型是在称为最大似然估计或 MLE 的概率框架下进行优化的，该框架涉及找到一组最能解释观测数据的参数。

这涉及选择一个似然函数，该函数定义了在给定模型参数的情况下一组观测值（数据）的可能性。当使用对数似然函数时（这是常见的），通常被称为为模型优化对数似然。由于在实践中最小化函数比最大化函数更常见，因此对数似然函数通过在前面加上负号来反转。这将其转换为负对数似然函数或简称为 NLL。在最大似然估计框架下推导伯努利概率分布函数（两个类别）的对数似然函数时，计算结果为：

$$\mathrm{NLL}(P,Q) = -\big(P(\mathit{class0}) \times \log(Q(\mathit{class0})) + P(\mathit{class1}) \times \log(Q(\mathit{class1}))\big) \tag{23.9}$$

该量可以通过计算似然函数的对数的平均值在所有训练示例上进行平均。对于二元分类问题，负对数似然通常缩写为 simply *log loss*，作为为逻辑回归推导的损失函数。

$$\text{log loss} = \text{negative log-likelihood, under a Bernoulli probability distribution} \tag{23.10}$$

我们可以看到，负对数似然与用于伯努利概率分布函数（两个事件或类别）的交叉熵所使用的计算相同。事实上，多项分布（多类分类）的负对数似然也与交叉熵的计算相匹配。

### 23.6.2 对数损失和交叉熵计算的是同一事物

对于二元分类问题，*log loss*、*cross-entropy* 和 *negative log-likelihood* 可以互换使用。更一般地，在分类模型的损失函数上下文中，术语 *cross-entropy* 和 *negative log-likelihood* 可以互换使用。

> The negative log-likelihood for logistic regression is given by [...] This is also called the cross-entropy error function.

> — 第 246 页，*Machine Learning: A Probabilistic Perspective*，2012 年。

因此，计算 log loss 将给出与计算伯努利概率分布的交叉熵相同的量。我们可以通过使用 scikit-learn API 中的 `log_loss()` 函数计算 log loss 来确认这一点。对上一节中相同的实际概率和预测概率集合计算平均 log loss 应该与计算平均交叉熵得到相同的结果。完整的示例列在下面。

```python
# calculate log loss for classification problem with scikit-learn
from sklearn.metrics import log_loss
from numpy import asarray
# define classification data
p = [1, 1, 1, 1, 1, 0, 0, 0, 0, 0]
q = [0.8, 0.9, 0.9, 0.6, 0.8, 0.1, 0.4, 0.2, 0.1, 0.3]
# define data as expected, e.g. probability for each event {0, 1}
y_true = asarray([[1-v, v] for v in p])
y_pred = asarray([[1-v, v] for v in q])
# calculate the average log loss
ll = log_loss(y_true, y_pred)
print('Average Log Loss: %.3f' % ll)
```

清单 23.24：计算期望概率与预测概率之间平均对数损失的示例。

运行示例给出了预期的 0.247 对数损失结果，这与使用平均交叉熵计算得到的 0.247 纳特相匹配。

```text
Average Log Loss: 0.247
```

清单 23.25：计算期望概率与预测概率之间平均对数损失的示例输出。

这并不意味着 log loss 计算交叉熵或交叉熵计算 log loss。相反，它们是来自不同研究领域的不同的量，在计算分类任务的损失函数条件下，会导致等效的计算和结果。具体来说，交叉熵损失函数在伯努利或多项分布下等价于最大似然函数。这展示了最大似然估计研究与离散概率分布的信息论之间的联系。

它并不局限于离散概率分布，这一事实让许多初次听说的人感到惊讶。具体来说，在最大似然估计框架下优化的线性回归假设目标变量服从高斯连续概率分布，并涉及最小化均方误差函数。这等价于具有高斯概率分布的随机变量的交叉熵。

> Any loss consisting of a negative log-likelihood is a cross-entropy between the empirical distribution defined by the training set and the probability distribution defined by model. For example, mean squared error is the cross-entropy between the empirical distribution and a Gaussian model.
> 
> — 第 132 页，*Deep Learning*，2016 年。

这有点令人震惊，来自连续随机变量的微分熵领域。这意味着，如果你计算两个覆盖相同事件（具有相同的均值和标准差）的高斯随机变量之间的均方误差，那么你就是在计算变量之间的交叉熵。这也意味着，如果你使用均方误差损失来优化神经网络模型以解决回归问题，那么实际上你正在使用交叉熵损失。
