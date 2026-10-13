
$$
\widehat{\mathbf{\theta}}: \min_{\mathbf{\theta} \in \mathbb{R}^{l}} \left\| \mathbf{\theta} \right\|_{1}, \text{s.t.} \left( \mathbf{y} - X\mathbf{\theta} \right)^{T}\left( \mathbf{y} - X\mathbf{\theta} \right) \leq \epsilon,
$$

给定用户定义的参数 $\rho, \epsilon \geq 0$。公式 [(9.7)](#Chp009_417-462_B9780443292385000159.xhtml#deq9) 称为 LASSO，而 [(9.8)](#Chp009_417-462_B9780443292385000159.xhtml#deq10) 中的公式称为*基追踪去噪*（BPDN）（例如，[15]）。对于特定的 $\lambda, \epsilon$ 和 $\rho$ 的选择，这三种公式是等价的（参见，例如，[14]）。请注意，公式 [(9.6)](#Chp009_417-462_B9780443292385000159.xhtml#deq8) 中最小化的代价函数对应于 [(9.7)](#Chp009_417-462_B9780443292385000159.xhtml#deq9) 中公式的拉格朗日函数。然而，除非 $X$ 的列相互正交，否则这种 $\lambda, \epsilon$ 和 $\rho$ 之间的函数依赖关系很难计算。此外，这种等价性并不一定意味着这三种公式求解起来同样容易或困难。正如我们稍后在本章中将看到的，算法已沿着上述每一种公式开发而成。从现在开始，我们将稍微滥用标准术语，将这三种公式统称为 LASSO 任务，具体公式将从上下文中显而易见，如果未明确说明的话。

我们知道岭回归允许有闭式解，即

$$
\widehat{\mathbf{\theta}}_{R} = \left( X^{T}X + \lambda I \right)^{-1}X^{T}\mathbf{y}.
$$

相比之下，LASSO 则不存在这种情况，其求解需要迭代技术。很容易看出，LASSO 可以表述为一个带有线性不等式的标准凸二次规划问题。确实，我们可以将公式 [(9.6)](#Chp009_417-462_B9780443292385000159.xhtml#deq8) 重写为
