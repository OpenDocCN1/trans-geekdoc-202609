

查看（6.11）可知，还需要计算交叉协方差项 \(\Sigma_{xy}\)（边缘分布 \(p(x)\) 和 \(p(y)\) 已知，且 \(\Sigma_{yx} = \Sigma_{xy}^\top\)）：

\[
\Sigma_{xy} = \mathrm{Cov}[x, y] = \mathbb{E}_{X,Y}[x y^\top] - \mathbb{E}_X[x] \mathbb{E}_Y[y]^\top = \mathbb{E}_{X,Y}[x y^\top] - \mu_x \mu_y^\top,
\]

其中 \(\mu_x\) 和 \(\mu_y\) 已知。因此，还需要计算

\[
\mathbb{E}_{X,Y}[x y^\top] = \mathbb{E}_X[x (A x + b + w)^\top] = \mathbb{E}_X[x x^\top] A^\top + \mathbb{E}_X[x] b^\top = \mathbb{E}_X[x x^\top] A^\top + \mu_x b^\top.
\]

由于

\[
\mu_x \mu_y^\top = \mu_x \mu_x^\top A^\top + \mu_x b^\top
\]

我们可以得到所需的交叉协方差

\[
\Sigma_{xy} = \mathbb{E}_X[x x^\top] A^\top + \mu_x b^\top - \mu_x \mu_x^\top A^\top - \mu_x b^\top = (\mathbb{E}_X[x x^\top] - \mu_x \mu_x^\top) A^\top = \Sigma_x A^\top.
\]

最后，

\[
\mu_{x|y} = \mu_x + \Sigma_x A^\top (A \Sigma_x A^\top + Q)^{-1} (y - A \mu_x - b), \qquad
\Sigma_{x|y} = \Sigma_x - \Sigma_x A^\top (A \Sigma_x A^\top + Q)^{-1} A \Sigma_x.
\]

## 6.13 概率积分变换

给定一个连续随机变量 \(x\)，其累积分布函数为 \(F_X(x)\)，证明随机变量 \(y = F_X(x)\) 服从均匀分布。

**证明。** 我们需要证明 \(Y\) 的累积分布函数定义了一个均匀随机变量的分布。回顾概率公理（第 6.1 节）可知，概率必须是非负的，并且总和（或积分）为 1。因此，\(Y = F_X(x)\) 的所有可能取值构成区间 \([0, 1]\)。对于任意 \(F_X(x)\)，其逆函数 \(F_X^{-1}\) 存在，这是因为我们假设 \(F_X(x)\) 严格单调递增，下面将使用这一点。

给定任意连续随机变量 \(X\)，根据累积分布函数的定义，有

\[
F_Y(y) = P(Y \le y) = P(F_X(x) \le y) \quad \text{(transformation of interest)}
\]
\[
= P(X \le F_X^{-1}(y)) \quad \text{(inverse exists)}
\]
\[
= F_X(F_X^{-1}(y)) \quad \text{(definition of cdf)}
\]
\[
= y,
\]

最后一行成立，是因为 \(F_X(x)\) 与其逆函数复合后得到恒等变换。\(F_Y(y) = y\) 再结合 \(y\) 位于区间 \([0, 1]\) 内这一事实，意味着 \(F_Y(y)\) 是定义在单位区间上的均匀随机变量的累积分布函数。

## 连续优化

### 练习

**7.1** 考虑一元函数

\[
f(x) = x^3 + 6x^2 - 3x - 5.
\]

求出其驻点，并指出它们分别是极大点、极小点还是鞍点。

给定函数 \(f(x)\)，可以得到如下梯度和 Hessian：

\[
\frac{df}{dx} = 3x^2 + 12x - 3
\]
\[
\frac{d^2 f}{dx^2} = 6x + 12.
\]

令梯度为零并求解 \(x\)，即可得到驻点。一种方法是使用二次函数公式，但下面展示如何通过配方法求解。注意到

\[
(x + 2)^2 = x^2 + 4x + 4
\]

因此（将所有项除以 3 后），有

\[
(x^2 + 4x) - 1 = ((x + 2)^2 - 4) - 1.
\]

令其等于零，可以得到

\[
(x + 2)^2 = 5,
\]

因此

\[
x = -2 \pm \sqrt{5}.
\]

将 \(\frac{df}{dx} = 0\) 的解代入 Hessian，可得

\[
\frac{d^2 f}{dx^2}(-2 - \sqrt{5}) \approx -13.4 \quad \text{and} \quad \frac{d^2 f}{dx^2}(-2 + \sqrt{5}) \approx 13.4.
\]

这意味着左侧的驻点是极大点，右侧的驻点是极小点。图 7.1 对此进行了说明。

**7.2** 考虑随机梯度下降的更新方程（公式（7.15））。当使用大小为 1 的小批量时，写出相应的更新公式。

\[
\boldsymbol{\theta}_{i+1} = \boldsymbol{\theta}_i - \gamma_i (\nabla L(\boldsymbol{\theta}_i))^\top = \boldsymbol{\theta}_i - \gamma_i \nabla L_k(\boldsymbol{\theta}_i)^\top
\]

其中，\(k\) 是随机选取的样本的索引。

**7.3** 判断以下陈述是真还是假：

**7.7** 考虑图 7.4 所示的二次规划问题：

\[
\min_{x \in \mathbb{R}^2} \frac{1}{2}
\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}^\top
\begin{bmatrix} 2 & 1 \\ 1 & 4 \end{bmatrix}
\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}
+
\begin{bmatrix} 5 \\ 3 \end{bmatrix}^\top
\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}
\]

约束条件为

\[
\begin{bmatrix} 1 & 0 \\ -1 & 0 \\ 0 & 1 \\ 0 & -1 \end{bmatrix}
\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}
\le
\begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix}.
\]

使用拉格朗日对偶性推导其对偶二次规划问题。

令

\[
Q = \begin{bmatrix} 2 & 1 \\ 1 & 4 \end{bmatrix}, \quad
c = \begin{bmatrix} 5 \\ 3 \end{bmatrix}, \quad
A = \begin{bmatrix} 1 & 0 \\ -1 & 0 \\ 0 & 1 \\ 0 & -1 \end{bmatrix}, \quad
b = \begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix}.
\]

根据（7.45）和（7.52），对偶优化问题为

\[
\max_{\lambda \in \mathbb{R}^4} -\frac{1}{2} \left( \begin{bmatrix} 5 \\ 3 \end{bmatrix} + A^\top \lambda \right)^\top Q^{-1} \left( \begin{bmatrix} 5 \\ 3 \end{bmatrix} + A^\top \lambda \right) - \lambda^\top b
\]

约束条件为 \(\lambda \ge 0\)，

将其展开可得

\[
\max_{\lambda \in \mathbb{R}^4} -\frac{1}{14} \left( 88 + \begin{bmatrix} 33 \\ -35 \\ 1 \\ -3 \end{bmatrix}^\top \lambda + \lambda^\top \begin{bmatrix} 4 & -4 & -1 & 1 \\ -4 & 4 & 1 & -1 \\ -1 & 1 & 2 & -2 \\ 1 & -1 & -2 & 2 \end{bmatrix} \lambda \right)
\]

约束条件为 \(\lambda \ge 0\)。

### 另一种推导方法

写出拉格朗日函数：

\[
L(x, \lambda) = \frac{1}{2} x^\top \begin{bmatrix} 2 & 1 \\ 1 & 4 \end{bmatrix} x + \begin{bmatrix} 5 \\ 3 \end{bmatrix}^\top x + \lambda^\top (A x - b).
\]

对 \(x\) 求导并令其等于零：

\[
\nabla_x L = x^\top \begin{bmatrix} 2 & 1 \\ 1 & 4 \end{bmatrix} + \begin{bmatrix} 5 \\ 3 \end{bmatrix}^\top + \lambda^\top A = 0.
\]

求解 \(x\)：

\[
x^\top = -\left( \begin{bmatrix} 5 \\ 3 \end{bmatrix}^\top + \lambda^\top A \right) Q^{-1}.
\]

乘积。

*提示：对适当的函数求梯度，并令梯度等于零。*

根据 Legendre–Fenchel 共轭的定义，

\[
f^*(s) = \sup_{x \in \mathbb{R}^D} \sum_{d=1}^{D} s_d x_d - x_d \log x_d.
\]

为方便记号，定义函数

\[
g(x) = \sum_{d=1}^{D} s_d x_d - x_d \log x_d.
\]

\(g(x)\) 关于 \(x_d\) 的梯度为

\[
\frac{\partial g(x)}{\partial x_d} = s_d - \frac{x_d}{x_d} - \log x_d = s_d - 1 - \log x_d.
\]

令梯度为零，得到

\[
x_d = \exp(s_d - 1).
\]

将 \(x_d\) 的最优值代回 \(f^*(s)\)，得到

\[
f^*(s) = \sum_{d=1}^{D} \left[ s_d \exp(s_d - 1) - (s_d - 1)\exp(s_d - 1) \right] = \sum_{d=1}^{D} \exp(s_d - 1).
\]

**7.10** 考虑函数

\[
f(x) = \frac{1}{2} x^\top A x + b^\top x + c,
\]

其中 \(A\) 是严格正定的，这意味着它是可逆的。推导 \(f(x)\) 的凸共轭。

*提示：对适当的函数求梯度，并令梯度等于零。*

根据 Legendre–Fenchel 变换的定义，

\[
f^*(s) = \sup_{x \in \mathbb{R}^D} s^\top x - \frac{1}{2} x^\top A x - b^\top x - c.
\]

为方便记号，定义函数

\[
g(x) = s^\top x - \frac{1}{2} x^\top A x - b^\top x - c.
\]

\(g(x)\) 关于 \(x\) 的梯度为

\[
\frac{\partial g(x)}{\partial x} = s^\top - x^\top A - b^\top.
\]

令梯度为零，并注意到 \(A^\top = A\)，有

\[
s^\top - x^\top A - b^\top = 0,
\]

因此 \(A^\top x = s - b\)，所以

\[
x = A^{-1}(s - b).
\]

