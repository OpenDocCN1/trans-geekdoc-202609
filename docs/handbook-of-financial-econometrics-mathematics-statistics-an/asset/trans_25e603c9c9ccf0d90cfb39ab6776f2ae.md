

$\hat{\beta}_j''$ 和 $\hat{\alpha}_j''$ 是利用 $R_{jt}$、$R_{Tt}$ 和 $R'_{mt}$ 的可观测值得到的 $\beta_j''$ 和 $\alpha_j''$ 的样本估计值。[^5] 注意，$\psi_j$ 的符号再次取决于 $\beta_j''$ 大于还是小于1。

## 62.3 假设 $R_m$ 和 $R_b$ 存在测量误差时 Plim b̂ 的推导

Friend和Blume（1970）将詹森绩效度量估计值 $\hat{\alpha}_j''$ 对系统性风险估计值 $\hat{\beta}_j''$ 进行回归，以检验单因子CAPM是否是一个有用的模型。如果 $R_{mt}$ 和 $R_{bt}$ 的测量误差确实如我们假设的那样存在，则FB的回归可以看作具有如下形式：

$$
\hat{\alpha}_j'' = a + b \hat{\beta}_j'' + V_j, \tag{62.15}
$$

其中 $V_j \sim N(0, \sigma_V^2)$。经过大量整理，并令 $b$ 的真实值为零，可以证明[^6]：

$$
\operatorname{plim}_{j\to\infty} \hat{b} = \frac{-B + \tau + \frac{\theta k}{1-\theta} - \frac{\sigma_s^2(B+k-\tau)}{\sigma_{\beta_j}^2(1-\theta)^2}}{1 + \frac{\sigma_s^2}{\sigma_{\beta_j}^2(1-\theta)^2}}, \tag{62.16}
$$

其中 $k = \bar{R}_m - \bar{R}_b$，$\sigma_{\beta_j}^2 = \beta_j\text{的方差}$，$\sigma_s^2 = S_j\text{的方差}$，以及 $\theta = (\sigma_e^2 + \sigma_\eta^2)/(\sigma_M^2 + \sigma_e^2 + \sigma_\eta^2)$。

如果 $R_m$ 和 $R_b$ 均不存在测量误差，则(62.16)简化为

$$
\operatorname{plim}_{j\to\infty} b = -\frac{\sigma_s^2 k}{\sigma_{\beta_j}^2 + \sigma_s^2}. \tag{62.17}
$$

FB实际上使用方程(62.17)来解释以下事实：抽样误差对 $\beta_j$ 的影响不会导致 $\hat{b}$ 为负。然而，当仅考虑 $R_m$ 和 $R_b$ 中的恒定测量误差时，(62.16)简化为

$$
\operatorname{plim}_{j\to\infty} \hat{b} = \frac{-B + \tau - \left[\sigma_s^2 (B + k - \tau)/\sigma_{\beta_j}^2\right]}{1 + \sigma_s^2/\sigma_{\beta_j}^2}. \tag{62.18}
$$

方程(62.18)可用于解释FB的主要发现：$b < 0$，因为(62.18)可以改写为

$$
\operatorname{plim}_{j\to\infty} \hat{b} = -\frac{\sigma_s^2 k}{\sigma_{\beta_j}^2 + \sigma_s^2} - B + \tau. \tag{62.19}
$$

其中方程(62.19)的第一项表示第一轮回归中系统性风险样本变异引起的偏误，$-B$ 表示借贷利率差异引起的偏误，$\tau$ 表示 $R_m$ 测量误差引起的偏误。因此，如果 $-B + \tau$ 显著为负（正），那么当第一轮回归中 $\beta_j$ 的抽样变异引起的偏误非常小时，$\hat{b}$ 也将在渐近意义下为负（正）。由于 $-B = R_f - R_b < 0$，FB将 $\hat{b} < 0$ 归因于借贷利率差异的设定，似乎是一个合理的命题。

最后，当把样本期划分为两个子时期时，FB发现1960–1964年的 $\hat{b}$ 为负，而1965–1968年的 $\hat{b}$ 为正。FB将后一种现象归因于市场收益率中的“未预期升值”，尽管FB并未严格定义该术语。如果按照许多经济学家的做法，FB将未预期升值定义为市场已实现收益率与该时期期望值之差，那么后者不会对 $b$ 造成任何偏误，因为单因子模型已纳入了 $R'_m$ 的随机性。然而，根据我们的方程(62.19)，如果 $-B + \tau$ 为正（负），$b$ 可以为正（负）。进一步地，如果资本市场上不属于纽约证券交易所上市股票部分的收益率具有大于1的 $\beta$，那么当已实现的 $R_m$ 为正（负）时，某个子时期的 $\tau$ 可以为正（负）。因此，即使 $-B < 0$，繁荣期的 $b$ 可能为正，而衰退期的 $b$ 仍然为负。

## 62.4 CAPM的另一种假设检验方法

BJS和MS也使用了一种替代假设检验方法。在考虑测量误差之后，用于检验系统性风险预测能力的原假设为

$$
H_0: c = \tau - B, \quad d = \bar{R}_m - \bar{R}_b = (\bar{R}'_m - \bar{R}_T) + (\tau - B), \tag{62.20}
$$

其中 $c$ 和 $d$ 是线性关系的截距和斜率

$$
\bar{R}_j = c + d \hat{\beta}_j. \tag{62.21}
$$

$\psi_j$ 和 $s_j$ 对 $c$ 和 $d$ 的估计值的影响可以利用(62.13a)进行分析。如果假设 $\psi_j$ 服从均值为 $(1 - \bar{\beta})(\sigma_e^2 + \sigma_\eta^2)/(\sigma_M^2 + \sigma_e^2 + \sigma_\eta^2)$、有限方差为 $\sigma_{\beta_j}^2 \left[\sigma_e^2 + \frac{\sigma_\eta^2}{\sigma_M^2 + \sigma_e^2 + \sigma_\eta^2}\right]^2$ 的正态分布，则 $\hat{c}$ 和 $\hat{d}$ 的概率极限为

$$
\operatorname{plim}_{j\to\infty} \hat{d} = \frac{d\left(\frac{\sigma_M^2 + \sigma_e^2 + \sigma_\eta^2}{\sigma_M^2}\right)}{1 + \sigma_s^2/\sigma_{\beta_j}^2}, \tag{62.22a}
$$

$$
\operatorname{plim}_{j\to\infty} \hat{c} = -B + \frac{d(1-\bar{\beta}_j)(\sigma_e^2+\sigma_\eta^2)}{\sigma_M^2+\sigma_e^2+\sigma_\eta^2} + \lambda \bar{\beta}_j + \frac{\lambda(1-\bar{\beta}_j)(\sigma_e^2+\sigma_\eta^2)}{\sigma_M^2+\sigma_e^2+\sigma_\eta^2}, \tag{62.22b}
$$

其中 $\lambda$ 是 $\hat{d}$ 的渐近偏误，即 $\operatorname{plim}_{j\to\infty} \hat{d} - d$。

将(62.16)与(62.22a)进行比较，可以看出，将 $\alpha$ 对 $\beta$ 回归比本节所述的方法会对估计参数产生更大的偏误。原因是 $b$ 的估计除了受 $\beta_j$ 的样本变异以及 $R_b$ 和 $R_m$ 的随机测量误差影响外，还受到 $R_b$ 和 $R_m$ 的恒定测量误差的影响。然而，$\bar{R}_m$ 和 $\bar{R}_b$ 均不可观测，在原假设中使用 $(\bar{R}'_m - \bar{R}_T)$ 替代 $(\bar{R}_m - \bar{R}_b)$。因此，待检验的假设并未被精确地表述。因此，即使估计参数的偏误较小，也不意味着该检验在统计上更具功效。顺便提一下，(62.22a)是Black、Jensen和Scholes（1972）所得结果的推广形式，他们只考虑了抽样变异的影响。

下面考察 $b$ 与 $d$ 之间的关系，以及(62.15)与(62.21)的决定系数之间的相对大小：

- (i) 根据回归斜率的定义，我们有

$$
\hat{b}=\frac{\operatorname{Cov}(\hat{\alpha}_j,\hat{\beta}_j)}{\operatorname{Var}(\hat{\beta}_j)}
=\frac{\operatorname{Cov}\{(\bar{R}_j-\bar{R}_T)-\hat{\beta}_j(\bar{R}'_m-\bar{R}_T),\hat{\beta}_j\}}{\operatorname{Var}(\hat{\beta}_j)}
=\frac{\operatorname{Cov}[(\bar{R}_j-\bar{R}_T),\hat{\beta}_j]}{\operatorname{Var}(\hat{\beta}_j)}-\frac{(\bar{R}'_m-\bar{R}_T)\operatorname{Var}(\hat{\beta}_j)}{\operatorname{Var}(\hat{\beta}_j)}
=\hat{d}-(\bar{R}'_m-\bar{R}_T). \tag{62.23}
$$

- (ii) (62.15)的决定系数可以推导为[^8]：

$$
R_1=\frac{\operatorname{Cov}(x,y)-k\operatorname{Var}(y)}{\sqrt{\operatorname{Var}(y)\left(\operatorname{Var}(x)+k^2\operatorname{Var}(y)-2k\operatorname{Cov}(x,y)\right)}}
=\left[\frac{\operatorname{Cov}(x,y)}{\sqrt{\operatorname{Var}(y)\operatorname{Var}(x)}}-k\sqrt{\frac{\operatorname{Var}(y)}{\operatorname{Var}(x)}}\right]
\left[\frac{\sqrt{\operatorname{Var}(x)}}{\sqrt{\operatorname{Var}(x)+k^2\operatorname{Var}(y)-2k\operatorname{Cov}(x,y)}}\right], \tag{62.24}
$$

其中 $x=\bar{R}_j-\bar{R}_T$，$k=\bar{R}'_m-\bar{R}_T$，$y=\hat{\beta}_j$。

类似地，(62.21)的决定系数可以定义为

$$
R_2=\frac{\operatorname{Cov}(x,y)}{\sqrt{\operatorname{Var}(y)\operatorname{Var}(x)}}. \tag{62.25}
$$

通过比较 $R_1$ 和 $R_2$，可以发现(62.15)的决定系数由三个不同的分量决定，即：(1)(62.21)的决定系数；(2) $k\sqrt{\operatorname{Var}(y)/\operatorname{Var}(x)}$；(3) $\left[\frac{\operatorname{Var}(x)}{\operatorname{Var}(x)+k^2\operatorname{Var}(y)-2k\operatorname{Cov}(x,y)}\right]^{1/2}$。如果 $\operatorname{Cov}(x,y)$ 趋近于零，则 $R_1^2$ 将趋近于 $\frac{k^2\operatorname{Var}(y)}{\operatorname{Var}(x)+k^2\operatorname{Var}(y)}$。因此，$R_1^2$ 的大小通常不同于 $R_2^2$ 的大小。

Jensen（1968）利用 $\hat{\alpha}'_j$（$j=1,\dots,m$）的样本分布来展示詹森绩效度量的有用性。Black、Jensen和Scholes使用了类似的概念对CAPM进行时间序列检验。此外，他们声称时间序列检验不受系统性风险测量误差的影响。然而，从(62.13b)我们证明了 $\hat{\alpha}_j''$ 的样本分布受到：(1) $\beta_j$ 的样本变异，以及(2) $R_b$ 和 $R_m$ 两者的测量误差的影响。[^10]

## 62.5 结论

总而言之，我们的分析表明，CAPM的横截面检验和时间序列检验都会受到 $R_b$ 和 $R_m$ 测量误差以及系统性风险样本变异的影响。因此，对CAPM实证结果的解释必须极为谨慎。此外，也应重新考虑普通最小二乘法的使用，并在可能之处采用变量误差方法。

至于进一步研究的领域，显然测量误差也会影响从双因子模型得到的估计，因为上文提出的单因子变量误差模型在概念上与双因子模型颇为相似。[^11] 最后，还存在与 $\beta$ 的非平稳性相关的问题，这可能意味着当前的CAPM从一开始就未被正确设定（参见Galai和Masulis（1976））。

## 参考文献

- Black, F.、Jensen, M. C. 和 Scholes, M.（1972）。资本资产定价模型：若干经验检验。载于 M. C. Jensen 主编《资本市场理论研究》，纽约：普雷格出版社。
- Blume, M. 和 Friend, I.（1973）。资本资产定价模型的新视角。*金融学杂志*，28，19-33。
- Brennan, M. J.（1971）。借贷利率差异下的资本市场均衡。*金融与数量分析杂志*，7，1197-1205。
- Cramer, H.（1946）。*统计的数学方法*。普林斯顿大学出版社。
- Fama, E. F.（1968）。风险、收益与均衡：若干澄清性评论。*金融学杂志*，23(1)，29-40。
- Friend, I. 和 Blume, M.（1970）。不确定性下的投资组合绩效度量。*美国经济评论*，60，561-575。
- Galai, D. 和 Masulis, R. W.（1976）。期权定价模型与股票的风险因子。*金融经济学杂志*，3，53-81。
- Jen, F. C.（1970）。关于随机游走与技术理论的讨论：补充证据。*金融学杂志*，25，495-499。

## 脚注

[^5]: 当 $R_b$ 和 $R_m$ 均无测量误差时，方程(13)简化为 a) $\beta_j = \hat{\beta}_j + S_j$ 和 $\alpha_j = \hat{\alpha}_j + S_j(\bar{R}_m - \bar{R}_b)$。这是Friend和Blume（1970）以及Black、Jensen和Scholes [1972]所采用的结果。

[^6]: 见附录。

[^10]: 由于 $\hat{\alpha}_j''$ 除詹森度量 $\alpha_j''$ 的真实值外，还包含分量 $\psi_j$、$s_j$、$B$ 和 $\tau$。

[^11]: 从Black等人（1972）和本章的结果可以看出，即使BJS的方法可能减少了样本变异，所谓零贝塔因子的估计也仍然无法避免测量误差。不过，仍需要在实践中推导新的程序来消除这些误差。

