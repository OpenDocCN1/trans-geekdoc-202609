

如果 $\mathbf{A}$ 的求值代价高昂，但 $\mathbf{A}\mathbf{v}$（对于随机向量 $\mathbf{v}$）很便宜，我们可以利用式 (C.37) 中的 Hutchinson 迹估计器，按如下方式构造 Frobenius 范数的随机近似：

$$
\|\mathbf{A}\|_{F}^{2}
= \operatorname{tr}(\mathbf{A}^{\top}\mathbf{A})
= \mathbb{E}[\mathbf{v}^{\top}\mathbf{A}^{\top}\mathbf{A}\mathbf{v}]
= \mathbb{E}[\|\mathbf{A}\mathbf{v}\|_{2}^{2}]
\tag{C.28}
$$

其中 $\mathbf{v}\sim\mathcal{N}(\mathbf{0},\mathbf{I})$。

## C.1.4 矩阵的性质

在本节中，我们讨论矩阵的各种标量性质。

### C.1.4.1 方阵的迹

方阵 $\mathbf{A}\in\mathbb{R}^{n\times n}$ 的**迹**，记为 $\operatorname{tr}(\mathbf{A})$，是矩阵中对角线元素之和：

$$
\operatorname{tr}(\mathbf{A})\triangleq\sum_{i=1}^{n}A_{ii}.
\tag{C.29}
$$

迹具有以下性质，其中 $c\in\mathbb{R}$ 是一个标量，$\mathbf{A},\mathbf{B}\in\mathbb{R}^{n\times n}$ 是方阵：

$$
\operatorname{tr}(\mathbf{A})=\operatorname{tr}(\mathbf{A}^{\top})
\tag{C.30}
$$

$$
\operatorname{tr}(\mathbf{A}+\mathbf{B})=\operatorname{tr}(\mathbf{A})+\operatorname{tr}(\mathbf{B})
\tag{C.31}
$$

$$
\operatorname{tr}(c\mathbf{A})=c\,\operatorname{tr}(\mathbf{A})
\tag{C.32}
$$

$$
\operatorname{tr}(\mathbf{A}\mathbf{B})=\operatorname{tr}(\mathbf{B}\mathbf{A})
\tag{C.33}
$$

$$
\operatorname{tr}(\mathbf{A})=\sum_{i=1}^{n}\lambda_{i}\text{ where }\lambda_{i}\text{ are the eigenvalues of }\mathbf{A}
\tag{C.34}
$$

我们还有以下重要的**循环置换性质**：对于使得 $\mathbf{A}\mathbf{B}\mathbf{C}$ 为方阵的 $\mathbf{A},\mathbf{B},\mathbf{C}$，

$$
\operatorname{tr}(\mathbf{A}\mathbf{B}\mathbf{C})=\operatorname{tr}(\mathbf{B}\mathbf{C}\mathbf{A})=\operatorname{tr}(\mathbf{C}\mathbf{A}\mathbf{B})
\tag{C.35}
$$

由此，我们可以推导出**迹技巧**，它将标量内积 $\mathbf{x}^{\top}\mathbf{A}\mathbf{x}$ 改写如下：

$$
\mathbf{x}^{\top}\mathbf{A}\mathbf{x}
= \operatorname{tr}(\mathbf{x}^{\top}\mathbf{A}\mathbf{x})
= \operatorname{tr}(\mathbf{x}\mathbf{x}^{\top}\mathbf{A})
\tag{C.36}
$$

在某些情况下，计算矩阵 $\mathbf{A}$ 可能代价高昂，但我们可以廉价地计算矩阵-向量乘积 $\mathbf{A}\mathbf{v}$。假设 $\mathbf{v}$ 是一个随机向量，且 $\mathbb{E}[\mathbf{v}\mathbf{v}^{\top}]=\mathbf{I}$。在这种情况下，我们可以利用以下恒等式构造 $\operatorname{tr}(\mathbf{A})$ 的蒙特卡洛近似：

$$
\operatorname{tr}(\mathbf{A})
= \operatorname{tr}\big(\mathbf{A}\,\mathbb{E}[\mathbf{v}\mathbf{v}^{\top}]\big)
= \mathbb{E}[\operatorname{tr}(\mathbf{A}\mathbf{v}\mathbf{v}^{\top})]
= \mathbb{E}[\operatorname{tr}(\mathbf{v}^{\top}\mathbf{A}\mathbf{v})]
\tag{C.37}
$$

这被称为 **Hutchinson 迹估计器** [Hut90]。

### C.1.4.2 方阵的行列式

方阵的**行列式**，记为 $\det(\mathbf{A})$ 或 $|\mathbf{A}|$，衡量的是当该矩阵被视为线性变换时，它对单位体积的改变程度。（其正式定义相当复杂，此处不需要。）

行列式算子满足以下性质，其中 $\mathbf{A},\mathbf{B}\in\mathbb{R}^{n\times n}$：

$$
|\mathbf{A}|=|\mathbf{A}^{\top}|
\tag{C.38}
$$

$$
|c\mathbf{A}|=c^{n}|\mathbf{A}|
\tag{C.39}
$$

$$
|\mathbf{A}\mathbf{B}|=|\mathbf{A}||\mathbf{B}|
\tag{C.40}
$$

$$
|\mathbf{A}|=0 \text{ iff } \mathbf{A} \text{ is singular}
\tag{C.41}
$$

$$
|\mathbf{A}^{-1}|=1/|\mathbf{A}| \text{ if } \mathbf{A} \text{ is not singular}
\tag{C.42}
$$

$$
|\mathbf{A}|=\prod_{i=1}^{n}\lambda_{i} \text{ where } \lambda_{i} \text{ are the eigenvalues of } \mathbf{A}
\tag{C.43}
$$

$$
\log|\mathbf{A}|=\operatorname{tr}(\log \mathbf{A})
\tag{C.44}
$$

### C.1.4.3 矩阵的秩

矩阵 $\mathbf{A}$ 的**列秩**是其列向量所张成空间的维度，**行秩**是其行向量所张成空间的维度。线性代数中的一个基本事实（可以用附录 C.5 中讨论的 SVD 证明）是：对于任何矩阵 $\mathbf{A}$，$\operatorname{columnrank}(\mathbf{A}) = \operatorname{rowrank}(\mathbf{A})$，因此该量简称为 $\mathbf{A}$ 的**秩**，记为 $\operatorname{rank}(\mathbf{A})$。以下是秩的一些基本性质：

- 对于 $\mathbf{A} \in \mathbb{R}^{m \times n}$，$\operatorname{rank}(\mathbf{A}) \le \min(m, n)$。若 $\operatorname{rank}(\mathbf{A}) = \min(m, n)$，则称 $\mathbf{A}$ 为**满秩**；否则称其为**秩亏缺**。
- 对于 $\mathbf{A} \in \mathbb{R}^{m \times n}$，$\operatorname{rank}(\mathbf{A}) = \operatorname{rank}(\mathbf{A}^{\top}) = \operatorname{rank}(\mathbf{A}^{\top}\mathbf{A}) = \operatorname{rank}(\mathbf{A}\mathbf{A}^{\top})$。
- 对于 $\mathbf{A} \in \mathbb{R}^{m \times n}$，$\mathbf{B} \in \mathbb{R}^{n \times p}$，$\operatorname{rank}(\mathbf{A}\mathbf{B}) \le \min(\operatorname{rank}(\mathbf{A}), \operatorname{rank}(\mathbf{B}))$。
- 对于 $\mathbf{A},\mathbf{B} \in \mathbb{R}^{m \times n}$，$\operatorname{rank}(\mathbf{A}+\mathbf{B}) \le \operatorname{rank}(\mathbf{A}) + \operatorname{rank}(\mathbf{B})$。

可以证明，方阵可逆当且仅当它是满秩的。

### C.1.4.4 条件数

矩阵 $\mathbf{A}$ 的**条件数**衡量涉及 $\mathbf{A}$ 的任何计算在数值上有多稳定。其定义如下：

$$
\kappa(\mathbf{A}) \triangleq \|\mathbf{A}\| \cdot \|\mathbf{A}^{-1}\|
\tag{C.45}
$$

其中 $\|\mathbf{A}\|$ 是矩阵的范数。我们可以证明 $\kappa(\mathbf{A}) \ge 1$。（条件数取决于我们使用哪种范数；除非另有说明，否则我们假定使用 $\ell_2$ 范数。）

如果 $\kappa(\mathbf{A})$ 很小（接近 1），我们就说 $\mathbf{A}$ 是**良态的**；如果 $\kappa(\mathbf{A})$ 很大，则称其为**病态的**。大的条件数意味着 $\mathbf{A}$ 接近奇异。与行列式的大小相比，这是衡量接近奇异程度的更好指标。例如，假设 $\mathbf{A} = 0.1\,\mathbf{I}_{100 \times 100}$。此时 $\det(\mathbf{A}) = 10^{-100}$，这似乎表明 $\mathbf{A}$ 接近奇异，但 $\kappa(\mathbf{A}) = 1$，这意味着 $\mathbf{A}$ 是良态的，反映了 $\mathbf{A}\mathbf{x}$ 只是将 $\mathbf{x}$ 的元素按 $0.1$ 进行缩放这一事实。

为了更好地理解条件数，考虑线性方程组 $\mathbf{A}\mathbf{x} = \mathbf{b}$。如果 $\mathbf{A}$ 是非奇异的，则唯一解为 $\mathbf{x} = \mathbf{A}^{-1}\mathbf{b}$。假设我们将 $\mathbf{b}$ 改为 $\mathbf{b} + \Delta\mathbf{b}$；这对 $\mathbf{x}$ 会有什么影响？新的解必须满足

$$
\mathbf{A}(\mathbf{x} + \Delta\mathbf{x}) = \mathbf{b} + \Delta\mathbf{b}
\tag{C.46}
$$

其中

$$
\Delta\mathbf{x} = \mathbf{A}^{-1}\Delta\mathbf{b}
\tag{C.47}
$$

如果很小的 $\Delta\mathbf{b}$ 导致很小的 $\Delta\mathbf{x}$，我们就说 $\mathbf{A}$ 是**良态的**；否则我们就说 $\mathbf{A}$ 是**病态的**。

例如，假设

$$
\mathbf{A} = \frac{1}{2} \begin{pmatrix} 1 & 1 \\ 1+10^{-10} & 1-10^{-10} \end{pmatrix}, \quad
\mathbf{A}^{-1} = \begin{pmatrix} 1-10^{10} & 10^{10} \\ 1+10^{10} & -10^{10} \end{pmatrix}
\tag{C.48}
$$

对于 $\mathbf{b} = (1, 1)$，解为 $\mathbf{x} = (1, 1)$。如果我们将 $\mathbf{b}$ 改变 $\Delta\mathbf{b}$，解变为

$$
\Delta\mathbf{x} = \mathbf{A}^{-1}\Delta\mathbf{b}
= \begin{pmatrix} \Delta b_1 - 10^{10}(\Delta b_1 - \Delta b_2) \\ \Delta b_1 + 10^{10}(\Delta b_1 - \Delta b_2) \end{pmatrix}
\tag{C.49}
$$

因此，$\mathbf{b}$ 的微小变化可能导致 $\mathbf{x}$ 的极其巨大的变化，因为 $\mathbf{A}$ 是病态的（$\kappa(\mathbf{A}) = 2 \times 10^{10}$）。

在 $\ell_2$ 范数的情况下，条件数等于最大奇异值与最小奇异值之比（奇异值在附录 C.5 中定义）；此外，奇异值是 $\mathbf{A}^{\top}\mathbf{A}$ 的特征值的平方根：

$$
\kappa(\mathbf{A}) = \frac{\sigma_{\max}}{\sigma_{\min}} = \sqrt{\frac{\lambda_{\max}}{\lambda_{\min}}}
\tag{C.50}
$$

我们可以通过考虑二次目标函数 $f(\mathbf{x}) = \mathbf{x}^{\top}\mathbf{A}\mathbf{x}$ 来进一步理解条件数。如果我们绘制该函数的水平集，它将是椭圆形的，如第 C.4.4 节所示。随着 $\mathbf{A}$ 的条件数增大，椭圆沿某些方向变得越来越拉长，对应于函数空间中一条非常狭窄的谷。如果 $\kappa = 1$（可能的最小值），水平集将是圆形的。

## C.1.5 特殊类型的矩阵

在本节中，我们将列出一些具有各种结构形式的常见矩阵类型。

### C.1.5.1 对角矩阵

**对角矩阵**是所有非对角线元素均为 0 的矩阵。这通常记为 $\mathbf{D} = \operatorname{diag}(d_1, d_2, \dots, d_n)$，即

$$
\mathbf{D} = \begin{pmatrix}
d_1 & 0 & \cdots & 0 \\
0 & d_2 & \cdots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & d_n
\end{pmatrix}
\tag{C.51}
$$

**单位矩阵**，记为 $\mathbf{I} \in \mathbb{R}^{n \times n}$，是对角线上为 1、其余位置为 0 的方阵，$\mathbf{I} = \operatorname{diag}(1, 1, \dots, 1)$。它有这样的性质：对于所有 $\mathbf{A} \in \mathbb{R}^{n \times n}$，

$$
\mathbf{A}\mathbf{I} = \mathbf{A} = \mathbf{I}\mathbf{A}
\tag{C.52}
$$

其中 $\mathbf{I}$ 的大小由 $\mathbf{A}$ 的维度决定，以便可以进行矩阵乘法。

我们可以使用 $\mathbf{d} = \operatorname{diag}(\mathbf{D})$ 从矩阵中提取对角向量。我们可以通过写成 $\mathbf{D} = \operatorname{diag}(\mathbf{d})$ 将向量转换为对角矩阵。

**分块对角**矩阵是主对角线上的元素为矩阵、其余位置为 0 的矩阵，例如，

$$
\begin{pmatrix} \mathbf{A} & \mathbf{0} \\ \mathbf{0} & \mathbf{B} \end{pmatrix}
\tag{C.53}
$$

**带状对角矩阵**仅在对角线以及对角线两侧的 $k$ 条对角线上有非零元素，其中 $k$ 是带宽。例如，一个**三对角** $6 \times 6$ 矩阵看起来像这样：

$$
\begin{bmatrix}
A_{11} & A_{12} & 0 & \cdots & \cdots & 0 \\
A_{21} & A_{22} & A_{23} & \ddots & \ddots & \vdots \\
0 & A_{32} & A_{33} & A_{34} & \ddots & \vdots \\
\vdots & \ddots & A_{43} & A_{44} & A_{45} & 0 \\
\vdots & \ddots & \ddots & A_{54} & A_{55} & A_{56} \\
0 & \cdots & \cdots & 0 & A_{65} & A_{66}
\end{bmatrix}
\tag{C.54}
$$

### C.1.5.2 三角矩阵

**上三角矩阵**仅在对角线上及其上方有非零元素。**下三角矩阵**仅在对角线上及其下方有非零元素。三角矩阵有一个有用的性质：$\mathbf{A}$ 的对角线元素就是 $\mathbf{A}$ 的特征值，因此行列式等于对角线元素的乘积：$\det(\mathbf{A}) = \prod_i A_{ii}$。

### C.1.5.3 正定矩阵

给定方阵 $\mathbf{A} \in \mathbb{R}^{n \times n}$ 和向量 $\mathbf{x} \in \mathbb{R}^n$，标量值 $\mathbf{x}^{\top}\mathbf{A}\mathbf{x}$ 被称为**二次型**。显式写出，我们可以看到

$$
\mathbf{x}^{\top}\mathbf{A}\mathbf{x}
= \sum_{i=1}^{n} \sum_{j=1}^{n} A_{ij} x_i x_j.
\tag{C.55}
$$

