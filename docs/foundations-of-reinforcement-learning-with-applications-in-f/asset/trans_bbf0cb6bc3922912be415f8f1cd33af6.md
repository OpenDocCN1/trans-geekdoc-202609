

$$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{w}} = \\alpha\_{\\mathbf{\\mathbf{w}}} \\cdot (R\_{t + 1} + \\gamma \\cdot Q(S\_{t + 1},\\pi\_{D}(S\_{t + 1};\\mathbf{\\mathbf{\\theta}});\\mathbf{\\mathbf{w}}) - Q(S\_{t},A\_{t};\\mathbf{\\mathbf{w}})) \\cdot \\nabla\_{\\mathbf{\\mathbf{w}}}Q(S\_{t},A\_{t};\\mathbf{\\mathbf{w}})} \\\\ \\end{array}$$  

$$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{\\theta}} = \\alpha\_{\\mathbf{\\mathbf{\\theta}}} \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}\\pi\_{D}(S\_{t};\\mathbf{\\mathbf{\\theta}}) \\cdot \\nabla_{a}Q(S\_{t},a;\\mathbf{\\mathbf{w}})|_{a = \\pi\_{D}(S\_{t};\\mathbf{\\mathbf{\\theta}})}} \\\\ \\end{array}$$  

Critic Bias 可以通过 DPG 的兼容函数近似定理来解决（有关详细信息，请参阅 Silver 等人的论文）。由函数近似的自举非策略学习引起的不稳定性可以通过梯度时序差分（GTD）来解决。

## 14.9 进化策略

我们以进化策略一节结束本章——这是一类用于解决 MDP 控制问题的算法。我们要首先强调，从技术上讲，进化策略并不是 RL 算法（原因我们将在解释进化策略技术后阐明）。然而，进化策略在解决 MDP 控制问题时有时非常有效，因此，作为解决 MDP 控制的广泛方法的一部分，我们给予了适当的覆盖。我们在本章中介绍它们，是因为它们与策略梯度算法表面上相似（同样，它们不是 RL 算法，因此也不是策略梯度算法）。

进化策略（缩写为 ES）实际上是指一种技术/方法，最好理解为一种黑盒优化。它在 20 世纪 70 年代作为 *启发式搜索方法* 而流行起来。它松散地受到生物自然进化的启发。我们专注于 ES 的一个子类，即自然进化策略（缩写为 NES）。

这种方法的原始设置非常通用，与解决 MDP 完全无关。让我们先了解这种通用设置。给定目标函数 *F*(**ψ**)，其中 **ψ** 指的是参数，我们考虑 **ψ** 上的概率分布 *p*[**θ**](**ψ**)，其中 **θ** 指的是概率分布的参数。在这种通用设置中，目标是最大化平均目标 𝔼[**ψ** ∼ *p*[**θ**]]\[*F*(**ψ**)].

我们通过随机梯度上升来搜索最优 *θ*，如下所示：

$$\\begin{aligned} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}(\\mathbb{E}\_{\\mathbf{\\mathbf{\\psi}}\\sim p\_{\\mathbf{\\mathbf{\\theta}}}}\\lbrack F(\\mathbf{\\mathbf{\\psi}})\\rbrack)} & {= \\nabla\_{\\mathbf{\\mathbf{\\theta}}}({\\int\_{\\mathbf{\\mathbf{\\psi}}}p\_{\\mathbf{\\mathbf{\\theta}}}}(\\mathbf{\\mathbf{\\psi}}) \\cdot F(\\mathbf{\\mathbf{\\psi}}) \\cdot d\\mathbf{\\mathbf{\\psi}})} \\\\ & {= {\\int\_{\\mathbf{\\mathbf{\\psi}}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}(p\_{\\mathbf{\\mathbf{\\theta}}}(\\mathbf{\\mathbf{\\psi}})) \\cdot F(\\mathbf{\\mathbf{\\psi}}) \\cdot d\\mathbf{\\mathbf{\\psi}}} \\\\ & {= {\\int\_{\\mathbf{\\mathbf{\\psi}}}p\_{\\mathbf{\\mathbf{\\theta}}}}(\\mathbf{\\mathbf{\\psi}}) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}(\\log p\_{\\mathbf{\\mathbf{\\theta}}}(\\mathbf{\\mathbf{\\psi}})) \\cdot F(\\mathbf{\\mathbf{\\psi}}) \\cdot d\\mathbf{\\mathbf{\\psi}}} \\\\ & {= \\mathbb{E}\_{\\mathbf{\\mathbf{\\psi}}\\sim p\_{\\mathbf{\\mathbf{\\theta}}}}\\lbrack\\nabla\_{\\mathbf{\\mathbf{\\theta}}}(\\log p\_{\\mathbf{\\mathbf{\\theta}}}(\\mathbf{\\mathbf{\\psi}})) \\cdot F(\\mathbf{\\mathbf{\\psi}})\\rbrack} \\\\ \\end{aligned}$$  

(14.2)

现在让我们看看如何将 NES 应用于解决 MDP 控制。我们将 *F*( ⋅ ) 设置为 MDP 的（随机）*回报*。 **ψ** 对应于确定性策略 *π*[**ψ**]:𝒩→𝒜 的参数。 **ψ** ∈ ℝ^(*m*) 从各向同性 *m* 变量高斯分布中抽取，即均值向量为 **θ** ∈ ℝ^(*m*) 且固定对角协方差矩阵 *σ*²**I**[**m**] 的高斯分布，其中 *σ* ∈ ℝ 保持固定，**I**[**m**] 是 *m* × *m* 单位矩阵。平均目标（*期望回报*）可以写成：

$$\\begin{array}{r} {\\mathbb{E}\_{\\mathbf{\\mathbf{\\psi}}\\sim p\_{\\mathbf{\\mathbf{\\theta}}}}\\lbrack F(\\mathbf{\\mathbf{\\psi}})\\rbrack = \\mathbb{E}\_{\\mathbf{\\epsilon}\\sim\\mathcal{N}(0,\\mathbf{\\mathbf{I}}\_{\\mathbf{\\mathbf{m}}})}\\lbrack F(\\mathbf{\\mathbf{\\theta}} + \\sigma \\cdot \\mathbf{\\epsilon})\\rbrack} \\\\ \\end{array}$$  

其中 **ϵ** ∈ ℝ^(*m*) 是生成 **ψ** 的标准正态随机变量。因此，从方程 (14.2) 开始，*期望回报* 的梯度（∇[**θ**]）可以写成：

$$\\begin{array}{r} {\\mathbb{E}\_{\\mathbf{\\mathbf{\\psi}}\\sim p\_{\\mathbf{\\mathbf{\\theta}}}}\\lbrack\\nabla\_{\\mathbf{\\mathbf{\\theta}}}(\\log p\_{\\mathbf{\\mathbf{\\theta}}}(\\mathbf{\\mathbf{\\psi}})) \\cdot F(\\mathbf{\\mathbf{\\psi}})\\rbrack} \\\\ \\end{array}$$  

$$\\begin{array}{r} {= \\mathbb{E}\_{\\mathbf{\\mathbf{\\psi}}\\sim\\mathcal{N}(\\mathbf{\\mathbf{\\theta}},\\sigma^{2}\\mathbf{\\mathbf{I}}\_{\\mathbf{\\mathbf{m}}})}\\lbrack\\nabla\_{\\mathbf{\\mathbf{\\theta}}}(\\frac{- {(\\mathbf{\\mathbf{\\psi}} - \\mathbf{\\mathbf{\\theta}})}^{T} \\cdot (\\mathbf{\\mathbf{\\psi}} - \\mathbf{\\mathbf{\\theta}})}{2\\sigma^{2}}) \\cdot F(\\mathbf{\\mathbf{\\psi}})\\rbrack} \\\\ \\end{array}$$  

$$\\begin{array}{r} {= \\frac{1}{\\sigma} \\cdot \\mathbb{E}\_{\\mathbf{\\epsilon}\\sim\\mathcal{N}(0,\\mathbf{\\mathbf{I}}\_{\\mathbf{\\mathbf{m}}})}\\lbrack\\mathbf{\\epsilon} \\cdot F(\\mathbf{\\mathbf{\\theta}} + \\sigma \\cdot \\mathbf{\\epsilon})\\rbrack} \\\\ \\end{array}$$  

现在我们提出了一种基于采样的算法来解决 MDP。上述公式有助于通过采样多个 **ϵ**（每个 **ϵ** 代表一个 *策略* *π*[**θ** + *σ* ⋅ **ϵ**]），并在大量（*n*）个 **ϵ** 样本上对 **ϵ** ⋅ *F*(**θ** + *σ* ⋅ **ϵ**) 进行平均来估计 *期望回报* 的梯度。

请注意，评估 *F*(**θ** + *σ* ⋅ **ϵ**) 涉及为给定的采样 **ϵ** 运行一个 episode，并获得该 episode 的 *回报* *F*(**θ** + *σ* ⋅ **ϵ**)。因此，我们有 *n* 个 **ϵ** 值，*nPolicies* *π*[**θ** + *σ* ⋅ **ϵ**]，和 *nReturns* *F*(**θ** + *σ* ⋅ **ϵ**)。

给定梯度估计，我们沿着这个梯度方向更新 **θ**，这反过来导致 **ϵ** 的新样本（新的 *Policies* *π*[**θ** + *σ* ⋅ **ϵ**] 集合），该过程重复直到 𝔼[**ϵ** ∼ 𝒩(0, **I**[**m**])]\[*F*(**θ** + *σ* ⋅ **ϵ**)\] 被最大化。

算法的关键输入是：

*   学习率（SGD 步长）*α*

*   标准差 *σ*

*   参数向量 **θ**[**0**] 的初始值

有了这些输入，对于每次迭代 *t* = 0, 1, 2, …，算法执行以下步骤：

*   采样 **ϵ**[**1**],**ϵ**[**2**],…**ϵ**[**n**] ∼ 𝒩(0, **I**[**m**])。

*   计算回报 *F*[*i*]←*F*(**θ**[**t**]+*σ*⋅**ϵ**[**i**])，其中 *i* = 1, 2, …, *n*。

*   $\\left. \\mathbf{\\mathbf{\\theta}}\_{\\mathbf{\\mathbf{t}} + \\mathbf{1}}\\leftarrow\\mathbf{\\mathbf{\\theta}}\_{\\mathbf{\\mathbf{t}}} + \\frac{\\alpha}{n\\sigma}{\\sum\\limits\_{i = 1}^{n}\\mathbf{\\epsilon}\_{\\mathbf{\\mathbf{i}}}} \\cdot F\_{i} \\right.$

