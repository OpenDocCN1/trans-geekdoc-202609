
有界激活函数（例如 0 到 1 或 −1 到 1）也常被称为 `squashing functions`（[Sarle, 1994](#ref.xhtml#re_CIT000322)）。例如，正如我们将看到的，`sigmoid` 函数具有将值“压缩”到有界区间内的这一特性（[Lederer, 2021](#ref.xhtml#re_CIT000213)）。再次强调，这并非意味着任何物理动作，而只是说明激活函数的效果是输出有界区间内的值。激活函数也不必在每个输出上保持一致，可以为每个输出使用不同的激活函数。

### 15.5.2 激活函数类型

正如我们所见，我们不太可能仅使用 `identity` 函数，而更倾向于使用更复杂的函数，其中大多数为 `nonlinear`，以捕捉我们试图建模的数据或过程的复杂非线性方面。在神经网络中使用的最受欢迎的激活函数通常是 `logistic`、`tanh` 和 `ReLu`（[Lederer, 2021](#ref.xhtml#re_CIT000213)），然而最近已提出一些新颖的函数，包括 `softplus`、`elu`、`selu` 和 `swish`。我们稍后将介绍其中一些激活函数。[Lederer (2021)](#ref.xhtml#re_CIT000213) 对这些函数以及更多函数提供了出色的综述。据 [Lederer (2021)](#ref.xhtml#re_CIT000213) 称，实践中应优先选择 `softsign` 和 `ReLu` 作为激活函数。`softsign` 函数由于其简单性而被发现相比 `tanh` 具有计算优势（[Lederer, 2021](#ref.xhtml#re_CIT000213)）。

然而，在选择激活函数时有一些重要的事项需要考虑。事实上，激活函数的选择会对神经网络的性能产生相当大的影响，因此如何选择“好”的激活函数已成为神经网络社区多年来的持续研究课题，整个文献都致力于此。正如 [Lederer (2021)](#ref.xhtml#re_CIT000213) 所指出的，“文献包含大量不同的激活函数，而对特定激活函数的支持与反对论点往往基于启发式和轶事542证据”（第 2 页）。此外，预测哪种激活函数在特定情况下效果最好可能非常困难甚至不可能（[Goodfellow, 2016](#ref.xhtml#re_CIT000131)）。

### 15.5.3 饱和与非饱和激活函数

理想情况下，激活函数在大多数点上应为 `differentiable` 且通常也是递增的。除此之外，我们可以选择范围广泛的激活函数，其中一些在不同上下文中比其他更可取。激活函数的一个非常重要的区分特征是它们是 `saturating` 还是 `non-saturating`。通常更倾向于非饱和激活函数而非饱和激活函数。然而，激活函数的要求并非绝对，也就是说这些要求在一定程度上是灵活的，并非在所有上下文中都更可取。

`saturating` 激活函数意味着对于大的输入，函数在某个常数值处渐近，例如 0 或 1。这是 `logistic sigmoid` 激活函数的特征（Dubey et al., [2022](#ref.xhtml#re_CIT000092)；[Murphy, 2022](#ref.xhtml#re_CIT000259）），

$$Logistic\\,\\, Sigmoid\\left( x \\right) = \\frac{1}{1 + e^{- x}}$$

(15.4)

该函数在 0 和 1 的值处饱和（或“渐近”）（Dubey et al., [2022](#ref.xhtml#re_CIT000092)）。即，

$$\\lim\\limits\_{x\\rightarrow - \\infty}\\left( \\frac{1}{1 + e^{- x}} \\right) = 0$$

and

$$\\lim\\limits\_{x\\rightarrow + \\infty}\\left( \\frac{1}{1 + e^{- x}} \\right) = 1$$

这些函数本质上会将输入“挤压”或“压缩”到上下界之间。不幸的是，正如我们即将讨论的，饱和激活函数会产生 `vanishing gradient problem`，其中目标函数的梯度变得非常接近 0，从而权重更新几乎不可能。`tanh` 函数，

$$\\tanh\\left( x \\right) = \\frac{e^{x} - e^{- x}}{e^{x} + e^{- x}}$$

(15.5)

也很受欢迎，也会压缩输入，但这次是在 −1 和 1 之间（Dubey et al., [2022](#ref.xhtml#re_CIT000092)）。

因此，训练非常深的神经网络的关键之一是选择 `non-saturating` 激活函数（[Murphy, 2022](#ref.xhtml#re_CIT000259)）。非饱和激活函数是指不渐近于常数值的函数，因此通常趋向于无穷大。即，

$$\\lim\\limits\_{x\\rightarrow\\infty}f\\left( x \\right) = \\infty$$

`rectified linear unit`（简称“ReLU”）就是这样一种非饱和激活函数，543

$${Re}LU\\left( x \\right) = \\max\\left( 0,x \\right) = \\left\\{ \\begin{array}{l} {x,\\,\\,\\,\\,\\, if\\,\\,\\,\\,\\, x \\geq 0} \\\\ {0,\\,\\,\\,\\,\\, otherwise} \\\\ \\end{array} \\right.$$

(15.6)

它是非饱和的，因为该函数的取值范围是从 0 到正无穷，即 \[0,∞)，正如我们在展示了几个竞争激活函数的 [图 15.5](#c15.xhtml#f15.5) 中所见。

![图 15.5 在神经网络中常用的一些激活函数。tanh 和 sigmoid 函数是饱和的，而 ReLu 是非饱和激活函数。返回正文。⏎](images/fig15.5.jpg)

`Figure 15.5` 在神经网络中常用的一些激活函数。`tanh` 和 `sigmoid` 函数是 `saturating`，而 `ReLu` 是 `non-saturating` 激活函数。[返回正文。⏎](#c15.xhtml#re_f15.5)

我们从 [图 15.5](#c15.xhtml#f15.5) 可以看出，`sigmoid function` 是饱和的，将输入值压缩到 \[0, 1\] 内。`tanh` 函数出于类似原因也是饱和的，这次将输入压缩到 \[−1, 1\] 内。`arctan`，另一种激活函数，也是饱和的。可以很容易看出 `ReLU` 函数是非饱和的，对于小于或等于 0 的值它恒为 0，对于大于 0 的值则线性递增，因此即使 `x` 值很大仍允许更新发生（[Alpaydin, 2020](#ref.xhtml#re_CIT000009)）。然而，对于负输入，`vanishing gradient problem` 仍然会出现（Dubey et al., [2022](#ref.xhtml#re_CIT000092)）。

> `A saturating activation function essentially “squeezes” the input values to be within specified bounds (e.g., 0, 1). A non-saturating activation function does not “bind” the input in this way and instead allows the function to typically go to infinity. When it comes to choosing an activation function for a neural network, non-saturating ones are often preferred over saturating ones.`

顺便说一下，所有这些函数都可以在软件中轻松绘制。例如，一个 `sigmoid` 激活函数在 Python 中（未显示绘图）可以非常简单地生成如下：

```
import matplotlib.pyplot as plt
import numpy as np
import math
x = np.linspace(-20, 20, 100)
y = 1/(1 + np.exp(-x))
plt.plot(x, y)
plt.xlabel(“x”)
plt.ylabel(“Sigmoid(X) Activation Function”)
plt.show()
```

#### 15.5.3.1 ReLU 的问题

`ReLU` 函数，也常因其形状而被称为 `positive-part function` 或 `ramp function`，是神经网络中使用最常见的激活函数之一。该函数的正部仅仅是 `identity` 函数，线性且斜率为 1。正是 `ReLU` 的这种 `near linearity` 在一定程度上使其具有吸引力，因为它可以允许使用基于梯度的方法进行易于优化，就像大多数线性模型的情况一样（[Goodfellow et al., 2016](#ref.xhtml#re_CIT000131)）。该函数的负部在 0 处恒定。更仔细地查看 `ReLU` 函数会揭示这些特征（[图 15.6](#c15.xhtml#f15.6)）。

