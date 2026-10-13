

$$
\mathbf{y} = \begin{bmatrix} y_{1} \\ \vdots \\ y_{N} \\ \end{bmatrix} \in \mathbb{R}^{N},\quad X := \begin{bmatrix} \mathbf{x}_{1}^{T} \\ \vdots \\ \mathbf{x}_{N}^{T} \\ \end{bmatrix} \in \mathbb{R}^{N \times l}.
$$

公式 [(6.1)](#Chp006_249-291_B9780443292385000123.xhtml#deq2) 可重写为

$$
\widehat{\mathbf{\theta}}_{LS} = \arg\min\limits_{\mathbf{\theta}}{\|\mathbf{e}\|}^{2},
$$

其中

$$
\mathbf{e} := \mathbf{y} - X\mathbf{\theta}
$$

且 $\|\cdot\|$ 表示欧几里得范数，它度量 $\mathbb{R}^{(N)}$ 中相应向量（即 $\mathbf{y}$ 和 $X\mathbf{\theta}$）之间的“距离”。确实，向量 $\mathbf{e}$ 的第 $n$ 个分量等于 $e[n] = y[n] - \mathbf{x}[n]^{(T)}\mathbf{\theta}$，由于内积的对称性，这等于 $y[n] - \mathbf{\theta}^{(T)}\mathbf{x}[n]$；此外，向量的平方欧几里得范数是其分量平方和，这使得 $\mathbf{e}$ 的平方范数与公式 [(6.1)](#Chp006_249-291_B9780443292385000123.xhtml#deq2) 中的平方误差和代价函数相同。

现在让我们用 $\mathbf{x}[1]^{(c)}, \dots, \mathbf{x}[l]^{(c)} \in \mathbb{R}^{(N)}$ 表示 $X$ 的列，即

$$
X = [\mathbf{x}[1]^{(c)}, \dots, \mathbf{x}[l]^{(c)}].
$$

那么上述矩阵-向量乘积可写为矩阵 $X$ 列的线性组合，即

