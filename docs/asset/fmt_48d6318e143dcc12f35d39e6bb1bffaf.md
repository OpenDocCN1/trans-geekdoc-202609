
图 29.2 包含了上述评估的 Ising 模型价格过程。视觉检查发现，由模拟 Ising 模型驱动的价格会发生突然下降，如索引时间 400 左右所示。然而，为了证实这些化事实（stylised facts），必须对大量的模拟进行适当的统计分析，并确认这些事实，例如收益的胖尾、序列相关性和波动性的长期记忆。

## 29.3 结论

因此我们可以得出结论，`q` 足够灵活，可以创建并模拟基于代理的计算模型。本节介绍的模型简单直接。它缺乏任何面向对象的方法，而这在代理建模社区中非常流行。通常情况下，代理是对象，代理之间的链接也是对象。例如，参考基于 C++ 的库 `Zarja` `zar`，它将代理和代理之间的链接定义为对象，其属性可以以模块化的方式定义。

在我们的方法中，我们的目标是展示除了与 `q` 连接的时间序列分析之外，处理基于代理模型的可能性。

## 经济物理学：基于代理的计算模型 593

本节介绍的模型仍然可以回答许多问题的问题，即与临界现象的出现有关的问题。介绍的模型可以通过包含多个资产并通过代理利益的相关性来分析价格相关性进行扩展。

模型捕捉金融时间序列化事实的能力为所提模型提供了另一个用途：作为用于模型/分析测试的随机金融时间序列生成器。这在需要合成数据来开发例如分析套件并测试其在真实数据下的性能时特别有用。此外，模型可以被设置为数据生成器，由行情机捕获并存储在数据库中——数据的另一种潜在用途。

我们鼓励读者运行自己的模拟，并考虑数值研究以下研究问题（但不限于）：

- 如果交互是随机的会？每次执行一次随机交互。
- 如果交易者可以与更多交易者交互会？扩展每个交易者周围的区域。使交互的交易者数量变为随机。
- 如果交易者可以交易多种资产会？扩展资产数量。
- 如果交易者可以交易多个单位会？扩展模型以处理非均匀交易量。
- 如果系统是庞大的会？扩展模型。
- 系统的化事实是什么？

## 618 结语

## 619 第 30 章

数据科学和机器学习被频繁提及。

## 结语：艺术

![](img/97f7581128bd0bdf85683d4c69d94242_621_0.png)

### 图 30.1 圆形

```
// convert into table

quantum.art.pivotColours:

// canvas with canvas and patterns:update (-1)^colour1, (-1)^colour2 from

(select x, colour1:y from canvas where colour=1)

(select x, colour2:y from canvas where colour=-1);
```

让我们生成两个画布，一个包含圆形，另一个包含正方形。在每幅图中，我们放置了 42 个对象。首先，我们生成一个随机圆形图案：

```
canvas1: empty;

canvas1: (quantum.art.placeCircle[100]/[42;canvas1]);

canvas1: quantum.art.pivotColours[canvas1];
```

然后生成一个随机正方形图案：

```
canvas2: empty;

canvas2: (quantum.art.placeSquare[100]/[42;canvas2]);

canvas2: quantum.art.pivotColours[canvas2];
```

图 30.1 描述了 `canvas2`，我们称之为“圆形”。图 30.2 描述了 `canvas2`，我们称之为“正方形”。这种随机性远未达到艺术家的水平，但图片背后的思想应该是可见的。几何对象与随机性的相互作用随之而来。让我们在纯随机性的基础上更进一步，为我们的艺术加入一些数学秩序。我们不再使用均匀放置，而是使用更高级的规则来放置对象。特别是，我们使用二次变换 $\propto x^2$ 增加了向右上角的概率。

## 机器学习

![](img/97f7581128bd0bdf85683d4c69d94242_622_0.png)

### 图 30.2 正方形

```
quantum.art.placeGradient:diameter; canvas

// diameter of the circle in units

// canvas with canvas to be modified

// random position, position is float

position: (sqrt first 1+1+exec x from canvas;sqrt first 1+1+exec y from canvas);

// find a circle around the position and invert the colour:update colour+neg[1] from canvas where diameter>=sqrt[x-position[0];2]+x-position[1];2];
```

![](img/97f7581128bd0bdf85683d4c69d9242_622_1.png)

### 图 30.3 梯度

让我们生成另一个具有新二次规则的画布：

```
canvas3: empty;

canvas3: (quantum.art.placeGradient[100]/[42;canvas3]);

canvas3: quantum.art.pivotColours[canvas3];
```
