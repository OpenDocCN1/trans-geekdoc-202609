
## 72.2 模型与估计

设 $\tilde{r}_t = (r_{1,t},\dots,r_{m,t})'$ 为时间 $t$ 的股票收益向量，$\tilde{\mu} = (\mu_1,\dots,\mu_m)'$ 为 $\tilde{r}_t$ 的均值，$r_t$ 为加权投资组合的收益，

$r_t = \sum_{i=1}^{m} w_i r_{i,t} = \mu + \sum_{i=1}^{m} w_i v_{i,t} u_{i,t}, \tag{72.1}$
其中 $\mu = \sum_{i=1}^{m} w_i \mu_i$，$\sum_{i=1}^{m} w_i = 1$，且权重 $\{w_i\}$ 允许为正、零或负。设 $\{S_t, t = 0,1,\dots\}$ 表示由其对数收益 $r_t = \ln(S_t/S_{t-1})$ 形成的价格过程。HCT-1 考虑了估计 $Q_\alpha(T)$ 的问题，即股票价格 $S_t$ 在 $T$ 时的 $\alpha$ 分位数，亦即 $\alpha = P\{S_T < Q_\alpha(T)\}$。首先，HCT-1 假设收益过程遵循由下式定义的 multivariate SV (MSV) 模型

$\tilde{r}_t = \tilde{\mu} + V_t U_t, \tag{72.2}$
其中 $V_t = \operatorname{diag}(v_{1,t},\dots,v_{m,t})$ 为对角矩阵，且 $v_{i,t} = \exp(Z_{i,t}/2)$，$i = 1,\dots,m$，$U_t = (u_{1,t},\dots,u_{m,t})'$ 为由独立同分布的 i.i.d. 随机向量组成的冲击序列，均值为 0 且正定协方差矩阵为 $\Sigma_U = [\sigma_{U,ij}]$，$Z_t = (Z_{1,t},\dots,Z_{m,t})'$ 遵循 $m$ 维平稳短记忆过程。

假设 $\sigma = \{E(r_t - \mu)^2\}^{1/2}$ 和 $\mu$ 均未知。在假设 $U_t$ 正态性的情况下，HCT-1 证明了 $B_T/\sigma \approx \Phi^{-1}(\alpha)$，其中 $B_T = (\ln(Q_\alpha(T)/S_0) - T\mu)/\sqrt{T}$，且 $\Phi^{-1}(\cdot)$ 为标准正态分布累积分布函数的逆函数。由此，提出对 $Q_\alpha(T)$ 的以下估计：

$\hat{Q}_\alpha(T) = S_0 \exp\big( \Phi^{-1}(\alpha) \sqrt{T} \hat{\sigma}_T + T \hat{\mu}_T \big), \tag{72.3}$
其中 $\hat{\sigma}_T = (T^{-1} \sum_{t=1}^T (r_t - \hat{\mu}_T)^2 )$ 且 $\hat{\mu}_T = T^{-1}\sum_{t=1}^T r_t$。此外，HCT-1 建立了估计误差序列 $\ln(\hat{Q}_\alpha(T)/Q_\alpha(T))$ 的渐近正态性，并据此构造了 $Q_\alpha(T)$ 的 $100(1-\beta)\%$ 置信区间：

$\hat{Q}_\alpha(T) \exp(-\sqrt{T} \hat{\sigma}_T U) \le Q_\alpha(T) \le \hat{Q}_\alpha(T) \exp(-\sqrt{T} \hat{\sigma}_T L), \tag{72.4}$
其中 $L$ 和 $U$ 分别为 $N(0,1)$ 的 $100(\beta/2)\%$ 和 $100(1-\beta/2)\%$ 分位数。

HCT-2 将 HCT-1 的结果推广到 CTE 的情形，并做了两点修改。首先，关于积分长度，在后者中它与样本量相同，而在前者中样本量 $n$ 与长度 $T$ 满足 $n = N \cdot T$，其中 $N$ 为某个正整数。其次，HCT-2 中考虑的 MSV 模型比 HCT-1 中的更为一般。

两个 CTE，$C_{\alpha}^{1,T}$ 和 $C_{\alpha}^{2,T}$，相等，即

$$
\left\{
\begin{array}{l}
H_0 : C_{\alpha}^{1,T} = C_{\alpha}^{2,T}, \\
H_1 : C_{\alpha}^{1,T} \neq C_{\alpha}^{2,T}.
\end{array}
\right.
\tag{72.9}
$$

如 HCT-2 所示，若加权投资组合收益的均值未知，且 $N$ 和 $T$ 满足 $T \ll N \ll T^2$，则当 $T$ 趋于无穷时

$$
\sqrt{N/T}\left(\hat{C}_{\alpha}^{i,T} - C_{\alpha}^{i,T}\right) \xrightarrow{d} N(0,\sigma_i^2), \quad \text{for } i = 1 \text{ and } 2,
\tag{72.10}
$$

其中，对 $i = 1$ 和 $2$，$\hat{C}_{\alpha}^{i,T}$ 为如式 (72.7) 定义的 $C_{\alpha}^{i,T}$ 的估计，$\sigma_1^2$ 和 $\sigma_2^2$ 分别为加权投资组合收益 $\{r_t\}$ 和 $\{s_t\}$ 的方差。为了利用式 (72.10) 对式 (72.9) 中指定的原假设进行 size-$\alpha$ 检验，我们构造检验统计量为

$$
\text{Test} = \sqrt{\frac{N}{T}} \frac{\hat{C}_{\alpha}^{1,T} - \hat{C}_{\alpha}^{2,T}}{\sqrt{\hat{\sigma}_{1,n}^2 + \hat{\sigma}_{2,n}^2}},
\tag{72.11}
$$

并在 $|\text{Test}| > Z_{1-\alpha/2}$ 时拒绝 $H_0$，其中 $\hat{\sigma}_{1,n}^2$ 和 $\hat{\sigma}_{2,n}^2$ 分别为 $\{r_t\}$ 和 $\{s_t\}$ 的样本方差。

## 72.4 模拟研究

本节通过模拟研究来考察式 (72.11) 定义的检验统计量 Test 的表现。检验的 size 和 power 分别在第 72.4.1 节和 72.4.2 节中研究。为简化起见，我们仅考虑 $m = 1$。首先，我们从下式模拟 $\{r_t\}_{t=1,\dots,n}$

$$
r_t = \mu_1 + V_{1,t}U_{1,t}, \quad V_{1,t} = \bar{\sigma}_1\exp(Z_{1,t}/2),
\tag{72.12}
$$

并独立地从下式模拟 $\{s_t\}_{t=1,\dots,n}$

$$
s_t = \mu_2 + V_{2,t}U_{2,t}, \quad V_{2,t} = \bar{\sigma}_2\exp(Z_{2,t}/2),
\tag{72.13}
$$

其中，对 $i = 1$ 和 $2$，$\{Z_{i,t}\}$ 为高斯 AR(1) 过程，由动态方程 $Z_{i,t} = \phi Z_{i,t-1} + \varepsilon_{i,t}$ 确定，其中 $\varepsilon_{i,t} \stackrel{iid}{\sim} N(0,\bar{\beta}_i^2(1-\phi^2))$，$U_{i,t} \stackrel{iid}{\sim} N(0,1)$。在整个模拟研究中，我们选择的设 计参数为 $\phi = 0.5$，$T = 84$，$105$ 和 $126$，$N = \lceil c_2 T^{\delta} \rceil$，$c_2 = 0.8$，$1.0$，和 $1.2$，$\delta = 0.8$ 和 $1.2$，且 $\alpha = 0.05$。记号 $\lceil x \rceil$ 用于表示大于或等于 $x$ 的最小整数。由于 $\phi = 0.5$ 固定，且根据式 (72.6)，$C_{\alpha}^{i,T}$ 的值由 $\mu_i$ 和 $\sigma_i^2 = \bar{\sigma}_i^2 \exp(\bar{\beta}_i^2/2)$ 确定，除去 $O(1/\sqrt{T})$ 的因子，因此只需 $(\mu_i, \bar{\beta}_i, \bar{\sigma}_i)$ 的值即可指定 $C_{\alpha}^{i,T}$ 的值。对 $C_{\alpha}^{1,T}$，我们选择 $(\mu_1, \bar{\beta}_1, \bar{\sigma}_1) = (0.0003, 0.4, 0.0099)$；对于 $(\mu_2, \bar{\beta}_2, \bar{\sigma}_2)$ 的值，它们会变化

### 72.4.1 检验统计量的大小

本节集中于检验的经验 size。对 $(\mu_2, \bar{\beta}_2, \bar{\sigma}_2)$ 的值，我们考虑两种情况：

Case 1 : $(\mu_2, \bar{\beta}_2, \bar{\sigma}_2) = (0.0003, 0.4, 0.0099)$，且
Case 2 : $(\mu_2, \bar{\beta}_2, \bar{\sigma}_2) = (0.0003, 0.8, 0.0088)$。

对于 Case 1，$\{s_t\}$ 是 $\{r_t\}$ 的独立拷贝，且 $C_{\alpha}^{1,T} = C_{\alpha}^{2,T}$。对于 Case 2，式 (72.6) 以及 $\mu_1 = \mu_2$，$\sigma_1^2 = E(r_t - \mu_1)^2 = \bar{\sigma}_1^2 \exp(\bar{\beta}_1^2/2) = \sigma_2^2$ 的事实意味着 $C_{\alpha}^{2,T} = C_{\alpha}^{1,T} + O(1/\sqrt{T})$。因此，原假设 $C_{\alpha}^{1,T} = C_{\alpha}^{2,T}$ 在 $T \to \infty$ 时渐近成立。

基于 1,000 次重复拒绝原假设的经验频率汇总在表 72.1 和表 72.2 中，分别对应 Case 1 和 Case 2。在这两个表中，拒绝率范围从 0.037 到 0.066，表明检验统计量的经验 size 接近其名义值。

**表 72.1:** $(\mu_2, \bar{\beta}_2, \bar{\sigma}_2) = (0.0003, 0.4, 0.0099)$。

| N\T | 84 | N\T | 105 | N\T | 126 |
|---|---|---|---|---|---|
| 28 | 0.059 | 34 | 0.051 | 39 | 0.061 |
| 35 | 0.057 | 42 | 0.050 | 48 | 0.043 |
| 42 | 0.066 | 50 | 0.045 | 58 | 0.054 |
| 164 | 0.048 | 214 | 0.060 | 266 | 0.050 |
| 204 | 0.049 | 267 | 0.046 | 332 | 0.048 |
| 245 | 0.051 | 320 | 0.048 | 398 | 0.037 |

**表 72.2:** $(\mu_2, \bar{\beta}_2, \bar{\sigma}_2) = (0.0003, 0.8, 0.0088)$。

| N\T | 84 | N\T | 105 | N\T | 126 |
|---|---|---|---|---|---|
| 28 | 0.061 | 34 | 0.056 | 39 | 0.055 |
| 35 | 0.063 | 42 | 0.053 | 48 | 0.047 |
| 42 | 0.065 | 50 | 0.043 | 58 | 0.060 |
| 164 | 0.053 | 214 | 0.054 | 266 | 0.048 |
| 204 | 0.054 | 267 | 0.052 | 332 | 0.055 |
| 245 | 0.052 | 320 | 0.054 | 398 | 0.043 |

## 表 72.3：实验概述。

| Case | μ₁ = μ₂ | σ₁² < σ₂² | β₁ = β₂ | σ₁ < σ₂ | Power |
|------|---------|-----------|---------|---------|-------|
| C3   | μ1 = μ2 | σ1² < σ2² | β1 = β2 | σ1 < σ2 | Relatively smaller |
| C4   | μ1 = μ2 | σ1² < σ2² | β1 < β2 | σ1 = σ2 | Relatively smaller |
| C5   | μ1 = μ2 | σ1² < σ2² | β1 < β2 | σ1 < σ2 | Middle |
| C6   | μ1 < μ2 | σ1² = σ2² | β1 = β2 | σ1 = σ2 | Relatively smaller |
| C7   | μ1 < μ2 | σ1² = σ2² | β1 < β2 | σ1 < σ2 | Relatively smaller |
| C8   | μ1 < μ2 | σ1² < σ2² | β1 < β2 | σ1 = σ2 | Relatively smaller |
| C9   | μ1 < μ2 | σ1² < σ2² | β1 < β2 | σ1 > σ2 | Relatively smaller |
| C10  | μ1 < μ2 | σ1² < σ2² | β1 = β2 | σ1 < σ2 | Middle |
| C11  | μ1 < μ2 | σ1² < σ2² | β1 < β2 | σ1 < σ2 | Relatively larger |

为计算所提检验统计量的经验 power，我们采用与第 72.4.1 节相同的 $(\mu_1,\bar{\beta}_1,\bar{\sigma}_1)$ 的真实值。对 $(\mu_2,\bar{\beta}_2,\bar{\sigma}_2)$，我们考虑九种不同的情况，标记为 C3,C4,..., 和 C11。这九个实验中的每一个都遵循以下三种设计之一：(i) $\mu_1 < \mu_2$，且 $\sigma_1^2 < \sigma_2^2$，(ii) $\mu_1 = \mu_2$，且 $\sigma_1^2 < \sigma_2^2$，(iii) $\mu_1 < \mu_2$，且 $\sigma_1^2 = \sigma_2^2$。不难看出，备择假设 $C_{\alpha1} \neq C_{\alpha2}$ 对这三种设计均成立。因此，每个实验产生的拒绝率即为检验的经验 power。

表 72.3 列出了九个不同实验情况 C3–C11 的 $(\mu_2,\bar{\beta}_2,\bar{\sigma}_2)$，并将其 power 表现总结为相对较小、中等和相对较大三类。九个实验情况在 18 个不同的 $(N,T)$ 下的详细 power 报告在表 72.4 中。一般而言，除少数情况外，power 随着 $N$ 或 $T$ 值的增加而增加。我们还注意到，情况 C11 的 power 水平相对较大，情况 C5 和 C10 为中等。对于其他情况，power 相对较小。所有这些结果表明，检验统计量在检测由两个独立时间序列的积分收益产生的两个 CTE 之间的差异方面具有相当好的 power。

在本节中，我们考虑将第 72.3 节中开发的检验应用于世界七大主要指数，CAC 40（法国）、DAX（德国）、DJIA（美国）、FTSE 100（英国）、NASDAQ（美国）、Nikkei 225
