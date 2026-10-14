
- Metropolis-Hastings (MH) 算法的基本思想是从当前状态 $x$ 基于提议分布 $q(x'|x)$ 提议移动到新状态 $x'$，然后根据确保满足细致平衡的 MH 比率接受或拒绝所提议的状态。
- 重要性采样的思想是在有趣的区域抽取样本（即 $p(x)$ 和 $|f(x)|$ 都较大的地方）。重要性采样通过从更易于采样的提议分布 $q(x)$ 中抽取样本来实现。

## 变分推断

**本章涵盖**

- 介绍 KL 变分推断
- 均值场近似
- Ising 模型中的图像去噪
- 互信息最大化

在上一章中，我们介绍了贝叶斯推断的两个主要流派之一：马尔可夫链蒙特卡洛。我们研究了不同的采样算法并使用样本近似后验分布。在本章中，我们将讨论贝叶斯推断的第二个流派：变分推断。*变分推断*（VI）是一类重要的近似推断算法；其基本思想是从具有可训练参数的可处理或易于计算的分布族中选择一个近似分布 $q(x)$，然后使该近似尽可能接近真实后验分布 $p(x)$。

正如我们在均值场部分将看到的那样，近似 $q(x)$ 可以采用联合后验分布的完全因子化表示。这种因子化显著加快了计算速度。我们将介绍 KL 散度并将其用作衡量近似分布与真实后验接近程度的一种方法。通过优化 KL 散度，我们将有效地把 VI 转化为一个优化问题。在下一节中，我们将推导证据下界（ELBO）

并以三种不同的方式对其进行解释，这将在我们实现用于图像去噪的均值场近似时变得非常有用。图像去噪算法被选中是因为它通过视觉示例说明了本节讨论的概念。

### 3.1 KL 变分推断

我们可以使用 KL 散度来衡量概率分布之间的距离。当对目标分布进行近似时，这特别有用，因为我们想要了解近似的接近程度。设 $q(x)$ 为我们的近似分布，$p(x)$ 为目标后验分布。那么，反向 KL 定义如下。

$$KL(q\|p)=\sum_x q(x)\log\frac{q(x)}{p(x)}$$

*近似分布*

*近似与实际的对数比*  
(3.1)

考虑一个简单的例子，其中我们的目标分布是标准一元正态分布 $p(x)\sim N(0,1)$，而我们的近似分布是均值为 $\mu$、方差为 $\sigma^2$ 的一元正态分布：$q(x)\sim N(\mu,\sigma^2)$。我们然后可以按如下方式计算 $KL(q\|p)$。

$$\begin{aligned}
KL(q\|p) &= \int q(x)\log\frac{q(x)}{p(x)}\\
&= -\int q(x)\log p(x)+\int q(x)\log q(x)\\
&= -\int q(x)\left[-\frac{1}{2}\log 2\pi-\frac{1}{2}x^2\right]\\
&\quad +\int q(x)\left[-\frac{1}{2}\log 2\pi\sigma^2-\frac{1}{2\sigma^2}(x-\mu)^2\right]\\
&= \left[\frac{1}{2}\log 2\pi+\frac{1}{2}(\sigma^2+\mu^2)\right]+\left[-\frac{1}{2}\log 2\pi\sigma^2-\frac{1}{2}\right]\\
&= -\frac{1}{2}\left(1+\log\sigma^2-\mu^2-\sigma^2\right)
\end{aligned}$$

(3.2)

我们可以可视化 $KL(q\|p)$ 随着近似分布 $q(x)$ 参数变化而变化的情况。设 $\sigma^2=4$ 固定，并使均值 $\mu\in[-4,4]$ 变化。我们得到图 3.1。

请注意，KL 散度是非负的，并且当 $\mu=0$ 时最小（即近似分布的均值等于目标分布 $p(x)\sim N(0,1)$ 的均值）。我们可以将 KL 散度解释为分布之间的距离度量。

称为 *矩投影* 或 *M-投影* 是零规避的 $q(x)$，并且会高估 $p(x)$ 的支撑，如图 3.2 所示。

![](img/325742126d3ff007c6c385f4ffb5c3be_66_0.png)

图 3.2 显示了具有 4 个分量的 2D 高斯混合 $p(x)$ 的样本以及近似分布 $q(x)$ 的密度椭圆。我们可以看到，优化前向 KL 会导致 $q(x)$ 位于零点（低密度区域），因为我们高估了 $q(x)$ 的支撑。另一方面，优化反向 KL 会导致 $q(x)$ 位于高斯混合的四个模态之一。

我们可以使用 Jensen 不等式推导出 ELBO，这是一个我们可以最大化以学习模型变分参数的目标。设 $x$ 为我们的数据，$z$ 为潜在变量，然后我们可以按如下方式推导我们的 ELBO 目标。

$$\log p(x) = \log \sum_z p(x,z) = \log \sum_z \frac{q(z)}{q(z)} p(x,z)$$ $$= \log E_{q(z)}\left[ \frac{p(x,z)}{q(z)} \right] \ge E_{q(z)}\left[ \log \frac{p(x,z)}{q(z)} \right]$$ $$= \underbrace{E_{q(z)}[\log p(x,z)]}_{\text{Energy term}} - \underbrace{E_{q(z)}[\log q(z)]}_{\text{Entropy term}} = \text{ELBO} \quad (3.6)$$

请注意，第一项是平均负能量，第二项是熵：因此，一个好的后验必须将其大部分概率质量分配给低能量区域（即联合概率密度高的区域），同时最大化 $q(z)$ 的熵。因此，与 MAP 估计器相比，变分推断防止 $q(z)$ 坍缩成一个原子。

ELBO 的一种形式强调，随着变分分布更好地近似后验，下界变得更紧。

$$\text{ELBO} = E_{q(z)}\left[ \log \frac{p(x,z)}{q(z)} \right] = E_{q(z)}\left[ \log \frac{p(z|x)p(x)}{q(z)} \right]$$ $$= \underbrace{-KL(q(z)||p(z|x))}_{\text{Distance between the approximating q(z) and the posterior p(z|x)}} + \log p(x) \quad (3.7)$$

因此，我们可以通过先验 $p(z)$ 或似然 $p(z|x)$ 改善模型对数证据 log p(x)，或通过改善变分后验近似 $q(z)$ 来改善 ELBO。

最后，我们可以按如下方式写出 ELBO。

ELBO = 1/n Σ_{i=1}^n [ E_{q(z)}[ log p(x_i|z_i) ] - KL(q(z_i)||p(z_i)) ]  (3.8)
样本似然
近似 q(z) 与样本 i 的先验 p(z) 之间的距离

这种版本强调了第 i 个观测值的似然项以及每个近似分布与先验之间的 KL 散度项。在所有前述情况下，关于 $q(z)$ 的期望可以通过从近似分布中采样来计算。让我们在下一节中查看最常见的变分近似之一。

### 3.2 均值场近似

变分推断最受欢迎的形式之一是均值场近似，其中我们假设后验是形式为完全因子化近似。

q(x) = ∏_i q_i(x_i)  (3.9)

这里，我们对每个边缘分布 $q_i(x_i)$ 的参数进行优化。我们可以像图 3.3 那样可视化完全因子化分布。

![](img/325742126d3ff007c6c385f4ffb5c3be_67_0.png)

图 3.3 真实后验（左）、结构化近似（中）和完全因子化近似（右）

对于具有三个随机变量 $x1$、$x2$ 和 $x3$ 的分布，我们有我们试图用完全因子化分布 $q(x1) q(x2) q(x3)$ 近似的真实后验 $p(x1, x2, x3)$。

我们的目标是最小化变分自由能 $J(q)$，或等价地最大化下界。

$$L(q) = -J(q) = \sum_{x} q(x) \log \frac{\tilde p(x)}{q(x)}\tag{3.10}$$

我们可以重写每个边缘分布 $q_j$ 的目标，保持其余项为常数，如 Kevin Murphy (2012) 所著《Probabilistic Machine Learning》第 21.3 节所示。

$$L(q_j) = \sum_{x} \prod_i q_i(x_i) \left[\log \tilde p(x) - \sum_k \log q_k(x_k)\right]$$ Mean-field approx

$$= \sum_{x_j}\sum_{x_{-j}} q_j(x_j)\prod_{i\neq j} q_i(x_i)\left[\log \tilde p(x) - \sum_k \log q_k(x_k)\right]$$ Factors out $q_j$

$$= \sum_{x_j} q_j(x_j)\log f_j(x_j) - \sum_{x_j} q_j(x_j)\sum_{x_{-j}}\prod_{i\neq j} q_i(x_i)\left[\sum_{k\neq j}\log q_k(x_k)+\log q_j(x_j)\right]$$

$$= \sum_{x_j} q_j(x_j)\log f_j(x_j) - \sum_{x_j} q_j(x_j)\log q_j(x_j) + \text{const}$$ Treats non-$q_j$ terms as constant $\tag{3.11}$

这里，我们定义了以下内容。

$$\log f_j(x_j) = \sum_{x_{-j}} \prod_{i\neq j} q_i(x_i) \log \tilde p(x) = E_{-q_j}[\log \tilde p(x)]\tag{3.12}$$

由于我们用平均值替换值，该方法被称为 *均值场*。我们可以重写 $L(q_j) = -KL(q_j \| f_j)$，因此通过设置 $q_j = f_j$ 或等价地方程 3.13 来最大化目标。

$$\log q_j(x_j) = \log f_j(x_j) = E_{-q_j}[\log \tilde p(x)]\tag{3.13}$$

这里，$q_j$ 的函数形式将由变量 $x_j$ 的类型及其概率模型决定。我们将在下一节中使用此结果从头推导图像去噪算法。
