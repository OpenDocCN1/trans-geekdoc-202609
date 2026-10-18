

最后，我们编写一个名为 `argmax` 的方法，它接收一个 `x` 值的可迭代对象作为输入，并返回使 𝔼[*f*(*x*; *w*)]\[*y*\] 最大化的 `x` 值。

![](images/comp06_5.jpg)

上述 `FunctionApprox` 和 `Gradient` 的代码位于文件 `rl/function_approx.py` 中。`rl/function_approx.py` 还包含一些便捷方法：`__add__`（用于将两个 `FunctionApprox` 相加）、`__mul__`（用于将 `FunctionApprox` 与实数标量相乘）以及 `__call__`（用于将 `FunctionApprox` 对象在语法上视为一个接收 `x: X` 作为输入的函数，本质上是对单个 `x` 值调用 `evaluate` 的简写）。`__add__` 和 `__mul__` 旨在对函数近似的内部参数 `w` 执行逐元素加法和标量乘法（有关将函数近似视为向量空间的说明，请参见 [附录 F](#appF.xhtml#appF)）。同样，它还为 `Gradient` 类包含 `__add__` 和 `__mul__` 方法，这些方法只是将调用委托给 `Gradient` 内部 `FunctionApprox` 的 `__add__` 和 `__mul__` 方法，并且它还包含 `zero` 方法，该方法返回一个 `Gradient`，该梯度对每个参数值均为零。

现在我们准备好介绍一种具体但简单的函数近似——线性函数近似的情况。

## 6.2 线性函数近似

我们定义一组特征函数

$$\\begin{array}{r} \\left. \\phi\_{j}:\\mathcal{X}\\rightarrow{\\mathbb{R}}\\text{~for~each~}j = 1,2,\\ldots,m \\right. \\\\ \\end{array}$$  

并定义 `ϕ`:𝒳→ℝ^(*m*) 为：

$$\\begin{array}{r} {\\phi(x) = (\\phi\_{1}(x),\\phi\_{2}(x),\\ldots,\\phi\_{m}(x))\\text{~for~all~}x \\in \\mathcal{X}} \\\\ \\end{array}$$  

我们将 `ϕ`(*x*) 视为所有 *x* ∈ 𝒳 的列向量。

对于线性函数近似，内部参数 `w` 表示为权重列向量 **w** = (*w*[1], *w*[2], …, *w*[*m*]) ∈ ℝ^(*m*)。线性函数近似基于以下假设：*y*|*x* 服从均值为

$$\\begin{array}{r} {\\mathbb{E}\_{M}\\lbrack y|x\\rbrack = {\\sum\\limits\_{j = 1}^{m}\\phi\_{j}}(x) \\cdot w\_{j} = \\phi{(x)}^{T} \\cdot \\mathbf{\\mathbf{w}}} \\\\ \\end{array}$$  

且方差 *σ*² 为常数的高斯分布，即，

$$\\begin{array}{r} {{\\mathbb{P}}\\lbrack y|x\\rbrack = f(x;\\mathbf{\\mathbf{w}})(y) = \\frac{1}{\\sqrt{2\\pi\\sigma^{2}}} \\cdot e^{- \\frac{{(y - \\phi{(x)}^{T} \\cdot \\mathbf{\\mathbf{w}})}^{2}}{2\\sigma^{2}}}} \\\\ \\end{array}$$  

因此，对于给定的数据点集合 \[*x*[*i*], *y*[*i*]|1 ≤ *i* ≤ *n*\]，交叉熵损失函数（忽略与 *σ*² 相关的常数项）定义为：

$$\\begin{array}{r} {\\mathcal{L}(\\mathbf{\\mathbf{w}}) = \\frac{1}{2n} \\cdot {\\sum\\limits\_{i = 1}^{n}{(\\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}} - y\_{i})}^{2}}} \\\\ \\end{array}$$  

请注意，此损失函数与线性（关于 **w**）预测 *ϕ*(*x*[*i*])^(*T*) ⋅ **w** 相对于与预测值 *x*[*i*] 关联的响应值 *y*[*i*] 的均方误差在所有 1 ≤ *i* ≤ *n* 上是相同的。

如果我们包含 *L*² 正则化（其中 *λ* 为正则化系数），则正则化损失函数为：

$$\\begin{array}{r} {\\mathcal{L}(\\mathbf{\\mathbf{w}}) = \\frac{1}{2n}({\\sum\\limits\_{i = 1}^{n}{(\\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}} - y\_{i})}^{2}}) + \\frac{1}{2} \\cdot \\lambda \\cdot |\\mathbf{\\mathbf{w}}|^{2}} \\\\ \\end{array}$$  

ℒ(**w**) 关于 **w** 的梯度为：

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{w}}}\\mathcal{L}(\\mathbf{\\mathbf{w}}) = \\frac{1}{n} \\cdot ({\\sum\\limits\_{i = 1}^{n}\\phi}(x\_{i}) \\cdot (\\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}} - y\_{i})) + \\lambda \\cdot \\mathbf{\\mathbf{w}}} \\\\ \\end{array}$$  

我们之前曾说过，对于我们想要实现的每个具体函数近似，如果目标函数 `Obj`(*x*[*i*], *y*[*i*]) 是交叉熵损失函数，我们可以识别一个模型计算值 `Out`(*x*[*i*])（模型的输出或模型的中间计算结果），使得 $\\frac{\\partial Obj(x\_{i},y\_{i})}{\\partial Out(x\_{i})}$ 等于预测误差 𝔼[*M*]\[*y*|*x*[*i*]\] − *y*[*i*]（对于每个训练数据点 (*x*[*i*], *y*[*i*])），并且我们可以提出一个数值算法来计算 ∇[*w*]`Out`(*x*[*i*])，这样通过链式法则，我们就能得到所需的梯度 ∇[*w*]`Obj`(*x*[*i*], *y*[*i*])（不带正则化）。在线性函数近似的情况下，模型计算值 `Out`(*x*[*i*]) 简单地是预测变量 `x`[*i*] 的模型预测值，即，

$$\\begin{array}{r} {Out(x\_{i}) = \\mathbb{E}\_{M}\\lbrack y|x\_{i}\\rbrack = \\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}}} \\\\ \\end{array}$$  

这一点可以通过以下事实得到验证：当 `Obj`(*x*[*i*], *y*[*i*]) 设置为交叉熵损失函数 ℒ(**w**)，且 `Out`(*x*[*i*]) 设置为模型预测值 *ϕ*(*x*[*i*])^(*T*) ⋅ **w**（针对训练数据点 (*x*[*i*], *y*[*i*])）时，

$$\\begin{array}{r} {\\frac{\\partial Obj(x\_{i},y\_{i})}{\\partial Out(x\_{i})} = \\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}} - y\_{i} = \\mathbb{E}\_{M}\\lbrack y|x\_{i}\\rbrack - y\_{i}} \\\\ \\end{array}$$  

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{w}}}Out(x\_{i}) = \\nabla\_{\\mathbf{\\mathbf{w}}}(\\phi{(x\_{i})}^{T} \\cdot \\mathbf{\\mathbf{w}}) = \\phi(x\_{i})} \\\\ \\end{array}$$  

我们可以通过梯度下降法（对 **w** 的变化与 ℒ(**w**) 关于 **w** 的梯度估计成比例）进行增量估计来求解 **w**^(\*)。如果在时间 *t* 时的 (*x*[*t*], *y*[*t*]) 数据为：

$$\\begin{array}{r} {\\lbrack(x\_{t,i},y\_{t,i})|1 \\leq i \\leq n\_{t}\\rbrack,} \\\\ \\end{array}$$  

那么在时间 *t* 时的梯度估计 𝒢[(*x*[*t*], *y*[*t*])](**w**[*t*]) 由以下公式给出：

$$\\begin{array}{r} {\\mathcal{G}\_{(x\_{t},y\_{t})}(\\mathbf{\\mathbf{w}}\_{t}) = \\frac{1}{n} \\cdot ({\\sum\\limits\_{i = 1}^{n\_{t}}\\phi}(x\_{t,i}) \\cdot (\\phi{(x\_{t,i})}^{T} \\cdot \\mathbf{\\mathbf{w}}\_{t} - y\_{t,i})) + \\lambda \\cdot \\mathbf{\\mathbf{w}}\_{t}} \\\\ \\end{array}$$  

这可以解释为迭代 *t* 中数据上的特征向量 *ϕ*(*x*[*t*, *i*]) 的平均值，这些向量由（标量）线性预测误差 *ϕ*(*x*[*t*, *i*])^(*T*) ⋅ **w**[*t*] − *y*[*t*, *i*] 加权（加上正则化项 *λ* ⋅ **w**[*t*]）。

然后，权重向量 **w** 的更新由以下公式给出：

$$\\begin{array}{r} {\\mathbf{\\mathbf{w}}\_{t + 1} = \\mathbf{\\mathbf{w}}\_{t} - \\alpha\_{t} \\cdot \\mathcal{G}\_{(x\_{t},y\_{t})}(\\mathbf{\\mathbf{w}}\_{t})} \\\\ \\end{array}$$  

其中 `α`[*t*] 是时间 *t* 时梯度下降的学习率。为了便于数值收敛，我们要求 `α`[*t*] 是时间 *t* 的适当函数。有许多数值算法可以实现 `α`[*t*] 的适当时间轨迹。我们将采用其中一种数值算法——ADAM（[Kingma and Ba 2015](#bib01.xhtml#refbib_35)），我们不仅将其用于线性函数近似，还将在后续用于深度神经网络函数近似。在编写线性函数近似的代码之前，我们需要先编写一些辅助代码来实现 ADAM 梯度下降算法。

