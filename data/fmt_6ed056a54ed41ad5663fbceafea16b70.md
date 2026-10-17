
预测值 `image_rsrc32V.jpg`: `[2.5, 0.0, 2, 8]`

### MAE 计算步骤

1. 计算每个真实值与预测值之间的绝对差。
2. 将所有绝对差求和。
3. 将总和除以数据点的数量以得到平均值。

### 逐步计算

1. 计算绝对差：`image_rsrc338.jpg`，`image_rsrc339.jpg`，`image_rsrc33A.jpg`，`image_rsrc33B.jpg`。
2. 绝对差和：`image_rsrc33C.jpg`。
3. 计算平均值：`image_rsrc335.jpg`，`image_rsrc33D.jpg`。

因此，给定示例数据的 `MAE` 为 0.5。

### 交叉熵 (Cross Entropy)

另一种重要的损失函数是交叉熵。公式如下：

```
image_rsrc33E.jpg
```

交叉熵是深度学习中常用的损失函数，以其快速学习的优势可用。

### 示例数据

真实值 `image_rsrc30D.jpg`: `[1, 0, 1, 0]`

预测值 `image_rsrc32V.jpg`: `[0.9, 0.1, 0.8, 0.4]`

### MAE 计算步骤

1. 对每对真实值和预测值应用交叉熵公式。
2. 将所有的单独熵求和。
3. 将总和除以数据点的数量以得到平均值。

### 逐步计算

1. 计算每对的交叉熵：`image_rsrc33F.jpg`，`image_rsrc33G.jpg`，`image_rsrc33H.jpg`，`image_rsrc33J.jpg`，`image_rsrc33K.jpg`，`image_rsrc33M.jpg`，`image_rsrc33N.jpg`，`image_rsrc33P.jpg`。
2. 熵和：`image_rsrc33R.jpg`。
3. 计算平均值：`image_rsrc335.jpg`，`image_rsrc33S.jpg`。

因此，给定示例数据的交叉熵损失为 0.2362。

然后，损失函数变成了一个熟悉的二次函数公式。此外，误差最小的点可以一眼识别出来。虽然肉眼可以瞬间发现误差最小的点，遗憾的是，机器无法做到这一点。然而，有一个关键事实需要注意：误差最小的点始终是切线斜率为零的地方。

![](img/image_rsrc33W.jpg)

因此，梯度下降通过计算某点 ![](img/image_rsrc30T.jpg) 处的梯度来工作，如果梯度为负，则增加 ![](img/image_rsrc30T.jpg)，如果梯度为正，则减小 ![](img/image_rsrc30T.jpg)。梯度越大，变化越大；梯度越接近 0，变化越小。这种方法逐渐找到梯度趋于 0 的点。当 ![](img/image_rsrc30T.jpg) 达到该点时，误差达到最小。

### 数学表达式

根据泰勒展开（Taylor approximation）:

![](img/image_rsrc33X.jpg)![](img/image_rsrc33Y.jpg)

因此，对于损失函数 (C) 和权重 ![](img/image_rsrc33Z.jpg):

![](img/image_rsrc340.jpg)![](img/image_rsrc341.jpg)![](img/image_rsrc342.jpg)![](img/image_rsrc343.jpg)![](img/image_rsrc344.jpg)

为了最大化 ![](img/image_rsrc345.jpg)，即最大化损失的变化，或者换句话说，尽可能快地下降到最小点，

![](img/image_rsrc346.jpg)

权重的变化必须等于梯度。因此，梯度下降的数学表达式如下：

![](img/image_rsrc347.jpg)

其中 ![](img/image_rsrc348.jpg) 代表权重，![](img/_rsrc30P.jpg) 是学习率，![](img/_rsrc349.jpg) 是损失函数的梯度。`image_rsrc349.jpg` 代表给定点处的梯度，`image_rsrc34A.jpg` 的计算方式为 ![](img/image_rsrc34B.jpg)，意味着它的量级与梯度相同但方向相反。

因此，通过权重相对于损失函数的变化来重写梯度下降，我们可以用熟悉的梯度下降公式将其表示如下：

![](img/image_rsrc34C.jpg)

我们将在下一章结合反向传播算法探索梯度下降的具体示例。

## 6.4 总结

梯度下降是机器学习和深度学习中常用的一种优化算法，通过最小化损失函数来寻找模型的优化参数。损失函数衡量模型预测值与真实值之间的差异，常见的示例有 MSE、MAE 和交叉熵。梯度下降的工作是计算损失函数的梯度并迭代更新参数，以向梯度为 0 点（即最小值）移动。在数学上，这涉及到在梯度为负时增加参数，在梯度为正时减少参数。此过程不断重复直到损失函数最小化，从而增强深度学习模型的性能。

# 第 7 章：反向传播算法

## 7.1 反向传播算法背景

从 20 世纪 60 年代到 80 年初，神经网络的研究集中在单层感知机等浅层网络。然而，在反向传播算法开发之前，训练深度网络（如多层感知机）是一项挑战性问题。1986 年，研究人员 David E. Rumelhart、Geoffrey E. Hinton 和 Ronald J. Williams 介绍了反向传播算法。这一突破使得深度网络的训练成为可能，并且仍然是深度学习中最广泛使用的算法之一。

## 7.2 反向传播算法的必要性

为了理解反向传播算法的必要性，让我们考虑 MNIST 数据集。MNIST 由 70,000 张手写数字图像组成，每张 28x28 像素，导致每张图像有 784 个数据点。假设我们想构建如下结构的神经网络来识别这些数字：

![](img/image_rsrc34D.jpg)

- 输入层：784 个神经元
- 隐藏层：100 个神经元
- 输出层：10 个神经元

在这种情况下，连接权重的数量将为 79,400，偏置的数量为 110（隐藏层 100 个 + 输出层 10 个）。为了计算一张图像的损失，我们需要对权重进行 79,400 次操作。更新一个参数需要 7,640,000 次操作，由于我们需要单独更新每个参数，总操作次数将达到 80 万亿次。假设 CPU 的处理速度为每秒 8.5 亿次操作（基于 i7），更新一次 3 层神经网络的权重需要 23 小时。鉴于寻找优化权重需要数百或数千次迭代，显然，如果没有反向传播算法，现代深度学习和人工智能时代永远不会可能。

## 7.3 反向传播

让我们深入研究反向传播算法。为了掌握核心概念，让我们考虑一个简单的多层神经网络。假设我们有如下结构的神经网络：

![](img/image_rsrc34E.jpg)

让我们考虑如下结构的简单多层神经网络：

- 输入层：2 个神经元
- 隐藏层：2 个神经元
- 输出层：1 个神经元
- 输入值：![](img/image_rsrc300.jpg) 和 ![](img/image_rsrc301.jpg)
- 隐藏层权重：第一个神经元使用 ![](img/image_rsrc303.jpg), ![](img/image_rsrc305.jpg)，第二个神经元使用 ![](img/image_rsrc304.jpg), ![](img/image_rsrc34F.jpg)
- 输出层权重：![](img/image_rsrc34G.jpg), ![](img/image_rsrc34H.jpg)

我们将使用 `sigmoid` 函数作为激活函数，使用均方误差（`MSE`）作为损失函数。我们将随机初始化所有权重并将学习率设置为 `0.1`。现在我们准备好开始了。

使用反向传播训练神经网络可以分为三个主要步骤。重复步骤 1 到 3 以找到优化参数的过程被称为训练或优化过程。

### 反向传播的步骤

### 步骤 1：前向传播 (Forward Pass)

![](img/image_rsrc34J.jpg)

前向传播非常直观。给定输入值，过程如下：

![](img/image_rsrc34K.jpg)

将输入值乘以连接权重 ![](img/image_rsrc303.jpg) 和 ![](img/image_rsrc305.jpg) 并求和，得到隐藏层节点 ![](img/image_rsrc34M.jpg)。

![](img/image_rsrc34N.jpg)

同样，将输入值乘以连接权重 ![](img/image_rsrc304.jpg) 和 ![](img/image_rsrc34F.jpg) 并求和，得到隐藏层节点 ![](img/image_rsrc34P.jpg)。

![](img/image_rsrc34R.jpg)

接下来，隐藏层节点通过激活函数。

![](img/image_rsrc34S.jpg)

接下来，连接权重 ![](img/image_rsrc34G.jpg) 和 ![](img/image_rsrc34H.jpg) 的乘积求和并传递给输出层神经元 ![](img/image_rsrc34T.jpg)。

![](img/image_rsrc34U.jpg)

最后对输出层应用 `sigmoid` 函数计算最终输出。这完成了前向传播。

### 步骤 2：损失计算

为了计算损失，我们使用 `MSE` 公式：

![](img/image_rsrc32S.jpg)

由于我们只有一个输出神经元，通过将 ![](img/image_rsrc31M.jpg) 设置为 1 来简化公式。

![](img/image_rsrc34V.jpg)

我们代入预测值 ![](img/image_rsrc32V.jpg) 和真实值 ![](img/image_rsrc30D.jpg) 来计算误差 ![](img/image_rsrc34W.jpg)。

![](img/image_rsrc34X.jpg)

得到的误差 ![](img/image_rsrc34W.jpg) 为 0.125。

### 步骤 3：反向传播

首先，使用反向传播更新权重 ![](img/image_rsrc34G.jpg)。在上一章中，我们查看了梯度下降的权重更新公式。对于 ![](img/image_rsrc34G.jpg)，如下：

![](img/image_rsrc34Y.jpg)

因此，为了更新 ![](img/image_rsrc34G.jpg)，我们需要计算导数 ![](img/image_rsrc34Z.jpg)。然而，由于无法直接找到 ![](img/image_rsrc34Z.jpg)，我们使用名为链式法则（Chain Rule）的技巧。

链式法则是反向传播算法的关键。当我们我们需要找到两个变量之间的导数但不知道它们之间的直接关系时，我们可以通过已知的导数逐步扩展。通过解决每个部分，我们最终可以解决整个问题。

![](img/image_rsrc350.jpg)

因为通过顺序消除每个变量，我们留下了我们需要寻找的关系。链式法则的数学证明可能相当挑战性，但理解链式法则的概念并不困难。

例如，让我们考虑以下问题：

“猎豹的速度是狮子的两倍，狮子的速度是熊的两倍，而熊的速度是人类的 1.5 倍。猎豹的速度比人类快几倍？”

![](img/image_rsrc351.jpg)[](image_rsrc352.jpg)[](image_rsrc353.jpg)[](image_rsrc354.jpg)[](image_rsrc355.jpg)[](image_rsrc356.jpg)

然后我们可以得出结论：猎豹的速度是人类的 6 倍。

这说明了链式法则的概念。利用链式法则的这一属性，我们可以将权重的变化 ![](img/image_rsrc357.jpg) 和损失的变化分解成部分并进行计算。这是反向传播算法的核心思想。

让我们逐步计算每个部分。首先，我们将找到 ![](img/image_rsrc358.jpg)/ ![](img/image_rsrc359.jpg)。

![](img/image_rsrc35A.jpg)

对该方程关于 ![](img/image_rsrc35B.jpg 求导，我们得到以下结果。鉴于 ![](image_rsrc35B.jpg 的值为 0.646，将其代入方程得到 ![](image_rsrc35C.jpg)= -0.71。

![](img/image_rsrc35D.jpg)[](image_rsrc35E.jpg)

现在，下一步是计算 ![](img/image_rsrc35F.jpg)。在正向传播过程中，我们使用了以下 sigmoid 函数。sigmoid 函数的数学公式如下。

![](img/image_rsrc35G.jpg)

在我们的情况下，我们可以使用 ![](img/image_rsrc35H.jpg) 和 ![](img/image_rsrc35J.jpg) 来表示它。通过这样替换变量并跳过复杂的求导过程，sigmoid 函数对 ![](img/image_rsrc35J.jpg 的导数可以简单表示如下。

![](image_rsrc35K.jpg)[](image_rsrc35M.jpg)

然后，由于 ![](img/image_rsrc35N.jpg 的值为 0.646，我们可以很容易地计算 sigmoid 对 ![](image_rsrc35P.jpg 的导数。

![](image_rsrc35R.jpg)

接下来，让我们计算第三项 ![](img/image_rsrc35S.jpg)

![](img/image_rsrc35T.jpg)

接下来，第三项 ![](img/image_rsrc35S.jpg 很简单。由于 ![](image_rsrc35U.jpg)，对 ![](img/image_rsrc34T.jpg 关于 ![](image_rsrc34G.jpg 求偏导得到 ![](image_rsrc35V.jpg)。

![](img/image_rsrc35U.jpg)[](image_rsrc35W.jpg)

由于 ![](img/image_rsrc35V.jpg 在正向传播过程中计算结果为 0.615，我们现在可以使用这个值来找到 ![](image_rsrc34Z.jpg)。

![](img/image_rsrc350.jpg)[](image_rsrc35X.jpg)

然后，根据梯度下降算法的权重更新公式，

![](img/image_rsrc35Y.jpg)

我们将 -0.1 代入梯度，0.55 代入当前权重，并将学习率设置为 0.1，如下所示：

![](img/image_rsrc35Z.jpg)[](image_rsrc360.jpg)

那么 ![](img/_rsrc34G.jpg 的新权重变为 0.56。

现在轮到 ![](image_rsrc34H.jpg 了。使用链式法则，我们可以这样计算：

![](image_rsrc361.jpg)

然而，部分 ![](img/image_rsrc362.jpg 与之前计算的相同。因此，我们如下所示替换这些值：

![](image_rsrc363.jpg)

第三项同样使用以下公式计算：

![](img/image_rsrc364.jpg)[](image_rsrc35U.jpg)[](image_rsrc365.jpg)

我们发现 ![](img/image_rsrc366.jpg)。代入所有值，我们可以计算：

![](img/image_rsrc367.jpg)

![](img/image_rsrc368.jpg)= -0.095。

因此，根据梯度下降的权重更新公式，

![](img/image_rsrc369.jpg)

鉴于梯度为 -0.095，当前权重为 0.45，学习率为 0.1，我们可以代入这些值：

![](img/image_rsrc36A.jpg)[](image_rsrc36B.jpg)

因此，新权重 ![](img/_rsrc34H.jpg 变为 0.4595。

现在第二层的权重已经更新，让我们移动到第一层。

![](image_rsrc36C.jpg)

![](img/image_rsrc303.jpg 也遵循链式法则。现在，![](image_rsrc303.jpg 可以表示如下：

![](image_rsrc36D.jpg)

由于 ![](img/image_rsrc362.jpg 已经计算，我们可以从之前的计算中重用该值 ![](image_rsrc36E.jpg)。

而项 ![](img/_rsrc36F.jpg 可以从我们之前对 ![](_rsrc34G.jpg 的计算中重用，根据方程：

![](image_rsrc36G.jpg)[](image_rsrc35U.jpg)[](image_rsrc36H.jpg)

然后 ![](img/_rsrc36J.jpg 可以写为：

![](image_rsrc36K.jpg)

由于 ![](img/_rsrc36M.jpg 是 sigmoid 函数的导数，因此可以使用正向传播过程中得到的 ![](_rsrc35V.jpg 值进行计算。

![](image_rsrc36N.jpg)[](image_rsrc36P.jpg)[](image_rsrc36R.jpg)

最后，使用 ![](img/_rsrc34M.jpg 的公式可以找到 ![](_rsrc36S.jpg。最后一项变为输入值 ![](_rsrc307.jpg)。

![](img/image_rsrc36T.jpg)[](image_rsrc36U.jpg)

如果我们这些这些值并计算，会发现 ![](img/_rsrc36J.jpg 为 -0.0106。

![](image_rsrc36V.jpg)[](image_rsrc36W.jpg)

因此，剩下的任务是更新。通过应用权重更新公式，我们计算出 ![](img/_rsrc303.jpg 变为 0.7010。

![](image_rsrc36X.jpg)[](image_rsrc36Y.jpg)[](image_rsrc36Z.jpg)

以相同的方式，我们可以计算 ![](img/_rsrc370.jpg), ![](img/_rsrc371.jpg 和 ![](_rsrc372.jpg)。

### ![](img/_rsrc304.jpg 的权重更新
