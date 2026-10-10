
可以视为惩罚项的负。事实上，取后验分布的负对数并进行最小化而不是极大化，重建回归。

对于更通用的 `$c$` 先验分布，让 `α` 包含控制联合分布 `p(c|D, α, σ²)` 的所有参数。通过对系数 `c` 积分来消除对潜变量的依赖。因此平均

遍历所有可能的解。这被称为对 `c` 进行*边缘化*（marginalizing），其结果为*边缘*似然（marginal likelihood）。

```
$$\mathcal{L}(t\mathbf{D}, \alpha, \sigma^2) = \int p(t,\mathbf{D},\mathbf{c}|\alpha, \sigma^2)dc\mathbf{c}$$
```

这是我们旨在最大化的目标。`α` 的极大似然估计是使 `L(tD, α, σ²)` 最大化的值。在下一节中，我们将重新回顾一种寻找最大值的技巧。

## 8.12 期望最大化

在下文中，我们省略模型对设计矩阵 `D` 的依赖关系。*期望最大化（Expectation-Maximization, EM）*算法通过迭代交替两个步骤来达到最大值。推导过程需要一些展开。

根据*链式法则*（chain rule），也称为*乘积法则*（product rule），我们有：

```
$p(t,\mathbf{c},\sigma^2) = p(t,\mathbf{c}|\alpha, \sigma^2)p(\mathbf{c}|\alpha, \sigma^2)$
```

对两边取对数得到：

```
$log p(t,\mathbf{c},\sigma^2) = \log p(t,\mathbf{c}|\alpha, \sigma^2) + \log p(\mathbf{c}|\alpha, \sigma^2)$
```

两边都可以被视为随机变量 `c` 的函数，我们可以相对于任何分布 `q(c)` 取期望：

```
$$\int q(\mathbf{c}) \log p(t,\mathbf{c},\sigma^2)dc\mathbf{c} = \int q(\mathbf{c}) \log p(t,\mathbf{c}|\alpha, \sigma^2)dc\mathbf{c}$$
$$+ \int q(\mathbf{c}) \log p(t|\mathbf{c},\alpha, \sigma^2)dc\mathbf{c}$$
$$= \int q(\mathbf{c}) \log p(t,\mathbf{c}|\alpha, \sigma^2)dc\mathbf{c}$$
```

由于 `q(c)dc = 1`。重新排列后得到：

```
$$\log p(t,\alpha, \sigma^2) = \mathcal{L}(t\alpha, \sigma^2) = \int q(\mathbf{c}) \log p(t,\mathbf{c}|\alpha, \sigma^2)dc\mathbf{c}$$
$$- \int q(\mathbf{c}) \log p(t,\mathbf{c}|\alpha, \sigma^2)dc\mathbf{c}$$
```

我们可以在右侧减去并加上项 `q(c)log q(c)`，得到：

```
$$\log \mathcal{L}(t\alpha, \sigma^2) = \int q(\mathbf{c}) \log \frac{p(t,\mathbf{c}|\alpha, \sigma^2)}{q(\mathbf{c})}dc\mathbf{c} - \int q(\mathbf{c}) \log \frac{q(\mathbf{c})}{q(\mathbf{c})}dc\mathbf{c} (8.4)$$
```

利用对数的性质。`L(tα, σ²)` 也被称为*对数似然*（log likelihood）或*对数证据*（log evidence）。

第二项（包括负号）是分布 `q(c)` 与后验分布 `p(c|t, α, σ²)` 之间的 Kullback-Leibler 散度（KL 散度）。它也被区分信息、信息散度和信息增益，因为信息是通过观测 `t`获得的。对于两个概率密度函数 `p` 和 `q`，KL 散度定义为：

```
$D_{KL}(p||q) = - \int p(x) \log \frac{q(x)}{p(x)} dx = \mathbb{E}_p [ -log \frac{q(x)}{p(x)} ]$
```

`E_p` 表示相对于分布 `p` 的期望。使用詹森不等式（Jensen's inequality）：

```
$D_{KL}(p||q) \geq - \mathbb{E}_p [ \log \frac{q(x)}{p(x)} ] = - \int p(x) \log \frac{q(x)}{p(x)} dx = - \int q(x) dx = 0$
```

由于 `log 1 = 0`（Bishop (2006) 提供了证明的更多细节）。因此，KL 散度始终为正，且仅当几乎处处满足 `p(c|t, α, σ²) = q(c)` 时为零。

因此，(8.4) 中的第一项：

```
$\int \frac{p(t, c | α, \sigma²)}{q(c)} dc$
```

是 `log L(t|α, σ²)` 的下界。最大化是通过交替进行关于 `q(c)` 和关于 `α` 的最大化来使下界最大化的。

令 `α^k` 为 `α` 的当前估计值。下界在相对于 `q(c)` 的意义上是最大值，当且仅当 `q(c) = p(c|t, α^k, σ²)` 时。下一步是通过最大化以下公式找到 `α^{k+1}`：

```
$\int \frac{p(t, c | α, \sigma²)}{p(c|t, α^k, σ²)} \log \frac{p(t, c | α^k, σ²)}{p(c|t, α^k, σ²)} dc = - \int p(t, c | α^k, σ²)$
```

第二项独立于 `α`。因此，对于最大化只有第一项是相关的。注意：第一项是相对于后验分布当前估计值的对数期望。这就是期望最大化算法的名字。

## 8.13 贝斯学习

作为一个特定例子，`c` 的先验分布为均值为零、方差为 `α^{-1}` 的正态分布。我们的起点是权重之间没有协方差。也就是说，权重互不影响。多元先验分布给出：

```
$p(\mathbf{c}|\alpha) = (2\pi)^{-M/2}\prod_{m=1}^M \alpha_m^{1/2}\exp\left(-\frac{\alpha_m c_m^2}{2}\right) = (2\pi)^{-M/2}|\mathbf{A}|^{1/2}\exp\left(-\frac{1}{2}\mathbf{c}^T\mathbf{Ac}\right)$
```

其中 `A` 是一个元素为 `A_{mm}=α_m` 的对角矩阵，`|A|` 表示行列式。多元后验分布 `p(t,D,α,σ²)` 由贝叶法则给出，并与先验和似然函数的积正比：

```
$p(t,\mathbf{D},\alpha,\sigma^2) = \frac{p(\alpha)\mathcal{L}(t|\mathbf{D},\sigma^2)}{\int p(\alpha)\mathcal{L}(t|\mathbf{D},\sigma^2)d\mathbf{c}}$ (8.5)
```

现在：

```
$p(\alpha)\mathcal{L}(t|\mathbf{D},\sigma^2) = (2\pi)^{-M/2}|\mathbf{A}|^{1/2}\exp\left(-\frac{1}{2}\mathbf{c}^T\mathbf{Ac}\right) = (2\pi)^{-N/2}\exp\left(-\frac{1}{2\sigma^2}(\mathbf{t}-\mathbf{Dc})^T(\mathbf{t}-\mathbf{Dc})\right)$
```

乘数项在分数中抵消，集中在指数项中：

```
$-\frac{1}{2}[\mathbf{c}^T(\mathbf{A}+\sigma^{-2}\mathbf{D}^T\mathbf{D})\mathbf{c}-\sigma^{-2}\mathbf{c}^T\mathbf{D}^T\mathbf{t}+\sigma^{-2}\mathbf{t}^T]$
```

考虑到平方项，我们看到后验分布的协方差矩阵必须是：

```
$\mathbf{\Sigma} = (\mathbf{A}+\sigma^{-2}\mathbf{D}^T\mathbf{D})$, (8.6)
```

它是对称且正定的。通过引入均值 `μ` 来配方：

```
$-\frac{1}{2}[(\mathbf{c}-\mu)^T\mathbf{\Sigma}^{-1}(\mathbf{c}-\mu)+2\mathbf{c}^T\mathbf{\Sigma}^{-1}\mu-\sigma^{-2}\mathbf{c}^T\mathbf{D}^T\mathbf{t}+\sigma^{-2}\mathbf{t}^T]$
```

`c^T` 中的线性项需要抵消，这意味着我们需要 `Σ^{-1}μ=σ^{-2}D^T t`。因此，后验分布的均值为：

```
$\mu=\sigma^{-2}\mathbf{D}^T\mathbf{t}.$ (8.7)
```

指数中剩余的所有项相对于 `c` 都是常数。由于指数的存在，它们是乘因子并在分数中抵消。剩下的是计算分母，抵消后为：

```
$$\exp\left(-\frac{1}{2}(\mathbf{c}-\mu)^T\mathbf{\Sigma}^{-1}(\mathbf{c}-\mu)\right) dc$$
```

然而，已知：

```
$(2\pi)^{-M/2}\exp\left(-\frac{1}{2}(\mathbf{c}-\mu)^T\mathbf{\Sigma}^{-1}(\mathbf{c}-\mu)\right) dc$$
```

等于 1，因为它是正态概率函数的积分。那么分母的积分就是 `(2π)^{M/2}Σ^{1/2}`。

总结来说，后验分布是正态的，其为：

```
$$\mu(\mathbf{t}, \mathbf{D}, \alpha, \sigma^2) \sim \mathcal{N}(\mu, \Sigma)$$
```

其中 `μ` 和 `Σ` 由 (8.7) 和 (8.6) 给出。回回普通最小二法计算系数为：

```
$$\mathbf{c} = (\mathbf{D}^T\mathbf{D})^{-1}\mathbf{D}^T\mathbf{t},$$
```

而回归确定的系数为：

```
$$\mathbf{c} = (\mathbf{I} + \mathbf{D}^T\mathbf{D})^{-1}\mathbf{D}^T$$
```

其中 `λ` 是一个需要适当选择的参数。将 (8.6) 插入 (8.7) ：

```
$$\mu =(\mathbf{A}+\sigma^{-2}\mathbf{D}^T\mathbf{D})^{-1}\sigma^{-2}\mathbf{D}^T\mathbf{t}$$
```

加上 `σ² A` 是为了防止 `D` 可能奇异。贝斯方法的主要区别特征是：首先，学习特定的系数向量，给 `c` 出一个多元后验分布，从中可以推导出 `c`。让 `c = μ` 也是常见的。其次，超参数 `α₁, …, α_M` 通过最大化边缘似然来优化，如下文所示。

一旦找到系数的后验分布，对于数据 `x_n` 的测量值 `t_n` 就可以进行概率解释。当我们想起 `t_n` 是由一个过程产生时：

```
$t_n =(\mathbf{x}_n)^T\mathbf{c} + \epsilon_n,$
```

其中 `(x_n)^T` 是 `D` 的第 `n` 行，即在 `x_n` 处的所有基函数。现在，`(x_n)^T c` 是正态变量 `c` 的线性变换，因此也是正态分布。另一个 `ε_n` 是均值为零、方差为 `σ²` 的正态噪声。因此，`t_n` 是两个正态变量的和。`t_n` 的概率解释是它抽自一个单变量正态分布：

```
$$\text{mean} \quad =(\mathbf{x}_n)^T\mathbf{\mu}$\n$\text{variance} \quad \sigma_n^2 =\sigma^2 +(\mathbf{x}_n)^T\Sigma\mathbf{d}(\mathbf{x}_n).$$
```

如果方差较小，说明模型在该点对数据的解释良好。如果方差很大，则说明模型在该点是不够的。这可能表明基函数字典不适用于这些数据，需要进行修正。

超参数的最优值通过最大化边际似然 `L(α, σ²)` 来找到，这正是式 (8.5) 的分母。保留乘法常数（在之前的分析中已消去），边际似然为：

```
$$\mathcal{L}(\boldsymbol{\alpha}, \sigma^2) = |A|^{1/2}(2\pi)^{-N/2}|\Sigma|^{1/2}\exp\left(-\frac{1}{2}\sigma^{-4}t^T t+\frac{1}{2}\boldsymbol{\mu}^T\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}\right)$$
```

我们首先考虑指数中的项。代入 (8.7)，它变为：

```
$$-[\sigma^{-2}t^T t-\boldsymbol{\mu}^T\boldsymbol{\Sigma}^{-1}\boldsymbol{\mu}] = -\frac{1}{2}[\sigma^{-6}t^T t-\sigma^{-4}t^T\boldsymbol{D}^T\boldsymbol{\Sigma}^{-1}\boldsymbol{D}t] = -\frac{1}{2}[\sigma^{-4}(\sigma^2)^{-1}-\sigma^{-2}(\boldsymbol{D}^T\boldsymbol{\Sigma}^{-1}\boldsymbol{D})^{-1}]t$$
```

其中 `I` 是 `N × N` 单位矩阵。通过将 `Σ` 写为 `(A+D^T σ² I^{-1} D)^{-1}` 并使用 A.1.3 中的 *Woodbury恒等式*，可以简化为：

```
$-\frac{1}{2}t^T(\sigma^2I+\boldsymbol{D}^T\boldsymbol{D})^{-1}t.$
```

因此，边际似然的均值为零，其协方差矩阵为：

```
$$\boldsymbol{C} = \sigma^2I+\boldsymbol{D}^T\boldsymbol{D}.$$
```

我们需要检查乘法常数是否与此一致。为此，

```
$|\boldsymbol{\Sigma}| = |\boldsymbol{\Sigma}^{-1}|^{-1}=|A+\boldsymbol{D}^T(\sigma^2I)^{-1}\boldsymbol{D}|^{-1}.$
```

使用 A.1.5 中的 *矩阵行列式引引*，我们得到：

```
$|\boldsymbol{\Sigma}|=|\sigma^2I+\boldsymbol{D}^T\boldsymbol{D})^{-1}|\sigma^{-2}|\boldsymbol{C}|=|\boldsymbol{C}|^{-1}|(\sigma^2)^N.$
```

将此结果与其他乘法常数结合，我们看到：

```
$$\mathcal{L}(\boldsymbol{\alpha}, \sigma^2) = (2\pi)^{-N/2}|\boldsymbol{C}|^{-1/2}\exp\left(-\frac{1}{2}t^T\boldsymbol{C}^{-1}t\right).$$
```

我们不是最大化这个值，而是最大化边际似然的对数，后后称为*对数证据*（log evidence）。我们将这个*目标函数*标记为：

```
$$\mathcal{L}(\boldsymbol{\alpha}) =-\frac{1}{2}(N\log 2\pi + \log |\boldsymbol{C}| + t^T\boldsymbol{C}^{-1}t). \quad (8.8)$$
```

我们想要关于超参数 `α` 最大化该函数。为此，我们分离出单个超参数的贡献。首先注意，由于 `A` 是对角矩阵，`C` 可以重写为：

```
$C = \sigma^2 I + \sum_{m=1}^{M} \frac{1}{\alpha_m} d_m d_m^T$
```

令：

```
$C_{-i} = \sigma^2 I + \sum_{m \neq i}^{M} \frac{1}{\alpha_m} d_m d_m^T = C - \frac{1}{\alpha_i} d_i d_i^T$
```

且 `α_{-i} = (α₁,…,α_{i-1},α_{i+1},…,α_M)^T`。使用 A.1.4 中的 Sherman-Morrison 公式，我们得到：
