

为了保持简单，让我们假设平均奖励的采样分布是高斯分布（对于每个 `a`），因此我们为每个臂 `a` 维护 `μ[a]` 和 `σ[a]` 的估计值，以表示 `a` 的平均奖励采样分布的均值和标准差。`μ[a]` 将计算为迄今为止臂 `a` 所见样本奖励的平均值。`σ[a]` 将计算为平均奖励估计的标准误，即迄今所见奖励的样本标准差除以样本数量的平方根（对于给定的臂 `a`）。假设在玩了几次臂之后，我们得到了 3 个臂的平均奖励高斯采样分布，如 [图 15.2](#chapter15.xhtml#fig15_2) 所示。让我们将这三个臂称为红色、蓝色和绿色。[图 15.2](#chapter15.xhtml#fig15_2) 中的正态分布显示红色臂为实线曲线，蓝色臂为虚线曲线，绿色臂为点划线曲线。蓝色臂具有最高的 `σ[a]`。这可能是因为样本标准差较高，也可能是因为我们只玩了几次蓝色臂（请记住，样本数量的平方根出现在标准误计算的分母中）。现在看这个图，我们必须决定接下来选择哪个臂。`Optimism in the Face of Uncertainty` 背后的直觉是，对于臂 `a`，我们对 `Q(a)` 越不确定，就越重要去玩那个臂。这是因为对 `Q(a)` 的更多不确定性使其更有可能成为最佳臂（在其他条件相同的情况下）。粗略的启发式方法是选择所有臂中 `μ[a] + c ⋅ σ[a]` 值最高的臂（对于某个固定的 `c ∈ ℝ^+`）。因此，我们正在比较（跨动作）比平均奖励估计高出 `c` 个标准误的值（即平均奖励适当置信区间的上端）。在这个图中，假设 `μ[a] + c ⋅ σ[a]` 对蓝色臂最高。所以我们玩蓝色臂，假设我们为蓝色臂获得了一个相当低的奖励。这可能对蓝色臂的采样分布产生两种影响——它可以降低蓝色的 `μ[a]`，也可以降低蓝色的 `σ[a]`（仅仅因为蓝色臂样本数量的增长这一事实）。有了蓝色臂的新 `μ[a]` 和 `σ[a]`，假设更新后的采样分布如 [图 15.3](#chapter15.xhtml#fig15_3) 所示。随着蓝色臂平均奖励采样分布变窄，假设红色臂现在具有最高的 `μ[a] + c ⋅ σ[a]`，因此我们玩红色臂。这个过程会持续进行，直到采样分布足够窄，使我们对动作的平均奖励有足够的信心（即，获得 `Q(a)` 的可靠估计），以便我们能够锁定具有最高 `Q(a)` 的动作。

![Figure 15.2 Q-Value Distributions](images/fig15_2.jpg)

[Figure 15.2](#chapter15.xhtml#b15fig15_2) Q-Value Distributions

![Figure 15.3 Q-Value Distributions](images/fig15_3.jpg)

[Figure 15.3](#chapter15.xhtml#b15fig15_3) Q-Value Distributions

值得强调的是，`Optimism in the Face of Uncertainty` 是解决探索-利用困境的绝佳方法，因为无论由于乐观主义而产生的探索是否产生大奖励，你都会获益。如果它确实产生了大奖励，你会立即通过收集大奖励而获益。如果它没有产生大奖励，你仍然会通过获取某些动作（你已探索过的）可能不是最佳动作的知识而获益，这有助于你从长远来看，将注意力集中在其他动作上。

对 `Optimism in the Face of Uncertainty` 上述直觉的形式化是 `Upper Confidence Bounds`（缩写为 UCB）的概念。UCB 的思想是，除了估计 `Q̂[t](a)`（在 `t` 个时间步之后，对于每个 `a`）之外，我们还维护一个估计 `Û[t](a)`，它代表 `a` 的平均奖励的置信区间宽度上限（在 `t` 个时间步之后），使得 `Q(a) < Q̂[t](a) + Û[t](a)` 以高概率成立。这自然取决于 `a` 被选择的次数（称其为 `N[t](a)`）。`N[t](a)` 的小值意味着 `Û[t](a)` 的大值，因为平均奖励的估计相当不确定。另一方面，`N[t](a)` 的大值意味着 `Û[t](a)` 的小值，因为平均奖励的估计相当确定。我们将 `Q̂[t](a) + Û[t](a)` 称为 `Upper Confidence Bound`（或简称 UCB）。其思想是选择最大化 UCB 的动作。形式上，为下一个（`t + 1`）个时间步选择的动作 `A[t + 1]` 如下：

$$
\begin{array}{r}
{A_{t + 1} = \text{arg}\,\text{max}_{a \in \mathcal{A}}\left\{ {\hat{Q}}_{t}(a) + {\hat{U}}_{t}(a) \right\}} \\
\end{array}
$$

接下来，我们开发著名的 UCB1 算法。为此，我们借鉴了统计学中一个重要的结果，即 Hoeffding's Inequality。

### 15.4.1 Hoeffding's Inequality

我们不加证明地陈述 Hoeffding's Inequality。

我们可以将 Hoeffding's Inequality 应用于奖励具有 `[0,1]` 支撑概率分布的 MAB 问题实例。在时间步 `t` 选择动作 `a` 的条件下，样本均值 `X̄_n` 特化为 `Q̂[t](a)`，我们设置 `n = N[t](a)` 和 `u = Û[t](a)`。因此，

$$
\begin{array}{r}
{\mathbb{P}\lbrack Q(a) > {\hat{Q}}_{t}(a) + {\hat{U}}_{t}(a)\rbrack \leq e^{- 2N_{t}(a) \cdot {\hat{U}}_{t}{(a)}^{2}}} \\
\end{array}
$$

接下来，我们为 `Q(a)` 超过 UCB `Q̂[t](a) + Û[t](a)` 选取一个小概率 `p`。现在求解 `Û[t](a)`，如下：

$$
\begin{array}{r}
\left. e^{- 2N_{t}(a) \cdot {\hat{U}}_{t}{(a)}^{2}} = p\Rightarrow{\hat{U}}_{t}(a) = \sqrt{\frac{- \log p}{2N_{t}(a)}} \right. \\
\end{array}
$$

随着我们观察到更多奖励，我们减小 `p`，例如，`p = t^(−α)`（对于某个固定的 `α > 0`）。这确保了当 `t→∞` 时我们选择最优动作。因此，

$$
\begin{array}{r}
{{\hat{U}}_{t}(a) = \sqrt{\frac{\alpha\log t}{2N_{t}(a)}}} \\
\end{array}
$$

### 15.4.2 UCB1 Algorithm

这得出了由 Auer, Cesa-Bianchi, Fischer ([Auer, Cesa-Bianchi, and Fischer 2002](#bib01.xhtml#refbib_4)) 提出的 UCB1 算法，适用于任意分布且界限在 `[0, 1]` 内的臂：

$$
\begin{array}{r}
{A_{t + 1} = \text{arg}\,\text{max}_{a \in \mathcal{A}}\left\{ {\hat{Q}}_{t}(a) + \sqrt{\frac{\alpha\log t}{2N_{t}(a)}} \right\}} \\
\end{array}
$$

已证明 UCB1 算法在渐近意义上实现了对数总遗憾。具体来说，

现在让我们在代码中实现 UCB1 算法。下面的类 `UCB1` 实现了抽象基类 `MABBase` 的接口。我们为 `[0, B]` 范围的奖励实现了以下代码（将上述 UCB1 公式从 `[0, 1]` 范围适当调整到 `[0, B]` 范围）。`B` 作为构造函数输入 `bounds_range` 指定。构造函数输入 `alpha` 对应上述指定的参数 `α`。`get_episode_rewards_actions` 实现了 `MABBase` 的 `@abstractmethod` 接口，其下面的代码应该不言自明。

![](images/comp15_4.jpg)

上述代码位于文件 `rl/chapter14/ucb1.py` 中。`__main__` 中的代码设置了一个具有 6 个臂的 `UCB1` 实例，每个臂都具有二项分布，`n = 10` 和 `p = {0.4,0.8,0.1,0.5,0.9,0.2}` 分别对应 6 个臂。当运行 1000 个时间步、500 个回合和 `α = 4` 时，我们得到如 [图 15.4](#chapter15.xhtml#fig15_4) 所示的总遗憾曲线。

![Figure 15.4 UCB1 Total Regret Curve](images/fig15_4.jpg)

[Figure 15.4](#chapter15.xhtml#b15fig15_4) UCB1 Total Regret Curve

