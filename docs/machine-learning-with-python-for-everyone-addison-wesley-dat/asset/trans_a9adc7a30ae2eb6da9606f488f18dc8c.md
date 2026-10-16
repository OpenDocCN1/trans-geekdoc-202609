

## 15.6.2 线性回归的 PGM 视角

让我们将 PGM 的思想应用到线性回归上。

### 15.6.2.1 完整写法

下面说明这对我们传统（GOF）线性回归是如何运作的。我们首先绘制一个模型（图15.6），展示特征和权重如何相互作用。这幅图与我们为神经网络形式的线性回归所绘制的模型非常相似，只是额外添加了所学习权重的占位分布。

![](img/d94e4cd766940d79abed0bc6ba4e4344_547_0.png)

图15.6：线性回归的概率图模型。

我们探索 PGM 的主要工具将是 pymc3。其中 mc 代表 Monte Carlo（蒙特卡洛），一个著名的赌场。当你看到这个名字时，心里可以简单地把它替换成“随机性”。

```
In [29]:
import pymc3 as pm

# getting really hard to convince toolkits to be less verbose
```

```
import logging
pymc3_log = logging.getLogger('pymc3')
pymc3_log.setLevel(2**20)
```

在本书大部分内容中，我们都把这个细节略过了——但当我们用线性回归预测一个值时，我们实际上预测的是一个单一的输出目标值，它是在该位置上所有可能结果的均值。实际上，如果我们的数据不完美，这个值上下会有一些波动空间。这种可能存在的波动空间——GOF 线性回归对每次预测都视为相同——是一个正态分布。是的，正态分布真的无处不在。这个正态分布以预测值为中心，并围绕该中心有一个标准差，因此它表现为线性回归线上下的一条带状区域。我们的预测仍然落在线性回归线上。新增的组件仅仅是类似于回归线周围的容差带。当我们把线性回归视为 PGM 时，我们通过指定标准差来显式地揭示这个隐藏细节。

让我们把图15.6中的图转换成代码：

In [30]:

```
with pm.Model() as model:
    # boilerplate-ish setup of the distributions of our
    # guesses for things we don't know
    sd          = pm.HalfNormal('sd', sd=1)
    intercept   = pm.Normal('Intercept', 0, sd=20)
    ftr_1_wgt   = pm.Normal('ftr_1_wgt', 0, sd=20)

    # outcomes made from initial guess and input data
    # this is y = m x + b in an alternate form
    preds = ftr_1_wgt * linreg_table['ftr_1'] + intercept

    # relationship between guesses, input data, and actual outputs
    # target = preds + noise(sd)  (noise == tolerance around the line)
    target = pm.Normal('tgt',
                       mu=preds, sd=sd,
                       observed=linreg_table['tgt'])

    linreg_trace = pm.sample(1000, verbose=-1, progressbar=False)
```

做完这些之后，看不到任何输出有点令人失望。不过别担心。

In [31]:

```
pm.summary(linreg_trace)[['mean']]
```

|  | mean |
|---|---|
| **Intercept** | 2.0000 |
| **ftr_1_wgt** | 3.0000 |
| **sd** | 0.0000 |

这*真的*很令人欣慰。虽然我们走了完全不同的路径来到此处，但我们看到权重估计值分别为 3 和 2——正是我们用 `linreg_table` 生成数据时所使用的值。同样令人欣慰的是，我们对数据噪声的估计 `sd` 为 0。我们在生成 `linreg_table` 中的数据时没有加入任何噪声。我们已尽可能地完美了。

### 15.6.2.2 简略写法

那个代码示例中列出的细节很多。幸运的是，我们不必每次都指定这些细节。相反，我们可以写一个简单的公式，告诉 `pymc3`：目标依赖于 `ftr_1`，并且加一个常数作为 +1 的技巧。然后，`pymc3` 会替我们完成上面写出的所有填充工作。`family=` 参数与我们在完整写法中的 `target=` 赋值起着相同的作用。两者都告诉我们，我们正在构建一个以预测值为中心、带有一定容差带的正态分布。

In [32]:

```
with pm.Model() as model:
    pm.glm.GLM.from_formula('tgt ~ ftr_1', linreg_table,
                            family=pm.glm.families.Normal())
    linreg_trace = pm.sample(5000, verbose=-1, progressbar=False)
pm.summary(linreg_trace)[['mean']]
```

|  | mean |
|---|---|
| **Intercept** | 2.0000 |
| **ftr_1** | 3.0000 |
| **sd** | 0.0000 |

这里的名称是特征的名称。如果能够清楚地表明它们是这些特征上的*权重*值，我会更高兴。不过，我的观点已经表达清楚了。我们得到了相同的权重答案，这令人安心。现在，我想提一下 PGM 的一个好处：我们可以看到一个*范围*内的可能答案，而不是只有一个单一答案。那会是什么样子呢？

In [33]:

```
%%capture

# workaround for a problem: writing to a tmp file.
%matplotlib qt

fig, axes = plt.subplots(3,2,figsize=(12,6))
axes = pm.traceplot(linreg_trace, ax=axes)
for ax in axes[:,-1]:
    ax.set_visible(False)

plt.gcf().savefig('outputs/work-around.png')
```

In [34]:

```
Image('outputs/work-around.png', width=800, height=2400)
```

Out[34]:

![](img/d94e4cd766940d79abed0bc6ba4e4344_550_0.png)

我们可以像线性回归一样快速构建几乎完全相同的模型，只是使用稍微不同的 family：现在我们需要使用 Binomial 作为目标分布。每当你看到 binomial，就可以立刻用抛硬币的心智模型来理解。由于我们的逻辑回归示例有两个类别，我们可以把它们看作正面和反面。然后，我们只是在寻找抛到正面的概率。用二项分布替换正态分布——就得到以下代码：

In [35]:

```
with pm.Model() as model:
    pm.glm.GLM.from_formula('tgt ~ ftr_1', logreg_table,
                            family=pm.glm.families.Binomial())
    logreg_trace = pm.sample(10000, verbose=-1, progressbar=False)
pm.summary(logreg_trace)['mean']
```

Out[35]:

|  | mean |
|---|---|
| Intercept | 22.6166 |
| ftr_1 | -2.2497 |

这里的结果并不精确：真实的原始值是 20 和 −2。但请记住，我们的 logreg_table 比线性回归数据更真实一些。它在中间部分包含了噪声，这些例子的分类并非完美地分为正面和反面——也就是我们原本的 0 和 1。

对于线性回归，我们观察了权重的单变量——独立——分布。我们还可以观察权重的双变量——联合——分布。对于逻辑回归示例，让我们看看这两个权重最可能取值组合在什么位置。

In [36]:

```
%matplotlib inline

df_trace = pm.trace_to_dataframe(logreg_trace)
sns.jointplot('ftr_1', 'Intercept', data=df_trace,
              kind='kde', stat_func=None, height=4);
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_553_0.png)

较深色的区域代表最可能的权重组合。我们看到这两个权重并不是相互独立的。如果 ftr_1 的权重稍微上升——也就是说，不那么负了——截距的权重就必须稍微下降。

你可以把这想象成规划一次长途驾车。如果你的到达时间目标固定，你可以选择某个出发时间和某个驾驶速度。如果你早点出发，就可以开得慢一点。如果你晚点出发——节假日疯狂，说的就是你——你就必须开快一点才能在同一时间到达。对我们的逻辑回归模型而言，在同一时间到达——图中的深色区域——意味着我们看到的数据很可能来自出发时间与驾驶速度之间的某种权衡。

## 15.7 章末

### 15.7.1 小结

我们在这里讨论了三个主要主题：（1）如何使用通用优化求解几种不同的学习算法；（2）如何使用神经网络表示线性回归和逻辑回归；（3）如何使用概率图模型表示线性回归和逻辑回归。一个关键点是，这两种模型是非常近的亲缘关系。

第二点是，*所有*学习方法从根本上来说都在做类似的事情。最后一点值得思考：神经网络和 PGM 可以表达非常*复杂*的模型——但它们是由非常*简单*的组件构建而成的。

### 15.7.2 注记

如果你有兴趣了解更多关于优化的内容，可以在微积分课上看看求零点和导数，或者找一些 Youtube 视频。你甚至可以拿到关于“寻优”的完整学位。在数学、商学和工程项目中，都有人在研究优化。

## 逻辑回归与损失

对于 $z = \beta x$，逻辑回归模型中的概率为 $p_{y=1} = \frac{1}{1+e^{-z}}$。这也给出 $p = \text{logistic}(z) = \text{logistic}(\beta x)$。最小化交叉熵损失可以得到以下表达式：

- 对于 0/1：$-y z + \log(1 + e^{z})$
- 对于 $\pm1$：$\log(1 + e^{-y z})$

当我们在 NN 中超越二分类问题时，我们会为目标使用 one-hot 编码，并并行解决多个单类问题。然后，我们不再使用 logistic 函数，而是使用一个称为 *softmax* 的函数。接着，我们取可能目标中概率最高的类别。

## 神经网络

要用四句话概括神经网络的历史真的很难。它始于 20 世纪 40 年代中期，并在 1960 年前后以及 1980 年代经历了一系列繁荣与萧条的周期。在 20 世纪 90 年代中期到 2010 年代初期，主要的理论和实际硬件问题都得到了可行的解决方案。想要一个*稍微*更详细的回顾，可以参阅 Lewis 和 Denning 发表在 2018 年 12 月《*Communications of the ACM*》上的《学习机器学习》一文。

我先前简要提到，我们可以扩展神经网络以处理不止二分类目标的问题。这里有一个将这些技术应用于二分类问题的超级快速示例。你可以通过增加 n_classes 来调整类别数量，以处理更大的问题。

In [37]:

```python
from keras.utils import to_categorical as k_to_categorical
def Keras_MultiLogisticRegression(n_ftrs, n_classes):
    model = km.Sequential()
    model.add(kl.Dense(n_classes,
                    activation='softmax',
                    input_dim=n_ftrs))
    model.compile(optimizer=ko.SGD(), loss='categorical_crossentropy')
    return model

logreg_nn2 = Keras_MultiLogisticRegression(1, 2)
```

