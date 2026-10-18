

上述描述的梯度下降法在样本量 `n` 较大时不推荐使用，因为这会导致每次迭代中求和项 `σ∑(i∈I(n)(t)) y_i x_i` 的计算开销很高。作为一种流行的替代方法，可以使用 `stochastic gradient descent` (SGD) 方法；有关简要介绍，另见附录 `11.A.1`。在 SGD 中，每次迭代时仅考虑一个单独的数据点来更新参数；并且我们重复该过程，旨在获得 `ω` 的最终估计。如果数据恰好是真正的线性可分的，即存在 `ω* ∈ R^(p+1)` 使得对所有 `i` 都有 `sgn((ω*)^T x_i) = y_i`，那么通过随机梯度下降法可以保证 `ω` 收敛到最优权重。为此，通过比较每次更新前后的参数 `ω^(t)` 和 `ω^(t+1)`，SGD 在 `(t+1)` 步处的损失函数实际上是减小的。在每个步骤中，有两种情况需要考虑：

![FIGURE 11.4 An update of the estimate for ω under gradient descent method at the (t+1)‐th iteration.](images/c11f004.png)

[**FIGURE 11.4**](#c11.xhtml#R_c11-fig-0004) An update of the estimate for `ω` under gradient descent method at the `(t+1)`‐th iteration.

1. **(1)** 如果选定的 `(x_i^(t+1), y_i^(t+1))` 已经被正确分类，则 `ω^(t+1) = ω^(t)`；否则，

