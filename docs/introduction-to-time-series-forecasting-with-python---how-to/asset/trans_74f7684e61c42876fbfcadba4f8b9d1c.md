

```python
from matplotlib import pyplot
# 创建随机游走
seed(1)
random_walk = list()
random_walk.append(-1 if random() < 0.5 else 1)
for i in range(1, 1000):
    movement = -1 if random() < 0.5 else 1
    value = random_walk[i-1] + movement
    random_walk.append(value)
# 计算差值
diff = list()
for i in range(1, len(random_walk)):
    value = random_walk[i] - random_walk[i - 1]
    diff.append(value)
# 绘制折线图
pyplot.plot(diff)
pyplot.show()
```

列表 11.6：计算随机游走差值序列的示例。

运行该示例会生成一个折线图，显示 1,000 次 -1 和 1 的移动，看起来杂乱无章。

![](img/da419ed7447ef051ee9d00167b7274cf_111_0.png)

这个差异图也清楚地表明，在这里我们除了随机移动序列外没有其他信息可用。没有可供学习的结构。既然时间序列现在是平稳的，我们可以重新计算差值序列的相关图。完整示例如下所示。

```python
# 绘制差值随机游走的自相关图
from random import seed
from random import random
from matplotlib import pyplot
from pandas.plotting import autocorrelation_plot
# 创建随机游走
seed(1)
random_walk = list()
random_walk.append(-1 if random() < 0.5 else 1)
for i in range(1, 1000):
    movement = -1 if random() < 0.5 else 1
    value = random_walk[i-1] + movement
    random_walk.append(value)
# 计算差值
diff = list()
for i in range(1, len(random_walk)):
    value = random_walk[i] - random_walk[i - 1]
    diff.append(value)
# 绘制折线图
autocorrelation_plot(diff)
pyplot.show()
```

列表 11.7：计算随机游走差值序列相关图的示例。

运行该示例，我们可以看到滞后观测值之间没有显著关系，正如随机游走的生成方式所预期的那样。所有相关性都很小，接近零，且低于 95% 和 99% 的置信水平（除了少数统计巧合之外）。

![](img/da419ed7447ef051ee9d00167b7274cf_113_0.png)

## 11.5 预测随机游走

随机游走是不可预测的；无法对其做出合理的预测。根据随机游走的构建方式，我们可以预期能做出的最佳预测是使用上一步的时间步的观测值作为下一步时间步将要发生的值。仅因为我们知道下一步时间步将是前一时间步的函数。这通常被称为朴素预测，或持久性模型（在第 18 章中介绍）。

我们可以通过首先将数据集拆分为训练集和测试集，然后使用持久性模型采用滚动预测方法来预测结果，从而在 Python 中实现这一点。一旦收集了测试集的所有预测值，即可计算均方根误差（RMSE）。

```python
# 随机游走的持久性预测
from random import seed
from random import random
from sklearn.metrics import mean_squared_error
from math import sqrt
# 生成随机游走
seed(1)
random_walk = list()
random_walk.append(-1 if random() < 0.5 else 1)
for i in range(1, 1000):
    movement = -1 if random() < 0.5 else 1
    value = random_walk[i-1] + movement
    random_walk.append(value)
# 准备数据集
train_size = int(len(random_walk) * 0.66)
train, test = random_walk[0:train_size], random_walk[train_size:]
# 持久性
predictions = list()
history = train[-1]
for i in range(len(test)):
    yhat = history
    predictions.append(yhat)
    history = test[i]
rms = sqrt(mean_squared_error(test, predictions))
print('Persistence RMSE: %.3f' % rms)
```

列表 11.8：使用持久性预测随机游走的示例。

运行该示例估算模型的 RMSE 为 1。这也是预期的，因为我们可以知道从一个时间步到下一个时间步的变化总是 1，无论是正方向还是负方向。

> 持久性 RMSE: 1.000

列表 11.9：使用持久性预测随机游走的输出。

随机游走初学者犯的另一类错误是假设如果知道误差范围（方差），那么我们就可以使用随机游走生成类型的过程来进行预测。也就是说，如果我们知道误差是 -1 或 1，那么为什么不在前一个值的基础上添加随机选择的 -1 或 1 来进行预测呢？我们可以在下面的 Python 代码中演示这种随机预测方法。

```python
# 随机游走的随机预测
from random import seed
from random import random
from sklearn.metrics import mean_squared_error
from math import sqrt
# 生成随机游走
seed(1)
random_walk = list()
random_walk.append(-1 if random() < 0.5 else 1)
for i in range(1, 1000):
    movement = -1 if random() < 0.5 else 1
    value = random_walk[i-1] + movement
    random_walk.append(value)
# 准备数据集
train_size = int(len(random_walk) * 0.66)
train, test = random_walk[0:train_size], random_walk[train_size:]
# 随机预测
predictions = list()
history = train[-1]
for i in range(len(test)):
    yhat = history + (-1 if random() < 0.5 else 1)
    predictions.append(yhat)
    history = test[i]
rms = sqrt(mean_squared_error(test, predictions))
print ('Random RMSE: %.3f' % rms)
```

列表 11.10：使用随机机会预测随机游走的示例。

运行该示例，我们可以看到，确实，该算法的性能比持久性方法更差，RMSE 为 1.328。

Random RMSE: 1.328

列表 11.11：使用随机机会预测随机游走的输出。

持久性，或朴素预测，是对随机游走时间序列所能做出的最佳预测。

## 11.6 你的时间序列是随机游走吗？

你的时间序列可能是随机游走。检查你的时间序列是否为随机游走的一些方法如下：

-   时间序列显示出强烈的时间依赖性，并且以线性或类似模式衰减。
-   时间序列是非平稳的，使其平稳化后显示数据中没有明显的可学习结构。
-   持久性模型提供了最可靠的预测来源。

最后一个观点对于时间序列预测至关重要。使用持久性模型的基线预测可以快速揭示你是否能做得更好。如果不能，你很可能正在处理一个随机游走。许多时间序列都是随机游走，特别是证券价格随时间的变化。随机游走假说是一种理论，认为股票市场价格是随机游走，无法预测⁶。

随机游走是指未来的步骤或方向不能基于过去的历史进行预测。当这个术语应用于股票市场时，它意味着股价的短期变化是不可预测的。

> — 第 26 页，《漫步华尔街》。

人类思维到处都能发现模式，我们必须警惕自己，不要自欺欺人，以免浪费时间开发针对随机游走过程的复杂模型。

## 11.7 总结

在本教程中，你发现了如何使用 Python 探索随机游走。具体来说，你学习了：

-   如何在 Python 中创建随机游走过程。
-   如何探索随机游走的自相关和非平稳结构。
-   如何对随机游走时间序列进行预测。

⁶ https://en.wikipedia.org/wiki/Random_walk_hypothesis

### 11.7.1 下一步

在下一课中，你将发现如何将时间序列分解为水平、趋势和季节性等组成部分。

# 第 12 章

# 分解时间序列数据

时间序列分解涉及将序列视为水平、趋势、季节性和噪声成分的组合。分解为思考时间序列以及更好地理解时间序列分析和预测中的问题提供了一个有用的抽象模型。在本教程中，你将发现时间序列分解以及如何使用 Python 自动将时间序列拆分为其组成部分。完成本教程后，你将知道：

-   时间序列分解的分析方法及其如何帮助预测。
-   如何在 Python 中自动分解时间序列数据。
-   如何分解加法和乘法时间序列问题并绘制结果。

让我们开始吧。

## 12.1 时间序列成分

选择预测方法的一个有用抽象是将时间序列分解为系统性和非系统性成分。

-   **系统性：** 时间序列中具有一致性或重复性并且可以描述和建模的成分。
-   **非系统性：** 时间序列中无法直接建模的成分。

给定的时间序列被认为由三个系统性成分组成，包括水平、趋势、季节性，以及一个称为噪声的非系统性成分。这些成分定义如下：

-   **水平：** 序列中的平均值。
-   **趋势：** 序列中增加或减少的值。
-   **季节性：** 序列中重复的短期周期。
-   **噪声：** 序列中的随机波动。

