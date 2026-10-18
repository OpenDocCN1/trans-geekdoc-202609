

$$\\begin{array}{ll} {V\_{t}^{\*}(s\_{t}) = \\max\_{a\_{t} \\in \\mathcal{A}\_{t}}\\left\\{ \\sum\\limits\_{s\_{t + 1} \\in \\mathcal{S}\_{t + 1}}\\sum\\limits\_{r\_{t + 1} \\in \\mathcal{D}\_{t + 1}} \\right.} & \\left. {(\\mathcal{P}\_{R})}_{t}(s\_{t},a\_{t},r\_{t + 1},s\_{t + 1}) \\cdot (r\_{t + 1} + \\gamma \\cdot W\_{t + 1}^{\*}(s\_{t + 1})) \\right\\} \\\\ & {\\text{~for~all~}t = 0,1,\\ldots,T - 1,s\_{t} \\in \\mathcal{N}\_{t}} \\\\ \\end{array}$$

(5.9)

where

$$\\begin{array}{l} {W\_{t}^{\*}(s\_{t}) = \\left\\{ \\begin{array}{ll} {V\_{t}^{\*}(s\_{t})} & {\\text{~if~}s\_{t} \\in \\mathcal{N}\_{t}} \\\\ 0 & {\\text{~if~}s\_{t} \\in \\mathcal{T}\_{t}} \\\\ \\end{array}~ \\right.\\text{~for~all~}t = 1,2,\\ldots,T} \\\\ \\end{array}$$

相关的最优（确定性）策略

$$\\begin{array}{r} \\left. {(\\pi\_{D}^{\*})}\_{t}:\\mathcal{N}\_{t}\\rightarrow\\mathcal{A}\_{t} \\right. \\\\ \\end{array}$$

定义如下：

(*π*[*D*]^(\*))[*t*](*s*[*t*]) = arg max[*a*[*t*] ∈ 𝒜[*t*]]{∑\_*s*[*t* + 1]∈𝒮[*t* + 1]∑\_*r*[*t* + 1]∈𝒟[*t* + 1] &(𝒫[*R*])[*t*](*s*[*t*],*a*[*t*],*r*[*t* + 1],*s*[*t* + 1])⋅(*r*[*t* + 1]+*γ*⋅*W*[*t* + 1]^(\*)(*s*[*t* + 1]))} & for all *t* = 0, 1, …, *T* − 1, *s*[*t*] ∈ 𝒩[*t*]\\end{align}

(5.10)

因此，对于有限 MDP，这产生了一个简单的算法来计算所有 `t` 的 `V[t]^*`，只需从 `t = T - 1` 递减到 `t = 0`，使用方程 (5.9) 计算 `V[t]^*`，并使用方程 (5.10) 计算所有 `t = 0, 1, …, T - 1` 的 `(π[D]^*)[t]`，基于已知的 `W[t + 1]^*` 值（因为我们正在递减时间索引 `t`）。

该算法是将值迭代适应于有限时域情况的算法，采用了这种简单的“时间回溯”技术（称为 `Backward Induction`）。让我们编写一些代码来实现这个算法。我们得到一个关于增广（有限）状态空间 `WithTime[S]` 的 MDP。因此，这个 MDP 的类型是 `FiniteMarkovDecisionProcess[WithTime[S], A]`。我们的第一个任务是将该 MDP 的状态-奖励概率转移函数 `P[R]` “解包”为一个时间索引的状态-奖励概率转移函数序列 `(P[R])[t]`，`t = 0, 1, …, T - 1`。这是通过以下函数 `unwrap_finite_horizon_MDP` 完成的（`itertools.groupby` 按时间步长对增广状态进行分组，函数 `without_time` 在将状态放入 `(P[R])[t]` 时去除增广状态的时间步长，即 `Sequence[StateActionMapping[S, A]]`）。

![](images/comp05_18.jpg)

现在我们已经将状态-奖励转移函数 `(P[R])[t]` 按 `Sequence[StateActionMapping[S, A]]` 的形式排列好了，我们准备执行时间回溯算法来计算 `V[t]^*`。以下函数 `optimal_vf_and_policy` 通过直接使用方程 (5.9) 和 (5.10) 来完成此任务，如上所述。

![](images/comp05_19.jpg)

如果对于所有 `t`，`|N[t]|` 是 `O(m)`，且 `|A[t]|` 是 `O(k)`，则该算法的运行时间为 `O(m² ⋅ k ⋅ T)`。

请注意，这些针对有限时域有限 MDP 的算法不需要像常规策略评估和值迭代那样进行“收敛迭代”。相反，在这些算法中，我们只需沿时间向后走，并立即从下一时间步长的值函数（由于我们是向后走，该值函数已知）得到每个时间步长的值函数。这种“值函数反向传播”技术被称为 `Backward Induction` 算法，在许多金融应用中非常常见（我们将在本书后面看到）。上述时间回溯代码位于文件 `rl/finite_horizon.py` 中。

## 5.14 产品生命周期终点/季节终点的动态定价

现在我们考虑一个相当重要的商业应用——动态定价。我们考虑的是产品达到生命周期终点或季节终点后，我们不再希望继续销售该产品的情况。我们需要根据产品库存量、距离生命周期终点/季节终点还有多少天，以及客户需求作为价格调整函数的预期，动态地上下调整价格。为了具体说明，假设你拥有一家超市，距离万圣节还有 `T` 天。你刚从供应商处收到 `M` 个万圣节面具，在最后的 `T` 天内不会再收到任何库存。你希望在每天开始时动态设定万圣节面具的售价，以最大化从今天到万圣节的万圣节面具 *预期总销售额* （假设万圣节后没有人会购买万圣节面具）。

假设对于 `T` 天中的每一天，在一天开始时，你需要从 `N` 个价格 `P[1]`、`P[2]`、…、`P[N] ∈ ℝ` 中选择一个作为当天的价格，你选择的价格将成为当天所有面具的售价。假设任何一天万圣节面具的客户需求遵循均值为 `λ[i] ∈ ℝ` 的泊松概率分布，如果你将当天的价格设为 `P[i]`（其中 `i` 是 1、2、…、`N` 中的一个选择）。请注意，在任何一天，需求可能会超过商店中万圣节面具的数量，在这种情况下，当天售出的面具数量将等于当天开始时拥有的面具数量。

该 MDP 的状态由一对 `(t, I[t])` 给出，其中 `t ∈ {0,1,…,T}` 表示时间索引，`I[t] ∈ {0,1,…,M}` 表示时间 `t` 时的库存。根据前一节的记号，对于所有 `t = 0, 1, …, T`，`S[t] = {0,1,…,M}`，因此 `I[t] ∈ S[t]`。对于所有 `t = 0, 1, …, T - 1`，`N[t] = S[t]`，且 `N[T] = ∅`。时间 `t` 的动作选择可以表示为从 1 到 `N` 的整数选择。因此，`A[t] = {1,2,…,N}`。

请注意：

$$\\begin{array}{r} {I\_{0} = M,I\_{t + 1} = \\max(0,I\_{t} - d\_{t})\\text{~for~}0 \\leq t < T} \\\\ \\end{array}$$

其中 `d[t]` 是第 `t` 天的随机需求，遵循均值为 `λ[i]` 的泊松分布，如果第 `t` 天的动作（价格选择索引）为 `i ∈ A[t]`。另外，请注意，第 `t` 天的销售收入等于 `min(I[t], d[t]) ⋅ P[i]`。因此，时间索引 `t` 的状态-奖励概率转移函数

$$\\begin{array}{r} \\left. {(\\mathcal{P}\_{R})}\_{t}:\\mathcal{N}\_{t} \\times \\mathcal{A}\_{t} \\times \\mathcal{D}\_{t + 1} \\times \\mathcal{S}\_{t + 1}\\rightarrow\\lbrack 0,1\\rbrack \\right. \\\\ \\end{array}$$

定义如下：

$$\\begin{array}{l} {{(\\mathcal{P}\_{R})}\_{t}(I\_{t},i,r\_{t + 1},I\_{t} - k) = \\left\\{ \\begin{array}{ll} \\frac{e^{- \\lambda\_{i}}\\lambda\_{i}^{k}}{k!} & {\\text{~if~}k < I\_{t}\\text{~and~}r\_{t + 1} = k \\cdot P\_{i}} \\\\ {\\sum\\limits\_{j = I\_{t}}^{\\infty}\\frac{e^{- \\lambda\_{i}}\\lambda\_{i}^{j}}{j!}} & {\\text{~if~}k = I\_{t}\\text{~and~}r\_{t + 1} = k \\cdot P\_{i}} \\\\ 0 & \\text{~otherwise~} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$

对于所有 `0 ≤ t < T`

使用 `(P[R])[t]` 的定义，并使用边界条件 `W[T]^*(I[T]) = 0` 对于所有 `I[T] ∈ {0,1,…,M}`，我们可以执行时间回溯算法来计算 `V[t]^*` 及其相关的最优（确定性）策略 `(π[D]^*)[t]` 对于所有 `0 ≤ t < T`。

现在让我们编写一些代码来将这个动态规划问题表示为 `FiniteMarkovDecisionProcess` 并确定其最优策略，即任何可用库存水平 `I[t]` 时时间步长 `t` 的最优（动态）价格。类型 `N[t]` 是 `int`，类型 `A[t]` 也是 `int`。因此，我们创建一个类型为 `FiniteMarkovDecisionProcess[WithTime[int], int]` 的 MDP（因为增广状态空间是 `WithTime[int]`）。我们的第一个任务是构造类型为 `P[R]` 的：

![](images/comp05_20.jpg)

