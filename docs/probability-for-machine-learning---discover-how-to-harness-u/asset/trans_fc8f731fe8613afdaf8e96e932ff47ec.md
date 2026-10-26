
> — 《关于昂贵成本函数的贝叶斯优化教程，应用于主动用户建模和分层强化学习》，2010。

**代理函数**：可高效采样的目标函数的贝叶斯近似。

代理函数为我们提供了目标函数的估计值，可用于指导未来的采样。采样涉及在称为 *采集* 函数的函数中谨慎使用后验，例如用于获取更多样本。我们希望利用对目标函数的信念来采样最有可能产生回报的搜索空间区域，因此采集函数将优化搜索中位置的条件概率以生成下一个样本。

**采集函数**：利用后验从搜索空间中选择下一个样本的技术。

一旦收集了额外的样本及其通过目标函数 $f()$ 的评估，它们将被添加到数据 $D$ 中，然后后验将被更新。该过程重复进行，直到找到目标函数的极值、找到足够好的结果或资源耗尽。贝叶斯优化算法可总结如下：

1. 通过优化采集函数选择样本。
2. 使用目标函数评估样本。
3. 更新数据，进而更新代理函数。
4. 返回 1。

## 19.4 如何执行贝叶斯优化

在本节中，我们将通过从头开始为一个简单的一维测试函数开发实现来探索贝叶斯优化的工作原理。首先，我们将定义测试问题，然后说明如何使用代理函数对输入到输出的映射进行建模。接下来，我们将了解如何使用采集函数高效地搜索代理函数，然后将所有这些元素整合到贝叶斯优化流程中。

### 19.4.1 测试问题

第一步是定义一个测试问题。我们将使用一个具有五个峰值的多峰问题，计算公式为：

$$ y = x^2 \times \sin(5 \times \pi \times x)^6 \tag{19.5} $$

其中 $x$ 是范围在 $[0,1]$ 内的实数值，$\pi$ 是 pi 的值。我们将通过添加均值为零、标准差为 0.1 的高斯噪声来增强此函数。这意味着实际评估会加上正负随机值，使得函数难以优化。下面的 `objective()` 函数实现了这一点。

下面列出了我们希望优化的测试函数的完整示例。

```python
# example of the test problem
from math import sin
from math import pi
from numpy import arange
from numpy import argmax
from numpy.random import normal
from matplotlib import pyplot

# objective function
def objective(x, noise=0.1):
    noise = normal(loc=0, scale=noise)
    return (x**2 * sin(5 * pi * x)**6.0) + noise

# grid-based sample of the domain [0,1]
X = arange(0, 1, 0.01)
# sample the domain without noise
y = [objective(x, 0) for x in X]
# sample the domain with noise
ynoise = [objective(x) for x in X]
# find best result
ix = argmax(y)
print('Optima: x=%.3f, y=%.3f' % (X[ix], y[ix]))
# plot the points with noise
pyplot.scatter(X, ynoise)
# plot the points without noise
pyplot.plot(X, y)
# show the plot
pyplot.show()
```

Listing 19.7: 示例：绘制目标函数的样本。

运行该示例首先报告全局最优解为输入值 0.9，其得分为 0.81。

```
Optima: x=0.900, y=0.810
```

Listing 19.8: 从采样目标函数得到的最优解示例输出。

然后创建一个图表，显示样本的噪声评估（点）和目标函数的无噪声真实形状（线）。由于噪声目标函数的随机性，你的具体点会有所不同。

![](img/6ef657cfead7281442f755181c4f6e50_182_0.png)

Figure 19.1: 使用噪声（点）和非噪声（线）目标函数评估的输入样本图。

现在我们有了测试问题，让我们回顾如何训练代理函数。

### 19.4.2 代理函数

代理函数是一种用于最佳逼近输入示例到输出分数映射的技术。在概率上，它总结了在给定可用数据 ($D$) 的情况下目标函数 ($f$) 的条件概率，或 $P(f|D)$。有多种技术可用于此目的，尽管最流行的方法是将问题视为回归预测建模问题，其中数据代表输入，分数代表模型的输出。这通常最好使用随机森林或高斯过程进行建模。高斯过程（Gaussian Process，GP）是一种在假设多元高斯分布的情况下在变量上构建联合概率分布的模型。因此，它能够高效有效地总结大量函数，并在模型获得更多观测时实现平滑过渡。

这种平滑结构和基于数据的向新函数的平滑过渡是我们采样域时期望的属性，而模型的基于多元高斯的基础意味着模型的估计将是具有标准差的分布的均值；这将在后期的采集函数中有所帮助。因此，使用 GP 回归模型通常是首选。

我们可以使用来自输入样本 ($X$) 和目标函数 ($y$) 的噪声评估的 GaussianProcessRegressor scikit-learn 实现来拟合 GP 回归模型。首先，必须定义模型。定义 GP 模型的一个重要方面是核函数。它根据实际数据观测之间的距离度量控制函数在特定点的形状。可以使用的核函数有很多，其中一些可能对特定数据集提供更好的性能。默认情况下，使用径向基函数（Radial Basis Function，RBF），效果良好。

```python
...
# define the model
model = GaussianProcessRegressor()
```

Listing 19.9: 示例：定义高斯过程模型。

定义后，模型可以通过调用 `fit()` 函数直接在训练数据集上拟合。定义的模型可以在任何时候通过对 `fit()` 的另一次调用，使用更新的数据附加到现有数据上再次拟合。

```python
...
# fit the model
model.fit(X, y)
```

Listing 19.10: 示例：拟合高斯过程模型。

模型将估计为其提供的一个或多个样本的成本。通过调用 `predict()` 函数使用模型。给定样本的结果将是该点分布的均值。我们还可以通过指定参数 `return_std=True` 来获取函数中该点分布的标准差；例如：

```python
...
yhat = model.predict(X, return_std=True)
```

Listing 19.11: 示例：使用高斯过程模型进行预测。

如果我们在感兴趣采样的给定点处分布很薄，该函数可能会产生警告。因此，我们可以在进行预测时静默所有警告。下面的 `surrogate()` 函数接收已拟合的模型和一个或多个样本，并返回估计的均值和标准差成本，同时不打印任何警告。

```python
# surrogate or approximation for the objective function
def surrogate(model, X):
    # catch any warning generated when making a prediction
    with catch_warnings():
        # ignore generated warnings
        simplefilter("ignore")
        return model.predict(X, return_std=True)
```

Listing 19.12: 示例：用于逼近目标函数的代理函数。

我们可以在任何时候调用此函数来估计一个或多个样本的成本，例如在下一节中我们想要优化采集函数时。目前，有趣的是看看代理函数在随机样本训练后在整个域上的表现。我们可以通过首先在 100 个数据点的随机样本及其带噪声的真实目标函数值上拟合 GP 模型来实现这一点。然后我们可以绘制这些点的散点图。接下来，我们可以在输入域上进行基于网格的采样并估计
