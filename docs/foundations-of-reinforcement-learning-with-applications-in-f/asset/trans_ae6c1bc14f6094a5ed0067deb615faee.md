

$$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{\\theta}} = \\alpha\_{\\mathbf{\\mathbf{\\theta}}} \\cdot \\gamma^{t} \\cdot (\\nabla\_{\\mathbf{\\mathbf{\\theta}}}\\log\\pi(S\_{t};A\_{t};\\mathbf{\\mathbf{\\theta}})) \\cdot (R\_{t + 1} + \\gamma \\cdot V(S\_{t + 1};\\mathbf{\\mathbf{v}}) - V(S\_{t};\\mathbf{\\mathbf{v}}))} \\\\ \\end{array}$$

where `α`[`θ`] 是 Policy Mean 函数近似的学习率。

![](images/comp14_12.jpg)

上述代码位于文件 `rl/policy_gradient.py` 中。

同样，我们可以使用资格迹（即 TD(`λ`)）实现 Actor-Critic 算法，既用于状态-值函数近似，也用于策略均值函数近似。每次原子体验后，状态-值函数近似的参数 `v` 和策略均值函数近似的参数 `θ` 的更新公式如下：

$$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{v}} = \\alpha\_{\\mathbf{\\mathbf{v}}} \\cdot (R\_{t + 1} + \\gamma \\cdot V(S\_{t + 1};\\mathbf{\\mathbf{v}}) - V(S\_{t};\\mathbf{\\mathbf{v}})) \\cdot \\mathbf{\\mathbf{E}}\_{\\mathbf{\\mathbf{v}}}} \\\\ \\end{array}$$

$$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{\\theta}} = \\alpha\_{\\mathbf{\\mathbf{\\theta}}} \\cdot (R\_{t + 1} + \\gamma \\cdot V(S\_{t + 1};\\mathbf{\\mathbf{v}}) - V(S\_{t};\\mathbf{\\mathbf{v}})) \\cdot \\mathbf{\\mathbf{E}}\_{\\mathbf{\\mathbf{\\theta}}}} \\\\ \\end{array}$$

其中，资格迹 `E`[`v`] 和 `E`[`θ`] 在每次原子体验后按以下方式更新：

$$\\begin{array}{r} \\left. \\mathbf{\\mathbf{E}}\_{\\mathbf{\\mathbf{v}}}\\leftarrow\\gamma \\cdot \\lambda\_{\\mathbf{\\mathbf{v}}} \\cdot \\mathbf{\\mathbf{E}}\_{\\mathbf{\\mathbf{v}}} + \\nabla\_{\\mathbf{\\mathbf{v}}}V(S\_{t};\\mathbf{\\mathbf{v}}) \\right. \\\\ \\end{array}$$

$$\\begin{array}{r} \\left. \\mathbf{\\mathbf{E}}\_{\\mathbf{\\mathbf{\\theta}}}\\leftarrow\\gamma \\cdot \\lambda\_{\\mathbf{\\mathbf{\\theta}}} \\cdot \\mathbf{\\mathbf{E}}\_{\\mathbf{\\mathbf{\\theta}}} + \\gamma^{t} \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}\\log\\pi(S\_{t},A\_{t};\\mathbf{\\mathbf{\\theta}}) \\right. \\\\ \\end{array}$$

其中，`λ`[`v`] 和 `λ`[`θ`] 分别是状态-值函数近似和策略均值函数近似的 TD(`λ`) 参数。

我们鼓励你在代码中实现使用资格迹的 Actor-Critic 算法。

现在让我们在之前为测试 REINFORCE 而创建的 AssetAllocPG 实例上比较这些方法，即时间步 `T` = 5，`μ` = 13%，`σ` = 20%，`r` = 7%，CARA 系数 `a` = 1.0，每次迹体验开始时的财富概率分布为 𝒩(1.0, 0.1)，以及给定状态下策略概率分布动作的常数标准差 `σ` 为 0.5。`rl/chapter13/asset_alloc_pg.py` 中的 `__main__` 代码在每个 episode 后（共 50,000 个 episode）评估上述实现的每个 PG 算法的策略均值函数近似的起始状态（`t` = 0，`W`[0] = 1.0）的平均动作。然后它绘制了 50,000 个 episode 中起始状态评估平均动作的进度（每个点绘制为 200 个 episode 批次的平均值），以及来自已知闭式解的起始状态最优动作的基准。[图 14.1](#chapter14.xhtml#fig14_1) 显示了该图表，验证了我们关于这些算法偏差和方差的上述观点。

![Figure 14.1 PG 算法的进度](images/fig14_1.jpg)

[图 14.1](#chapter14.xhtml#b14fig14_1) PG 算法的进度

Actor-Critic 方法在 20 世纪 70 年代末和 80 年代开发，但在 90 年代未受到重视。在过去二十年中，Actor-Critic 方法出现了复兴。有关 Actor-Critic 方法的更详细内容，请参阅 Degris、White、Sutton 的论文（[Degris, White, and Sutton 2012](#bib01.xhtml#refbib_24)）。

## 14.7 使用兼容函数近似克服偏差

我们讨论了很多关于减少 PG 算法方差以加快收敛的内容。具体来说，我们讨论了以下作为 Actor-Critic 算法形式的 `Q`^(`π`)(`s`, `a`) 代理，以减少方差。

*   `Q`(`s`, `a`; `w`)

*   `A`(`s`, `a`; `w`, `v`) = `Q`(`s`, `a`; `w`) − `V`(`s`; `v`)

*   `δ`(`s`, `s`^′, `r`; `v`) = `r` + `γ` ⋅ `V`(`s`^′; `v`) − `V`(`s`; `v`)

然而，PG 算法中上述每个 `Q`^(`π`)(`s`, `a`) 代理都存在偏差。在本节中，我们讨论如何克服偏差。克服偏差的基础是一个重要的定理，称为兼容函数近似定理。我们陈述并证明该定理，然后解释如何在 PG 算法中使用它。

此证明最初发表在 Sutton、McAllester、Singh、Mansour 的著名论文《带函数近似的强化学习策略梯度方法》（R. [Sutton et al. 2001](#bib01.xhtml#refbib_63)）中。

这意味着，如果定理的兼容性假设得到满足，我们可以使用评论家函数近似 `Q`(`s`, `a`; `w`[`θ`]^(\*))，同时仍然拥有精确的策略梯度（即，由于使用 Q-值函数的函数近似而没有偏差）。但是，请注意，在实践中，我们遵循 GPI 的精神，不会让当前 `θ` 下的 `Q`(`s`, `a`; `w`) 收敛。相反，我们频繁更新 `w` 和 `θ`，结果证明这在降低偏差方面已经足够好。

启用兼容函数近似的一种简单方法是将 `Q`(`s`, `a`; `w`) 设为线性函数近似，其线性函数近似的特征等于策略函数近似的得分，如下所示：

$$\\begin{array}{r} {Q(s,a;\\mathbf{\\mathbf{w}}) = {\\sum\\limits\_{i = 1}^{m}\\frac{\\partial\\log\\pi(s,a;\\mathbf{\\mathbf{\\theta}})}{\\partial\\theta\_{i}}} \\cdot w\_{i}\\text{~for~all~}s \\in \\mathcal{N},\\text{~for~all~}a \\in \\mathcal{A}} \\\\ \\end{array}$$

这意味着线性函数近似的特征函数 `η`(`s`, `a`) = (`η`[1](`s`, `a`), `η`[2](`s`, ` a`), …, `η`[`m`](`s`, `a`)) 由以下公式给出：

$$\\begin{array}{r} {\\eta\_{i}(s,a) = \\frac{\\partial\\log\\pi(s,a;\\mathbf{\\mathbf{\\theta}})}{\\partial\\theta\_{i}}\\text{~for~all~}s \\in \\mathcal{N},\\text{~for~all~}a \\in \\mathcal{A},\\text{~for~all~}i = 1,\\ldots,m} \\\\ \\end{array}$$

这意味着特征函数 `η` 与得分完全相等。请注意，尽管这里我们假设 `Q`(`s`, `a`; `w`) 是线性函数近似，但策略函数近似 `π`(`s`, `a`; `θ`) 可以更灵活。所要求的只是 `θ` 包含恰好 `m` 个参数（与 `w` 的参数数量 `m` 匹配），并且每个偏导数 $\\frac{\\partial\\log\\pi(s,a;\\mathbf{\\mathbf{\\theta}})}{\\partial\\theta\_{i}}$ 都与线性函数近似 `Q`(`s`, `a`; `w`) 的相应特征 `η`[`i`](`s`, `a`) 对齐。这意味着随着 `θ` 的更新（作为随机梯度上升的结果），`π`(`s`, `a`; `θ`) 更新，因此特征函数 `η`(`s`, `a`) = ∇[`θ`]log `π`(`s`, `a`; `θ`) 更新。这意味着对于给定的 (`s`, `a`) 对，特征向量 `η`(`s`, `a`) 不是常数。相反，对于给定的 (`s`, `a`) 对，特征向量 `η`(`s`, `a`) 随 `θ` 的变化而变化。

如果我们假设在 [第 14.3 节](#chapter14.xhtml#sec14_3) 中描述的有限动作空间的 `π`(`s`, `a`; `θ`) 标准函数近似，则：

$$\\begin{array}{r} {\\mathbf{\\mathbf{\\eta}}(s,a) = \\phi(s,a) - {\\sum\\limits\_{b \\in \\mathcal{A}}\\pi}(s,b;\\mathbf{\\mathbf{\\theta}}) \\cdot \\phi(s,b)\\text{~for~all~}s \\in \\mathcal{N}\\text{~for~all~}a \\in \\mathcal{A}} \\\\ \\end{array}$$

