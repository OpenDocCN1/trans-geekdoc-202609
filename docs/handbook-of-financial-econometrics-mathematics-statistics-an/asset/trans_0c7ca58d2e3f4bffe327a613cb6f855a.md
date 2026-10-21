
贝塔值，而对于“透明”公司则相反。在本文中，我们应用标准市场模型在加法收益率框架以及乘法收益率框架下分析非聚合贝塔与聚合贝塔之间的关系。并且我们发现了经验证据（使用静态和动态模型）支持我们的观点，即系统风险和 $R^2$ 的估计是频率依赖的。

在第 114.2 节，我们将推导在加法收益率下非聚合贝塔与聚合贝塔之间的关系，并展示 Chen (1980) 关于乘法收益率的结果。在第 114.3 节，我们将展示时间聚合对估计决定系数 $R^2$ 影响的推导。经验证据在第 114.4 节展示。最后，第 114.5 节进行结论。

## 114.2 系统风险系数的时间聚合

### 114.2.1 在加法假设下时间聚合对贝塔的影响

遵循 Schwartz 和 Whitcomb (1977a,b)，任意第 $i$ 家公司或投资组合在 $T$ 年期间的市场模型定义为

$$R_{Tij} = \alpha_{Ti} + \beta_{Ti}R_{TMj} + U_{Tij},\ i = 1,2,\dots,I\ \text{and}\ j = 1,2,\dots,J,$$
(114.1)

其中 $R_{TMj} = \log(I_{Tj}/I_{Tj-1})$ 是第 $j$ 个长度为 $T$ 的子期间每年的“市场”连续复利收益率，而 $R_{Tij} = \log_e((P_{Tj}+D_{Tj})/P_{Tj-1})$ 是第 $i$ 家公司或投资组合在第 $j$ 个长度为 $T$ 的子期间每年的连续复利收益率。

然后对于任意第 $t$ 个持续 $n$ 年的短期间（$n < T$），写出模型（为简洁省略公司指标 $i$ 和观测指标 $j$）如下：

$$r_t = \alpha_n + \beta_n r_{Mt} + u_t,\quad t = 1,2,\dots,N\ \text{where}\ N = T/n.$$
(114.2)

$R_T$ 与 $r_t$、$R_{MT}$ 与 $r_{MT}$ 之间的关系定义如下：

$$R_T = \sum_{t=1}^{T/n} r_t,$$
(114.3a)

$$R_{MT} = \sum_{t=1}^{T/n} r_{Mt}.$$
(114.3b)

方程 (114.3a) 和 (114.3b) 显示，长期间的收益率可以通过不相交的每个单独子期间收益率之和来表示。并且该性质称为可加性。例如，如果 $r_t$ 和 $r_{Mt}$ 表示月度收益率且 $T/n = 3$，则 $R_T$ 和 $R_{MT}$ 将表示季度收益率。

为简化分析，以月度收益率为单位的市场模型偏离均值定义如下¹：

$$Y_t = \beta X_t + u_t, \quad t = 1,2,\dots,N \tag{114.4}$$

其中 $Y_t = r_t - \bar{r}_t$，$X_t = r_{Mt} - \bar{r}_{Mt}$，$\beta$ 为标量参数，且 $u_t$ 为非自相关的误差项，对所有 $t$ 满足 $E(u_t)=0$ 且 $E(u_t^2)=\sigma^2$。

遵循 Zeller 和 Montimarquette (1971) 以及 (114.3) 中定义的定义，以 $N$ 期间收益率为单位的无截距市场模型如下所示：

$$\boldsymbol{A}\boldsymbol{Y} = \boldsymbol{A}\boldsymbol{X}\beta + \boldsymbol{A}\boldsymbol{U} \tag{114.5a}$$

其中 $\boldsymbol{Y}' = (Y_1, Y_2, \dots, Y_{(J\times N)})$，$\boldsymbol{X}' = (X_1, X_2, \dots, X_{(J\times N)})$，$\boldsymbol{U}' = (u_1, u_2, \dots, u_{(J\times N)})$，且 $\boldsymbol{A}$ 是一个 $J \times (J \times N)$ 矩阵，形式为

$$\boldsymbol{A} = \begin{bmatrix} \boldsymbol{I}' & \boldsymbol{o}' & \dots & \boldsymbol{o}' \\ \boldsymbol{o}' & \boldsymbol{I}' & \dots & \boldsymbol{o}' \\ \dots & \dots & \dots & \dots \\ \boldsymbol{o}' & \boldsymbol{o}' & \dots & \boldsymbol{I}' \end{bmatrix},$$

且 $\boldsymbol{I}' = (1,1,\dots,1)$ 和 $\boldsymbol{o}' = (0,0,\dots,0)$ 是 $1 \times N$ 的行向量。

此外，我们规定

$$\boldsymbol{A}_j'\boldsymbol{Y} = \beta \boldsymbol{A}_j'\boldsymbol{X} + \boldsymbol{A}_j'\boldsymbol{U} \tag{114.5b}$$

其中 $\boldsymbol{A}_j'$ 是 $\boldsymbol{A}$ 的第 $j$ 行。

鉴于关于 (114.4) 中 $\boldsymbol{U}$ 元素的假设，我们有 $E(\boldsymbol{A}\boldsymbol{U}) = 0$，且 (114.4) 中 $\boldsymbol{A}\boldsymbol{U}$ 的 $J \times J$ 协方差矩阵为

$$E(\boldsymbol{A}\boldsymbol{U}\boldsymbol{U}'\boldsymbol{A}') = \sigma^2 \begin{bmatrix} N & & \\ & N & \\ & & \ddots & \\ & & & N \end{bmatrix}. \tag{114.6}$$

$\beta$ 的 OLS 估计定义为

\[ \tilde{\beta} = (\boldsymbol{X}' \boldsymbol{A}' \boldsymbol{A} \boldsymbol{X})^{-1} \boldsymbol{X}' \boldsymbol{A}' \boldsymbol{A} \boldsymbol{Y}. \tag{114.7} \]

$\beta$ 的最小方差线性无偏 (MVLU) 估计量定义为

\[ \beta^* = [\boldsymbol{X}' \boldsymbol{A}' (\boldsymbol{A} \boldsymbol{A}')^{-1} \boldsymbol{A} \boldsymbol{X}]^{-1} \boldsymbol{X}' \boldsymbol{A}' (\boldsymbol{A}' \boldsymbol{A})^{-1} \boldsymbol{A} \boldsymbol{Y} \]
\[ = [\boldsymbol{X}' \boldsymbol{A}' \boldsymbol{A} \boldsymbol{X}]^{-1} \boldsymbol{X}' \boldsymbol{A}' \boldsymbol{A} \boldsymbol{Y} = \tilde{\beta}. \tag{114.8} \]

该结果表明系统风险的普通最小二乘 (OLS) 估计量等价于广义最小二乘 (GLS) 估计量。因此 OLS 估计量是一个 MVLU 估计量。

方程 (114.4) 和 (114.5) 是无截距的简单回归。与聚合数据相关的斜率可以定义为

\[ \beta_a^2 = \left[ \frac{\text{Cov}(\boldsymbol{A}'_j \boldsymbol{Y}, \boldsymbol{A}'_j \boldsymbol{X})}{\text{Var}(\boldsymbol{A}'_j \boldsymbol{X})} \right]^2 = r_a^2 \frac{\text{Var}(\boldsymbol{A}'_j \boldsymbol{Y})}{\text{Var}(\boldsymbol{A}'_j \boldsymbol{X})}, \tag{114.9} \]

其中 $r_a$ 是 $\boldsymbol{A}'_j \boldsymbol{Y}$ 与 $\boldsymbol{A}'_j \boldsymbol{X}$ 之间的相关系数。

方程 (114.9) 可用于证明，即使市场收益率存在自相关，与加法收益率相关的先验系统风险也不受时间聚合的影响。遵循方程 (114.9)，可以证明

\[ \text{Var}(\boldsymbol{A}'_j \boldsymbol{X}) = \boldsymbol{A}'_j \text{Var}(\boldsymbol{X}) \boldsymbol{A}_j = \mathbf{I}' \text{Var}(\mathbf{X}_j) \mathbf{I} \]
\[ = \text{Var}(X_t) \left[ N + 2 \sum_{s=1}^{N-1} (N - s) \rho_X^s \right], \tag{114.10} \]

其中 $\boldsymbol{X}_j$ 是包含聚合期间 $N$ 个市场收益率的列向量，且上述方程是通过假设 Var$(X_t)$ = Var$(X_{t-s})$ 对 $s = 1,2,...,N-1$，$X_t$ 的滞后 $s$ 自协方差全部相等，即 Cov$(X_t, X_{t-s})$ = Cov$(X_{t-k}, X_{t-k-s})$ 对所有 $k$ 和 $s$ 成立而推导的。并且 $\rho_X^s$ 表示解释变量的 $s$ 阶自相关系数，即市场超额预期收益率。为简化，我们记 $P_N = 2 \sum_{i=1}^{N-1} (N - i) \rho_X^s$。

此外，如本章附录所示，可以得到

\[ \text{Cov}(\boldsymbol{A}'_j \boldsymbol{Y}, \boldsymbol{A}'_j \boldsymbol{X}) = \text{Cov}(X_t, Y_t)[N + \Gamma_N], \tag{114.11} \]

其中

\[ \Gamma_N = \sum_{s=1}^{N-1} (N - s) \frac{\rho_{XY}^s + \rho_{XY}^{-s}}{\rho_{XY}} = \sum_{s=1}^{N-1} (N - s) q_{XY}^s. \tag{114.12} \]

方程 (114.11) 是 Hawawini (1980) 中所指的协方差-时间函数 (C-T Function)。比值 $\frac{\rho_{XY}^{s}+\rho_{XY}^{-s}}{\rho_{XY}}$ 称为 $s$ 阶 $q$-比值。它是单位（非聚合）收益率中 $s$ 阶的领先 ($\rho_{XY}^{s}$) 和滞后 ($\rho_{XY}^{-s}$) 临时交叉相关系数之和除以同期交叉相关系数 ($\rho_{XY}$)。我们将该比值记为 $q_{XY}^{s}$。

由方程 (114.10)、(114.11) 和系统风险系数的定义可得

$$\beta_{a}^{2} = \frac{\text{Cov}(X_{t}, Y_{t})[N + \Gamma_{N}]}{\text{Var}(X_{t})[N + \text{P}_{N}]} = \beta_{u}^{2} \times \frac{N + \sum_{s=1}^{N-1} (N - s) q_{XY}^{s}}{N + 2 \sum_{s=1}^{N-1} (N - s) \rho_{X}^{s}}. \tag{114.13}$$

记时间聚合因子为 $\Phi(N) = \frac{N+\sum_{s=1}^{N-1} (N-s) q_{XY}^{s}}{N+2 \sum_{s=1}^{N-1} (N-s) \rho_{X}^{s}}$。因此，与加法收益率相关的先验系统风险是频率依赖的。系统系数估计的时间聚合效应的方向和大小由 $\Phi(N)$ 与 1 之差的符号和绝对值给出。合理地认为，如果 $\Phi(N)$ 大于 1，则时间聚合效应为正（聚合贝塔大于非聚合贝塔）。而如果 $\Phi(N)$ 小于 1，则效应被认为为负。此外，我们可以推测，对于时间间隔的变化，Phi 乘数 $\Phi(N)$ 与 1 之间的较大差异将表明聚合与非聚合贝塔估计之间的差距更大。

在第 114.3 节，我们将通过计算每个公司在不同时间频率下的 $\Phi$ 并将其与贝塔的实际变化趋势进行比较来检验我们的结果。

### 114.2.2 在乘法假设下时间聚合对贝塔的影响

在乘法收益率假设下继续讨论 Schwartz 和 Whitcomb (1977) 的 $T$ 年市场模型，适用于任意第 $i$ 家公司或投资组合。在乘法框架中，$R_{TMj} = \frac{I_{Tj} - I_{Tj-1}}{I_{Tj-1}}$，是第 $j$ 个长度为 $T$ 的子期间的“市场”简单收益率。$R_{Tij} = \frac{P_{Tj} + D_{Tj} - P_{Tj-1}}{P_{Tj-1}}$，是第 $j$ 个长度为 $T$ 的子期间的简单收益率
