
# 求解 FSLE 的 FGDO 方法

在这里，采用 FGDO 技术来求解 FSE，随后给出一种改进的算法。

考虑 FSE $\widetilde{M}\widetilde{X} = \widetilde{\mathcal{Y}}$，其中 $\widetilde{M}$ 是对称正定矩阵（SPDM）。我们需要找到某个二次函数的最小值，该最小值即为方程组 $\widetilde{M}\widetilde{X} - \widetilde{\mathcal{Y}}$ 的解。

取二次函数：

(5.10) $F\left( X \right) = \frac{1}{2}\widetilde{X}^{T}\widetilde{M}\widetilde{X} - \widetilde{X}^{T}\widetilde{\mathcal{Y}}$

$$
\widetilde{M} = \begin{bmatrix} 
\left\lbrack {{\widetilde{\mathcal{m}}}_{L_{11}},{\widetilde{\mathcal{m}}}_{N_{11}},{\widetilde{\mathcal{m}}}_{R_{11}}} \right\rbrack & \left\lbrack {{\widetilde{\mathcal{m}}}_{L_{12}},{\widetilde{\mathcal{m}}}_{N_{12}},{\widetilde{\mathcal{m}}}_{R_{12}}} \right\rbrack & \cdots & \left\lbrack {{\widetilde{\mathcal{m}}}_{L_{1n}},{\widetilde{\mathcal{m}}}_{N_{1n}},{\widetilde{\mathcal{m}}}_{R_{1n}}} \right\rbrack \\ 
\left\lbrack {{\widetilde{\mathcal{m}}}_{L_{21}},{\widetilde{\mathcal{m}}}_{N_{21}},{\widetilde{\mathcal{m}}}_{R_{21}}} \right\rbrack & \left\lbrack {{\widetilde{\mathcal{m}}}_{L_{22}},{\widetilde{\mathcal{m}}}_{N_{22}},{\widetilde{\mathcal{m}}}_{R_{22}}} \right\rbrack & \cdots & \left\lbrack {{\widetilde{\mathcal{m}}}_{L_{1n}},{\widetilde{\mathcal{m}}}_{N_{1n}},{\widetilde{\mathcal{m}}}_{R_{1n}}} \right\rbrack \\ 
\vdots & \vdots & \ddots & \vdots \\ 
\left\lbrack {{\widetilde{\mathcal{m}}}_{L_{n1}},{\widetilde{\mathcal{m}}}_{N_{n1}},{\widetilde{\mathcal{m}}}_{R_{11}}} \right\rbrack & \left\lbrack {{\widetilde{\mathcal{m}}}_{L_{n2}},{\widetilde{\mathcal{m}}}_{N_{n2}},{\widetilde{\mathcal{m}}}_{R_{n2}}} \right\rbrack & \cdots & \left\lbrack {{\widetilde{\mathcal{m}}}_{L_{nn}},{\widetilde{\mathcal{m}}}_{N_{nn}},{\widetilde{\mathcal{m}}}_{R_{nn}}}} \right\rbrack \\ 
\end{bmatrix}, 
{\widetilde{X}}_{n \times 1} = \begin{bmatrix} 
\left\lbrack {{\widetilde{x}}_{L_{1}},{\widetilde{x}}_{N_{1}},{\widetilde{x}}_{R_{1}}} \right\rbrack \\ 
\left\lbrack {{\widetilde{x}}_{L_{2}},{\widetilde{x}}_{N_{2}},{\widetilde{x}}_{R_{2}}} \right\rbrack \\ 
\vdots \\ 
\left\lbrack {{\widetilde{x}}_{L_{n}},{\widetilde{x}}_{N_{n}},{\widetilde{x}}_{R_{n}}} \right\rbrack \\ 
\end{bmatrix}, 
\widetilde{\mathcal{Y}} = \begin{bmatrix} 
\left\lbrack {{\widetilde{b}}_{L_{1}},{\widetilde{b}}_{N_{1}},{\widetilde{b}}_{R_{1}}} \right\rbrack \\ 
\left\lbrack {{\widetilde{b}}_{L_{2}},{\widetilde{b}}_{N_{2}},{\widetilde{b}}_{R_{2}}} \right\rbrack \\ 
\vdots \\ 
\left\lbrack {{\widetilde{b}}_{L_{n}},{\widetilde{b}}_{N_{n}},{\widetilde{b}}_{R_{n}}} \right\rbrack \\ 
\end{bmatrix}
$$

上述系统写作如下：

(5.11) $\sum\limits_{i,j = 1}^{n}\left\lbrack {{\widetilde{\mathcal{m}}}_{L_{ij}}^{\alpha},{\widetilde{\mathcal{m}}}_{R_{ij}}^{\alpha}} \right\rbrack\left\lbrack {{\widetilde{x}}_{L_{j}}^{\alpha},{\widetilde{x}}_{R_{j}}^{\alpha}} \right\rbrack = \left\lbrack {{\widetilde{b}}_{L_{j}}^{\alpha},{\widetilde{b}}_{R_{j}}^{\alpha}} \right\rbrack.$

方程 (5.11)可以等价地表示为：

(5.12) $M_{L} = \sum\limits_{i,j = 1}^{n}{\widetilde{\mathcal{m}}}_{L_{ij}}^{\alpha}{\widetilde{x}}_{L_{j}}^{\alpha} = {\widetilde{b}}_{L_{j}}^{\alpha}$

(5.13) $M_{R} = \sum\limits_{i,j = 1}^{n}{\widetilde{\mathcal{m}}}_{R_{ij}}^{\alpha}{\widetilde{x}}_{R_{j}}^{\alpha} = {\widetilde{b}}_{R_{j}}^{\alpha}$

方程 (5.12)和(5.13)可以写成二次函数的形式：

$F\left( X \right) = \left\lbrack {M_{L},M_{R}} \right\rbrack = \frac{1}{2}\left\lbrack {{\widetilde{x}}_{L_{j}}^{\alpha},{\widetilde{x}}_{R_{j}}^{\alpha}} \right\rbrack^{T}\left\lbrack {{\mathcal{m}}_{L_{ij}}^{\alpha},{\widetilde{\mathcal{m}}}_{R_{ij}}^{\alpha}} \right\rbrack\left\lbrack {{\widetilde{x}}_{L_{j}}^{\alpha},{\widetilde{x}}_{R_{j}}^{\alpha}} \right\rbrack - \left\lbrack {{\widetilde{x}}_{L_{j}}^{\alpha},{\widetilde{x}}_{R_{j}}^{\alpha}} \right\rbrack^{T}\left\lbrack {{\widetilde{b}}_{L_{j}}^{\alpha},{\widetilde{b}}_{R_{j}}^{\alpha}} \right\rbrack$

通过使用梯度下降法求解 (10)。我们得到给定函数`${\widetilde{\mathcal{m}}}_{L_{ij}}^{\alpha},{\widetilde{\mathcal{m}}}_{R_{ij}}^{\alpha}}$的梯度是对称的。

(5.14) $\nabla F\left( X \right) = \left\lbrack {{\widetilde{\mathcal{m}}}_{L_{ij}}^{\alpha},{\widetilde{\mathcal{m}}}_{R_{ij}}^{\alpha}} \right\rbrack\left\lbrack {{\widetilde{x}}_{L_{j}}^{\alpha},{\widetilde{x}}_{R_{j}}^{\alpha}} \right\rbrack - \left\lbrack {{\widetilde{b}}_{L_{j}}^{\alpha},{\widetilde{b}}_{R_{j}}^{\alpha}} \right\rbrack$

(5.15) $\nabla F(X) = \left\lbrack {{\widetilde{b}}_{L_{j}}^{\alpha},{\widetilde{b}}_{R_{j}}^{\alpha}} \right\rbrack - \left\lbrack {{\widetilde{a}}_{L_{ij}}^{\alpha},{\widetilde{a}}_{R_{ij}}^{\alpha}} \right\rbrack\left\lbrack {{\widetilde{x}}_{L_{j}}^{\alpha},{\widetilde{x}}_{R_{j}}^{\alpha}} \right\rbrack$

(5.16) $\left\lbrack {{\widetilde{r}}_{L_{j}}^{\alpha},{\widetilde{r}}_{R_{j}}^{\alpha}} \right\rbrack_{k} = \left\lbrack {{\widetilde{b}}_{L_{j}}^{\alpha},{\widetilde{b}}_{R_{j}}^{\alpha}} \right\rbrack - \left\lbrack {{\widetilde{\mathcal{m}}}_{L_{ij}}^{\alpha},{\widetilde{\mathcal{m}}}_{R_{ij}}^{\alpha}} \right\rbrack\left\lbrack {{\widetilde{x}}_{L_{j}}^{\alpha},{\widetilde{x}}_{R_{j}}^{\alpha}} \right\rbrack,$

为`\widetilde{X}_k` (ch05.xhtml#equ47)的残差点。然后，`\widetilde{X}_k` (ch05.xhtml#equ48)更新如下：

(5.17) $\left\lbrack {{\widetilde{x}}_{L_{j}}^{\alpha},{\widetilde{x}}_{R_{j}}^{\alpha}} \right\rbrack_{k} = \left\lbrack {{\widetilde{b}}_{L_{j}}^{\alpha},{\widetilde{b}}_{R_{j}}^{\alpha}} \right\rbrack - \left\lbrack {{\widetilde{\lambda}}_{L_{j}}^{\alpha},{\widetilde{\lambda}}_{R_{j}}^{\alpha}} \right\rbrack_{k}\left\lbrack {{\widetilde{r}}_{L_{j}}^{\alpha},{\widetilde{r}}_{R_{j}}^{\alpha}} \right\rbrack,$

且`\widetilde{X}_k` (ch05.xhtml#equ49)通过梯度下降法更新，其中矩阵`\widetilde{M}` (ch05.xhtml#equ50)是非奇异矩阵。

$$
\left\lbrack {{\widetilde{x}}_{L_{j}}^{\alpha},{\widetilde{x}}_{R_{j}}^{\alpha}} \right\rbrack_{k+1} = \left\lbrack {{\widetilde{x}}_{L_{j}}^{\alpha},{\widetilde{x}}_{R_{j}}^{\alpha}} \right\rbrack_{k} - \left\lbrack {{\widetilde{\lambda}}_{L_{j}}^{\alpha},{\widetilde{\lambda}}_{R_{j}}^{\alpha}} \right\rbrack_{k}\left\lbrack {{\widetilde{r}}_{L_{j}}^{\alpha},{\widetilde{r}}_{R_{j}}^{\alpha}} \right\rbrack
$$

其中
