

子集选择是通过适当选择 $\lambda$ 来实现，使得如果 \(\boldsymbol{\beta} = (\boldsymbol{\beta}_1^\top, \boldsymbol{\beta}_2^\top)^\top\) 定义良好，那么相应地，LASSO R-估计器产生参数的划分为 \(\boldsymbol{\beta}_n = (\boldsymbol{\beta}_{1n}^\top, \boldsymbol{\beta}_{2n}^\top)^\top$。

当 \(\boldsymbol{\beta}_2 = \mathbf{0}$ 时，Eq. (6.3.1) 中的模型简化为受限模型

\(\boldsymbol{y} = X_1 \boldsymbol{\beta}_1 + \boldsymbol{\varepsilon}, \quad (6.3.3)\)

where

\(X_1 = (x_1^{(1)}, \dots, x_n^{(1)}), \quad x_i^{(1)} \in \mathbb{R}^{p_1}.$

因此，\(\boldsymbol{\beta}_1$ 的受限 R-估计器（RRE）由以下给出

\(\hat{\boldsymbol{\beta}}_{1n}^{RR} = \operatorname{argmin}_{\boldsymbol{\beta}_1 \in \mathbb{R}^{p_1}} \{ D_n(\boldsymbol{\beta}_1) \}\)

where

\(D_n(\boldsymbol{\beta}_1) = \sum_{i=1}^n (y_i - (x_i^{(1)} - \bar{x}^{(1)})^\top \boldsymbol{\beta}_1) a_n(R_{n_i}(\boldsymbol{\beta}_1))$

其中 \(x_i^{(1)}\) 为 \(X_1$ 的第 \(i$ 行，且 \(\bar{x}^{(1)} = n^{-1} \sum_{i=1}^n x_i^{(1)}\). 另外，\(y_i - (x_i^{(1)})^\top \boldsymbol{\beta}_1\) 在 \(y_1 - (x_1^{(1)})^\top \boldsymbol{\beta}_1, \dots, y_n - (x_n^{(1)})^\top \boldsymbol{\beta}_1\) 中的秩记为 \(R_{n_i}(\boldsymbol{\beta}_1)\).

等价地，RRE 可通过以下方式得到

\(\hat{\boldsymbol{\beta}}_{1n}^{RR} = \operatorname{argmin}_{\boldsymbol{\beta}_1 \in \mathbb{R}^{p_1}} \{ \| \boldsymbol{L}_n(\boldsymbol{\beta}_1) \| \} \quad (6.3.4)\)

where

\(\boldsymbol{L}_n(\boldsymbol{\beta}_1) = (L_{n_1}(\boldsymbol{\beta}_1), \dots, L_{n_{p_1}}(\boldsymbol{\beta}_1))^\top .\)

这里

\(L_{n_i}(\boldsymbol{\beta}_1) = \frac{1}{\sqrt{n}} (x_i^{(1)} - \bar{x}^{(1)}) a_n(R_{n_i}(\boldsymbol{\beta}_1)).\)

然后，使用 Jurečková (1971) 的 AUL，我们有

\(\sqrt{n} \left( \hat{\boldsymbol{\beta}}_{1n}^{RR} - \boldsymbol{\beta}_1 \right) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_1} (0, \gamma^2 C_{11}^{-1}) \quad (6.3.5)\)

where

\(\boldsymbol{C} = \begin{pmatrix} \boldsymbol{C}_{11} & \boldsymbol{C}_{12} \\ \boldsymbol{C}_{21} & \boldsymbol{C}_{22} \end{pmatrix} .\)

令 \(\boldsymbol{C}^{-1} = (C^{ij})\)，其中 \(C^{ij}\) 为 \(\boldsymbol{C}^{-1}$ 的第 \(j$ 个对角块。则

\(\boldsymbol{C}^{-1} = \begin{pmatrix} \boldsymbol{C}^{11} & \boldsymbol{C}^{12} \\ \boldsymbol{C}^{21} & \boldsymbol{C}^{22} \end{pmatrix}.$

当我们怀疑 \(\boldsymbol{\beta}_2$（一个 \(p_2$-维系数向量）为零且 \(\boldsymbol{\beta}_1$（一个 \(p_1$-维系数向量）非零时，我们主要关注 \(\boldsymbol{\beta} = (\boldsymbol{\beta}_1^\top, \boldsymbol{\beta}_2^\top)^\top\) 的 R-估计。那么，\(\boldsymbol{\beta}$ 的 URE 和 RRE 分别可写为

\(\hat{\boldsymbol{\beta}}_n^{\text{UR}} = \begin{pmatrix} \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}} \\ \hat{\boldsymbol{\beta}}_{2n}^{\text{UR}} \end{pmatrix} \text{ 和 } \hat{\boldsymbol{\beta}}_n^{\text{RR}} = \begin{pmatrix} \hat{\boldsymbol{\beta}}_{1n}^{\text{RR}} \\ \boldsymbol{0} \end{pmatrix}. \quad (6.3.6)\)

从 \(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}\) 和 \(\hat{\boldsymbol{\beta}}_{2n}^{\text{UR}}\) 的边际分布，我们有

\(\begin{aligned} \sqrt{n}\left(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}} - \boldsymbol{\beta}_1\right) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_1}\left(\boldsymbol{0}, \eta^2 \boldsymbol{C}_{11|2}^{-1}\right) \\ \sqrt{n}\left(\hat{\boldsymbol{\beta}}_{2n}^{\text{UR}} - \boldsymbol{\beta}_2\right) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_2}\left(\boldsymbol{0}, \eta^2 \boldsymbol{C}_{22:1}^{-1}\right), \end{aligned}\)

where

\(\begin{aligned} \boldsymbol{C}_{11\cdot 2} &= \boldsymbol{C}_{11} - \boldsymbol{C}_{12} \boldsymbol{C}_{22}^{-1} \boldsymbol{C}_{12} \\ \boldsymbol{C}_{22\cdot 1} &= \boldsymbol{C}_{22} - \boldsymbol{C}_{21} \boldsymbol{C}_{11}^{-1} \boldsymbol{C}_{21}. \end{aligned}\)

\(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}\) 的 ADL\(_2\)-风险由以下给出

\(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}) = \eta^2 \left( \text{tr}(\boldsymbol{C}_{11\cdot 2}^{-1}) + \text{tr}(\boldsymbol{C}_{22:1}^{-1}) \right). \quad (6.3.7)\)

接下来，考虑局部备择假设为

\(\mathcal{H}_{\mathcal{A}} : \boldsymbol{\beta}_{2(n)} = \frac{1}{\sqrt{n}} \boldsymbol{\delta}_2, \quad \boldsymbol{\delta}_2 = (\delta_2, \dots, \delta_{2_{p_2}})^\top. \quad (6.3.8)\)

在局部备择假设下，ADL\(_2\)-风险\((\hat{\boldsymbol{\beta}}_n^{\text{RR}})\) 由以下给出

\(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{RR}}) = \eta^2 \left( \text{tr}(\boldsymbol{C}_{11}^{-1}) + \frac{1}{\eta^2} \boldsymbol{\delta}_2^\top \boldsymbol{\delta}_2 \right). \quad (6.3.9)\)

接下来，基于 \(\Delta^2$ 的定义，我们使用 Courant 定理（见 Anderson, 2003 的定理 A.2.4）得到

\(\text{Ch}_{\min}(\boldsymbol{C}_{22:1}^{-1}) \leq \frac{\boldsymbol{\delta}_2^\top \boldsymbol{\delta}_2}{\boldsymbol{\delta}_2^\top \boldsymbol{C}_{22:1} \boldsymbol{\delta}_2} \leq \text{Ch}_{\max}(\boldsymbol{C}_{22:1}^{-1}),\) 其中 Ch$_{max(min)}(A)$ 是 $A$ 的最大（最小）特征值。我们得到

\(\eta^2\Delta^2 Ch_{min}(C_{22:1}^{-1}) \le \delta_2^\top \delta_2 \le \eta^2\Delta^2 Ch_{max}(C_{22:1}^{-1}).\) (6.3.10)

因此，ADL$_2$-风险($\hat{\beta}_n^{RR}$) 的下界（用 ‘*’ 表示）由以下给出

\(ADL_2^{*risk}(\hat{\beta}_n^{RR}) = \eta^2 tr(C_{11}^{-1}) + \Delta^2 Ch_{min}(C_{22:1}^{-1}).\)

$\hat{\beta}_n^{RR}$ 的 ADRE 由以下给出

\(ADRE(\hat{\beta}_n^{RR} : \hat{\beta}_n^{UR}) = \frac{tr(C_{11:2}^{-1}) + tr(C_{22:1}^{-1})}{tr(C_{11}^{-1}) + \Delta^2 Ch_{min}(C_{22:1}^{-1})},\)
\(= \left( 1 + \frac{tr(C_{22:1}^{-1})}{tr(C_{11:2}^{-1})} \right) \left( \frac{tr(C_{11:2}^{-1})}{tr(C_{11}^{-1})} \right)\)
\(\times \left( 1 + \frac{\Delta^2 Ch_{min}(C_{22:1}^{-1})}{tr(C_{11}^{-1})} \right)^{-1}\) (6.3.11)

其中 Ch$_{min}(A)$ 是矩阵 $A$ 的最小特征值。

如果我们使用权重 $C_{11:2}$ 和 $C_{22:1}$，则得到

\(ADRE(\hat{\beta}_n^{RR} : \hat{\beta}_n^{UR}) = \frac{p_1 + p_2}{tr(C_{11}^{-1}C_{11:2}) + \Delta^2}, \text{ 其中 } \Delta^2 = \frac{\delta_2^\top C_{11:2} \delta_2}{\eta^2}.\) (6.3.12)

## 6.4 \(\beta$ 的一般收缩 R-估计器

在本节中，我们假设 \(\beta = (\beta_1^\top, \beta_2^\top)^\top$ 具有稀疏性，即 \(\beta_2$ 可能等于或接近 **0**。一般来说，\(\beta$ 的收缩 R-估计器定义为

\(\hat{\beta}_n^{ShrinkageR}_{(c)} = (\hat{c}\beta_{1n}^{UR\top}, c\hat{\beta}_{2n}^{UR\top})^\top, \quad 0 < c < 1\)

其中 \(c$ 可以是常数或随机变量。因此，在局部备择假设下，\(\beta_{2(n)} : n^{-\frac{1}{2}} \delta_2$，我们有

\(ADB(\hat{\beta}_n^{ShrinkageR}_{(c)}(c)) = (\mathbf{0}, -(1-c)\delta_2)^\top,\)

和

\(ADL_2\text{-risk}(\hat{\beta}_n^{ShrinkageR}_{(c)}(c)) = \eta^2 tr(C_{11:2}^{-1}) + c^2\eta^2 tr(C_{22:1}^{-1}) + (1-c)^2 \delta_2^\top \delta_2.\) (6.4.1)

对于渐近风险函数，每当我们使用来自 Eq. (6.3.10) 的 \(\delta_2^T \delta_2$ 的下界时，我们写 \(\text{ADL}_2^*$-风险，而不是 \(\text{ADL}_2$-风险。因此，

\(\text{ADL}_2^*\text{-risk}(\hat{\beta}_n^{\text{ShrinkageR}}(c)) = \eta^2 \text{tr}(\mathbf{C}_{11:2}^{-1}) + c^2 \eta^2 \text{tr}(\mathbf{C}_{22:1}^{-1}) + (1-c)^2 \eta^2 \Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1}).\qquad (6.4.2)\)

对 R.H.S. 关于 \(c$ 最小化，我们有

\(c^* = \frac{\Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{22:1}^{-1}) + \Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1})}.\)

因此，\(\hat{\beta}_n^{\text{ShrinkageR}}(c^*)$ 的 \(\text{ADL}_2$-风险下界由以下给出

\(\text{ADL}_2^*\text{-risk}(\hat{\beta}_n^{\text{ShrinkageR}}(c^*)) = \eta^2 \left( \text{tr}(\mathbf{C}_{11:2}^{-1}) + \frac{\text{tr}(\mathbf{C}_{22:1}^{-1})\Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{22:1}^{-1}) + \Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1})} \right).\qquad (6.4.3)\)

然后 ADRE 由以下给出

\(\text{ADRE}(\hat{\beta}_n^{\text{ShrinkageR}}(c^*) : \hat{\beta}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} \right) \times \left( 1 + \frac{\text{tr}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} \left( \frac{\Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{22:1}^{-1}) + \Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1})} \right) \right)^{-1} \ge 1.\)

### 6.4.1 初步检验 R-估计器

\(\beta$ 的初步检验 R-估计器由以下给出

\(\hat{\beta}_n^{\text{PTR}}(\lambda) = \begin{pmatrix} \hat{\beta}_{1n}^\text{UR} \\ \hat{\beta}_{2n}^\text{UR} I(\mathcal{L}_n > \lambda^2) \end{pmatrix}.\qquad (6.4.4)\)

对于原假设 \(\mathcal{H}_o : \beta_2 = \mathbf{0}$ 与备择假设 \(\mathcal{H}_A : \beta_2 \neq \mathbf{0}$ 的检验，我们考虑划分

\(\mathbf{L}_n(\beta_1, \beta_2) = (\mathbf{L}_{n(1)}^T(\beta_1, \beta_2), \mathbf{L}_{n(2)}^T(\beta_1, \beta_2))^T,\qquad (6.4.5)\)

where

\(\mathbf{L}_{n(1)}(\beta_1, \beta_2) = (\mathbf{L}_{n_1}(\beta_1, \beta_2), \dots, \mathbf{L}_{n_{p_1}}(\beta_1, \beta_2))^T,\)

