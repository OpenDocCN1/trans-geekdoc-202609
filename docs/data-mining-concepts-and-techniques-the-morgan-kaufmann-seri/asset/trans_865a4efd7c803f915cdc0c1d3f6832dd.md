

采用如下形式：

$$
\begin{aligned}
\min \quad & a + \mathbf{b}^T \mathbf{x} + \frac{1}{2} \mathbf{x}^T \mathbf{C} \mathbf{x} \\
s.t. \quad & \mathbf{Px} \le \mathbf{d} \\
& \mathbf{Qx} = \mathbf{e}.
\end{aligned}
$$
(A.48)

为了不失一般性，我们可以假设矩阵 C 是对称的。
典型的例子是 *受约束回归分析*

$$
\begin{aligned}
\min_{\mathbf{x}} \quad & ||\mathbf{Ax} - \mathbf{b}||_2^2 \\
s.t. \quad & |\mathbf{l}[i]| \le \mathbf{x}[i] \le \mathbf{u}[i], \forall i,
\end{aligned}
$$
(A.49)

这等价于

$$
\begin{aligned}
\min_{\mathbf{x}} \quad & \mathbf{x}^T \mathbf{A}^T \mathbf{A} \mathbf{x} - 2\mathbf{b}^T \mathbf{A} \mathbf{x} + \mathbf{b}^T \mathbf{b} \\
s.t. \quad & |\mathbf{l}[i]| \le \mathbf{x}[i] \le \mathbf{u}[i], \forall i.
\end{aligned}
$$
(A.50)

针对各种 QP 存在多种灵活的解法。在本节中，我们提供针对 *等式约束 QP (EQP)* 的解法，通用 QP 的解法可在参考文献注释中找到。EQP 是仅存在等式约束的 QP，其目标函数采用如下形式：

$$
\begin{aligned}
\min \quad & \mathbf{b}^T \mathbf{x} + \frac{1}{2} \mathbf{x}^T \mathbf{C} \mathbf{x} \\
s.t. \quad & \mathbf{Qx} = \mathbf{e},
\end{aligned}
$$
(A.51)

常数项已被舍去。如果 \(\mathbf{x}^*\) 是 EQP 的解，则一个必要条件是存在满足以下 *KKT 系统* 的 \(\boldsymbol{\lambda}^*\) 向量：

$$
\left[ \begin{array}{cc} \mathbf{C} & \mathbf{Q}^T \\ \mathbf{Q} & 0 \end{array} \right] \left[ \begin{array}{c} -\mathbf{p} \\ \boldsymbol{\lambda}^* \end{array} \right] = \left[ \begin{array}{c} \mathbf{b} + \mathbf{Cx} \\ \mathbf{Qx} - \mathbf{e} \end{array} \right],
$$
(A.52)

其中 \(\mathbf{x}\) 是解的估计，\(\mathbf{x}^* = \mathbf{x} + \mathbf{p}\)。如果 \(\mathbf{Q}\) 是正定的，根据 Eq. (A.52) 我们可以从以下方程中得到 \(\boldsymbol{\lambda}^*\)：

$$(\mathbf{Q} \mathbf{C}^{-1} \mathbf{Q}^T) \boldsymbol{\lambda}^* = \mathbf{Q} \mathbf{C}^{-1} \mathbf{b} + \mathbf{e}.$$
(A.53)

因此 \(\mathbf{p}\) 可以从以下方程中得到：

$$
\mathbf{Cp} = \mathbf{Q}^T \boldsymbol{\lambda}^* - \mathbf{b} - \mathbf{Cx},
$$
(A.54)

由此我们可以得到最终解 \(\mathbf{x}^*\)。

## A.3 矩阵与线性代数

### A.3.1 线性系统 Ax = b

在本节中，我们讨论三种类型的线性系统 Ax = b：(1) \(\mathbf{A} \in \mathbb{R}^{n \times n}\) 是标准方阵，(2) \(\mathbf{A} \in \mathbb{R}^{n \times m}\)，n > m，A 的行数多于列数（超定），(3) \(\mathbf{A} \in \mathbb{R}^{n \times m}\)，n < m，A 的行数少于列数（欠定）。

#### 标准方阵系统

如果 A 可逆，我们可以直接使用矩阵逆 A^{-1} 求解：

```
Ax = b => x = A^{-1}b. (A.55)
```

迭代方法提供了解线性系统的间接方式。广泛使用的迭代方法包括 Jacobi 方法、Richardson 方法、Krylov 子空间方法等。迭代方法的关键思想是选择合适的 S 和 d，并建立如下形式的迭代：

```
x^{(k+1)} = Sx^{(k)} + d. (A.56)
```

在每次迭代中，残差误差 \(\|\mathbf{x}^{(k)} - \mathbf{x}^*\|\) 会减小，其中 \(\mathbf{x}^*\) 是 Ax = b 的解。经过几次迭代后，\(\mathbf{x}^{(k)}\) 收敛到 \(\mathbf{x}^*\)。

预处理方法旨在寻找一个更简单的矩阵 P，它接近 A，即 (A - P) 具有低秩或小范数。然后，我们求解 P^{-1}Ax = P^{-1}b 而不是 Ax = b，因为处理 P^{-1}A 通常更快。P 的一些典型选择包括使用 A 主对角线的对角矩阵、复制 A 对应部分的三角矩阵等。

#### 超定系统

假设 \(\mathbf{A}\) 具有线性无关的列，\(\operatorname{rank}(\mathbf{A}) = m\)，则有

```
Ax = b <=> A^T Ax = A^T b <=> x = (A^T A)^{-1} A^T b, (A.57)
```

这给出了使 ||Ax - b||^2 最小化的解。

当 A^T A 不可逆时，最小二乘解为 x = A^+b，其中 A^+ 是 A 的伪逆。具体来说，我们先对 A 进行奇异值分解 (SVD) 得到 A = UΣV^T，然后有 A^+ = VΣ^{-1}U^T。

#### 欠定系统

对于欠定系统，存在许多最小二乘解，结果表明 A^+b 是范数 ||x||^2 最小的最小二乘解。与超定系统类似，当 \(\mathbf{A}\) 具有线性无关的行，\(\operatorname{rank}(\mathbf{A}) = n\) 时，有

```
Ax = b <=> x = A^T (AA^T)^{-1} b. (A.58)
```

在某些情况下，我们希望用 \(\ell^2\) 惩罚项对线性系统进行正则化。因此我们的优化目标变为

```
Minimize ||Ax - b||^2 + δ^2||x||_2^2, (A.59)
```

其中 \(\delta^2\) 是惩罚项的权重。这等价于求解 \((\mathbf{A}^\top \mathbf{A} + \delta^2 \mathbf{I})\mathbf{x} = \mathbf{A}^\top \mathbf{b}\)，这种方法称为岭回归。

### A.3.2 向量和矩阵的范数

#### 向量范数

向量的范数定义为从向量空间 \(V\) 到实数的映射：\(\|\cdot\| : V \rightarrow \mathbb{R}\)。给定向量 \(\mathbf{v}\)，它测量向量 \(\|\mathbf{v}\|\) 的长度。对于每个 \(\mathbf{v}, \mathbf{w} \in V\) 和 \(c \in \mathbb{R}\)，以下三个性质始终成立：

- 正定性：\(\|\mathbf{v}\| \ge 0\) 且 \(\|\mathbf{v}\| = 0 \Longleftrightarrow \mathbf{v} = 0\)。
- 绝对齐次性：\(\|c\mathbf{v}\| = |c| \|\mathbf{v}\|\)，其中 \(|c|\) 是 \(c\) 的绝对值。
- 三角不等式：\(\|\mathbf{v} + \mathbf{w}\| \le \|\mathbf{v}\| + \|\mathbf{w}\|\)。

这里，我们给出一些常用向量范数的定义：

- \(\ell^1\) 范数（曼哈顿范数）：\(\|\mathbf{v}\|_1 = \sum_i |\mathbf{v}[i]|\)。
- \(\ell^2\) 范数（欧几里得范数）：\(\|\mathbf{v}\|_2 = \sqrt{\sum_i \mathbf{v}[i]^2} = \sqrt{\mathbf{v}^\top \mathbf{v}}\)。
- \(\ell^\infty\) 范数：\(\|\mathbf{v}\|_\infty = \max_i |\mathbf{v}[i]|\)。

#### 矩阵范数

诱导矩阵范数可由向量范数诱导得到：

\(\|\mathbf{A}\| = \max_{\mathbf{v} \neq 0} \frac{\|\mathbf{A}\mathbf{v}\|}{\|\mathbf{v}\|}\)。

除了向量范数满足的性质外，诱导矩阵范数还具有以下性质，即对于所有 \(\mathbf{A}, \mathbf{B}\) 和 \(\mathbf{v}\)，\(\|\mathbf{A}\mathbf{v}\| \le \|\mathbf{A}\| \|\mathbf{v}\|\) 且 \(\|\mathbf{A}\mathbf{B}\| \le \|\mathbf{A}\| \|\mathbf{B}\|\)。

这里，我们介绍如何计算一些典型的矩阵范数：

- \(\ell^1\) 范数是 \(\mathbf{A}\) 列中最大的 \(\ell^1\) 范数：\(\|\mathbf{A}\|_1 = \max_j \sum_i |\mathbf{A}[i, j]|\)。
- \(\ell^2\) 范数是 \(\mathbf{A}\) 的最大奇异值：\(\|\mathbf{A}\|_2 = \sqrt{\maxeig(\mathbf{A}^T \mathbf{A})}\)，其中 \(\maxeig(\cdot)\) 表示最大特征值。
- \(\ell^\infty\) 范数是 \(\mathbf{A}\) 行中最大的 \(\ell^1\) 范数：\(\|\mathbf{A}\|_\infty = \max_i \sum_j |\mathbf{A}[i, j]|\)。
- Frobenius 范数来自 \(\mathbf{A}\) 的奇异值 \(\sigma_i\) (\(i = 1, \dots, r\))，即 \(\|\mathbf{A}\|_F^2 = \sigma_1^2 + \cdots + \sigma_r^2\)，其中 \(r\) 是矩阵 \(\mathbf{A}\) 的秩。它也可以通过以下方式推导：\(\|\mathbf{A}\|_F = \sum_{ij} |\mathbf{A}[i, j]|^2\)。

### A.3.3 矩阵分解

#### 特征值与特征值分解

给定方阵 \(\mathbf{A} \in \mathbb{R}^{n \times n}\)，如果 \(\lambda \in \mathbb{R}\) 和 \(\mathbf{x} \in \mathbb{R}^n \setminus \{\mathbf{0}\}\) 满足 \(\mathbf{A}\mathbf{x} = \lambda \mathbf{x}\)，则称 \(\lambda\) 为 \(\mathbf{A}\) 的特征值，\(\mathbf{x}\) 为对应的特征向量。\(^1\) 从 \(\mathbf{A}\mathbf{x} = \lambda \mathbf{x}\)，我们得到 \((\mathbf{A} - \lambda \mathbf{I})\mathbf{x} = 0\)。由于 \(\mathbf{x}\) 不是零向量，\(\mathbf{A} - \lambda \mathbf{I}\) 不可逆，其行列式必须为零。要计算 A 的所有特征值，需要求解方程 \(\det(\mathbf{A} - \lambda \mathbf{I}) = 0\) 的根。由于该方程关于 λ 有 n 次，总共有 n 个特征值，可能存在重复。

- 特征值之和等于迹：\(\operatorname{tr}(\mathbf{A}) = \sum_{i=1}^n \lambda_i\)。
- 特征值之积等于行列式：\(\det(\mathbf{A}) = \prod_{i=1}^n \lambda_i\)。

当矩阵 A 有 n 个线性无关的特征向量时，它可以分解为

```
A = X\Lambda X^{-1},
```

其中 X 的列是 A 的 n 个特征向量，\(\Lambda\) 是对角矩阵，其对角线元素是 A 的 n 个特征值。这种分解称为特征值分解。注意对称矩阵总是有 n 个线性无关的特征向量，并且总是可以进行特征值分解。从 A = X\Lambda X^{-1}，我们得到 A^k = X\Lambda^k X^{-1}，这意味着 A^k 的特征值为 \(\lambda_1^k, \cdots, \lambda_n^k\)。此外，对于每个 v \in R^n，它可以写成 v = c_1 x_1 + \cdots + c_n x_n。这提供了一种更简单的方式来计算 A^k v：

```
A^k v = c_1 \lambda_1^k x_1 + \cdots + c_n \lambda_n^k x_n.
```

#### 奇异值分解 (SVD)

给定矩阵 \(\mathbf{A} \in \mathbb{R}^{m \times n}\) 且秩为 r，A 的 SVD 写为

```
A = U \Sigma V^T,
```

其中 \(\mathbf{U} \in \mathbb{R}^{m \times n}\) 是包含 \(\mathbf{A}\mathbf{A}^T\) 标准正交特征向量的正交矩阵，\(\mathbf{V} \in \mathbb{R}^{n \times n}\) 是包含 \(\mathbf{A}^T \mathbf{A}\) 标准正交特征向量的正交矩阵，\(\Sigma \in \mathbb{R}^{m \times n}\) 是满足 \(\Sigma_{ii} = \sigma_i\)、\(i = 1, \cdots, r\) 且其他元素均为零的矩阵。这里，我们称 \(\sigma_1, \cdots, \sigma_r\) 为奇异值。奇异值均为正数并按降序排列。注意，与特征值分解不同，SVD 适用于任何矩形矩阵。

要计算 SVD，我们先对 \(\mathbf{A}^T \mathbf{A}\) 进行特征值分解并得到正交特征向量 \(\mathbf{v}_1, \cdots, \mathbf{v}_r\)。从 SVD 的形式可知，\(\mathbf{A}\mathbf{v}_k = \mathbf{u}_k \sigma_k\)，\(k = 1, \cdots, r\)。因此 \(\mathbf{u}_k = \frac{\mathbf{A}\mathbf{v}_k}{\sigma_k}\)，\(k = 1, \cdots, r\)。对于 V 的最后 n - r 列，有 \(\mathbf{A}\mathbf{v}_k = 0\)，\(k = r + 1, \cdots, n\)。因此 \(\mathbf{v}_{r+1}, \cdots, \mathbf{v}_n\) 是 A 零空间的正交基。同样，\(\mathbf{u}_{r+1}, \cdots, \mathbf{u}_m\) 是 \(\mathbf{A}^T\) 零空间的正交基。

使用 SVD，A 可以写成秩一矩阵之和：

```
A = \sigma_1 u_1 v_1^T + \cdots + \sigma_r u_r v_r^T.
```

这为矩阵近似提供了重要因素。具体来说，奇异值 \(\sigma_1, \sigma_2, \cdots, \sigma_r\) 按其重要性排序。第一项 \(\sigma_1 u_1 v_1^T\) 是最接近 A 的秩一矩阵，这意味着只有当秩一矩阵 \(\mathbf{B} = \sigma_1 u_1 v_1^T\) 时，\(\|\mathbf{A} - \mathbf{B}\|\) 在 \(\ell_2\) 范数和 Frobenius 范数意义下才取得最小值。此外，\(\mathbf{A}_k = \sigma_1 u_1 v_1^T + \cdots + \sigma_k u_k v_k^T\) 是最接近 A 的秩 k 近似。

