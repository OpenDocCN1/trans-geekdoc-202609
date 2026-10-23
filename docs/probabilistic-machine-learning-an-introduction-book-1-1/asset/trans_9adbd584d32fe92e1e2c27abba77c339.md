
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_825_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_825_1.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_825_2.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_825_3.png)

图 C.9：图像的低秩近似。左上：原始图像大小为 200 × 320，因此秩为 200。后续图像的秩分别为 2、5 和 20。由 svd_image_demo.py 生成。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_825_4.png)

图 C.10：小丑图像的前 100 个对数奇异值（实红线），以及通过随机打乱像素得到的数据矩阵（点状绿线）。由 svd_image_demo.py 生成。改编自 [HTF09] 的图 14.24。

### C.5.5 Truncated SVD

设 A = USV^T 为 A 的 SVD，且 Â_K = U_K S_K V_K^⊤，其中我们使用 U 和 V 的前 K 列。可以证明它是最佳秩 K 近似，在最小化 ||A - Â_K||_F^2 的意义上。

如果 K = r = rank(A)，则该分解不会引入误差。但如果 K < r，我们会产生一定误差。这称为截断 SVD。如果奇异值迅速衰减，如自然数据中常见（参见例如图 C.10），误差将很小。使用秩 K 近似表示 N × D 矩阵所需的总参数数为

NK + KD + K = K(N + D + 1) (C.185)

例如，考虑图 C.9（左上）中的 200 × 320 像素图像。它包含 64,000 个数字。我们看到秩为 20 的近似，仅用 (200 + 320 + 1) × 20 = 10,420 个数字就是一个非常好的近似。

可以证明该近似的误差为

$$\|\mathbf{A} - \hat{\mathbf{A}}\|_F = \sum_{k=K+1}^{r} \sigma_k \tag{C.186}$$

其中 $\sigma_k$ 是 $\mathbf{A}$ 的第 $k$ 个奇异值。此外，可以证明 SVD 为矩阵提供了最佳秩 $K$ 近似（在最小化上述 Frobenius 范数的意义上最佳）。

## C.6 Other matrix decompositions

在本节中，我们简要回顾一些其他有用的矩阵分解。

### C.6.1 LU factorization

我们可以将任意方阵 $\mathbf{A}$ 分解为一个下三角矩阵 $\mathbf{L}$ 和一个上三角矩阵 $\mathbf{U}$ 的乘积。例如，

$$\begin{bmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{bmatrix} = \begin{bmatrix} l_{11} & 0 & 0 \\ l_{21} & l_{22} & 0 \\ l_{31} & l_{32} & l_{33} \end{bmatrix} \begin{bmatrix} u_{11} & u_{12} & u_{13} \\ 0 & u_{22} & u_{23} \\ 0 & 0 & u_{33} \end{bmatrix}. \tag{C.187}$$

一般情况下，在创建该分解之前可能需要对矩阵中的条目进行置换。为了解释这一点，假设 $a_{11}=0$。由于 $a_{11}=l_{11}u_{11}$，这意味着 $l_{11}$ 或 $u_{11}$ 或两者都必须为零，但这将意味着 $\mathbf{L}$ 或 $\mathbf{U}$ 是奇异的。为避免这种情况，算法的第一步可以简单地重新排序行，使第一个元素非零。这对后续步骤重复进行。我们可以用

$$\mathbf{P}\mathbf{A} = \mathbf{L}\mathbf{U} \tag{C.188}$$

表示该过程

其中 $\mathbf{P}$ 是一个置换矩阵，即一个方二进制矩阵，其中 $P_{ij}=1$ 当且仅当行 $j$ 被置换到行 $i$。这称为 **partial pivoting.**

### C.6.2 QR decomposition

假设我们有 $\mathbf{A} \in \mathbb{R}^{m\times n}$ 表示一组线性无关的基向量（因此 $m \ge n$），并且我们想要找到一系列标准正交向量 $\mathbf{q}_1,\mathbf{q}_2,\dots$ 来张成 $\operatorname{span}(\mathbf{a}_1),\operatorname{span}(\mathbf{a}_1,\mathbf{a}_2)$ 等的逐次子空间。换句话说，我们想要找到向量 $\mathbf{q}_j$ 和系数 $r_{ij}$ 使得

$$\begin{pmatrix} \mathbf{a}_1 & \mathbf{a}_2 & \cdots & \mathbf{a}_n \end{pmatrix} = \begin{pmatrix} \mathbf{q}_1 & \mathbf{q}_2 & \cdots & \mathbf{q}_n \end{pmatrix} \begin{pmatrix} r_{11} & r_{12} & \cdots & r_{1n} \\ & r_{22} & \cdots & r_{2n} \\ & & \ddots & \\ & & & r_{nn} \end{pmatrix} \tag{C.189}$$

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_827_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_827_1.png)

*图 C.11：* QR 分解的说明，**A = QR**，其中 **Q**^T **Q = I** 且 **R** 为上三角。*(a)* 高瘦矩阵。阴影部分在经济尺寸版本中不计算，因为不需要。*(b)* 短宽矩阵。

我们可以写成

**a**₁ = r₁₁ **q**₁  (C.190)
**a**₂ = r₁₂ **q**₁ + r₂₂ **q**₂  (C.191)
⋮
**a**ₙ = r₁ₙ **q**₁ + ⋯ + rₙₙ **q**ₙ  (C.192)

所以我们看到 **q**₁ 张成 **a**₁ 的空间，**q**₁ 和 **q**₂ 张成 {**a**₁, **a**₂} 的空间，等等。

在矩阵记法中，我们有

**A = Q̂ R̂**  (C.193)

其中 **Q̂** 是具有标准正交列的 *m × n* 矩阵，**R̂** 是 *n × n* 且为上三角。这称为 **reduced QR** 或 **economy sized QR** 分解 **A**；参见图 C.11。

完整的 QR 分解在 **Q̂** 后附加额外的 *m − n* 个标准正交列，使其成为方正交矩阵 **Q**，满足 **Q Q**^T = **Q**^T **Q = I**。此外，我们在 **R̂** 后附加全零行，使其成为仍为上三角的 *m × n* 矩阵，称为 **R**：参见图 C.11。**R** 中的零条目“消去”了 **Q** 中的新列，因此结果与 **Q̂ R̂** 相同。

QR 分解通常用于求解线性方程组，如我们在 Sec. 11.2.2.3 中讨论的。

### C.6.3 Cholesky decomposition

任何对称正定矩阵都可以分解为 **A = R**^T **R**，其中 **R** 是上三角且对角元素为实数正数。（这也可以写成 **A = L L**^T，其中 **L = R**^T 为下三角。）这称为 **Cholesky factorization** 或 **matrix square root**。在 NumPy 中，这由 `np.linalg.cholesky` 实现。该操作的计算复杂度为 *O(V³)*，其中 *V* 是变量数，但对于稀疏矩阵可能更低。下面我们给出该分解的一些应用。

### C.7.1 Solving square systems

在 $m = n$ 的情况下，我们可以通过计算 LU 分解 **A** = **LU** 来求解 **x**，然后按如下步骤进行：

**A x = b**  (C.200)
**L U x = b**  (C.201)
**U x = L⁻¹ b ≜ y**  (C.202)
**x = U⁻¹ y**  (C.203)

关键点是 **L** 和 **U** 都是三角矩阵，因此我们可以避免取矩阵逆，而使用称为 **backsubstitution** 的方法。

特别地，我们可以不取逆而按如下方式求解 **y = L⁻¹ b**。首先我们写

$\begin{pmatrix} L_{11} & & \\ L_{21} & L_{22} & \\ & \ddots & \\ L_{n1} & L_{n2} & \cdots & L_{nn} \end{pmatrix} \begin{pmatrix} y_1 \\ \vdots \\ y_n \end{pmatrix} = \begin{pmatrix} b_1 \\ \vdots \\ b_n \end{pmatrix}$  (C.204)

因此我们可以先求解 $L_{nn} y_n = b_n$ 来找到 $y_n$。然后我们将其代入求解

$L_{n-1,n-1} y_{n-1} + L_{n-1,n} y_n = b_{n-1}$  (C.205)

求 $y_{n-1}$，等等。该过程通常用 **backslash operator** 表示，**y = L \ b**。一旦我们得到 **y**，我们就可以以类似的方式使用回代求解 **x = U⁻¹ y**。

### C.7.2 Solving underconstrained systems (least norm estimation)

在本节中，我们考虑欠约束的情况，其中 $m < n$。我们假设行线性无关，因此 **A** 是满秩的。

当 $m < n$ 时，存在多个可能解，其形式为

$\{\mathbf{x} : \mathbf{A x} = \mathbf{b}\} = \{\mathbf{x}_p + \mathbf{z} : \mathbf{z} \in \text{nullspace}(\mathbf{A})\}$  (C.206)

其中 $\mathbf{x}_p$ 是任意特定解。标准做法是选择具有最小 $\ell_2$ 范数的特定解，即

$\hat{\mathbf{x}} = \arg\min_{\mathbf{x}} \|\mathbf{x}\|_2^2 \text{ s.t. } \mathbf{A x} = \mathbf{b}$  (C.207)

我们可以使用 *right* 伪逆计算最小范数解：

$\mathbf{x}_{\text{pinv}} = \mathbf{A}^\top (\mathbf{A A}^\top)^{-1} \mathbf{b}$  (C.208)

为了解释这一点，假设 **x** 是另一个解，因此 **A x = b**，且 **A(x - x_pinv) = 0**。于是

$(\mathbf{x} - \mathbf{x}_{\text{pinv}})^\top \mathbf{x}_{\text{pinv}} = (\mathbf{x} - \mathbf{x}_{\text{pinv}})^\top \mathbf{A}^\top (\mathbf{A A}^\top)^{-1} \mathbf{b} = (\mathbf{A}(\mathbf{x} - \mathbf{x}_{\text{pinv}}))^\top (\mathbf{A A}^\top)^{-1} \mathbf{b} = 0$  (C.209)
