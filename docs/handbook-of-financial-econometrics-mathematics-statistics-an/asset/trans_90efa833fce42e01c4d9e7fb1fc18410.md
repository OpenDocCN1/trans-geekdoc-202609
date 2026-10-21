
P* 在 Z 上。比较方程 (116.35) 和方程 (116.38) 显示 σ²_{P*|DIV_{t-1}} 等于 σ²_{P*|Z} 仅当 P* 与 Z 不相关时。否则，σ²_{P*|DIV_{t-1}} < σ²_{P*|Z}，意味着共线性增加了收益的 OLS 估计中的偏差。此外，如方程 (116.39) 所示，除非 Z 与 P* 独立，否则 Z 的无误差测量的参数估计通常是有偏的。

## 116.3.1.2 同时方程模型中 2SLS 估计量的渐近偏差

Dhrymes 和 Kurz (1967)、Fama (1974)、Smirlock 和 Marshall (1983) 以及 Lee 等 (2016) 研究了企业投资与股利决策之间的经验关系。在本研究中，构建了如下联立方程系统：

```
ΔDIV_t = γ1 ΔK_t + α0 + α1 DIV_{t-1} + α2 P*_t + ε1t,
ΔK_t = γ2 ΔDIV_t + β0 + β1 K_{t-1} + β2 Q*_t + ε2t,
```

其中 ΔDIV_t 和 ΔK_t 分别是企业 i 从 t−1 年到 t 年的股利和资本存量的变化。DIV_{t-1} 和 K_{t-1} 是企业 i 在 t 年的股利和资本存量。P*_t 是企业 i 在 t 年的预期收益。Q*_t 是企业 i 在 t 年的边际 q。该系统 (116.40) 可改写为如下矩阵形式：

```
Y = X* β + ε,
```

其中 Y = (ΔDIV, ΔK) 是两个内生变量的 T × 2 矩阵，X* = (1 DIV_{t-1} K_{t-1} P* Q*) 是系统中所有外生变量的 T × 5 矩阵，包括 X* 第一个向量中的常数项。这里，ΔDIV_{-1} 和 K_{-1} 分别是 ΔDIV 和 K 的一期滞后数据矩阵。ε = (ε1, ε2)' 是均值向量为零且协方差矩阵为 Σ 的两个扰动的 T × 2 矩阵。参数矩阵 Γ 和 β 定义为

```
Γ = [1 −γ1 ; −γ2 1] and β = [α0 α1 0 α2 0 ; β0 0 β1 0 β2 ]'
```

对结构式模型 (116.32) 右乘 Γ^{−1}，我们得到如下简化式模型：

```
Y = X* β Γ^{−1} + ε Γ^{−1} = X* Π* + e,
```

其中 Π* = β Γ^{−1} 是简化式模型的参数矩阵。扰动向量 e 的均值向量为零，协方差矩阵为 Ω = Γ^{−1} Σ Γ^{−1}。

这里，我们用全部 T 个观测值重写联立方程模型 (116.41) 中的第 j 个方程：

y_j = Y_j γ_j + X_j* β_j + ε_j* = Z_j* δ_j + ε_j,   j = 1,2,   (116.44)

其中 y_j 表示第 j 个方程左端内生变量的 T × 1 观测向量。Y_j 表示该方程右端内生变量的 T × 1 数据矩阵。X_j* 是该方程中所有外生变量的数据矩阵。例如，考虑联立方程模型中的股利方程，y_j 和 Y_j 的数据矩阵分别定义为 ΔDIV 和 ΔK。X_j* = [1 ΔDIV_{-1} P*] 是 T × 3 解释变量数据矩阵，其中 ΔDIV_{-1} 表示 ΔDIV 的一期滞后数据矩阵。Z_j* = [ΔK 1 ΔDIV_{-1} P*] 是该方程右端所有变量的 T × 4 数据矩阵。由于共同决定的变量 y_j 和 Y_j (ΔDIV 和 ΔK) 在系统中内生决定，它们与扰动项相关。这种相关性通常会造成估计困难，因为普通最小二乘估计量是有偏且不一致的（例如 Johnston 和 DiNardo, 1997, Greene, 2018）。两阶段最小二乘 (2SLS) 方法是处理由 Z_j* 与 ε_j 相关导致此内生性问题最常用的方法。

然而，实际上预期收益 (P*) 和边际 q (Q*) 是不可观测的。现在我们假设 P* 和 Q* 存在如下测量误差：

P = P* + v_p   and   Q = Q* + v_q,   (116.45)

其中 P 和 Q 分别表示会计收益和托宾 q 的观测数据矩阵。假设测量误差 v_p 和 v_q 与所有解释变量和随机扰动 ε 独立：

y_j = Y_j γ_j + X_j β_j + ν_j = Z_j δ_j + ε_j,   j = 1,2,   (116.46)

其中 Z_j = [Y_j X_j]。2SLS 估计使用系统中所有外生变量作为工具变量来获得 Y_j 的预测值。在第一阶段，我们将 Y_j 对系统中所有外生变量 X = [1 ΔDIV_{-1} K_{-1} P Q] 回归以获得该方程 (116.46) 右端内生变量的预测值，Ŷ_j = X(X'X)^-1 X'Y_j。在第二阶段，我们将 y_j 对 Ŷ_j 和 X_j 回归以获得方程 (116.46) 中 δ_j 的估计量。用 Ŷ_j 代替 Z_j 中的 Y_j 得到 W_j = [Ŷ_j X_j]。注意

**W**'_j **W**_j = **W**'_j **Z**_j, 方程 (116.46) 中 **δ**_j 的 2SLS 估计量为

$$\hat{\delta}_j^{2SLS} = (\mathbf{W}'_j\mathbf{W}_j)^{-1}\mathbf{W}'_j\mathbf{y}_j$$

$$= \begin{bmatrix} \hat{\mathbf{Y}}'_j\hat{\mathbf{Y}}_j & \hat{\mathbf{Y}}'_j\mathbf{X}_j \\ \mathbf{X}'_j\hat{\mathbf{Y}}_j & \mathbf{X}'_j\mathbf{X}_j \end{bmatrix}^{-1} \begin{bmatrix} \hat{\mathbf{Y}}'_j\mathbf{y}_j \\ \mathbf{X}'_j\mathbf{y}_j \end{bmatrix} = \begin{bmatrix} \hat{\mathbf{Y}}'_j\mathbf{Y}_j & \mathbf{Y}'_j\mathbf{X}_j \\ \mathbf{X}'_j\mathbf{Y}_j & \mathbf{X}'_j\mathbf{X}_j \end{bmatrix}^{-1} \begin{bmatrix} \hat{\mathbf{Y}}'_j\mathbf{y}_j \\ \mathbf{X}'_j\mathbf{y}_j \end{bmatrix}.$$
(116.47)

用 **X**(**X**'**X**)^(-1)**X**'**Y**_j 代替 (116.46) 中的 **Ŷ**_j，得到等价于

$$\hat{\delta}_j^{2SLS} = (\mathbf{Z}'_j\mathbf{X}(\mathbf{X}'\mathbf{X})^{-1}\mathbf{X}'\mathbf{Z}_j)^{-1}\mathbf{Z}'_j\mathbf{X}(\mathbf{X}'\mathbf{X})^{-1}\mathbf{X}'\mathbf{y}_j,$$
(116.48)

其中 **y**_j = ΔDIV，**Z**_j = [ΔK 1 ΔDIV_{-1} P]，以及 **X** = [1 ΔDIV_{-1} K_{-1} P Q] 为观测数据矩阵。

这里，研究了测量误差对结构参数 2SLS 估计的影响。为了研究 2SLS 估计量的渐近偏差，我们将方程 (116.48) 中的 2SLS 估计量重写如下：

$$\hat{\delta}_j^{2SLS} = (\mathbf{Z}'_j\mathbf{X}(\mathbf{X}'\mathbf{X})^{-1}\mathbf{X}'\mathbf{Z}_j)^{-1}\mathbf{Z}'_j\mathbf{X}(\mathbf{X}'\mathbf{X})^{-1}\mathbf{X}'(\mathbf{Z}^*_j\delta_j + \varepsilon_j)$$

$$= \delta_j + (\mathbf{Z}'_j\mathbf{X}(\mathbf{X}'\mathbf{X})^{-1}\mathbf{X}'\mathbf{Z}_j)^{-1}\mathbf{Z}'_j\mathbf{X}(\mathbf{X}'\mathbf{X})^{-1}\mathbf{X}'([\mathbf{0}\,\nu_j]\delta_j + \varepsilon_j).$$
(116.49)

这里，我们定义 **Z**_j = [**Y**_j **X**_j] = [**Y**_j **X***_j + ν_j] = **Z***_j + [**0** ν_j]，且 ν_j 是第 j 个方程右端包含的外生变量对应的测量误差子矩阵。因此，我们可以发现 2SLS 估计量的抽样误差取决于三个部分：T^{-1}(**X**'**X**)、T^{-1}(**X**'**Z**_j) 和 T^{-1}(**X**'([**0** ν_j]δ_j + ε_j))。我们从第一项 T^{-1}(**X**'**X**) 开始

- (i) $T^{-1}(\mathbf{X}'\mathbf{X})$:

$$\operatorname{plim}T^{-1}(\mathbf{X}'\mathbf{X}) = \operatorname{plim}T^{-1}((\mathbf{X}^* + \nu)'(\mathbf{X}^* + \nu))$$

$$= \operatorname{plim}T^{-1}(\mathbf{X}^{*\prime}\mathbf{X}^*) + \theta \equiv \Sigma + \theta,$$
(116.50)

其中 **θ** 是测量误差 **v** 的协方差矩阵。为简化起见，我们假设测量误差相互独立，即矩阵 **θ** 为对角矩阵。根据方程 (116.50)，我们预测第一阶段中 **Ŷ**_j = **X**(**X**'**X**)^(-1)**X**'**Y**_j 的偏差会传递到第二阶段，从而结构参数的估计会受到测量误差的影响。

- (ii) $T^{-1}(\mathbf{X}'\mathbf{Z}_j)$: 为求解感兴趣的变量，我们将 $\mathbf{Y}$ 矩阵分为两部分，对应方程 (116.46) 中的一个因变量内生变量 $\mathbf{y}_j$ 和解释内生变量 $\mathbf{Y}_j$。$\mathbf{X}^*$ 矩阵可类似地划分为两部分，对应包含的外生变量 $\mathbf{X}^*_j$ 和排除的外生变量 $\mathbf{X}^*_{-j}$。简化式模型 (116.43) 的第 $j$ 个方程可重写为

$(\mathbf{y}_j|\mathbf{Y}_j) = [\mathbf{X}^*_j\ \mathbf{X}^*_{-j}]\begin{bmatrix}\mathbf{\Pi}^*_1 & \mathbf{\Pi}^*_j \\ \mathbf{\Pi}^*_2 & \mathbf{\Pi}^*_{-j}\end{bmatrix} + (\mathbf{e}_j|\mathbf{e}_{-j}).\tag{116.51}

然后，我们将简化式模型 (116.12) 对应第 $j$ 个方程中解释内生变量 $\mathbf{Y}_j$ 重写如下：

$\mathbf{Y}_j = \mathbf{X}^*_j\mathbf{\Pi}^*_j + \mathbf{X}^*_{-j}\mathbf{\Pi}^*_{-j} + \mathbf{e}_{-j},\tag{116.52}$

其中 $\mathbf{X}^*_j$ 是方程 (116.44) 中出现的解释外生变量。$\mathbf{\Pi}^*_j$ 表示对应于方程 (116.44) 中出现的 $\mathbf{X}^*_j$ 的 $\mathbf{\Pi}^*$ 的子矩阵。$\mathbf{X}^*_{-j}$ 和 $\mathbf{\Pi}^*_{-j}$ 分别是 $\mathbf{X}^*$ 和 $\mathbf{\Pi}^*$ 的子矩阵，对应于在第 $j$ 个方程中不出现的解释变量。我们重新排列 $\mathbf{X}$ 的列，使得第一部分为 $\mathbf{X}_j$，即

$\mathbf{X} = [\mathbf{X}_j\ \mathbf{X}_{-j}],\tag{116.53}$

其中 $\mathbf{X}_{-j}$ 是在第 $j$ 个方程中不出现的观测外生变量。由式 (116.45)、(116.52) 和 (116.53) 可得

$\mathbf{Y}_j = \mathbf{X}_j\mathbf{\Pi}^*_j + \mathbf{X}_{-j}\mathbf{\Pi}^*_{-j} + \mathbf{e}_{-j} - \boldsymbol{\nu}_j\mathbf{\Pi}^*_j - \boldsymbol{\nu}_{-j}\mathbf{\Pi}^*_{-j},\tag{116.54}$

其中 $\boldsymbol{\nu}_j$ 和 $\boldsymbol{\nu}_{-j}$ 分别是对应于 $\mathbf{X}^*_j$ 和 $\mathbf{X}^*_{-j}$ 的测量误差。

$\mathbf{X}'\mathbf{Z}_j = [\mathbf{X}_j\ \mathbf{X}_{-j}]'[\mathbf{Y}_j\ \mathbf{X}_j] = \begin{bmatrix}\mathbf{X}'_j\mathbf{Y}_j & \mathbf{X}'_j\mathbf{X}_j \\ \mathbf{X}'_{-j}\mathbf{Y}_j & \mathbf{X}'_{-j}\mathbf{X}_j\end{bmatrix}$
$= \begin{bmatrix}\mathbf{X}'_j\mathbf{X}_j & \mathbf{X}'_j\mathbf{X}_{-j} \\ \mathbf{X}'_{-j}\mathbf{X}_j & \mathbf{X}'_{-j}\mathbf{X}_{-j}\end{bmatrix}\begin{bmatrix}\mathbf{\Pi}^*_j & \mathbf{I} \\ \mathbf{\Pi}^*_{-j} & \mathbf{0}\end{bmatrix} - \begin{bmatrix}\mathbf{X}'_j\boldsymbol{\nu}_j\mathbf{\Pi}^*_j + \mathbf{X}'_j\boldsymbol{\nu}_{-j}\mathbf{\Pi}^*_{-j} & \mathbf{0} \\ \mathbf{X}'_{-j}\boldsymbol{\nu}_j\mathbf{\Pi}^*_j + \mathbf{X}'_{-j}\boldsymbol{\nu}_{-j}\mathbf{\Pi}^*_{-j} & \mathbf{0}\end{bmatrix}$
$+ \begin{bmatrix}\mathbf{X}'_j\mathbf{e}_{-j} & \mathbf{0} \\ \mathbf{X}'_{-j}\mathbf{e}_{-j} & \mathbf{0}\end{bmatrix}.\tag{116.55}$
