

$$\\begin{array}{r} {df(t,Y\_{t}) = \\frac{\\partial f}{\\partial t} \\cdot dt + \\frac{\\partial f}{\\partial Y\_{t}} \\cdot (\\mu\_{t} \\cdot dt + \\sigma\_{t} \\cdot dz\_{t}) + \\frac{1}{2} \\cdot \\frac{\\partial^{2}f}{\partial Y\_{t}{}^{2}} \\cdot {(\\mu\_{t} \\cdot dt + \\sigma\_{t} \\cdot dz\_{t})}^{2} + \\ldots} \\\\ \\end{array}$$

接下来，我们使用规则：`(*dt*)² = 0`, `dt ⋅ dz[t] = 0`, `(*dz[t*])² = dt` 来得到 `Ito's Lemma`：

$$\\begin{array}{r} {df(t,Y\_{t}) = (\\frac{\\partial f}{\\partial t} + \\mu\_{t} \\cdot \\frac{\\partial f}{\\partial Y\_{t}} + \\frac{\\sigma\_{t}^{2}}{2} \\cdot \\frac{\\partial^{2}f}{\partial Y\_{t}{}^{2}}) \\cdot dt + \\sigma\_{t} \\cdot \\frac{\\partial f}{\\partial Y\_{t}} \\cdot dz\_{t}} \\\\ \\end{array}$$

(C.1)

`Ito's Lemma` 描述了关于 `Ito Process` `Y` 的函数 `f` 的随机过程，其表达式涉及 `f` 的偏导数，以及定义 `Y` 的漂移 `μ` 和分散 `σ` 过程。

如果我们将 `Y` 推广为 `n` 维随机过程（作为列向量），其中 `μ[t]` 为 `n` 维（随机）列向量，`σ[t]` 为 `n × m`（随机）矩阵，`z[t]` 为 `m` 个独立标准布朗运动组成的 `m` 维向量（如下所示）：

$$\\begin{array}{r} {d\\mathbf{\\mathbf{Y}}\_{t} = \\mathbf{\\mathbf{\\mu}}\_{t} \\cdot dt + \\mathbf{\\mathbf{\\sigma}}\_{t} \\cdot d\\mathbf{\\mathbf{z}}\_{t}} \\\\ \\end{array}$$

那么我们就得到了 `Ito's Lemma` 的多变量版本，如下所示：

$$\\begin{array}{r} {df(t,\\mathbf{\\mathbf{Y}}\_{t}) = (\\frac{\\partial f}{\\partial t} + {(\\nabla\_{\\mathbf{\\mathbf{Y}}}f)}^{T} \\cdot \\mathbf{\\mathbf{\\mu}}\_{t} + \\frac{1}{2}Tr\\lbrack\\mathbf{\\mathbf{\\sigma}}\_{t}^{T} \\cdot (\\Delta\_{\\mathbf{\\mathbf{Y}}}f) \\cdot \\mathbf{\\mathbf{\\sigma}}\_{t}\\rbrack) \\cdot dt + {(\\nabla\_{\\mathbf{\\mathbf{Y}}}f)}^{T} \\cdot \\mathbf{\\mathbf{\\sigma}}\_{t} \\cdot d\\mathbf{\\mathbf{z}}\_{t}} \\\\ \\end{array}$$

(C.2)

其中，符号 `∇` 表示函数的梯度，符号 `Δ` 表示函数的黑塞矩阵，符号 `Tr` 表示矩阵的迹。

接下来，我们介绍两种常见的 `Ito` 过程，并使用 `Ito's Lemma` 求解由这些 `Ito` 过程表示的随机微分方程：

## C.7 对数正态过程

考虑一个随机过程 `x`，其形式如下，描述为以下 `Ito` 过程：

$$\\begin{array}{r} {dx\_{t} = \\mu(t) \\cdot x\_{t} \\cdot dt + \\sigma(t) \\cdot x\_{t} \\cdot dz\_{t}} \\\\ \\end{array}$$

注意，这里 `z` 是标准（一维）布朗运动，`μ, σ` 是时间 `t` 的确定性函数。通过定义 `x[t]` 的适当函数并应用 `Ito's Lemma`，可以轻松求解，如下所示：

$$\\begin{array}{r} {y\_{t} = \\log(x\_{t})} \\\\ \\end{array}$$

对 `y[t]` 相对于 `x[t]` 应用 `Ito's Lemma`，我们得到：

$$\\begin{aligned} {dy\_{t}} & {= (\\mu(t) \\cdot x\_{t} \\cdot \\frac{1}{x\_{t}} - \\frac{\\sigma^{2}(t) \\cdot x\_{t}^{2}}{2} \\cdot \\frac{1}{x\_{t}^{2}}) \\cdot dt + \\sigma(t) \\cdot x\_{t} \\cdot \\frac{1}{x\_{t}} \\cdot dz\_{t}} \\\\ & {= (\\mu(t) - \\frac{\\sigma^{2}(t)}{2}) \\cdot dt + \\sigma(t) \\cdot dz\_{t}} \\\\ \\end{aligned}$$

所以，

$$\\begin{array}{r} {y\_{T} = y\_{S} + {\\int\_{S}^{T}{(\\mu(t) - \\frac{\\sigma^{2}(t)}{2})}} \\cdot dt + {\\int\_{S}^{T}\\sigma}(t) \\cdot dz\_{t}} \\\\ \\end{array}$$

$$\\begin{array}{r} {x\_{T} = x\_{S} \\cdot e^{{\\int\_{S}^{T}{(\\mu(t) - \\frac{\\sigma^{2}(t)}{2})}} \\cdot dt + {\\int\_{S}^{T}\\sigma}(t) \\cdot dz\_{t}}} \\\\ \\end{array}$$

`x[T]|x[S]` 服从对数正态分布，即，

$$\\begin{array}{r} {\\left. y\_{T} = \\log(x\_{T}) \\right.\\sim\\mathcal{N}(\\log(x\_{S}) + {\\int\_{S}^{T}{(\\mu(t) - \\frac{\\sigma^{2}(t)}{2})}} \\cdot dt,{\\int\_{S}^{T}\\sigma^{2}}(t) \\cdot dt)} \\\\ \\end{array}$$

$$\\begin{array}{r} {E\\lbrack x\_{T}|x\_{S}\\rbrack = x\_{S} \\cdot e^{{\\int\_{S}^{T}\\mu}(t) \\cdot dt}} \\\\ \\end{array}$$

$$\\begin{array}{r} {E\\lbrack x\_{T}^{2}|x\_{S}\\rbrack = x\_{S}^{2} \\cdot e^{{\\int\_{S}^{T}{(2\\mu(t) + \\sigma^{2}(t))}} \\cdot dt}} \\\\ \\end{array}$$

$$\\begin{array}{r} {Variance\\lbrack x\_{T}|x\_{S}\\rbrack = E\\lbrack x\_{T}^{2}|x\_{S}\\rbrack - {(E\\lbrack x\_{T}|x\_{S}\\rbrack)}^{2} = x\_{S}^{2} \\cdot e^{{\\int\_{S}^{T}2}\\mu(t) \\cdot dt} \\cdot (e^{{\\int\_{S}^{T}\\sigma^{2}}(t) \\cdot dt} - 1)} \\\\ \\end{array}$$

`μ(t) = μ`（常数）和 `σ(t) = σ`（常数）的特例是一种非常常见的 `Ito` 过程，广泛应用于金融/经济学（因其简单性、可处理性以及实用性），被称为几何布朗运动，以反映该过程的随机增量（`σ ⋅ x[t] ⋅ dz[t]`）与过程水平 `x[t]` 成倍数关系。如果我们考虑这个特例，我们得到：

$$\\begin{array}{r} {\\left. y\_{T} = \\log(x\_{T}) \\right.\\sim\\mathcal{N}(\\log(x\_{S}) + (\\mu - \\frac{\\sigma^{2}}{2})(T - S),\\sigma^{2}(T - S))} \\\\ \\end{array}$$

$$\\begin{array}{r} {E\\lbrack x\_{T}|x\_{S}\\rbrack = x\_{S} \\cdot e^{\\mu(T - S)}} \\\\ \\end{array}$$

$$\\begin{array}{r} {Variance\\lbrack x\_{T}|x\_{S}\\rbrack = x\_{S}^{2} \\cdot e^{2\\mu(T - S)} \\cdot (e^{\\sigma^{2}(T - S)} - 1)} \\\\ \\end{array}$$

## C.8 均值回归过程

现在我们考虑一个随机过程 `x`，其形式如下，描述为以下 `Ito` 过程：

$$\\begin{array}{r} {dx\_{t} = \\mu(t) \\cdot x\_{t} \\cdot dt + \\sigma(t) \\cdot dz\_{t}} \\\\ \\end{array}$$

与前一节中的过程一样，`z` 是标准（一维）布朗运动，`μ, σ` 是时间 `t` 的确定性函数。通过定义 `x[t]` 的适当函数并应用 `Ito's Lemma`，可以轻松求解，如下所示：

$$\\begin{array}{r} {y\_{t} = x\_{t} \\cdot e^{- {\\int\_{0}^{t}\\mu}(u) \\cdot du}} \\\\ \\end{array}$$

对 `y[t]` 相对于 `x[t]` 应用 `Ito's Lemma`，我们得到：

$$\\begin{aligned} {dy\_{t}} & {= ( - x\_{t} \\cdot \\mu(t) \\cdot e^{- {\\int\_{0}^{t}\\mu}(u) \\cdot du} + \\mu(t) \\cdot x\_{t} \\cdot e^{- {\\int\_{0}^{t}\\mu}(u) \\cdot du}) \\cdot dt + \\sigma(t) \\cdot e^{- {\\int\_{0}^{t}\\mu}(u) \\cdot du} \\cdot dz\_{t}} \\\\ & {= \\sigma(t) \\cdot e^{- {\\int\_{0}^{t}\\mu}(u) \\cdot du} \\cdot dz\_{t}} \\\\ \\end{aligned}$$

因此，过程 `y` 是一个鞅。使用 `Ito Isometry`，我们得到：

$$\\begin{array}{r} {\\left. y\_{T} \\right.\\sim\\mathcal{N}(y\_{S},{\\int\_{S}^{T}\\sigma^{2}}(t) \\cdot e^{- {\\int\_{0}^{t}2}\\mu(u) \\cdot du} \\cdot dt)} \\\\ \\end{array}$$

因此，

$$\\begin{array}{r} {\\left. x\_{T} \\right.\\sim\\mathcal{N}(x\_{S} \\cdot e^{{\\int\_{S}^{T}\\mu}(t) \\cdot dt},e^{{\\int\_{0}^{T}2}\\mu(t) \\cdot dt} \\cdot {\\int\_{S}^{T}\\sigma^{2}}(t) \\cdot e^{- {\\int\_{0}^{t}2}\\mu(u) \\cdot du} \\cdot dt)} \\\\ \\end{array}$$

我们称这个过程为“均值回归”，因为当 `μ(t)` 为负时，该过程会以与 `−μ(t)` 成正比的速度以及与距基准线距离成正比的速度被“拉”到基准水平 0（因此我们说该过程回归到基准 0，且距离基准越远，均值回归强度越大）。如果 `μ(t)` 为正，则我们说该过程是“均值偏离”，以表示它被拉离基准水平 0。

`μ(t) = μ`（常数）和 `σ(t) = σ`（常数）的特例是一种相当常见的 `Ito` 过程（同样因其简单性、可处理性以及实用性），被称为奥恩斯坦-乌伦贝克过程，其均值（基准）水平设为 0。如果我们考虑这个特例，我们得到：

$$\\begin{array}{r} {\\left. x\_{T} \\right.\\sim\\mathcal{N}(x\_{S} \\cdot e^{\\mu(T - S)},\\frac{\\sigma^{2}}{2\\mu} \\cdot (e^{2\\mu(T - S)} - 1))} \\\\ \\end{array}$$

