

`avg_exec_price_diff` 指的是时间序列函数 `g[t]`，该函数返回市价单在时间 t 因吃掉买方限价单（Buy LOs）而导致的平均价格降低量。`g[t]` 的输入类型为 `PriceAndShares`，表示价格（float 类型）与股数（int 类型）的一对（在此情况下，价格为 `P[t]`，股数为时间 t 的市价单规模 `N[t]`）。如前所述，时间 t 的销售所得为：`N[t] ⋅ (P[t] − g[t](P[t], N[t]))`。

`price_dynamics` 指的是时间序列函数 `f[t]`，表示价格动态：`P[t + 1] ∼ f[t](P[t], N[t])`。`f[t]` 输出 `P[t + 1]` 的价格概率分布。

`utility_func` 指的是销售所得效用函数，包含任何风险厌恶因素。

`discount_factor` 指的是折扣因子 `γ`。

`func_approx` 指的是用于对每个时间步的值函数进行近似的 `ValueFunctionApprox` 类型（因为我们正在进行逆向归纳）。

`initial_price_distribution` 指的是时间 0 时价格 `P[0]` 的概率分布，用于生成每个时间步的状态样本（近似逆向归纳算法所需）。

![](images/comp10_11.jpg)

执行逆向归纳需要的两个关键要素是：

*   一个方法 `get_mdp`，给定时间步 `t`，生成表示从时间 `t` 到时间 `t + 1` 转移的 `MarkovDecisionProcess` 对象。`get_mdp` 中的类 `OptimalExecutionMDP` 实现了抽象类 `MarkovDecisionProcess` 的抽象方法 `step` 和 `actions`。代码应当相当自解释——这里只需指出几点。首先，传入 `step` 方法的输入 `p_r: NonTerminal[PriceAndShares]` 表示时间 `t` 的状态 `(P[t], R[t])`，而变量 `p_s: PriceAndShares` 表示 `(P[t], N[t])` 这一对，作为 `avg_exec_price_diff` 和 `price_dynamics`（`OptimalOrderExecution` 的属性）的输入。其次，请注意，`actions` 方法在时间 `t = T − 1` 时返回一个单个 int 的迭代器，这是由于约束 `N[T − 1] = R[T − 1]` 所致。

*   一个方法 `get_states_distribution`，返回时间 `t` 时状态 `(P[t], R[t])` 的概率分布（类型为 `SampledDistribution[NonTerminal[PriceAndShares]]`）。此处的代码与 [第 8 章](#chapter8.xhtml) 中 `AssetAllocDiscrete` 的 `get_states_distribution` 方法类似（基本上，从时间 0 向前遍历到时间 `t`，通过从状态转移概率分布中采样，并在每个时间步对所有动作进行均匀采样）。

![](images/comp10_12.jpg)

最后，我们使用以下方法 `backward_induction_vf_and_pi` 为每个时间步生成最优值函数和最优策略：

![](images/comp10_13.jpg)

上述代码位于文件 `rl/chapter9/optimal_order_execution.py` 中。我们鼓励你通过变化 `OptimalOrderExecution` 的输入来创建几个不同的实例（尝试不同的临时和永久价格冲击函数、不同的效用函数、施加一些约束等）。请注意，上述代码是出于教育目的而非高效计算目的编写的，因此逆向归纳 ADP 算法的收敛速度将会很慢。我们如何知道上述代码是正确的？嗯，我们需要创建一个简单的特例，产生一个闭式解，以便我们可以将 `OptimalOrderExecution` 生成的最优值函数和最优策略与之进行比较。这将是下一小节的主题。

### 10.2.1 无风险厌恶的简单线性价格冲击模型

现在我们考虑上述 MDP 的一个特例——一个简单的线性价格冲击模型，无风险厌恶。此外，为了分析上的可处理性，我们假设 `N`、`N[t]`、`P[t]` 均为无约束的连续值（即，取值 ∈ ℝ）。

我们假设简单的线性价格动态如下：

$$
\begin{array}{r} {P_{t + 1} = f_{t}(P_{t},N_{t},\epsilon) = P_{t} - \alpha \cdot N_{t} + \epsilon_{t}} \\\\ \end{array}
$$

其中 `α` ∈ ℝ，且对所有 `t` = 0, 1, …, `T − 1` 的 `ϵ[t]` 都是独立同分布（i.i.d.）的，且 𝔼[`ϵ[t]`|`N[t]`, `P[t]`] = 0。因此，永久价格冲击（作为期望）为 `α ⋅ N[t]`。

至于临时价格冲击，我们知道 `g[t]` 需要是 `N[t]` 的非递减函数。我们对 `g[t]` 假设一个简单的线性形式如下：

$$
\begin{array}{r} {g_{t}(P_{t},N_{t}) = \beta \cdot N_{t}\text{~for~all~}t = 0,1,\ldots,T - 1} \\\\ \end{array}
$$

其中 `β` ∈ ℝ[ ≥ 0] 为某个常数。因此，`Q[t]` = `P[t]` − `β⋅N[t]`。如上所述，我们假设无风险厌恶，即效用函数 `U(⋅)` 被假设为恒等函数。此外，我们假设 MDP 折扣因子 `γ` = 1。

请注意，所有这些假设都过于简单化，因此是对现实世界的不切实际的模型，但从这个简单模型入手有助于建立良好的直觉，并使我们能够通过从这个简单基础模型逐步增加复杂性/细微差别来开发更现实的模型。

与以往一样，为了求解控制问题，我们定义最优值函数并调用贝尔曼最优性方程。我们将使用我们现在非常熟悉的离散时间有限时域 MDP 的标准记号。

记策略 `π` 在时间 `t`（对所有 `t` = 0, 1, …`T − 1`）的值函数为：

$$
\begin{array}{r} {V_{t}^{\pi}((P_{t},R_{t})) = \mathbb{E}_{\pi}\lbrack{\sum\limits_{i = t}^{T - 1}N_{i}} \cdot (P_{i} - \beta \cdot N_{i})|(P_{t},R_{t})\rbrack} \\\\ \end{array}
$$

记时间 `t`（对所有 `t` = 0, 1, …, `T − 1`）的最优值函数为：

$$
\begin{array}{r} {V_{t}^{\*}((P_{t},R_{t})) = \max_{\pi}V_{t}^{\pi}((P_{t},R_{t}))} \\\\ \end{array}
$$

最优值函数对所有 `t` = 0, 1, …, `T − 2` 满足有限时域贝尔曼最优性方程，如下所示：

$$
\begin{array}{r} {V_{t}^{\*}((P_{t},R_{t})) = \max_{N_{t}}\left\{ N_{t} \cdot (P_{t} - \beta \cdot N_{t}) + \mathbb{E}\lbrack V_{t + 1}^{\*}((P_{t + 1},R_{t + 1}))\rbrack \right\}} \\\\ \end{array}
$$

以及

$$
\begin{array}{r} {V_{T - 1}^{\*}((P_{T - 1},R_{T - 1})) = N_{T - 1} \cdot (P_{T - 1} - \beta \cdot N_{T - 1}) = R_{T - 1} \cdot (P_{T - 1} - \beta \cdot R_{T - 1})} \\\\ \end{array}
$$

从上述内容，我们可以推断：

$$
\begin{array}{r} {V_{T - 2}^{\*}((P_{T - 2},R_{T - 2})) = \max_{N_{T - 2}}\left\{ N_{T - 2} \cdot (P_{T - 2} - \beta \cdot N_{T - 2}) + \mathbb{E}\lbrack R_{T - 1} \cdot (P_{T - 1} - \beta \cdot R_{T - 1})\rbrack \right\}} \\\\ \end{array}
$$

$$
\begin{array}{r} {= \max_{N_{T - 2}}\left\{ N_{T - 2} \cdot (P_{T - 2} - \beta \cdot N_{T - 2}) + \mathbb{E}\lbrack(R_{T - 2} - N_{T - 2})(P_{T - 1} - \beta \cdot (R_{T - 2} - N_{T - 2}))\rbrack \right\}} \\\\ \end{array}
$$

$$
\begin{array}{r} {= \max_{N_{T - 2}}\left\{ N_{T - 2} \cdot (P_{T - 2} - \beta \cdot N_{T - 2}) + (R_{T - 2} - N_{T - 2}) \cdot (P_{T - 2} - \alpha \cdot N_{T - 2} - \beta \cdot (R_{T - 2} - N_{T - 2})) \right\}} \\\\ \end{array}
$$

这简化为：

$$
\begin{array}{r} {V_{T - 2}^{\*}((P_{T - 2},R_{T - 2})) = \max_{N_{T - 2}}\left\{ R_{T - 2} \cdot P_{T - 2} - \beta \cdot R_{T - 2}^{2} + (\alpha - 2\beta)(N_{T - 2}^{2} - N_{T - 2} \cdot R_{T - 2}) \right\}} \\\\ \end{array}
$$

(10.9)

对于 `α` ≥ 2`β` 的情况，注意到 `N[T − 2]` ≤ `R[T − 2]`，我们有平凡解：

$$
\begin{array}{r} {N_{T - 2}^{\*} = 0\text{~or~}N_{T - 2}^{\*} = R_{T - 2}} \\\\ \end{array}
$$

