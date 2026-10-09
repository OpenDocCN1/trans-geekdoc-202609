
线性混合，其中 $S$ 是源图像集的矩阵，每个行向量代表一个源图像，$A$ 是混合矩阵。目标是找到恢复矩阵 $W$，并令 $WT=WAS=U$，从而得到使独立源图像得以再现的输出矩阵：$U=WT=WAS$。获得 $U$ 后，利用其行向量作为特征向量构建特征空间，每幅图像都由独立图像的线性组合表示。设 $F^{P}$ 为待识别图像。我们有 $F^{P}=\alpha_{1}U_{1}+\alpha_{2}U_{2}+\cdots+\alpha_{n}U_{n}$，其中 $\alpha=(\alpha_{1}, \alpha_{2}, \ldots, \alpha_{n})$ 是图像在特征空间中的组合系数。我们使用公式 $\alpha=(F^{P})^{T}\times(U)^{+}$，其中 $(U)^{+}$ 表示 $U$ 的伪逆，$(U)^{+}=U(UT^{T})^{-1}$。进一步地，利用新特征空间的坐标，我们可以使用分类器对图像进行分类。

二维源图像 $A$ 天然可以构建为对应的辛矩阵（参见附录 17.4）。设 $B$ 为待检测图像，并使用与处理源图像相同的方法。我们提取图像 $B$ 并构建对应检测图像的辛矩阵。由于图像 $A$ 和 $B$ 的表示矩阵在不同的辛基（octyl groups，此处译为辛基或辛群基，原文似为 symplectic bases/groups 的误写或特定术语）下是不同的，根据共形对称标准矩阵的变换性质，我们可以得到由 $A$ 和 $B$ 组成的矩阵 $A_{1}$ 和 $B_{1}$，其形式为 $\begin{pmatrix} A_{1} & O \\ O & B_{1} \end{pmatrix}$ 的辛矩阵，并使用标准收缩矩阵的简化方法对该矩阵 $\begin{pmatrix} A_{1} & O \\ O & B_{1} \end{pmatrix}$ 进行简化。此外，冯等人 [1] 描述了现有辛矩阵的特殊形式数量。如果辛矩阵处于特殊形式，它可以用作学习过程的训练样本。其他图像应通过相同方法处理，以实现分类目的。考虑辛群的特殊形式，

$M=\begin{pmatrix} A_{1} & O \\ O & B_{1} \end{pmatrix}\in Sp(2n)$。

我们可以得到

$M=\begin{pmatrix} A_{1} & O \\ O & A^{T^{-1}_{1}} \end{pmatrix}, A_{1}\in GL(n, R)$

其中 $A_{1}$ 是源图像的矩阵，其行列式也被计算为

$|M|=|A_{1}||A^{T^{-1}_{1}}|=1$。

在此，我们可以看到

$A_{1}\in GL(n, R)\Rightarrow A_{1}=TP, T^{T}T=I_{n}, P^{\prime}=P>0$（正定矩阵）。

通过计算，我们可以看到

$\begin{bmatrix} p \\ q \end{bmatrix}\in R^{2n}\rightarrow M\begin{bmatrix} p \\ q \end{bmatrix}=\begin{bmatrix} A_{1}p \\ \big(A^{-1}_{1}\big)^{\prime}q \end{bmatrix}\in R^{2n}$。

组合矩阵经过变换处理后得到

$$\begin{bmatrix} A_1 & 0 \\ 0 & A_1^{-1} \end{bmatrix} = \begin{bmatrix} T & 0 \\ 0 & T \end{bmatrix}\begin{bmatrix} P & 0 \\ 0 & P^{-1} \end{bmatrix}$$

其中

$$\begin{bmatrix} T & 0 \\ 0 & T \end{bmatrix} \in O(n) \subset U(n)O(n) = \left\{ \begin{bmatrix} T & 0 \\ 0 & T \end{bmatrix} | T^\prime T = I_n \right\}$$

$$= U(n) \cap \mathrm{GL}(n, \mathbb{R})\left\{ \begin{bmatrix} P & 0 \\ 0 & P^{-1} \end{bmatrix} | P^\prime = P > 0 \right\}\ 。$$

我们可以看到，辛矩阵可以分解为两个辛矩阵的乘积，所得的辛矩阵可以作为检测结果的矩阵。如果由待检查的另一幅图像组成的矩阵与通过源图像 $A$ 的共形变换获得的辛矩阵在形式上相同，则待检查图像与源图像一致，从而达到分类的目的。

### 3.2.2 辛群分类器的设计方法

在辛分类器的设计中，首先应将分类样本表示为辛群，然后利用辛群的张量表示将样本构建为对应的辛矩阵。简化辛矩阵，得到相应的训练特征，作为学习过程的训练样本。最后，以相同方式处理检测样本，并使用辛群分类算法获得样本特征。如果两类特征匹配，则输出结果。辛群分类器的设计方法可分为两个步骤：样本的辛矩阵表示以及辛空间下矩阵的简化方法。样本以辛群的张量形式表示；然后，给出样本的辛矩阵表示。下一步是简化辛矩阵。

#### 3.2.2.1 辛矩阵的简化方法

辛几何是相空间的几何学。辛空间（即相空间）具有特定的辛结构，依赖于双线性反对称非退化内积，即内积 $[x, y] = <x, Jy>$，其中

$$J = J_{2n} = \begin{bmatrix} 0 & +I_n \\ -I_n & 0 \end{bmatrix}\ 。$$

当 $n = 1$ 时，

$$[x, y] = \begin{bmatrix} x_1 & y_1 \\ x_2 & y_2 \end{bmatrix}\ 。$$

因此，与欧几里得空间相比，辛空间中的度量是面积度量而非长度度量，并且辛空间中存在正交概念，这是辛空间与欧几里得空间之间的本质区别。由于在奇数维中不存在经典意义上的非退化反对称阵列，此处的辛空间是偶数维的。辛几何中的辛变换本质上是非线性变换（也称为正则变换），适用于非线性系统处理。其特征值可以通过辛 QR 方法获得。辛 QR 与标准 QR 分解不同。其浮点运算量是原来的四分之一，且原始的 2n 维空间可以转换为 n 维空间。

**定理 3.2.** 任何矩阵都可以构建为哈密顿矩阵。对于矩阵 A，$\begin{bmatrix} A & O \\ 0 & -A^H \end{bmatrix}$ 是哈密顿矩阵 [22, 23]。

**定理 3.3.** 哈密顿矩阵在辛相似变换下保持不变 [22, 23]。

**定理 3.4.** 设 $H \in C^{2n\times 2n}$ 为哈密顿矩阵。则 $e^H$ 是辛矩阵 [2, 22, 23]。

**定理 3.5.** 设 $M = \begin{bmatrix} A_1 & B_1 \\ A_2 & B_2 \end{bmatrix} \in \mathrm{Sp}(2n)$。则 $M$ 可以分解为 $M = M_{2'}M_1M_2$，其中 $M_{2'} \in \mathrm{Sp}(2n)$，$M_1 \in \mathrm{Sp}_{2n}(2n)$，$M_2 \in \mathrm{Sp}_{2n}(2n)$。

*证明.*

$\begin{bmatrix} A_1 & B_1 \\ A_2 & B_2 \end{bmatrix} \begin{bmatrix} I & -A_1^{-1}B_1 \\ O & I \end{bmatrix} = \begin{bmatrix} A_1 & O \\ A_2 & B_2 - A_2A_1^{-1}B_1 \end{bmatrix}$

$\begin{bmatrix} I & O \\ -A_2A_1^{-1} & I \end{bmatrix} \begin{bmatrix} A_1 & O \\ A_2 & B_2 - A_2A_1^{-1}B_1 \end{bmatrix} = \begin{bmatrix} A_1 & O \\ O & B_2 - A_2A_1^{-1}B_1 \end{bmatrix}$

因为 $M = [A, B] \in \mathrm{Sp}(2n)$，$A^TJ B = I$ 且 $A'$ 是对称的，即

$A_1^tB_2 - A_2^tB_1 = I, A_2A_1^{-1} \in \mathrm{Sp}(2n)$

因此，

$A_1^{-1'} = B_2 - A_1^{-1}A_2B_1 = B_2 - (A_2A_1^{-1})^tB_1 = B_2 - A_2A_1^{-1}B_1$。

令

$M_1 = \begin{bmatrix} A_1 & O \\ O & B_2 - A_2A_1^{-1} \end{bmatrix} = \begin{bmatrix} A_1 & O \\ O & A_1^{-1'} \end{bmatrix} \in \mathrm{Sp}_{2n}(2n)$

$M_{2'} = \begin{bmatrix} I & O \\ -A_2A_1^{-1} & I \end{bmatrix} \in \mathrm{Sp}(2n); \quad M_2 = \begin{bmatrix} I & -A_1^{-1'}B_1 \\ O & I \end{bmatrix}^{-1} \in \mathrm{Sp}(2n)$；

因此，我们可以得到 $M = M_{2'}M_1M_2.$

**定理 3.6.** *任何辛矩阵都可以分解为三个特殊辛矩阵的乘积* [22, 23]：

$$M = M_0M_1M_2 \ ,\quad M_0, M_1, M_2 \in \mathrm{Sp}(2n) \ 。$$

*证明. 设* $M = [A, B] \in \mathrm{Sp}(2n)$。*则* $A \in U(n)$。*根据相关定理，存在* $M_0 \in \mathrm{Sp}(2n) = U(n)$ *使得*

$$A = M_0\begin{bmatrix}I & O \\ O & I \end{bmatrix}Q = M_0\begin{bmatrix}Q & O \\ O & Q'^{-1} \end{bmatrix} \ 。$$

*令*

$$B_1 = \begin{bmatrix}Q & O \\ O & Q'^{-1} \end{bmatrix}M_0^{-1}B \ ，$$

*即*

$$B = M_0\begin{bmatrix}Q & O \\ O & Q'^{-1} \end{bmatrix}\begin{bmatrix}C_1 \\ C_2 \end{bmatrix} \ 。$$

*因此，我们有*

$$\begin{aligned} M = [A, B] &= \left[ M_0\begin{bmatrix}Q & O \\ O & Q'^{-1} \end{bmatrix}\begin{bmatrix}I \\ O \end{bmatrix}, M_0\begin{bmatrix}Q & O \\ O & Q'^{-1} \end{bmatrix}\begin{bmatrix}C_1 \\ C_2 \end{bmatrix} \right] \\ &= M_0\begin{bmatrix}Q & O \\ O & Q'^{-1} \end{bmatrix}\begin{bmatrix}I & C_1 \\ O & C_2 \end{bmatrix} \in \mathrm{Sp}(2n) \\ &= M_0M_1M_2 \end{aligned}$$

*其中*

$$M_1 = \begin{bmatrix}Q & O \\ O & Q'^{-1} \end{bmatrix} \in \mathrm{Sp}(2n), M_2 = \begin{bmatrix}I & C_1 \\ O & C_2 \end{bmatrix} \in \mathrm{Sp}(2n) \ 。 \qquad \square$$

**定理 3.7.** *设* $S \in \mathbb{C}^{2n \times 2n}$ *为辛矩阵。则分解* $S = QR$，*其中* $Q$ *是辛酉矩阵，* $R$ *是上三角矩阵* [22, 23]。

**定理 3.8.** *两个辛矩阵的乘积是辛矩阵* [22, 23]。

对于哈密顿矩阵 $M$，我们可以使用辛相似变换来识别系统的特征值。此外，原始的 $2n$ 维空间可以转换为 $n$ 维空间。具体步骤如下：

- 令 $N = M^2 = \begin{bmatrix}A^T & G \\ F & -A \end{bmatrix}$
- 寻找一个辛矩阵 $Q$，并令 $Q^T N Q = \begin{bmatrix}B & R \\ O & B^T \end{bmatrix}$，其中 $B$ 是上 Hessenberg 矩阵（$b_{ij} = 0, i > j + 1$），且 $Q$ 是 Householder 矩阵 $H$。
- 通过辛 QR 分解方法计算 $\lambda(B) = \{ \mu_1, \ldots, \mu_n \}$。
- $\lambda_1 = \sqrt{\mu_i}, \lambda_{n+i} = -\lambda_i$。

