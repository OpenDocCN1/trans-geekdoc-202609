
$$
\mathbf{y} = \begin{bmatrix} y_{1} \\ \vdots \\ y_{N} \\ \end{bmatrix} \in \mathbb{R}^{N},\quad X := \begin{bmatrix} \mathbf{x}_{1}^{T} \\ \vdots \\ \mathbf{x}_{N}^{T} \\ \end{bmatrix} \in \mathbb{R}^{N \times l}.
$$

Eq. [(6.1)](#Chp006_249-291_B9780443292385000123.xhtml#deq2) can be then recast as

$$
\widehat{\mathbf{\theta}}_{LS} = \arg\min\limits_{\mathbf{\theta}}{\|\mathbf{e}\|}^{2},
$$

where

$$
\mathbf{e} := \mathbf{y} - X\mathbf{\theta}
$$

and $\|\cdot\|$ denotes the Euclidean norm, which measures the "distance" between the respective vectors in $\mathbb{R}^{(N)}$, i.e., $\mathbf{y}$ and $X\mathbf{\theta}$. Indeed, the $n$th component of the vector $\mathbf{e}$ is equal to $e[n] = y[n] - \mathbf{x}[n]^{(T)}\mathbf{\theta}$, which, due to the symmetry of the inner product, is equal to $y[n] - \mathbf{\theta}^{(T)}\mathbf{x}[n]$; furthermore, the square Euclidean norm of the vector is the sum of the squares of its components, which makes the square norm of $\mathbf{e}$ identical to the sum of squared errors cost in Eq. [(6.1)](#Chp006_249-291_B9780443292385000123.xhtml#deq2).

Let us now denote as $\mathbf{x}[1]^{(c)}, \dots, \mathbf{x}[l]^{(c)} \in \mathbb{R}^{(N)}$ the columns of $X$, i.e.,

$$
X = [\mathbf{x}[1]^{(c)}, \dots, \mathbf{x}[l]^{(c)}].
$$

Then the matrix-vector product above can be written as the linear combination of the columns of matrix $X$, i.e.,
