

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}^{nat}J(\\mathbf{\\mathbf{\\theta}}) = \\mathbf{\\mathbf{F}I}\\mathbf{\\mathbf{M}}\_{\\rho^{\\pi},\\pi}^{- 1}(\\mathbf{\\mathbf{\\theta}}) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}})} \\\\ \\end{array}$$  

where `FIM`[*ρ*[*π*], *π*] 表示相对于 *s* ∼ *ρ*^(*π*),*a* ∼ *π* 的 Fisher 信息矩阵。

我们在前一节中已经指出，如果为 *Q*^(*π*)(*s*, *a*) 启用兼容函数近似（Compatible Function Approximation）并使用线性函数近似，则我们有公式 (14.1)，即：

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}}) = \\mathbf{\\mathbf{F}I}\\mathbf{\\mathbf{M}}\_{\\rho^{\\pi},\\pi}(\\mathbf{\\mathbf{\\theta}}) \\cdot \\mathbf{\\mathbf{w}}\_{\\mathbf{\\mathbf{\\theta}}}^{\*}} \\\\ \\end{array}$$  

这意味着：

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}^{nat}J(\\mathbf{\\mathbf{\\theta}}) = \\mathbf{\\mathbf{w}}\_{\\mathbf{\\mathbf{\\theta}}}^{\*}} \\\\ \\end{array}$$  

这个紧凑的结果使得自然策略梯度（Natural Policy Gradient，NPG）拥有一个简单的算法：

*   每次原子体验（atomic experience）之后，根据评论家损失梯度更新评论家参数 `w`：

    $$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{w}} = \\alpha\_{\\mathbf{\\mathbf{w}}} \\cdot (R\_{t + 1} + \\gamma \\cdot \\mathbf{\\mathbf{S}C}{(S\_{t + 1},A\_{t + 1};\\mathbf{\\mathbf{\\theta}})}^{T} \\cdot \\mathbf{\\mathbf{w}} - \\mathbf{\\mathbf{S}C}{(S\_{t},A\_{t};\\mathbf{\\mathbf{\\theta}})}^{T} \\cdot \\mathbf{\\mathbf{w}}) \\cdot \\mathbf{\\mathbf{S}C}(S\_{t},A\_{t};\\mathbf{\\mathbf{\\theta}})} \\\\ \\end{array}$$  

*   每次原子体验之后，沿 `w` 的方向更新演员参数 `θ`：

    $$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{\\theta}} = \\alpha\_{\\mathbf{\\mathbf{\\theta}}} \\cdot \\mathbf{\\mathbf{w}}} \\\\ \\end{array}$$  

### 14.8.2 确定性策略梯度

确定性策略梯度（Deterministic Policy Gradient，缩写为 DPG）是对策略梯度的一种创造性改进。它不再为随机策略使用参数化函数近似，而是为连续动作空间中的确定性策略使用参数化函数近似。DPG 源自 Silver、Lever、Heess、Degris、Wiestra、Riedmiller 的论文（[Silver et al. 2014](#bib01.xhtml#refbib_57））。DPG 可以用 Q-值函数的期望梯度来表示，其估计效率远高于通常的（随机）策略梯度。（随机）策略梯度需要对状态空间和动作空间进行积分，而 DPG 只需对状态空间进行积分。因此，如果动作空间具有许多维度，计算（随机）策略梯度将需要更多样本。

在 Actor-Critic DPG 中，Actor 是确定性策略的函数近似，Critic 是 Q-值函数的函数近似。Silver 等人的论文为 DPG 提供了兼容函数近似定理（Compatible Function Approximation Theorem），以克服评论家近似偏差。该论文还表明，当策略方差趋于 0 时，DPG 是（随机）策略梯度的极限情况。这意味着 PG 的常用机制（如 Actor-Critic、兼容函数近似、自然策略梯度等）也适用于 DPG。

我们使用记号 *a* = *π*[*D*](*s*; **θ**) 来表示（可能是多维的）连续值动作 *a*，其值等于确定性策略函数近似 *π*[*D*]（由 **θ** 参数化）在状态 *s* 下的输出。

DPG 的核心思想可以通过关注 GPI 的基础，特别是 GPI 中的策略改进（Policy Improvement）来直观理解。对于连续动作空间，贪婪策略改进（对每个状态对动作取 argmax）是有问题的。因此，一个简单且有吸引力的替代方案是，沿 Q-值函数梯度的方向移动策略（而不是在每一步全局最大化 Q-值函数）。具体来说，对于遇到的每个状态 *s*，策略近似参数 **θ** 按照 ∇[**θ**]*Q*(*s*, *π*[*D*](*s*; **θ**)) 进行更新。请注意，策略改进的方向对每个状态都不同，因此策略改进的平均方向由以下公式给出：

$$\\begin{array}{r} {\\mathbb{E}\_{s\\sim\\rho^{\\mu}}\\lbrack\\nabla\_{\\mathbf{\\mathbf{\\theta}}}Q(s,\\pi\_{D}(s;\\mathbf{\\mathbf{\\theta}}))\\rbrack} \\\\ \\end{array}$$  

其中 *ρ*^(*μ*) 是我们为 PG 定义的相同的折扣聚合状态访问度量（Discounted-Aggregate State-Visitation Measure）（现在用于探索行为策略 *μ*）。

使用链式法则，上述表达式可以写成：

$$\\begin{array}{r} {\\mathbb{E}\_{s\\sim\\rho^{\\mu}}\\lbrack\\nabla\_{\\mathbf{\\mathbf{\\theta}}}\\pi\_{D}(s;\\mathbf{\\mathbf{\\theta}}) \\cdot \\nabla\_{a}Q^{\\pi\_{D}}(s,a)|\_{a = \\pi\_{D}(s;\\mathbf{\\mathbf{\\theta}})}\\rbrack} \\\\ \\end{array}$$  

请注意，∇[**θ**]*π*[*D*](*s*; **θ**) 是一个雅可比矩阵，因为它对可能是多维的动作 *a* = *π*[*D*](*s*; **θ**) 相对于 **θ** 中的每个参数求偏导数。正如我们在介绍（随机）策略梯度时所指出的，当 **θ** 变化时，策略 *π*[*D*] 会发生变化，从而改变状态分布 *ρ*^(*π*[*D*])。因此，不清楚这个计算是否确实能保证改进——它没有考虑 **θ** 的变化对 *ρ*^(*π*[*D*]) 的影响。然而，就像在 PGT 中一样，确定性策略梯度定理（Deterministic Policy Gradient Theorem，缩写为 DPGT）确保不需要计算 *ρ*^(*π*[*D*]) 相对于 **θ** 的梯度，并且上述描述的更新确实遵循了期望回报目标函数的梯度。我们现在通过陈述 DPGT 来形式化这一点。

类似于为（随机）策略梯度定义的期望回报目标，我们为 DPG 定义期望回报目标 *J*(**θ**) 为：

$$\\begin{aligned} {J(\\mathbf{\\mathbf{\\theta}})} & {= \\mathbb{E}\_{\\pi\_{D}}\\lbrack{\\sum\\limits\_{t = 0}^{\\infty}\\gamma^{t}} \\cdot R\_{t + 1}\\rbrack} \\\\ & {= {\\sum\\limits\_{s \\in \\mathcal{N}}\\rho^{\\pi\_{D}}}(s) \\cdot \\mathcal{R}\_{s}^{\\pi\_{D}(s;\\mathbf{\\mathbf{\\theta}})}} \\\\ & {= \\mathbb{E}\_{s\\sim\\rho^{\\pi\_{D}}}\\lbrack\\mathcal{R}\_{s}^{\\pi\_{D}(s;\\mathbf{\\mathbf{\\theta}})}\\rbrack} \\\\ \\end{aligned}$$  

其中

$$\\begin{array}{r} \\left. \\rho^{\\pi\_{D}}(s) = {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}{\\sum\\limits\_{t = 0}^{\\infty}\\gamma^{t}}} \\cdot p\_{0}(S\_{0}) \\cdot p(S\_{0}\\rightarrow s,t,\\pi\_{D}) \\right. \\\\ \\end{array}$$  

是在遵循确定性策略 *π*[*D*](*s*; **θ**) 时的折扣聚合状态访问度量。

与 PGT 证明的推导类似，我们得到了 DPGT，如下所示：

在实践中，我们使用一个 Actor-Critic 算法，并使用函数近似 *Q*(*s*, *a*; **w**) 作为 Q-值函数的评论家。由于近似的策略是确定性的，我们需要解决探索问题——这通常通过离策略控制（Off-Policy Control）来完成，即我们使用一个探索性的（随机）行为策略，而被近似（并通过 DPG 学习）的策略是目标（确定性）策略。在离策略的情况下，期望回报目标略有不同——它是在遵循行为策略时，目标策略下的状态发生概率下的期望 Q-值，而离策略确定性策略梯度是一个近似（非精确）公式。我们在演员中避免使用重要性采样，因为 DPG 不涉及对动作的积分；我们在评论家中通过使用 Q-Learning 来避免重要性采样。因此，对于离策略 Actor-Critic DPG，我们在由行为策略生成的轨迹体验中，在每次原子体验后更新评论家参数 `w` 和演员参数 `θ`。

