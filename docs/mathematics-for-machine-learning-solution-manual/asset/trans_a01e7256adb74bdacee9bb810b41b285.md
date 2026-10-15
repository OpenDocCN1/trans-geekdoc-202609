
其中

\[
\boldsymbol{A} = \begin{bmatrix} 6 & 4 & 3 \\ 6 & 0 & 9 \\ 0 & 8 & 0 \end{bmatrix}
\]

且 \(\sum_{i=1}^3 x_i = 1\).

我们首先将问题重新表述为求解齐次线性方程组。设 \(\boldsymbol{x}\) 在 \(\mathbb{R}^3\) 中。我们注意到 \(\boldsymbol{A}\boldsymbol{x} = 12\boldsymbol{x}\) 等价于 \((\boldsymbol{A} - 12I)\boldsymbol{x} = \boldsymbol{0}\)，它可以重写为齐次系统 \(\tilde{\boldsymbol{A}}\boldsymbol{x} = \boldsymbol{0}\)，其中我们定义

\[
\tilde{\boldsymbol{A}} = \begin{bmatrix} -6 & 4 & 3 \\ 6 & -12 & 9 \\ 0 & 8 & -12 \end{bmatrix}.
\]

约束 \(\sum_{i=1}^3 x_i = 1\) 可以转写为第四个方程，这促使我们考虑以下线性系统，我们将其化为行最简形：

\[
\left[\begin{array}{cccc|c}
-6 & 4 & 3 & 0\\
6 & -12 & 9 & 0\\
0 & 8 & -12 & 0\\
1 & 1 & 1 & 1
\end{array}\right]
\sim
\left[\begin{array}{cccc|c}
0 & -8 & 12 & 0\\
2 & -4 & 3 & 0\\
0 & 2 & -3 & 0\\
1 & 1 & 1 & 1
\end{array}\right]
\sim
\left[\begin{array}{cccc|c}
0 & 0 & 0 & 0\\
2 & 0 & -3 & 0\\
0 & 2 & -3 & 0\\
1 & 1 & 1 & 1
\end{array}\right]
\sim
\left[\begin{array}{ccc|c}
1 & 0 & -\frac32 & 0\\
0 & 1 & -\frac32 & 0\\
1 & 1 & 1 & 1
\end{array}\right]
\sim
\left[\begin{array}{ccc|c}
1 & 0 & -\frac32 & 0\\
0 & 1 & -\frac32 & 0\\
0 & 0 & 4 & 1
\end{array}\right]
\sim
\left[\begin{array}{ccc|c}
1 & 0 & 0 & \frac38\\
0 & 1 & 0 & \frac38\\
0 & 0 & 1 & \frac14
\end{array}\right]
\]

因此，我们得到唯一解

\[
\boldsymbol{x} = \begin{bmatrix} \tfrac{3}{8} \\ \tfrac{3}{8} \\ \tfrac{1}{4} \end{bmatrix} = \frac{1}{8} \begin{bmatrix} 3 \\ 3 \\ 2 \end{bmatrix}.
\]

## 2.8 若可能，确定下列矩阵的逆：

- **a.**
  \[
  A = \begin{bmatrix} 2 & 3 & 4 \\ 3 & 4 & 5 \\ 4 & 5 & 6 \end{bmatrix}
  \]

  确定矩阵的逆时，我们从增广矩阵 \([A \mid I]\) 开始并将其化为 \([I \mid B]\)，其中 \(B\) 恰好是 \(A^{-1}\)：

  \[
  \left[\begin{array}{ccc|ccc}
  2 & 3 & 4 & 1 & 0 & 0 \\
  3 & 4 & 5 & 0 & 1 & 0 \\
  4 & 5 & 6 & 0 & 0 & 1
  \end{array}\right]
  \xrightarrow{R_2\leftarrow R_2-\frac32R_1,\; R_3\leftarrow R_3-2R_1}
  \left[\begin{array}{ccc|ccc}
  2 & 3 & 4 & 1 & 0 & 0 \\
  0 & -\frac12 & -1 & -\frac32 & 1 & 0 \\
  0 & -1 & -2 & -2 & 0 & 1
  \end{array}\right]
  \xrightarrow{R_2\leftarrow R_2-\frac12R_3,\; R_3\leftarrow -R_3}
  \left[\begin{array}{ccc|ccc}
  2 & 3 & 4 & 1 & 0 & 0 \\
  0 & 0 & 0 & -\frac12 & 1 & -\frac12 \\
  0 & 1 & 2 & 2 & 0 & -1
  \end{array}\right].
  \]

  这里，我们看到该线性方程组无解。因此逆不存在。

- **b.**
  \[
  A = \begin{bmatrix} 1 & 0 & 1 & 0 \\ 0 & 1 & 1 & 0 \\ 1 & 1 & 0 & 1 \\ 1 & 1 & 1 & 0 \end{bmatrix}
  \]

  \[
  \left[\begin{array}{cccc|cccc}
  1 & 0 & 1 & 0 & 1 & 0 & 0 & 0 \\
  0 & 1 & 1 & 0 & 0 & 1 & 0 & 0 \\
  1 & 1 & 0 & 1 & 0 & 0 & 1 & 0 \\
  1 & 1 & 1 & 0 & 0 & 0 & 0 & 1
  \end{array}\right]
  \xrightarrow{R_3\leftarrow R_3-R_1,\; R_4\leftarrow R_4-R_1}
  \left[\begin{array}{cccc|cccc}
  1 & 0 & 1 & 0 & 1 & 0 & 0 & 0 \\
  0 & 1 & 1 & 0 & 0 & 1 & 0 & 0 \\
  0 & 1 & -1 & 1 & -1 & 0 & 1 & 0 \\
  0 & 1 & 0 & 0 & -1 & 0 & 0 & 1
  \end{array}\right]
  \]
  \[
  \xrightarrow{\text{swap }R_2,R_4}
  \left[\begin{array}{cccc|cccc}
  1 & 0 & 1 & 0 & 1 & 0 & 0 & 0 \\
  0 & 1 & 0 & 0 & -1 & 0 & 0 & 1 \\
  0 & 1 & -1 & 1 & -1 & 0 & 1 & 0 \\
  0 & 1 & 1 & 0 & 0 & 1 & 0 & 0
  \end{array}\right]
  \xrightarrow{R_3\leftarrow R_3-R_2,\; R_4\leftarrow R_4-R_2}
  \left[\begin{array}{cccc|cccc}
  1 & 0 & 1 & 0 & 1 & 0 & 0 & 0 \\
  0 & 1 & 0 & 0 & -1 & 0 & 0 & 1 \\
  0 & 0 & -1 & 1 & 0 & 0 & 1 & -1 \\
  0 & 0 & 1 & 0 & 1 & 1 & 0 & -1
  \end{array}\right]
  \]
  \[
  \xrightarrow{R_1\leftarrow R_1-R_4,\; R_3\leftarrow R_3+R_4}
  \left[\begin{array}{cccc|cccc}
  1 & 0 & 0 & 0 & 0 & -1 & 0 & 1 \\
  0 & 1 & 0 & 0 & -1 & 0 & 0 & 1 \\
  0 & 0 & 0 & 1 & 1 & 1 & 1 & -2 \\
  0 & 0 & 1 & 0 & 1 & 1 & 0 & -1
  \end{array}\right]
  \xrightarrow{\text{swap }R_3,R_4}
  \left[\begin{array}{cccc|cccc}
  1 & 0 & 0 & 0 & 0 & -1 & 0 & 1 \\
  0 & 1 & 0 & 0 & -1 & 0 & 0 & 1 \\
  0 & 0 & 1 & 0 & 1 & 1 & 0 & -1 \\
  0 & 0 & 0 & 1 & 1 & 1 & 1 & -2
  \end{array}\right]
  \]

  因此，

  \[
  A^{-1} = \left[\begin{array}{rrrr} 0 & -1 & 0 & 1 \\ -1 & 0 & 0 & 1 \\ 1 & 1 & 0 & -1 \\ 1 & 1 & 1 & -2 \end{array}\right]
  \]

## 2.9 下列哪些集合是 \(\mathbb{R}^3\) 的子空间？

- **a.** \(A=\{(\lambda,\lambda+\mu^3,\lambda-\mu^3)\mid \lambda,\mu\in\mathbb{R}\}\)
- **b.** \(B=\{(\lambda^2,-\lambda^2,0)\mid \lambda\in\mathbb{R}\}\)
- **c.** 设 \(\gamma\) 在 \(\mathbb{R}\) 中。 \(C=\{(\xi_1,\xi_2,\xi_3)\in\mathbb{R}^3\mid \xi_1-2\xi_2+3\xi_3=\gamma\}\)
- **d.** \(D=\{(\xi_1,\xi_2,\xi_3)\in\mathbb{R}^3\mid \xi_2\in\mathbb{Z}\}\)

作为提醒：设 \(V\) 为向量空间。 \(U\subseteq V\) 是子空间当且仅当

1. \(U\neq\varnothing\)。特别地 \(0\in U\)。
2. \(\forall a,b\in U\): \(a+b\in U\)  对内运算封闭
3. \(\forall a\in U,\lambda\in\mathbb{R}\): \(\lambda a\in U\)  对外运算封闭

标准向量空间性质（阿贝尔群、分配律、结合律和单位元）无需证明，因为它们继承自向量空间 \((\mathbb{R}^3,+,\cdot)\)。

现在我们来看集合 \(A,B,C,D\)。

- **a.**
  1. 我们有 \((0,0,0)\in A\) 当 \(\lambda=0=\mu\) 时。
  2. 设 \(a=(\lambda_1,\lambda_1+\mu_1^3,\lambda_1-\mu_1^3)\) 和 \(b=(\lambda_2,\lambda_2+\mu_2^3,\lambda_2-\mu_2^3)\) 为 \(A\) 的两个元素，其中 \(\lambda_1,\mu_1,\lambda_2,\mu_2\in\mathbb{R}\)。则，
    \[
    \begin{aligned}
    a+b
    &=(\lambda_1,\lambda_1+\mu_1^3,\lambda_1-\mu_1^3)+(\lambda_2,\lambda_2+\mu_2^3,\lambda_2-\mu_2^3)\\
    &=(\lambda_1+\lambda_2,\lambda_1+\mu_1^3+\lambda_2+\mu_2^3,\lambda_1-\mu_1^3+\lambda_2-\mu_2^3)\\
    &=(\lambda_1+\lambda_2,(\lambda_1+\lambda_2)+(\mu_1^3+\mu_2^3),(\lambda_1+\lambda_2)-(\mu_1^3+\mu_2^3)),
    \end{aligned}
    \]
    它属于 \(A\)。
  3. 设 \(\alpha\) 在 \(\mathbb{R}\) 中。则，
    \[
    \alpha(\lambda,\lambda+\mu^3,\lambda-\mu^3)=(\alpha\lambda,\alpha\lambda+\alpha\mu^3,\alpha\lambda-\alpha\mu^3)\in A.
    \]
    因此，\(A\) 是 \(\mathbb{R}^3\) 的子空间。

- **b.** 向量 \((1,-1,0)\) 属于 \(B\)，但 \((-1)\cdot(1,-1,0)=(-1,1,0)\) 不属于。因此，\(B\) 对数乘不封闭，不是 \(\mathbb{R}^3\) 的子空间。

- **c.** 设 \(A\in\mathbb{R}^{1\times3}\) 定义为 \(A=[1,-2,3]\)。集合 \(C\) 可写为：
  \[
  C=\{x\in\mathbb{R}^3\mid Ax=\gamma\}.
  \]
  我们首先注意到 \(\mathbf{0}\) 仅当 \(\gamma=0\) 时属于 \(C\)，因为 \(A\mathbf{0}=0\)。

  因此我们考虑 \(\gamma=0\) 并问 \(C\) 是否是 \(\mathbb{R}^3\) 的子空间。设 \(x\) 和 \(y\) 在 \(C\) 中。我们知道 \(Ax=0\) 且 \(Ay=0\)，于是
  \[
  A(x+y)=Ax+Ay=0+0=0.
  \]
  因此 \(x+y\) 属于 \(C\)。设 \(\lambda\) 在 \(\mathbb{R}\) 中。类似地，
  \[
  A(\lambda x)=\lambda(Ax)=\lambda 0=0.
  \]
  因此 \(C\) 对数乘封闭，从而当且仅当 \(\gamma=0\) 时是 \(\mathbb{R}^3\) 的子空间。

- **d.** 向量 \((0,1,0)\) 属于 \(D\) 但 \(\pi(0,1,0)\) 不属于，因此 \(D\) 不是 \(\mathbb{R}^3\) 的子空间。

## 2.10 下列向量组是否线性无关？

- **a.**
  \[
  x_1=\begin{bmatrix}2\\-1\\3\end{bmatrix},\quad x_2=\begin{bmatrix}1\\1\\-2\end{bmatrix},\quad x_3=\begin{bmatrix}3\\-3\\8\end{bmatrix}
  \]

  为了确定这些向量是否线性无关，我们检查 \(0\) 向量是否可以非平凡地表示为 \(x_1,\dots,x_3\) 的线性组合。因此，我们尝试求解齐次线性方程组 \(\sum_{i=1}^3 \lambda_i x_i=0\)，其中 \(\lambda_i\in\mathbb{R}\)。我们使用高斯消元法求解 \(Ax=0\)，其中
  \[
  A=\begin{bmatrix}2&1&3\\-1&1&-3\\3&-2&8\end{bmatrix},
  \]
  这导致行最简形
  \[
  \begin{bmatrix}1&0&2\\0&1&-1\\0&0&0\end{bmatrix}.
  \]
  这意味着 \(A\) 秩亏/奇异，因此三个向量线性相关。例如，取 \(\lambda_1=2,\lambda_2=-1,\lambda_3=-1\) 时，我们有非平凡线性组合 \(\sum_{i=1}^3\lambda_i x_i=0\)。

- **b.**
  \[
  x_1=\begin{bmatrix}1\\2\\1\\0\\0\end{bmatrix},\quad x_2=\begin{bmatrix}1\\1\\0\\1\\1\end{bmatrix},\quad x_3=\begin{bmatrix}1\\0\\0\\1\\1\end{bmatrix}
  \]

  这里，我们观察向量中 0 的分布。\(x_1\) 是唯一第三分量非零的向量。因此 \(\lambda_1\) 必须为 0。类似地，由于第二分量（已在 \(\lambda_1=0\) 的条件下），\(\lambda_2\) 必须为 0。最后 \(\lambda_3=0\)。因此三个向量线性无关。另一种使用高斯消元法的解法也是可行的，会得到相同结论。

## 2.11 写出

\[
\boldsymbol{y}=\begin{bmatrix}1\\-2\\5\end{bmatrix}
\]

作为

\[
\boldsymbol{x}_1=\begin{bmatrix}1\\1\\1\end{bmatrix},\quad \boldsymbol{x}_2=\begin{bmatrix}1\\2\\3\end{bmatrix},\quad \boldsymbol{x}_3=\begin{bmatrix}2\\-1\\1\end{bmatrix}
\]

的线性组合

我们寻找 \(\lambda_1,\dots,\lambda_3\in\mathbb{R}\)，使得 \(\sum_{i=1}^3\lambda_i\boldsymbol{x}_i=\boldsymbol{y}\)。因此我们需要求解非齐次线性方程组

\[
\begin{bmatrix}1&1&2&|&1\\1&2&-1&|&-2\\1&3&1&|&5\end{bmatrix}
\]

使用高斯消元法，我们得到 \(\lambda_1=-6\)，\(\lambda_2=3\)，\(\lambda_3=2\)。

## 2.12 考虑 \(\mathbb{R}^4\) 的两个子空间：

\[
U_1=\operatorname{span}\left\{\begin{bmatrix}1\\1\\-3\\1\end{bmatrix},\begin{bmatrix}2\\-1\\0\\-1\end{bmatrix},\begin{bmatrix}-1\\1\\-1\\1\end{bmatrix}\right\},\quad
U_2=\operatorname{span}\left\{\begin{bmatrix}-1\\-2\\2\\1\end{bmatrix},\begin{bmatrix}2\\-2\\0\\0\end{bmatrix},\begin{bmatrix}-3\\6\\-2\\-1\end{bmatrix}\right\}.
\]

求 \(U_1\cap U_2\) 的一个基。

我们首先检查 \(U_1\)（和 \(U_2\)）生成集中的向量是否线性相关。这样我们可以确定 \(U_1\) 和 \(U_2\) 的基，从而使后续计算更简单。

我们从 \(U_1\) 开始。为了判断三个向量是否线性相关，我们需要找到这些向量的线性组合，使其能非平凡地表示 \(\mathbf{0}\)，即 \(\lambda_1,\lambda_2,\lambda_3\in\mathbb{R}\)，使得

\[
\lambda_1\begin{bmatrix}1\\1\\-3\\1\end{bmatrix}+\lambda_2\begin{bmatrix}2\\-1\\0\\-1\end{bmatrix}+\lambda_3\begin{bmatrix}-1\\1\\-1\\1\end{bmatrix}=\begin{bmatrix}0\\0\\0\\0\end{bmatrix}.
\]

我们看到必然有：\(\lambda_3=-3\lambda_1\)（否则第三分量永远不可能为 0）。由此得到

\[
\lambda_1\begin{bmatrix}1+3\\1-3\\-3+3\\1-3\end{bmatrix}+\lambda_2\begin{bmatrix}2\\-1\\0\\-1\end{bmatrix}=\begin{bmatrix}0\\0\\0\\0\end{bmatrix}
\]
