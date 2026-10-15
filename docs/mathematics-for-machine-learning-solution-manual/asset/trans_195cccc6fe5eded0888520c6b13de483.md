
类似地，

$\mathbf{A}\cdot(\mathbf{B}\cdot\mathbf{C}) = \begin{bmatrix}1 & x & z\\0 & 1 & y\\0 & 0 & 1\end{bmatrix}\cdot\begin{bmatrix}1 & \alpha + a & \gamma + \alpha\beta + c\\0 & 1 & \beta + b\\0 & 0 & 1\end{bmatrix} = \begin{bmatrix}1 & \alpha + a + x & \gamma + \alpha\beta + x\beta + c + x b + z\\0 & 1 & \beta + b + y\\0 & 0 & 1\end{bmatrix} = (\mathbf{A}\cdot\mathbf{B})\cdot\mathbf{C}.$

因此，$\cdot$ 是可结合的。

- 单位元：对于 $\mathcal{G}$ 中的所有 $\mathbf{A}$，我们有：$I_3\cdot\mathbf{A}=\mathbf{A}=\mathbf{A}\cdot I_3$，因此 $I_3$ 是单位元。
- 非交换性：我们证明 $\cdot$ 不是可交换的。考虑矩阵 $\mathbf{X},\mathbf{Y}\in\mathcal{G}$，其中 $\mathbf{X}=\begin{bmatrix}1&1&0\\0&1&0\\0&0&1\end{bmatrix}$，$\mathbf{Y}=\begin{bmatrix}1&0&0\\0&1&1\\0&0&1\end{bmatrix}$。 (2.5) 则 $\mathbf{X}\cdot\mathbf{Y}=\begin{bmatrix}1&1&1\\0&1&1\\0&0&1\end{bmatrix}$，$\mathbf{Y}\cdot\mathbf{X}=\begin{bmatrix}1&1&0\\0&1&1\\0&0&1\end{bmatrix}\neq\mathbf{X}\cdot\mathbf{Y}$。因此，$\cdot$ 不是可交换的。
- 逆元：设我们寻找 $\mathbf{A}$ 的右逆 $\mathbf{A}_r^{-1}$。这样的矩阵应满足 $\mathbf{A}\mathbf{A}_r^{-1}=I_3$。因此我们求解线性系统 $[\mathbf{A}|I_3]$，将其转化为 $[I_3|\mathbf{A}_r^{-1}]$：$\sim\begin{bmatrix}1&x&z&|&1&0&0\\0&1&y&|&0&1&0\\0&0&1&|&0&0&1\end{bmatrix}\to\begin{bmatrix}1&x&0&|&1&0&-z\\0&1&0&|&0&1&-y\\0&0&1&|&0&0&1\end{bmatrix}\to\begin{bmatrix}1&0&0&|&1&-x&xy-z\\0&1&0&|&0&1&-y\\0&0&1&|&0&0&1\end{bmatrix}$。因此，我们得到右逆 $\mathbf{A}_r^{-1}=\begin{bmatrix}1&-x&xy-z\\0&1&-y\\0&0&1\end{bmatrix}\in\mathcal{G}$。

由于逆元的唯一性，如果左逆 $\mathbf{A}_l^{-1}$ 存在，则它等于右逆。但由于 $\cdot$ 不是可交换的，

我们需要手动检查是否也有 $AA_r^{-1}=I_3$，我们接下来进行：

$$A_r^{-1}A=\begin{bmatrix}1&-x&-z+xy\\0&1&-y\\0&0&1\end{bmatrix}\begin{bmatrix}1&x&z\\0&1&y\\0&0&1\end{bmatrix}$$

$$=\begin{bmatrix}1&x-x&z-xy-z+xy\\0&1&y+y\\0&0&1\end{bmatrix}=I_3.$$

因此，$\mathcal{G}$ 的每个元素都有逆。总体而言，$(\mathcal{G},\cdot)$ 是一个非阿贝尔群。

## 2.4 计算以下矩阵乘积，如有可能：

- a. $$\begin{bmatrix}1&2\\4&5\\7&8\end{bmatrix}\begin{bmatrix}1&1&0\\0&1&1\\1&0&1\end{bmatrix}$$

该矩阵乘积未定义。请注意相邻维度必须匹配（即 $m\times n$ 矩阵需要从右侧乘以 $n\times p$ 矩阵，或从左侧乘以 $k\times m$ 矩阵）。

- b. $$\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}\begin{bmatrix}1&1&0\\0&1&1\\1&0&1\end{bmatrix}=\begin{bmatrix}4&3&5\\10&9&11\\16&15&17\end{bmatrix}$$

- c. $$\begin{bmatrix}1&1&0\\0&1&1\\1&0&1\end{bmatrix}\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}=\begin{bmatrix}5&7&9\\11&13&15\\8&10&12\end{bmatrix}$$

- d. $$\begin{bmatrix}1&2&1&2\\4&1&-1&-4\end{bmatrix}\begin{bmatrix}0&3\\1&-1\\2&1\\5&2\end{bmatrix}=\begin{bmatrix}14&6\\-21&2\end{bmatrix}$$

- e. $$\begin{bmatrix}0&3\\1&-1\\2&1\\5&2\end{bmatrix}\begin{bmatrix}1&2&1&2\\4&1&-1&-4\end{bmatrix}=\begin{bmatrix}12&3&-3&-12\\-3&1&2&6\\6&5&1&0\\13&12&3&2\end{bmatrix}$$

## 2.5 求 $x$ 的所有解集合 $S$，使以下非齐次线性系统 $Ax=b$ 成立，其中 $A$ 和 $b$ 定义如下：

- a. $$A=\begin{bmatrix}1&1&-1&-1\\2&5&-7&-5\\2&-1&1&3\\5&2&-4&2\end{bmatrix},\quad b=\begin{bmatrix}1\\-2\\4\\6\end{bmatrix}$$

我们对增广矩阵应用高斯消元

$$\begin{bmatrix}1&1&-1&-1&|&1\\2&5&-7&-5&|&-2\\2&-1&1&3&|&4\\5&2&-4&2&|&6\end{bmatrix}\xrightarrow{-2R_1}\begin{bmatrix}1&1&-1&-1&|&1\\0&3&-5&-3&|&-4\\0&-3&3&5&|&2\\0&-3&1&7&|&1\end{bmatrix}\xrightarrow{-\frac13R_2}\begin{bmatrix}1&0&\frac23&0&|&\frac73\\0&1&-\frac53&-1&|&-\frac43\\0&0&-2&2&|&-2\\0&0&-4&4&|&-3\end{bmatrix}\xrightarrow{-2R_3}\begin{bmatrix}1&0&\frac23&0&|&\frac73\\0&1&-\frac53&-1&|&-\frac43\\0&0&-2&2&|&-2\\0&0&0&0&|&1\end{bmatrix}$$

最终线性系统的最后一行表明方程组无解，因此 $S = \emptyset$。

b.

$$A = \begin{bmatrix}1&-1&0&0&1\\1&1&0&-3&0\\2&-1&0&1&-1\\-1&2&0&-2&-1\end{bmatrix},\quad b = \begin{bmatrix}3\\6\\5\\-1\end{bmatrix}$$

我们再次写出增广矩阵并应用高斯消元以得到简化行阶梯形：

$$\begin{bmatrix}1&-1&0&0&1&|&3\\1&1&0&-3&0&|&6\\2&-1&0&1&-1&|&5\\-1&2&0&-2&-1&|&-1\end{bmatrix}\xrightarrow{}\begin{bmatrix}1&-1&0&0&1&|&3\\0&2&0&-3&-1&|&3\\0&1&0&1&-3&|&-1\\0&1&0&-2&0&|&2\end{bmatrix}\xrightarrow{}\begin{bmatrix}1&0&0&1&-2&|&2\\0&1&0&1&-3&|&-1\\0&0&0&-5&5&|&5\\0&0&0&-3&3&|&3\end{bmatrix}\xrightarrow{}\begin{bmatrix}1&0&0&1&-2&|&2\\0&1&0&1&-3&|&-1\\0&0&0&1&-1&|&-1\\0&0&0&0&0&|&0\end{bmatrix}\xrightarrow{}\begin{bmatrix}1&0&0&0&-1&|&3\\0&1&0&0&-2&|&0\\0&0&0&1&-1&|&-1\end{bmatrix}$$

从简化行阶梯形我们应用“Minus-1 技巧”以得到以下系统：

$$\begin{bmatrix}1&0&0&0&-1&|&3\\0&1&0&0&-2&|&0\\0&0&-1&0&0&|&0\\0&0&0&1&-1&|&-1\\0&0&0&0&-1&|&0\end{bmatrix}$$

系统的右端给出我们一个特解，而对应于 -1 主元的列是解空间的方向。我们于是得到所有可能解的集合为

$\mathcal{S} := \{ x \in \mathbb{R}^6 : x = \begin{bmatrix}3\\0\\0\\-1\\0\end{bmatrix} + \lambda_1 \begin{bmatrix}0\\0\\-1\\0\\0\end{bmatrix} + \lambda_2 \begin{bmatrix}-1\\-2\\0\\-1\\-1\end{bmatrix} \mid \lambda_1,\lambda_2 \in \mathbb{R} \}$

## 2.6 使用高斯消元，求非齐次方程组 $Ax = b$ 的所有解，其中

$\boldsymbol{A} = \begin{bmatrix}0&1&0&0&1&0\\0&0&0&1&1&0\\0&1&0&0&0&1\end{bmatrix}, \quad \boldsymbol{b} = \begin{bmatrix}2\\-1\\1\end{bmatrix}$。

我们首先确定增广矩阵 $[A|b]$ 的简化行阶梯形。

$$\begin{bmatrix}0&1&0&0&1&0&|&2\\0&0&0&1&1&0&|&-1\\0&1&0&0&0&1&|&1\end{bmatrix} -R_1 \sim \begin{bmatrix}0&1&0&0&1&0&|&2\\0&0&0&1&1&0&|&-1\\0&0&0&0&-1&1&|&-1\end{bmatrix} +R_3 \sim \begin{bmatrix}0&1&0&0&0&1&|&1\\0&0&0&1&0&1&|&-2\\0&0&0&0&1&-1&|&1\end{bmatrix}$$

该增广矩阵现在处于简化行阶梯形。应用“Minus-1 技巧”给出以下增广矩阵：

$$\begin{bmatrix}-1&0&0&0&0&0&|&0\\0&1&0&0&0&1&|&1\\0&0&-1&0&0&0&|&0\\0&0&0&1&0&1&|&-2\\0&0&0&0&1&-1&|&1\\0&0&0&0&0&-1&|&0\end{bmatrix}$$

该增广矩阵的右端给出我们一个特解，而对应于 -1 主元的列张成解空间 $S$。因此，我们得到通解

$$S = \left\{ \begin{bmatrix}0\\1\\0\\-2\\1\\0\end{bmatrix} + \lambda_1 \begin{bmatrix}-1\\0\\0\\0\\0\\0\end{bmatrix} + \lambda_2 \begin{bmatrix}0\\0\\-1\\0\\0\\0\end{bmatrix} + \lambda_3 \begin{bmatrix}0\\1\\0\\1\\-1\\-1\end{bmatrix} \;\Big|\; \lambda_1,\lambda_2,\lambda_3 \in \mathbb{R} \right\}$$

现在，我们求出一个使非齐次方程组成立的特解。从 RREF 可见 $x_2 = 1, x_4 = -2, x_5 = 1 + x_6$ 且 $x_1, x_3, x_6 \in \mathbb{R}$ 为自由变量（它们对应于增广矩阵的非主元列）。因此，一个特解为

$$x_p = \begin{bmatrix}0\\1\\0\\-2\\1\\0\end{bmatrix} \in \mathbb{R}^6.$$

通解加上齐次方程组 $A x = 0$ 的解。我们可以使用增广系统的 RREF 并利用 Minus-1 技巧读出这些解。对 RREF 在对角线上填充 -1 的行，我们得到

$$\begin{bmatrix}-1 & 0 & 0 & 0 & 0 & 0\\0 & 1 & 0 & 0 & 0 & 1\\0 & 0 & -1 & 0 & 0 & 0\\0 & 0 & 0 & 1 & 0 & 1\\0 & 0 & 0 & 0 & 1 & -1\\0 & 0 & 0 & 0 & 0 & -1\end{bmatrix}.$$

这给出通解

$$x_p + \lambda_1 \begin{bmatrix}-1\\0\\0\\0\\0\\0\end{bmatrix} + \lambda_2 \begin{bmatrix}0\\0\\-1\\0\\0\\0\end{bmatrix} + \lambda_3 \begin{bmatrix}0\\1\\0\\1\\-1\\-1\end{bmatrix}, \quad \lambda_1,\lambda_2,\lambda_3 \in \mathbb{R}.$$

## 2.7 求 $x = \begin{bmatrix}x_1\\x_2\\x_3\end{bmatrix} \in \mathbb{R}^3$ 中方程组 $A x = 12 x$ 的所有解，
