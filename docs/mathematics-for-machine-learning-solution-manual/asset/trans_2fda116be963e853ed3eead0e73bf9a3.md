
E3 的维度为 1（如上所述，它也不可能为其他值），并且

$E_1 = \text{span}\begin{bmatrix}-1\\-1\\-1\end{bmatrix}.$

（iv）因此，我们可以通过拼接特征空间的生成向量来找到新基 $P$。如果考虑矩阵

$\boldsymbol{P} = \begin{bmatrix}-1 & 1 & 1\\-1 & -1 & 0\\-1 & 0 & -1\end{bmatrix},$

（其列由基 $P$ 的基向量组成），那么我们的自同态相对于这个新基将具有对角形式：$\boldsymbol{D} = \text{diag}[3, 0, 0]$。提醒一下，$\text{diag}[3, 0, 0]$ 指的是对角线上为 $3, 0, 0$ 的 $3 \times 3$ 对角矩阵。注意，对角形式并不唯一，它取决于特征向量在新基中的顺序。例如，我们可以定义另一个由与 $\boldsymbol{P}$ 相同但顺序不同的向量组成的矩阵 $\boldsymbol{Q}$：

$\boldsymbol{Q} = \begin{bmatrix}1 & -1 & 1\\-1 & -1 & 0\\0 & -1 & -1\end{bmatrix}.$

如果我们使用这个矩阵，我们的自同态将具有另一种对角形式：$\boldsymbol{D}' = \text{diag}[0, 3, 0]$。持怀疑态度的学生可以验证 $\boldsymbol{Q}^{-1} \boldsymbol{A} \boldsymbol{Q} = \boldsymbol{D}'$ 且 $\boldsymbol{P}^{-1} \boldsymbol{A} \boldsymbol{P} = \boldsymbol{D}$。

### c.

$\boldsymbol{A} = \begin{bmatrix}5 & 4 & 2 & 1\\0 & 1 & -1 & -1\\-1 & -1 & 3 & 0\\1 & 1 & -1 & 2\end{bmatrix}$

$p(\lambda) = (\lambda - 1)(\lambda - 2)(\lambda - 4)^2$

$E_1 = \text{span}\begin{bmatrix}-1\\1\\0\\0\end{bmatrix},\quad E_2 = \text{span}\begin{bmatrix}1\\-1\\0\\1\end{bmatrix},\quad E_4 = \text{span}\begin{bmatrix}1\\0\\-1\\1\end{bmatrix}.$

此处我们看到 $\dim(E_4) = 1 \neq 2$（即特征值 4 的代数重数）。因此，$\boldsymbol{A}$ 不可对角化。

### d.

$\boldsymbol{A} = \begin{bmatrix}5 & -6 & -6\\-1 & 4 & 2\\3 & -6 & -4\end{bmatrix}$

（i）我们计算特征多项式 $p(\lambda)=\det(A-\lambda I)$ 如下：

$p(\lambda)=\begin{vmatrix}5-\lambda & -6 & -6\\ -1 & 4-\lambda & 2\\ 3 & -6 & -4-\lambda\end{vmatrix}$
$= (5-\lambda)(4-\lambda)(-4-\lambda)-36-36+18(4-\lambda)+12(5-\lambda)-6(-4-\lambda)$
$= -\lambda^3+5\lambda^2-8\lambda+4=(1-\lambda)(2-\lambda)^2,$

其中我们使用了萨鲁斯法则。特征多项式分解为线性因子，特征值为 $\lambda_1=1,\lambda_2=2$，其（代数）重数分别为 1 和 2。

（ii）如果特征空间的维数与相应特征值的重数相同，则矩阵可对角化。特征空间的维数是 $\ker(A-\lambda_i I)$ 的维数，其中 $\lambda_i$ 是特征值（此处为 1,2）。若要简单检查矩阵是否可对角化，只需计算 $A-\lambda_i I$ 的秩 $r_i$ 即可，因为特征空间的维数为 $n-r_i$（秩-零化度定理）。

让我们研究 $E_2$ 并对 $A-2I$ 应用高斯消元法：

$\begin{bmatrix}3 & -6 & -6\\ -1 & 2 & 2\\ 3 & -6 & -6\end{bmatrix}.$ (4.1)

（iii）我们可以立即看出该矩阵的秩为 1，因为第一行和第三行是第二行的三倍。因此，特征空间的维数为 $\dim(E_2)=3-1=2$，这与特征多项式 $p(\lambda)$ 中特征值 $\lambda=2$ 的代数重数一致。此外，我们知道 $E_1$ 的维数为 1，因为它不能超过其代数重数，而特征空间的维数至少为 1。因此，$A$ 是可对角化的。

（iv）对角矩阵很容易确定，因为它的对角线上只需包含特征值（以及相应的重数）：

$D=\begin{bmatrix}1 & 0 & 0\\ 0 & 2 & 0\\ 0 & 0 & 2\end{bmatrix}.$

（v）我们需要确定一个基，使得变换矩阵在该基下为对角矩阵。我们知道由特征向量组成的基恰好具有这一性质。因此，我们需要确定所有特征值的特征向量。请记住，如果 $x$ 满足 $Ax=\lambda x \iff (A-\lambda I)x=0$，则 $x$ 是特征值 $\lambda$ 的特征向量。因此，我们需要找到特征空间 $E_1,E_2$ 的基向量。

对于 $E_1=\ker(A-I)$，我们得到：

$\begin{bmatrix}4 & -6 & -6\\ -1 & 3 & 2\\ 3 & -6 & -5\end{bmatrix}+4R_2\quad\sim\quad\begin{bmatrix}0 & 6 & 2\\ -1 & 3 & 2\\ 0 & 3 & 1\end{bmatrix}\cdot(1/6)$
$\cdot(-1)\text{与 }R_1\text{ 交换}\quad -\tfrac12 R_1$
~→ $\begin{bmatrix}1 & -3 & -2\\0 & 1 & \frac13\\0 & 0 & 0\end{bmatrix}$ +3R₂ ~→ $\begin{bmatrix}1 & 0 & -1\\0 & 1 & \frac13\\0 & 0 & 0\end{bmatrix}$

该矩阵的秩为 2。由于 3 − 2 = 1，可知 dim(E₁) = 1，这与特征多项式中特征值 λ = 1 的代数重数一致。

（vi）从行最简形可以看出 $E_1 = \text{span}\left[\begin{matrix}3\\-1\\3\end{matrix}\right]$，我们的第一个特征向量为 $[3, -1, 3]^{\top}$。

（vii）我们继续确定 $E_2$ 的一个基，这将给出我们需要的另外两个基向量（记住 dim$(E_2)=2$）。从 (4.1) 我们（几乎）立即得到行最简形 $\begin{bmatrix}1 & -2 & -2\\0 & 0 & 0\\0 & 0 & 0\end{bmatrix}$，相应的特征空间为 $E_2 = \text{span}\left[\begin{matrix}2\\1\\0\end{matrix}, \begin{matrix}2\\0\\1\end{matrix}\right]$。

（viii）总的来说，使得 $A$ 具有对角形式 $D$ 的一个有序基由所有特征向量组成，即 $B = \left( \begin{bmatrix}3\\-1\\3\end{bmatrix}, \begin{bmatrix}2\\1\\0\end{bmatrix}, \begin{bmatrix}2\\0\\1\end{bmatrix} \right)$。

## 4.8 求矩阵 $A = \begin{bmatrix}3 & 2 & 2\\2 & 3 & -2\end{bmatrix}$ 的 SVD。 $A = \underbrace{\begin{bmatrix}\frac{1}{\sqrt2} & -\frac{1}{\sqrt2}\\\frac{1}{\sqrt2} & \frac{1}{\sqrt2}\end{bmatrix}}_{=U} \underbrace{\begin{bmatrix}5 & 0 & 0\\0 & 3 & 0\end{bmatrix}}_{=\Sigma} \underbrace{\begin{bmatrix}\frac{1}{\sqrt2} & -\frac{3}{\sqrt2} & -\frac{2}{3}\\\frac{1}{\sqrt2} & \frac{3}{\sqrt2} & \frac{2}{3}\\0 & -\frac{2\sqrt2}{3} & \frac{1}{3}\end{bmatrix}}_{=V}$

## 4.9 求矩阵 $A = \begin{bmatrix}2 & 2\\-1 & 1\end{bmatrix}$ 的奇异值分解。

（i）计算对称化矩阵 \(A^{\mathsf T}A\)。我们首先计算对称化矩阵

\[
A^{\mathsf T}A=
\begin{bmatrix}2&-1\\2&1\end{bmatrix}
\begin{bmatrix}2&2\\-1&1\end{bmatrix}
=
\begin{bmatrix}5&3\\3&5\end{bmatrix}.
\tag{4.2}
\]

（ii）从 \(A^{\mathsf T}A\) 求右奇异向量和奇异值。\(A^{\mathsf T}A\) 的特征多项式为

\[
(5-\lambda)^2-9=\lambda^2-10\lambda+16=0.
\tag{4.3}
\]

这给出特征值，按绝对值从大到小排序，\(\lambda_1=8\) 和 \(\lambda_2=2\)。相应的归一化特征向量分别为

\[
v_1=\begin{bmatrix}\frac{1}{\sqrt{2}}\\\frac{1}{\sqrt{2}}\end{bmatrix}
\quad\text{并且}\quad
v_2=\begin{bmatrix}\frac{1}{\sqrt{2}}\\-\frac{1}{\sqrt{2}}\end{bmatrix}.
\tag{4.4}
\]

因此我们得到了右奇异正交矩阵

\[
V=[v_1,v_2]=
\begin{bmatrix}
\frac{1}{\sqrt{2}}&\frac{1}{\sqrt{2}}\\
\frac{1}{\sqrt{2}}&-\frac{1}{\sqrt{2}}
\end{bmatrix}.
\tag{4.5}
\]

（iii）确定奇异值。我们通过特征值的平方根得到两个奇异值：\(\sigma_1=\sqrt{\lambda_1}=\sqrt{8}=2\sqrt{2}\) 和 \(\sigma_2=\sqrt{\lambda_2}=\sqrt{2}\)。我们构造奇异值对角矩阵为

\[
\Sigma=
\begin{bmatrix}\sigma_1&0\\0&\sigma_2\end{bmatrix}
=
\begin{bmatrix}2\sqrt{2}&0\\0&\sqrt{2}\end{bmatrix}.
\tag{4.6}
\]

（iv）求左奇异向量。我们必须用 \(A\) 映射两个特征向量 \(v_1,v_2\)。这会得到两个自洽方程，使我们能够找到正交特征向量 \(u_1,u_2\)：

\[
Av_1=(\sigma_1u_1v_1^{\mathsf T})v_1=\sigma_1u_1(v_1^{\mathsf T}v_1)=\sigma_1u_1=
\begin{bmatrix}2\sqrt{2}\\0\end{bmatrix}.
\]

\[
Av_2=(\sigma_2u_2v_2^{\mathsf T})v_2=\sigma_2u_2(v_2^{\mathsf T}v_2)=\sigma_2u_2=
\begin{bmatrix}0\\\sqrt{2}\end{bmatrix}.
\]

我们将左奇异向量分别除以各自的奇异值来进行归一化，得到 \(u_1=\begin{bmatrix}1\\0\end{bmatrix}\) 和 \(u_2=\begin{bmatrix}0\\1\end{bmatrix}\)，从而得到

\[
U=[u_1,u_2]=
\begin{bmatrix}1&0\\0&1\end{bmatrix}.
\tag{4.7}
\]

（v）组装左/右奇异向量和奇异值。\(A\) 的 SVD 为

\[
A=U\Sigma V^{\mathsf T}=
\begin{bmatrix}1&0\\0&1\end{bmatrix}
\begin{bmatrix}\sqrt{8}&0\\0&\sqrt{2}\end{bmatrix}
\begin{bmatrix}
\frac{1}{\sqrt{2}}&\frac{1}{\sqrt{2}}\\
\frac{1}{\sqrt{2}}&-\frac{1}{\sqrt{2}}
\end{bmatrix}.
\]

