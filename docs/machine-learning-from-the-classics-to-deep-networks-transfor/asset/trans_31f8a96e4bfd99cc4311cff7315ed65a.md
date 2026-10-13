
其中 `c` 和 `a` 是控制参数。该函数的图形如 [图 18.9](#Chp018_885-995_B978044329238500024X.xhtml#f0050) 所示。请注意，与 logistic sigmoid 函数相反，这是一个反对称函数，即 `f(−z) = −f(z)`。两者也被称为 *squashing*（压缩）函数，因为它们将输出限制在有限的数值范围内。

![Figure 18.8 The logistic sigmoid function for different values of the parameter a.](images/B978044329238500024X/gr008.jpg)

图 18.8 不同参数 `a` 值下的 logistic sigmoid 函数。

![Figure 18.9 The hyperbolic tangent squashing function for a = 1.7 and c = 4/3.](images/B978044329238500024X/gr009.jpg)

[图 18.9](#Chp018_885-995_B978044329238500024X.xhtml#cf0470) `a` = 1.7 和 `c` = 4/3 时的双曲正切压缩函数。

### 代价函数的非凸性

代价函数的优化一直是贯穿全书的一个反复出现的主题。在第 [5](#Chp005_177-248_B9780443292385000111.xhtml) 章中，介绍了梯度下降优化算法并概述了其部分收敛性质。随后，讨论了用于在线、逐样本模式下优化损失函数期望的随机逼近框架。梯度下降方案和在线优化原理构成了许多已被提出并用于训练前馈神经网络的优化算法的核心。我们之所以需要在神经网络的背景下专门讨论这些算法，是因为这些网络的 *多层* 结构带来了必须在应用现成的优化方案之前加以理解的困难。

在神经网络框架下处理代价函数（如公式 [(18.6)](#Chp018_885-995_B978044329238500024X.xhtml#deq14) 所示）的最小化时，一个主要困难在于其 *非凸性*。凸函数在第 [8](#Chp008_343-416_B9780443292385000147.xhtml) 章中已有讨论。在那里指出，对于凸函数的情况，每一个局部极小值也是全局极小值。例如，回顾 [图 8.3](#Chp008_343-416_B9780443292385000147.xhtml) 中典型的凸函数图形。根据函数极小值的定义，我们知道在该点梯度（在最简单的单参数空间中即导数）变为零。函数梯度变为零的点被称为 *临界点* 或 *驻点*。

然而，如果函数不是凸的，驻点可能属于以下三类之一：(a) 局部极小值（极大值），(b) 全局极小值（极大值），或 (c) 鞍点；参见一维空间情况下的 [图 18.10](#Chp018_885-995_B978044329238500024X.xhtml#f0055)。所有这些驻点在神经网络中都很重要。局部极小值是代价值 `J(θ[l])` 在 `θ[l]` 周围区域内变为最小的点。全局极小值 `θ[g]` 是满足 `J(θ[g]) ≤ J(θ)`，∀`θ` ∈ ℝ 的点。鞍点 `θ[s]` 既不是极小值也不是极大值，但其导数（一般情况下为梯度）等于零。

![Figure 18.10 A nonconvex function, besides the global, usually comprises a number of local minima and saddle points. To which minimum, out of the many, the algorithm will converge, depends on the point from which the algorithm was initialized. However, if the value of the cost at a local minimum, e.g., J(θl), is not much larger than that of the global minimum, i.e., J(θg), then θl can be a satisfactory solution in practice.](images/B978044329238500024X/gr010.jpg)

图 18.10 非凸函数除了全局极小值外，通常还包含若干局部极小值和鞍点。算法将收敛到众多极小值中的哪一个，取决于算法初始化的起始点。然而，如果某局部极小值处的代价值（例如 `J(θ[l])`）并不比全局极小值处的代价值（即 `J(θ[g])`）大很多，那么 `θ[l]` 在实践中可以是一个令人满意的解。

当采用梯度下降方案来最小化非凸代价函数时，算法可能收敛到局部极小值或全局极小值。以 [图 18.10](#Chp018_885-995_B978044329238500024X.xhtml#f0055) 为例。回顾第 [5](#Chp005_177-248_B9780443292385000111.xhtml) 章，梯度下降算法在一维情况下的更新规则变为

```
θ(new) = θ(old) − μ dJ/dθ|θ(old)
```
