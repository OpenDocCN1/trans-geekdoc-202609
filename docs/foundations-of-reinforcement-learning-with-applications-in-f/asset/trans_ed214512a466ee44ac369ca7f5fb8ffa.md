

$$\\begin{array}{r} {{\\int\_{t}^{T}e^{- \\rho(s - t)}} \\cdot \\frac{c\_{s}^{1 - \\gamma}}{1 - \\gamma} \\cdot ds + \\frac{e^{- \\rho(T - t)} \\cdot \\epsilon^{\\gamma} \\cdot W\_{T}^{1 - \\gamma}}{1 - \\gamma}} \\\\ \\end{array}$$  

我们的目标是找到 `Policy` :(`t`,`W`[*t*])→(`π`[*t*],`c`[*t*])，以最大化 `Expected Return`。请注意重要约束：`c`[*t*] ≥ 0，但 `π`[*t*] 是无约束的。

我们的第一步是写出汉密尔顿-雅可比-贝尔曼（HJB）方程（即连续时间中贝尔曼最优性方程的类比）。我们将最优值函数表示为 `V`^(\*)，使得时间 `t` 时财富 `W`[*t*] 的最优值为 `V`^(\*)(`t`, `W`[*t*])。请注意，与 [第 5 章](#chapter5.xhtml) 中 [第 5.13 节](#chapter5.xhtml#sec5_13) 不同，在那里我们将最优值函数表示为时间索引序列 `V`[*t*]^(\*)( ⋅ )，这里我们将 `t` 作为 `V`^(\*) 的显式函数参数。这是因为在连续时间设置中，我们关注最优值函数的时间微分。[附录 D](#appD.xhtml#appD) 提供了通用 HJB 表述的推导（[附录 D](#appD.xhtml#appD) 中的方程 (D.1)）——这个通用 HJB 方程在此特化为如下形式：

$$\\begin{array}{r} {\\max\_{\\pi\_{t},c\_{t}}\\left\\{ \\mathbb{E}\_{t}\\lbrack dV^{\*}(t,W\_{t}) + \\frac{c\_{t}^{1 - \\gamma}}{1 - \\gamma} \\cdot dt \\right\\} = \\rho \\cdot V^{\*}(t,W\_{t}) \\cdot dt} \\\\ \\end{array}$$  

(8.2)

现在对 `dV`^(\*) 使用伊托引数，去掉 `dz`[*t*] 项（因为它是鞅），并两边同时除以 `dt`，得到任何 0 ≤ `t` < `T` 的偏微分形式 HJB 方程，如下所示（这种变换的通用形式出现在 [附录 D](#appD.xhtml#appD) 中的方程 (D.2)）：

$$\\begin{array}{r} {\\max\_{\\pi\_{t},c\_{t}}\\left\\{ \\frac{\\partial V^{\*}}{\\partial t} + \\frac{\\partial V^{\*}}{\\partial W\_{t}} \\cdot ((\\pi\_{t}(\\mu - r) + r)W\_{t} - c\_{t}) + \\frac{\\partial^{2}V^{\*}}{\\partial W\_{t}{}^{2}} \\cdot \\frac{\\pi\_{t}^{2} \\cdot \\sigma^{2} \\cdot W\_{t}^{2}}{2} + \\frac{c\_{t}^{1 - \\gamma}}{1 - \\gamma} \\right\\} = \\rho \\cdot V^{\*}(t,W\_{t})} \\\\ \\end{array}$$  

(8.3)

这个 HJB 方程受以下终端条件约束：

$$\\begin{array}{r} {V^{\*}(T,W\_{T}) = \\epsilon^{\\gamma} \\cdot \\frac{W\_{T}^{1 - \\gamma}}{1 - \\gamma}} \\\\ \\end{array}$$  

让我们将方程 (8.3) 更简洁地写为：

$$\\begin{array}{r} {\\max\_{\\pi\_{t},c\_{t}}\\Phi(t,W\_{t};\\pi\_{t},c\_{t}) = \\rho \\cdot V^{\*}(t,W\_{t})} \\\\ \\end{array}$$  

(8.4)

值得再次强调的是，我们正在处理约束 `W`[*t*] > 0、`c`[*t*] ≥ 0，适用于 0 ≤ `t` < `T`。

为了找到最优 `π`[*t*]^(\*)、`c`[*t*]^(\*)，我们对 `Φ`(`t`, `W`[*t*]; `π`[*t*], `c`[*t*]) 分别对 `π`[*t*] 和 `c`[*t*] 求偏导数，并令其等于 0（Φ 的一阶条件）。Φ 对 `π`[*t*] 的偏导数为：

$$\\begin{array}{r} {(\\mu - r) \\cdot \\frac{\\partial V^{\*}}{\\partial W\_{t}} + \\frac{\\partial^{2}V^{\*}}{\\partial W\_{t}{}^{2}} \\cdot \\pi\_{t} \\cdot \\sigma^{2} \\cdot W\_{t} = 0} \\\\ \\end{array}$$  

$$\\begin{array}{r} \\left. \\Rightarrow\\pi\_{t}^{\*} = \\frac{- \\frac{\\partial V^{\*}}{\\partial W\_{t}} \\cdot (\\mu - r)}{\\frac{\\partial^{2}V^{\*}}{\\partial W\_{t}{}^{2}} \\cdot \\sigma^{2} \\cdot W\_{t}} \\right. \\\\ \\end{array}$$  

(8.5)

Φ 对 `c`[*t*] 的偏导数为：

$$\\begin{array}{r} {- \\frac{\\partial V^{\*}}{\\partial W\_{t}} + {(c\_{t}^{\*})}^{- \\gamma} = 0} \\\\ \\end{array}$$  

$$\\begin{array}{r} \\left. \\Rightarrow c\_{t}^{\*} = {(\\frac{\\partial V^{\*}}{\\partial W\_{t}})}^{\\frac{- 1}{\\gamma}} \\right. \\\\ \\end{array}$$  

(8.6)

现在将 `π`[*t*]^(\*)（来自方程 (8.5)）和 `c`[*t*]^(\*)（来自方程 (8.6)）代入 `Φ`(`t`, `W`[*t*]; `π`[*t*], `c`[*t*])（在方程 (8.3) 中），并令其等于 `ρ` ⋅ `V`^(\*)(`t`, `W`[*t*])。这给出了最优值函数偏微分方程（PDE）：

$$\\begin{array}{r} {\\frac{\\partial V^{\*}}{\\partial t} - \\frac{{(\\mu - r)}^{2}}{2\\sigma^{2}} \\cdot \\frac{{(\\frac{\\partial V^{\*}}{\\partial W\_{t}})}^{2}}{\\frac{\\partial^{2}V^{\*}}{\\partial W\_{t}{}^{2}}} + \\frac{\\partial V^{\*}}{\\partial W\_{t}} \\cdot r \\cdot W\_{t} + \\frac{\\gamma}{1 - \\gamma} \\cdot {(\\frac{\\partial V^{\*}}{\\partial W\_{t}})}^{\\frac{\\gamma - 1}{\\gamma}} = \\rho \\cdot V^{\*}(t,W\_{t})} \\\\ \\end{array}$$  

(8.7)

这个 PDE 的边界条件为：

$$\\begin{array}{r} {V^{\*}(T,W\_{T}) = \\epsilon^{\\gamma} \\cdot \\frac{W\_{T}^{1 - \\gamma}}{1 - \\gamma}} \\\\ \\end{array}$$  

在以下假设下，Φ 的二阶条件得到满足：对所有 0 ≤ `t` < `T`，均有 $c\_{t}^{\*} > 0,W\_{t} > 0,\\frac{\\partial^{2}V^{\*}}{\\partial W\_{t}{}^{2}} < 0$（我们将在后续推导的解中证明这些条件均满足），且对于凹函数 `U`( ⋅ )，即 `γ` > 0。

接下来，我们希望将 PDE (8.7) 简化为普通微分方程（ODE），以便求解（更简单的）ODE。为此，我们假设一个关于时间的确定性函数（`f`）的猜测解：

$$\\begin{array}{r} {V^{\*}(t,W\_{t}) = f{(t)}^{\\gamma} \\cdot \\frac{W\_{t}^{1 - \\gamma}}{1 - \\gamma}} \\\\ \\end{array}$$  

(8.8)

那么，

$$\\begin{array}{r} {\\frac{\\partial V^{\*}}{\\partial t} = \\gamma \\cdot f{(t)}^{\\gamma - 1} \\cdot f^{\\prime}(t) \\cdot \\frac{W\_{t}^{1 - \\gamma}}{1 - \\gamma}} \\\\ \\end{array}$$  

(8.9)

$$\\begin{array}{r} {\\frac{\\partial V^{\*}}{\\partial W\_{t}} = f{(t)}^{\\gamma} \\cdot W\_{t}^{- \\gamma}} \\\\ \\end{array}$$  

(8.10)

$$\\begin{array}{r} {\\frac{\\partial^{2}V^{\*}}{\\partial W\_{t}{}^{2}} = - f{(t)}^{\\gamma} \\cdot \\gamma \\cdot W\_{t}^{- \\gamma - 1}} \\\\ \\end{array}$$  

(8.11)

将猜测解代入 PDE，我们得到简单的 ODE：

$$\\begin{array}{r} {f^{\\prime}(t) = \\nu \\cdot f(t) - 1} \\\\ \\end{array}$$  

(8.12)

其中

$$\\begin{array}{r} {\\nu = \\frac{\\rho - (1 - \\gamma) \\cdot (\\frac{{(\\mu - r)}^{2}}{2\\sigma^{2}\\gamma} + r)}{\\gamma}} \\\\ \\end{array}$$  

我们注意到，遗赠函数 `B`(`T`) = *ϵ*^(`γ`) 在拟合 `t` = `T` 时的猜测解方面非常方便。这意味着这个 ODE 的边界条件是：`f`(`T`) = *ϵ*。因此，这个 ODE 连同这个边界条件有一个足够简单的解，如下所示：

$$\\begin{array}{l} {f(t) = \\left\\{ \\begin{array}{ll} \\frac{1 + (\\nu\\epsilon - 1) \\cdot e^{- \\nu(T - t)}}{\\nu} & {\\text{for~}\\nu \\neq 0} \\\\ {T - t + \\epsilon} & {\\text{for~}\\nu = 0} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

(8.13)

将 `V`^(\*)（来自方程 (8.8)）及其偏导数（来自方程 (8.9)、(8.10) 和 (8.11)）代入方程 (8.5) 和 (8.6)，我们得到：

$$\\begin{array}{r} {\\pi^{\*}(t,W\_{t}) = \\frac{\\mu - r}{\\sigma^{2}\\gamma}} \\\\ \\end{array}$$  

(8.14)

$$\\begin{array}{l} {c^{\*}(t,W\_{t}) = \\frac{W\_{t}}{f(t)} = \\left\\{ \\begin{array}{ll} \\frac{\\nu \\cdot W\_{t}}{1 + (\\nu\\epsilon - 1) \\cdot e^{- \\nu(T - t)}} & {\\text{for~}\\nu \\neq 0} \\\\ \\frac{W\_{t}}{T - t + \\epsilon} & {\\text{for~}\\nu = 0} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

(8.15)

最后，将 `f`(`t`) 的解（方程 (8.13)）代入方程 (8.8)，我们得到：

$$\\begin{array}{l} {V^{\*}(t,W\_{t}) = \\left\\{ \\begin{array}{ll} {\\frac{{(1 + (\\nu\\epsilon - 1) \\cdot e^{- \\nu(T - t)})}^{\\gamma}}{\\nu^{\\gamma}} \\cdot \\frac{W\_{t}^{1 - \\gamma}}{1 - \\gamma}} & {\\text{for~}\\nu \\neq 0} \\\\ \\frac{{(T - t + \\epsilon)}^{\\gamma} \\cdot W\_{t}^{1 - \\gamma}}{1 - \\gamma} & {\\text{for~}\\nu = 0} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$  

(8.16)

