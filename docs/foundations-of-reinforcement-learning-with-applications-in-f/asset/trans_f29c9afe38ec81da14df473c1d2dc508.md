

现在让我们为策略迭代算法编写一些代码。与策略评估不同，策略评估反复对值函数进行操作（并返回一个值函数），而策略迭代反复对值函数和策略的一对进行操作（并返回一个值函数和策略的一对）。在下面的代码中，请注意类型 `Tuple[V[S], FinitePolicy[S, A]]`，它表示一个值函数和策略的一对。函数 `policy_iteration` 反复将函数 `update` 应用于值函数和策略的一对。`update` 函数在将其输入 `vf_policy` 拆分为 `vf: V[S]` 和 `pi: FinitePolicy[S, A]` 后，从输入 `mdp` 和 `pi` 的组合中创建一个 MRP（`mrp: FiniteMarkovRewardProcess[S]`）。然后它对 `mrp` 执行策略评估（使用 `evaluate_mrp_result` 函数）以生成一个值函数 `policy_vf: V[S]`，最后从 `policy_vf` 创建一个贪婪（改进）策略，名为 `improved_pi`（使用之前编写的函数 `greedy_policy_from_vf`）。因此，函数 `update` 执行策略评估，然后执行策略改进。还要注意，`policy_iteration` 提供了一个选项，可以使用基于线性代数求解器的方法来计算给定策略的值函数（`mrp` 对象的 `get_value_function_vec` 方法），以防状态空间不太大。`policy_iteration` 返回一个迭代器，对该过程中由反复策略评估和策略改进产生的值函数和策略的一对进行迭代。`almost_equal_vf_pis` 是用于根据策略迭代产生的两个连续值函数之间的距离来决定终止的函数。`policy_iteration_result` 返回最终（最优）的值函数和策略的一对（来自 `policy_iteration` 产生的迭代器），基于 `almost_equal_vf_pis` 的终止标准。

![](images/comp05_7.jpg)

如果给定 MDP 的非终止状态数为 *m*，动作数（|𝒜|）为 *k*，则策略改进的运行时间为 *O*(*m*² ⋅ *k*)，我们之前已经看到，策略评估的每次迭代也是 *O*(*m*² ⋅ *k*)。

## 5.8 贝尔曼最优性算子与值迭代算法

通过对方程 (5.3) 中贪婪策略函数的定义进行微小调整（将 arg max 改为 *max*），我们定义了 *贝尔曼最优性算子*

$$
\begin{array}{r}
\left. \mathbf{\\mathbf{B}}^{\*}:{\\mathbb{R}}^{m}\rightarrow{\\mathbb{R}}^{m} \right.
\\end{array}
$$

作为向量空间 ℝ^(*m*) 中向量（表示值函数）的以下（非线性）变换

$$
\begin{array}{r}
{\mathbf{\\mathbf{B}}^{\*}(\\mathbf{\\mathbf{V}})(s) = \\max\_{a \\in \\mathcal{A}}\\left\\{ \\mathcal{R}(s,a) + \\gamma{\\sum\\limits\_{s^{\\prime} \\in \\mathcal{N}}\\mathcal{P}}(s,a,s^{\\prime}) \\cdot \\mathbf{\\mathbf{V}}(s^{\\prime}) \\right\\}\\text{~for~all~}s \\in \\mathcal{N}}
\\end{array}
$$

(5.5)

我们将在数学阐述中使用方程 (5.5)，但我们需要一个不同的（但等价的）表达式来表示 **B**^(\*)(**V**)(*s*) 以指导我们的代码，因为 `FiniteMarkovDecisionProcess` 的接口操作于 𝒫[*R*]，而不是 ℛ 和 𝒫。**B**^(\*)(**V**)(*s*) 的等价表达式如下：

$$
\begin{array}{r}
{\mathbf{\\mathbf{B}}^{\*}(\\mathbf{\\mathbf{V}})(s) = \\max\_{a \\in \\mathcal{A}}\\left\\{ {\\sum\\limits\_{s^{\\prime} \\in \\mathcal{S}}{\\sum\\limits\_{r \\in \\mathcal{D}}\\mathcal{P}\_{R}}}(s,a,r,s^{\\prime}) \\cdot (r + \\gamma \\cdot \\mathbf{\\mathbf{W}}(s^{\\prime})) \\right\\}\\text{~for~all~}s \\in \\mathcal{N}}
\\end{array}
$$

(5.6)

其中 **W** ∈ ℝ^(*n*) 定义为（与方程 (5.4) 的情况相同）：

$$
\begin{array}{l}
{\\mathbf{\\mathbf{W}}(s^{\\prime}) = \\left\\{ \\begin{array}{ll} {\\mathbf{\\mathbf{V}}(s^{\\prime})} & {\\text{~if~}s^{\\prime} \\in \\mathcal{N}} \\\\ 0 & {\\text{~if~}s^{\\prime} \\in \\mathcal{T} = \\mathcal{S} - \\mathcal{N}} \\\\ \\end{array}~ \\right.}
\\end{array}
$$

请注意，在方程 (5.6) 中，因为我们必须处理 𝒫[*R*]，所以我们需要考虑到所有状态 *s*^′ ∈ 𝒮 的转换（与方程 (5.5) 中转换到所有状态 *s*^′ ∈ 𝒩 相反），因此，我们需要小心处理转换到状态 *s*^′ ∈ 𝒯 的情况（基本上是通过使用上面描述的 **W** 函数）。

对于每个 *s* ∈ 𝒩，在 (5.5) 中产生最大化的动作 *a* ∈ 𝒜 是由确定性策略 *π*[*D*] 在 (5.3) 中规定的动作。因此，如果我们使用贪婪策略 *G*(**V**) 对任何值函数 **V** ∈ ℝ^(*m*) 应用贝尔曼策略算子，它应该与应用贝尔曼最优性算子相同。因此，

$$
\begin{array}{r}
{\\mathbf{\\mathbf{B}}^{G(\\mathbf{\\mathbf{V}})}(\\mathbf{\\mathbf{V}}) = \\mathbf{\\mathbf{B}}^{\*}(\\mathbf{\\mathbf{V}})\\text{~for~all~}\\mathbf{\\mathbf{V}} \\in {\\mathbb{R}}^{m}}
\\end{array}
$$

(5.7)

特别是，值得注意的是，通过将 **V** 专门化为策略 *π* 的值函数 **V**^(*π*)，我们得到：

$$
\begin{array}{r}
{\\mathbf{\\mathbf{B}}^{G(\\mathbf{\\mathbf{V}}^{\\pi})}(\\mathbf{\\mathbf{V}}^{\\pi}) = \\mathbf{\\mathbf{B}}^{\*}(\\mathbf{\\mathbf{V}}^{\\pi})}
\\end{array}
$$

这是使用改进策略 *G*(**V**^(*π*)) 的策略评估第一阶段的简洁表示（注意贝尔曼策略算子、贝尔曼最优性算子和贪婪策略函数是如何在这个方程中结合在一起的）。

很像贝尔曼策略算子 **B**^(*π*) 是由 MDP 贝尔曼策略方程（等价地，MRP 贝尔曼方程）所激发的那样，贝尔曼最优性算子 **B**^(\*) 是由 MDP 状态-值函数贝尔曼最优性方程（如下重述）所激发的：

$$
\begin{array}{r}
{\\mathbf{\\mathbf{V}}^{\*}(s) = \\max\_{a \\in \\mathcal{A}}\\left\\{ \\mathcal{R}(s,a) + \\gamma{\\sum\\limits\_{s^{\\prime} \\in \\mathcal{N}}\\mathcal{P}}(s,a,s^{\\prime}) \\cdot \\mathbf{\\mathbf{V}}^{\*}(s^{\\prime}) \\right\\}\\text{~for~all~}s \\in \\mathcal{N}}
\\end{array}
$$

因此，我们可以将 MDP 状态-值函数贝尔曼最优性方程简洁地表示为：

$$
\begin{array}{r}
{\\mathbf{\\mathbf{V}}^{\*} = \\mathbf{\\mathbf{B}}^{\*}(\\mathbf{\\mathbf{V}}^{\*})}
\\end{array}
$$

这意味着 **V**^(\*) ∈ ℝ^(*m*) 是贝尔曼最优性算子 **B**^(\*):ℝ^(*m*)→ℝ^(*m*) 的一个不动点。

请注意，我们提供的贪婪策略函数和贝尔曼最优性算子的定义可以推广到非有限 MDP，因此我们可以推广方程 (5.7) 以及 **V**^(\*) 是贝尔曼最优性算子不动点的说法仍然成立。但是，在本章中，由于我们专注于为有限 MDP 开发算法，我们将坚持我们为有限 MDP 提供的定义。

很像我们证明了 **B**^(*π*) 是一个收缩函数一样，我们想要证明 **B**^(\*) 是一个收缩函数（在 *L*^∞ 范数下），以便我们可以利用班纳赫不动点定理，并通过迭代应用贝尔曼最优性算子 **B**^(\*) 来解决控制问题。因此，我们需要证明对于所有 **X**、 **Y** ∈ ℝ^(*m*)，

$$
\begin{array}{r}
{\\max\_{s \\in \\mathcal{N}}|(\\mathbf{\\mathbf{B}}^{\*}(\\mathbf{\\mathbf{X}}) - \\mathbf{\\mathbf{B}}^{\*}(\\mathbf{\\mathbf{Y}}))(s)| \\leq \\gamma \\cdot \\max\_{s \\in \\mathcal{N}}|(\\mathbf{\\mathbf{X}} - \\mathbf{\\mathbf{Y}})(s)|}
\\end{array}
$$

这个证明比我们为 **B**^(*π*) 做的证明要难一些。在这里，我们需要利用 **B**^(\*) 的两个关键属性。

1.  单调性属性，即，对于所有 **X**、 **Y** ∈ ℝ^(*m*)，

