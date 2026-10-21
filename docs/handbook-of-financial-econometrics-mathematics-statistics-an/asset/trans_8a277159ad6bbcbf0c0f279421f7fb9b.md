
$U$, 用 $T$、$\sigma$ 和 $\beta$ 表示，这对于对风险厌恶参数 $\beta$ 进行推断很有用。相同的密度 $f(\mu)$ 由 (10) 给出，回顾比率 $\mu/\sigma=\sigma(\beta-1/2)$，

$$f(\mu)=c_1\sum_{r=0}^{\infty}\Gamma\left(\frac{2r+T+1}{4}\right)\frac{1}{r!}\left(\frac{2\sigma^2(\beta-1/2)Tu-(T-1)}{\sqrt{2\pi}\sigma}\right)^r\left(\frac{1}{u^2}\right)^{\frac{2r+T+1}{4}}, \tag{65.11}$$

其中，现在

$$c_1=\frac{e^{-\frac{T}{2}\sigma^2(\beta-1/2)^2}}{\sqrt{\pi}\,2^{\frac{T+3}{4}}\left(\frac{\sigma\sqrt{T}}{T-1}\right)^{\frac{T-1}{2}}\Gamma\left(\frac{T-1}{2}\right)}.$$

$\beta$ 的 MVU 估计量，记为 $\hat{\beta}$ 为

$$\hat{\beta}=\frac{T-3}{T-1}\frac{\bar{Y}}{S^2}+\frac{1}{2}. \tag{65.12}$$

$\hat{\beta}$ 是 MVU 估计量的事实很容易证明。众所周知 $\bar{Y}$ 和 $S^2$ 是 $\mu$ 和 $\sigma$ 的完备充分统计量，因此根据 Rao–Blackwell 定理，$\bar{Y}$ 和 $S^2$ 的函数且关于 $\beta$ 无偏的估计量是 $\beta$ 的 MVU 估计量 (Hogg and Craig, 1978)。也众所周知 $\bar{Y}$ 的期望值为 $\mu$，$1/S^2$ 的期望值为 $(1/\sigma^2)[(T-1)/(T-3)]$，因此 $[(T-3)/(T-1)](\bar{Y}/S^2)$ 的期望值为 $\mu/\sigma^2=\beta-1/2$，由此得到 (65.12)。

$\hat{\beta}$ 的均值为 $\beta$，$\hat{\beta}$ 的方差为

$$\operatorname{Var}(\hat{\beta})=\frac{T-3}{(T-5)\sigma^2}\left(\frac{1}{T}+\frac{2\mu^2}{(T-3)\sigma^2}\right), \tag{65.13}$$

它始终小于有偏估计量 $\hat{\beta}_{\mathrm{ML}}$ 的方差。

$\hat{\beta}$ 的精确抽样分布可由 (65.10) 或 (65.11) 得到，因为 $\hat{\beta}=[(T-3)/(T-1)]U+1/2$ 是统计量 $U$ 的线性变换。因此，$\hat{\beta}$ 的精确抽样分布用三个参数 $T$、$\sigma$ 和 $\beta$ 表示为 pdf，记为

$$\begin{aligned} f(\hat{\beta})={}&\frac{c_2}{v}\sum_{r=0}^{\infty}\Gamma\left(\frac{2r+T+1}{4}\right)\\ &\times\frac{1}{r!}\left(\frac{2T\sigma^2(\beta-1/2)(\hat{\beta}-1/2)\left(\frac{T-1}{T-3}\right)-(T-1)}{\sqrt{2T}\sigma(\hat{\beta}-1/2)\left(\frac{T-1}{T-3}\right)}\right)^r,\\ &-\infty<\hat{\beta}<\infty,\ \sigma>0,\ T>3,\ -\infty<\beta<\infty \tag{65.14} \end{aligned}$$

且其中

$c_2 = \frac{e^{-T(\beta-1/2)^2\sigma^2/2}}{\sqrt{\pi}2^{\frac{T-3}{4}}\left(\frac{\sigma\sqrt{T}}{T-1}\right)^{\frac{T-1}{2}}\Gamma\left(\frac{T-1}{2}\right)\frac{(T-1)}{(T-3)} = c_1\frac{(T-1)}{(T-3)},$

$v = \left[(\hat{\beta}-1/2)\left(\frac{(T-1)}{(T-3)}\right)\right]^{\frac{T+1}{2}}.$

尽管 $\hat{\beta}$ 的 pdf 由 (65.14) 给出，具有三个参数，且不是标准抽样分布族的成员，数值方法可用于 $f(\hat{\beta})$ 或 $\hat{\beta}$ 的累积分布函数，记为 $F(x)=\int_{-\infty}^{x} f(\hat{\beta})d\hat{\beta}$。例如，图 65.1 绘制了 $T=30$、$\sigma=1.5$ 时 $\hat{\beta}$ 的密度，分别对应 $\beta=1$ 和 $\beta=1.5$。当 $\beta=1$ 时，$E(\hat{\beta})=1.0$ 且 $Var(\hat{\beta})=0.056$。注意两条曲线都略微右偏，看起来近似于钟形曲线。

## 65.3 一个实证例子

为举例说明，1925 年至 1983 年期间纽约证券交易所的等权重指数是从 Center for

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2414_0.png)

图 65.1：MVU 相对风险厌恶估计量 ($\hat{\beta}$) 的概率分布。

Research in Security Prices (CRSP) at the University of Chicago and used as the proxy for the rates of return on the market portfolio. 1926 年至 1983 年的无风险利率代理是《Stocks, Bonds, and Inflation (1989)》中的美国国库券月利率。如上所述，$X=(1+R_m)/(1+R_f)$ 为超额收益率，即市场投资组合相对于无风险利率的收益率。Brown and Gibbons (1985) 基于代表性个人在不确定性下面临的动态消费投资组合问题的以下 Euler 条件，提出了相对风险厌恶参数的两种估计量。

$$E\left[(X-1)X^{-\beta}\right]=0, \tag{65.15}$$

其中 $\beta$ 为相对风险厌恶参数。

他们的第一个估计量是所谓的参数估计量；即由 (65.2) 给出的近似最大似然估计量。它基于 $X$ 的对数正态性假设。很容易证明该估计量的渐近方差为 $(\sigma^2+2\mu^2)/\sigma^4$（见附录）。他们的第二个估计量是非参数的，对偏离任何特定分布具有稳健性。

在表 65.1 中，我们基于这两种估计量，即 Brown and Gibbons (1985) 的参数估计量 $\hat{\beta}_{\mathrm{ML}}$ 和 MVU 估计量 $\hat{\beta}$，对三个样本期给出了实证结果，这些样本期的样本量接近 $T=30$ 或 100。第一个样本期为 1926 年 1 月至 1983 年 12 月，投资期限为七个月；第二个样本期为 1926 年 1 月至 1952 年 12 月，投资期限为 11 个月；第三个样本期为 1953 年 1 月至 1983 年 12 月，投资期限为 12 个月。应注意

**表 65.1：相对风险厌恶的估计。**

| 投资期限 样本期及样本量 $T$ | $\overline{\log X}$ | $S$ | $\hat{\beta}_{\mathrm{ML}}$（标准误差） | $\hat{\beta}$ |
|---|---:|---:|---:|---:|
| 7 个月<br>1/1926–12/1983<br>$T=99$ | 0.0531 | 0.25 | 1.36 (0.44) | 1.34 |
| 11 个月<br>1/1926–12/1952<br>$T=29$ | 0.0940 | 0.47 | 1.02 (0.52) | 0.98 |
| 12 个月<br>1/1953–12/1983<br>$T=31$ | 0.0795 | 0.23 | 2.08 (1.00) | 1.97 |

Kraus, A. and Litzenberger, R. (1975). Market Equilibrium in a Multiperiod State Preference Model with Logarithmic Utility. Journal of Finance, 30, 1213-1227.
Lintner, J. (1983). The Lognormality of securities returns, portfolio selection and market equilibrium. Unpublished manuscript, Harvard University.
Loève, M. (1963). Probability Theory, 3rd edn. Princeton, NJ: Van Nostrand.
Merton, R. (1971). Optimum Consumption and Portfolio Rules in a Continuous Time Model. Journal of Economic Theory, 3, 373-413.
Rothschild, M. and Stiglitz, J. (1971). Increasing Risk II: Its Economic Consequences. Journal of Economic Theory, 3, 66-84.
Royden, H. L. (1988). Real Analysis, 3rd Ed. New York: Macmillan.
Rubinstein, M. L. (1977). The strong case for the generalized logarithmic utility models as the premier model of financial markets. Financial Decision Making under Uncertainty. In H. Levy and M. Sarnat, eds., New York: Academic Press.
Samuelson, P. (1969). Lifetime Portfolio Selection by Dynamic Stochastics Programming. Review of Economics and Statistics, 51, 239-246.

## 附录 65A

考虑由 (65.2) 给出的 β 的近似最大似然估计量 β̂_ML。

### 结果 1.

E(β̂_ML) = [(T - 1)β - 1]/(T - 3)

证明：

E(β̂_ML) = E( Ȳ / S² + 1/2 ) = 1/2 + E(Ȳ) E(1/S²) = 1/2 + μ (T - 1)/(T - 3) 1/σ²
= [(T - 1)β - 1]/(T - 3).

### 结果 2.

Var(β̂_ML) = (T - 1)² / [(T - 3)(T - 5)σ⁴] ( σ²/T + 2μ²/(T - 3) )

证明：

Var(β̂_ML) = Var( Ȳ/S² + 1/2 ) = E( Ȳ/S² )² - [ E( Ȳ/S² ) ]²
= E( Ȳ/S² )² - (T - 1) μ² / [(T - 3) σ⁴]
and
E( Ȳ/S² )² = E(Ȳ²) E(1/S⁴) = (σ²/T + μ²) (T - 1)² / [(T - 3)(T - 5)] 1/σ⁴.
Therefore,
Var(β̂_ML) = (T - 1)² / [(T - 3)(T - 5)σ⁴] ( σ²/T + 2μ²/(T - 3) )
and the asymptotic variance follows by letting T → ∞.

## 注释

- (1) 在金融中，μ 表示预期市场风险溢价，且大于零。这意味着相对风险厌恶参数 β 将大于 1/2。然而在本章中，我们关注的是估计量而非总体参数 β。我们考虑的估计量，包括 Brown 和 Gibbons (1985) 研究的估计量，均不受相应参数限制的约束。
- (2) 其基础的结果被称为 Fubini 定理 (Loève 1963; Royden, 1988)。

