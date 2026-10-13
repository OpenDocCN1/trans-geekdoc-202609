
观察到 $w_n^{(i)}$ 既不依赖于 $a$ 也不依赖于 $\phi(\mathbf{x}_n; \boldsymbol{\theta})$；因此它可以被视为与样本 $n$ 相关联的权重。此外，其值完全取决于前几次递归获得的结果。

![Figure 7.14 The 0-1, exponential, log-loss, and squared error loss functions. They have all been normalized to cross the point (0,1). The horizontal axis for the squared error corresponds to y − F(x).](images/B9780443292385000135/gr014.jpg)

**Figure 7.14** 0-1、指数、对数损失和平方误差损失函数。它们都已被归一化以通过点 (0,1)。平方误差的横轴对应于 $y - F(\mathbf{x})$。

我们现在将重点转移到公式 [(7.89)](#Chp007_293-342_B9780443292385000135.xhtml#deq137) 中的代价上。优化取决于基分类器的具体形式。然而请注意，损失函数呈指数形式。此外，基分类器是二元的，因此 $\phi(\mathbf{x}; \boldsymbol{\theta}) \in \{-1, 1\}$。如果我们假设 $a > 0$（稍后我们将回到这一点），则公式 [(7.89)](#Chp007_293-342_B9780443292385000135.xhtml#deq137) 的优化很容易被看出等价于

$$
\boldsymbol{\theta}_i = \arg\min_{\boldsymbol{\theta}} P_i,
\tag{7.91}
$$

其中

$$
P_i := \sum_{n=1}^N w_n^{(i)} \chi_{(-\infty,0]}\left( y_n \phi(\mathbf{x}_n; \boldsymbol{\theta}) \right),
\tag{7.92}
$$

而 $\chi_{(-\infty,0]}(\cdot)$ 是 0-1 损失函数。^([^(48)](#fn48))

计算出最优 $\boldsymbol{\theta}_i$ 后，根据各自的定义可以容易地建立以下关系：

$$
\sum_{y_n \phi(\mathbf{x}_n; \boldsymbol{\theta}_i) \leq 0} w_n^{(i)} = P_i
\tag{7.93}
$$

以及

$$
\sum_{y_n \phi(\mathbf{x}_n; \boldsymbol{\theta}_i) > 0} w_n^{(i)} = 1 - P_i.
$$
