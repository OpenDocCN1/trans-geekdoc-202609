
我们有

$a = 1 + \text{INT}\left[\frac{\ln(X/S_0) - \mu + \sigma\sqrt{T}\sqrt{\frac{\theta}{1-\theta}}}{\sigma/\sqrt{T\theta(1-\theta)}}\right]$

然后，式 (102.50) 成立。现在

$Z_1 = \frac{a - T\varphi}{\sqrt{T\varphi(1-\varphi)}} = \frac{1 + \text{INT}\left[\frac{\ln(X/S_0) - \mu + \sigma\sqrt{T}\sqrt{\frac{\theta}{1-\theta}}}{\sigma/\sqrt{T\theta(1-\theta)}}\right] - T\varphi}{\sqrt{T\varphi(1-\varphi)}}. \quad (102.51)$

在极限情况下，项 $1 + \text{INT}[\cdot]$ 将简化为 $[\cdot]$。因此，$Z_1$ 可重新表述为

$Z_1 \sim \frac{\ln\left(\frac{X}{S_0}\right) - \mu}{\sigma\sqrt{\frac{\varphi(1-\varphi)}{\theta(1-\theta)}}} + \frac{\sqrt{T}(\theta - \varphi)}{\sqrt{\varphi(1-\varphi)}}. \quad (102.52)$

将式 (102.46) 和 (102.47) 中的 $H^+$ 和 $H^-$ 以及 $1+R = e^{r/T}$ 代入式 (102.39)，我们有

$\varphi = \frac{(1+R-H^-)H^+}{(1+R)(H^+ - H^-)} = \frac{\left(e^{r/T} - e^{\mu/T - (\sigma/\sqrt{T})\sqrt{\theta/(1-\theta)}}\right) e^{\mu/T + (\sigma/\sqrt{T})\sqrt{(1-\theta)/\theta}}}{e^{r/T}\left(e^{\mu/T + (\sigma/\sqrt{T})\sqrt{(1-\theta)/\theta}} - e^{\mu/T - (\sigma/\sqrt{T})\sqrt{\theta/(1-\theta)}}\right)}$
$= \frac{e^{(\sigma/\sqrt{T})\sqrt{(1-\theta)/\theta}} - e^{\mu/T - r/T} + \left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}} - \sqrt{\frac{\theta}{1-\theta}}\right)}{e^{(\sigma/\sqrt{T})\sqrt{(1-\theta)/\theta}} - e^{-(\sigma/\sqrt{T})\sqrt{\theta/(1-\theta)}}}. \quad (102.53)$

现在，我们在 $\frac{1}{\sqrt{T}}$ 中展开泰勒级数$^{11}$，并得到

$\varphi = \frac{\left(\frac{\sigma}{\sqrt{T}}\right)\sqrt{\frac{1-\theta}{\theta}} - (\mu - r)/T - \left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}} - \sqrt{\frac{\theta}{1-\theta}}\right) + O\left(\frac{1}{\sqrt{T}}\right)}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}} + \sqrt{\frac{\theta}{1-\theta}}\right) + O\left(\frac{1}{\sqrt{T}}\right)}$
$= \frac{\left(\frac{\sigma}{\sqrt{T}}\right)\sqrt{\frac{\theta}{1-\theta}} + O\left(\frac{1}{\sqrt{T}}\right)}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}} + \sqrt{\frac{\theta}{1-\theta}}\right) + O\left(\frac{1}{\sqrt{T}}\right)}, \quad (102.54)$

其中 $O\left(\frac{1}{\sqrt{T}}\right)$ 表示比 $\frac{1}{\sqrt{T}}$ 更快趋于零的函数。

可以证明

$$\lim_{T\to\infty}\varphi = \frac{\sqrt{\frac{\theta}{1-\theta}}}{\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}}= \frac{\sqrt{\frac{\theta}{1-\theta}}}{\sqrt{\frac{1-\theta+\theta}{\theta(1-\theta)}}}= \theta.$$ 
(102.55)

类似地，我们有

$$\sqrt{T}(\theta-\varphi)=\sqrt{T}\left(\theta-\frac{e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{\frac{\mu}{T}-\frac{r}{T}+(\frac{\sigma}{\sqrt{T}})\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)}}{e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{-(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{\theta}{1-\theta}}}}\right)$$ 

$$=\frac{\theta\sqrt{T}\left(e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{-(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{\theta}{1-\theta}}}\right)-\sqrt{T}\left(e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{\frac{\mu}{T}-\frac{r}{T}+(\frac{\sigma}{\sqrt{T}})\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)}\right)}{e^{(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{1-\theta}{\theta}}}-e^{-(\frac{\sigma}{\sqrt{T}})\sqrt{\frac{\theta}{1-\theta}}}}\.$$
(102.56)

我们也在 $\frac{1}{\sqrt{T}}$ 中展开泰勒级数，可以得到

$$\sqrt{T}(\theta-\varphi)=\frac{\theta\sqrt{T}\left[\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+\frac12\left(\frac{\sigma}{\sqrt{T}}\right)^2\left(\frac{1-\theta}{\theta}-\frac{\theta}{1-\theta}\right)+O\left(\frac1T\right)\right]}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}-\frac{\sqrt{T}\left[\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}\right)+\frac12\left(\frac{\sigma}{\sqrt{T}}\right)^2\left(\frac{1-\theta}{\theta}\right)-\left(\frac{\mu-r}{T}+\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)\right]}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}+\frac{\frac12\left(\frac{\sigma}{\sqrt{T}}\right)^2\left(\sqrt{\frac{1-\theta}{\theta}}-\sqrt{\frac{\theta}{1-\theta}}\right)^2+O\left(\frac1T\right)}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}$$ 

$$=\frac{\frac12\theta\frac{\sigma^2}{\sqrt{T}}\left(\frac{1-\theta}{\theta}-\frac{\theta}{1-\theta}\right)+\frac{\mu-r}{\sqrt{T}}+\frac12\frac{\sigma^2}{\sqrt{T}}\left(\frac{\theta}{1-\theta}-2\right)+O\left(\frac1{\sqrt{T}}\right)}{\left(\frac{\sigma}{\sqrt{T}}\right)\left(\sqrt{\frac{1-\theta}{\theta}}+\sqrt{\frac{\theta}{1-\theta}}\right)+O\left(\frac1{\sqrt{T}}\right)}.$$
(102.57)

## 表 102.2：Rendleman 和 Bartter 与 Cox 等方法的比较。

| 模型 | Rendleman and Bartter (1979) | Cox et al. (1979) |
|---|---|---|
| 数学和概率论知识 | 基础代数
泰勒展开
二项式定理
中心极限定理
二项分布的性质 | 基础代数
泰勒展开
二项式定理
中心极限定理
二项分布的性质
Lyapunov 条件 |
| 假设 | 股票对数收益率的均值和方差在期权存续期内保持不变 | 股票从一个时期到下一个时期遵循二项过程。它只能以概率 p 上涨 u 倍，或以概率 1 − p 下跌 d 倍
为了应用中心极限定理，需要选择 u、d 和 p |
| 优点和缺点 | 1. 具有数学和概率论本科水平训练的读者可以遵循此方法
2. 该方法直观，但推导更复杂且繁琐 | 1. 具有概率论高级知识的读者可以遵循此方法；但对于没有的读者，可能难以跟进
2. 对参数 u、d 和 p 的假设使此方法更受限制 |

(Lee et al., 2013b)。用 $S$ 表示当前股票价格，用 $S_t$ 表示第 $t$ 期末的股票价格。则 $\frac{S_t}{S_{t-1}} = \exp(K_t)$ 是一个服从对数正态分布的随机变量，其中 $K_t$ 是第 $t$ 期的收益率，并假设为服从正态分布的随机变量。假设每个 $K_t$ 具有相同的期望值 $\mu_k$ 和方差 $\sigma_k^2$。则 $K_1 + K_2 + \cdots + K_T$ 是一个期望值为 $T\mu_k$、方差为 $T\sigma_k^2$ 的正态随机变量。

## 对数正态分布的性质。

*如果连续随机变量 y 服从正态分布，则式 (102.61) 中定义的连续变量 x 服从对数正态分布：*

$x = e^{y}.$
(102.62)

如果变量 y 的均值为 μ，方差为 σ²，则变量 x 的均值 μ_x 和方差 σ_x² 分别定义如下：

μ_x = e^{μ+1/2 σ²}. (102.63) σ_x² = e^{2μ+σ²}(e^{σ²} - 1). (102.64)

根据该性质，我们可以将 $S_T / S = \exp(K₁ + K₂ + ⋯ + K_T)$ 的期望值定义为

E(S_T / S) = exp(T μ_k + T σ_k² / 2). (102.65)

在风险中性投资者的假设下，期望收益率 E(S_T / S) 假定为 e^{rT}（其中 r 为无风险利率）。换句话说，下式成立：

μ_k = r - σ_k² / 2. (102.66)

看涨期权价格 C 可通过以无风险利率贴现期权到期价格的期望值来确定：

C = e^{-rT} E[Max(S_T - X, 0)]. (102.67)

注意在式 (102.66) 中：Max(S_T - X, 0) = { S_T - X 当 S_T > X 时，0 否则，} 其中 T 为到期时间，X 为行使价。

设 x = S_T / S 服从对数正态分布。则有 C = e^{-rT} E[Max(S_T - X)] = e^{-rT} ∫_{X/S}^{∞} S [x - X/S] g(x) dx = e^{-rT} S ∫_{X/S}^{∞} x g(x) dx - e^{-rT} S X/S ∫_{X/S}^{∞} g(x) dx，(102.68) 其中 g(x) 是 x = S_T / S 的概率密度函数。

在这里，我们将利用正态分布、对数正态分布及其相互关系来推导 Black–Scholes 模型。我们
