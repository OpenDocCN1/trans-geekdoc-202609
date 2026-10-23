
可以证明，随着 $N$ 增大，这个和的分布趋近于

$$
p(S_N = u) = \frac{1}{\sqrt{2\pi N\sigma^2}} \exp\left(-\frac{(u-N\mu)^2}{2N\sigma^2}\right) \tag{D.80}
$$

因此量

$$
Z_N \triangleq \frac{S_N - N\mu}{\sigma\sqrt{N}} = \frac{\overline{X} - \mu}{\sigma/\sqrt{N}} \tag{D.81}
$$

的分布收敛到标准正态分布，其中 $\overline{X} = S_N/N$ 是样本均值。这被称为**中心极限定理**。证明参见例如 [Jay03, 第222页] 或 [Ric95, 第169页]。

在图 D.14 中，我们给出了一个例子：计算从 beta 分布中抽取的随机变量的样本均值。我们可以看到，该均值的抽样分布迅速收敛到高斯分布。

## D.6 习题

### 习题 D.1 [条件独立性]

（来源：Koller。）

a. 设 $H \in \{1, \dots, K\}$ 是一个离散随机变量，令 $e_1$ 和 $e_2$ 为另外两个随机变量 $E_1$ 和 $E_2$ 的观测值。假设我们希望计算向量

$$
\hat{P}(H \mid e_1, e_2) = (P(H=1 \mid e_1, e_2), \dots, P(H=K \mid e_1, e_2))
$$

下面哪组数字足以完成该计算？

- i. $P(e_1, e_2), P(H), P(e_1 \mid H), P(e_2 \mid H)$
- ii. $P(e_1, e_2), P(H), P(e_1, e_2 \mid H)$
- iii. $P(e_1 \mid H), P(e_2 \mid H), P(H)$

b. 现在假设 $E_1 \perp E_2 \mid H$（即，在给定 $H$ 时 $E_1$ 和 $E_2$ 条件独立）。此时上述三组中哪一组是充分的？

请给出最终结果，并展示你的计算过程。提示：使用贝叶斯法则。

### 习题 D.2 [两两独立并不意味着相互独立]

我们说两个随机变量是两两独立的，如果

$$
p(X_2 \mid X_1) = p(X_2) \tag{D.82}
$$

因此

$$
p(X_2, X_1) = p(X_1)p(X_2 \mid X_1) = p(X_1)p(X_2) \tag{D.83}
$$

我们说 $n$ 个随机变量是相互独立的，如果

$$
p(X_i \mid X_S) = p(X_i) \quad \text{ for } S \subseteq \{1, \dots, n\} \setminus \{i\} \tag{D.84}
$$

因此

$$
p(X_{1:n}) = \prod_{i=1}^{n} p(X_i) \tag{D.85}
$$

证明所有变量对之间的两两独立性并不必然意味着相互独立。只需给出一个反例即可。

### 习题 D.3 [条件独立性当且仅当联合分布可因式分解]

在正文中我们说过，$X \perp Y \mid Z$ 当且仅当

$$
p(x, y \mid z) = p(x \mid z)p(y \mid z) \tag{D.86}
$$

对所有满足 $p(z) > 0$ 的 $x, y, z$ 成立。现在证明如下等价定义：$X \perp Y \mid Z$ 当且仅当存在函数 $g$ 和 $h$，使得

$$
p(x, y \mid z) = g(x, z)h(y, z) \tag{D.87}
$$

对所有满足 $p(z) > 0$ 的 $x, y, z$ 成立。

### 习题 D.4 [不相关并不意味着独立]

设 $X \sim U(-1, 1)$，$Y = X^2$。显然 $Y$ 依赖于 $X$（事实上，$Y$ 由 $X$ 唯一确定）。然而，证明 $\rho(X, Y) = 0$。提示：若 $X \sim U(a, b)$，则 $\mathbb{E}[X] = (a + b)/2$，$\mathbb{V}[X] = (b - a)^2/12$。

### 习题 D.5 [相关系数在 -1 和 +1 之间]

证明 $-1 \le \rho(X, Y) \le 1$。

### 习题 D.6 [线性相关变量的相关系数为 ±1]

证明：若 $Y = aX + b$，其中 $a > 0$，$b$ 为某参数，则 $\rho(X, Y) = 1$。类似地，若 $a < 0$，则 $\rho(X, Y) = -1$。

### 习题 D.7 [随机变量的线性组合]

设 $\mathbf{x}$ 是一个均值为 $\mathbf{m}$、协方差矩阵为 $\Sigma$ 的随机向量。设 $\mathbf{A}$ 和 $\mathbf{B}$ 是矩阵。

- a. 推导 $\mathbf{A}\mathbf{x}$ 的协方差矩阵。
- b. 证明 $\mathrm{tr}(\mathbf{A}\mathbf{B}) = \mathrm{tr}(\mathbf{B}\mathbf{A})$。
- c. 推导 $\mathbb{E}\left[\mathbf{X}^{T}\mathbf{A}\mathbf{X}\right]$ 的表达式。

### 习题 D.8 [两个随机变量的最小值的期望]

设 $X, Y$ 是从区间 $[0, 1]$ 中独立且均匀随机抽取的两个点。最左边点的期望位置是多少？

### 习题 D.9 [两个高斯分布的卷积仍是高斯分布]

证明两个高斯分布的卷积是一个高斯分布，即

$$
p(y) = \mathcal{N}(x_1 \mid \mu_1, \sigma_1^2) * \mathcal{N}(x_2 \mid \mu_2, \sigma_2^2) = \mathcal{N}(y \mid \mu_1 + \mu_2, \sigma_1^2 + \sigma_2^2) \tag{D.88}
$$

其中 $y = x_1 + x_2$，$x_1 \sim \mathcal{N}(\mu_1, \sigma_1^2)$，$x_2 \sim \mathcal{N}(\mu_2, \sigma_2^2)$。

### 习题 D.10 [和的方差]

证明和的方差为

$$
\mathbb{V}[X + Y] = \mathbb{V}[X] + \mathbb{V}[Y] + 2\mathrm{Cov}[X, Y], \tag{D.89}
$$

其中 $\mathrm{Cov}[X, Y]$ 是 $X$ 与 $Y$ 之间的协方差。

### 习题 D.11 [推导逆伽马密度]

设 $X \sim \mathrm{Ga}(a, b)$，$Y = 1/X$。推导 $Y$ 的分布。

### 习题 D.12 [Beta 分布的均值、众数、方差]

设 $\theta \sim \mathrm{Beta}(a, b)$。证明其均值、众数和方差由下式给出

$$
\mathbb{E}[\theta] = \frac{a}{a + b} \tag{D.90}
$$

$$
\mathbb{V}[\theta] = \frac{ab}{(a + b)^2 (a + b + 1)} \tag{D.91}
$$

$$
\mathrm{mode}[\theta] = \frac{a - 1}{a + b - 2} \tag{D.92}
$$

## E 频率派统计学

### E.1 引言

我们在第 7 章中描述的统计推断方法被称为贝叶斯统计学。它将模型的参数视为与其他任何未知随机变量一样，并应用概率论的规则从数据中推断这些参数。人们也曾尝试设计一些统计推断方法，这些方法避免将参数视为随机变量，从而避免使用先验和贝叶斯法则。这种替代方法被称为**频率派统计学**、**经典统计学**或**正统统计学**。

其基本思想（在附录 E.3 中正式化）是：通过计算从数据中估计的量（如参数或预测标签）在数据改变时如何变化来表示不确定性。正是这种跨重复试验的变化概念，构成了频率派方法对不确定性进行建模的基础。相比之下，贝叶斯方法将概率视为信息而非重复试验。这使得贝叶斯方法能够计算一次性事件的概率，正如我们在第 D.1.1 节中讨论的那样。也许更重要的是，贝叶斯方法避免了某些困扰频率派方法的悖论（见第 E.8.2 节）。这些病态问题促使著名统计学家 George Box 说道：

> 我相信，要让一个聪明人相信当前[频率派]统计实践是合理的将非常困难，但通过似然和贝叶斯定理的方法则会容易得多。—— George Box, 1962（引自 [Jay76]）。

尽管如此，熟悉频率派统计学仍然很有用，因为它被广泛使用，并且其中一些关键概念即使对贝叶斯主义者也很有用 [Rub84]。

### E.2 Fisher 信息矩阵（FIM）

本节讨论一个重要的量，称为 **Fisher 信息矩阵**，它与对数似然函数的曲率有关。该量有许多应用，其中一些列在表 E.1 中。关于 Fisher 信息及其应用的更详细教程，参见 [Lv+17]。

表 E.1：本书讨论的 Fisher 信息矩阵的一些应用。

| 应用 | 章节 |
| --- | --- |
| MLE 的渐近抽样分布 | 第 E.3.1 节 |
| Cramér-Rao 下界 | 第 E.4.2.1 节 |
| Jeffreys 无信息先验 | 第 7.3.1 节 |
| 自然梯度下降 | 第 5.3.4 节 |

#### E.2.1 定义

得分函数定义为对数似然的梯度：

$$
s(\theta) \triangleq \nabla \log p(x \mid \theta) \tag{E.1}
$$

Fisher 信息矩阵（FIM）定义为得分函数的协方差：

$$
F(\theta) \triangleq \mathbb{E}_{x \sim p(x \mid \theta)} \left[ \nabla \log p(x \mid \theta) \nabla \log p(x \mid \theta)^T \right] \tag{E.2}
$$

因此第 $(i,j)$ 个元素的形式为

$$
F_{ij} = \mathbb{E}_{x \sim p(x \mid \theta)} \left[ \left( \frac{\partial}{\partial \theta_i} \log p(x \mid \theta) \right) \left( \frac{\partial}{\partial \theta_j} \log p(x \mid \theta) \right) \right] \tag{E.3}
$$

我们将在下文对这个量给出解释。

#### E.2.2 FIM 与 NLL 的 Hessian 矩阵之间的联系

到目前为止，我们已经定义了 FIM，但尚未解释为什么它是一个有趣或有用的计算量。在本节中，我们将证明 Fisher 信息矩阵等于负对数似然（NLL）的期望 Hessian 矩阵

$$
\mathrm{NLL}(\theta) = -\log p(D \mid \theta) \tag{E.4}
$$

由于 Hessian 矩阵度量了似然的曲率，我们可以看到 FIM 告诉我们似然函数能在多大程度上确定最佳参数集。（如果似然函数是平坦的，我们就无法推断出任何关于参数的信息；但如果它是单个点上的 delta 函数，则最佳参数向量将被唯一确定。）因此，FIM 与 MLE 的频率派不确定性概念密切相关；这种不确定性体现在，如果我们从模型中抽取多个不同的数据集并分别计算 MLE，我们预期会看到的方差。

更精确地，我们有如下定理：

**定理 E.2.1.**

$$
F(\theta)_{ij} \triangleq \mathbb{E}_{x \sim p(x \mid \theta)} \left[ \left( \frac{\partial}{\partial \theta_i} \log p(x \mid \theta) \right) \left( \frac{\partial}{\partial \theta_j} \log p(x \mid \theta) \right) \right] = - \mathbb{E}_{x \sim p(x \mid \theta)} \left[ \frac{\partial^2}{\partial \theta_i \, \partial \theta_j} \log p(x \mid \theta) \right] \tag{E.5}
$$

在证明这个结果之前，我们先建立以下重要引理。

