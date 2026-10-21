
- L. H. P. Lang 和 R. H. Litzenberger (1989)。股息公告：现金流信号 vs. 自由现金流假说？ Journal of Financial Economics, 24, 181–191.
- C. F. Lee 和 J. Shi (2010)。金融和计量经济学研究中替代 ODE 的应用, in Cheng F. Lee, Alice C. Lee, and John Lee, ed.: Handbook of Quantitative Finance and Risk Management (Springer), 1293–1300.
- C. F. Lee, C. Wu, and M. Djarraya (1987)。股息调整过程的进一步实证研究。 Journal of Econometrics, 35, 267–285.
- E. M. Lerner 和 W. T. Carleton (1966a)。企业的融资决策。 Journal of Finance, 21, 202–214.
- E. M. Lerner 和 W. T. Carleton (1966b)。金融分析理论, New York, NY: Harcourt, Brace & World.
- E. Lie (2000)。盈余资金与代理问题：增量现金支付的实证研究。 Review of Financial Studies, 13, 219–248.
- J. Lintner (1962)。股息、收益、杠杆、股价及对企业的资本供给。 Review of Economics and Statistics, 44, 243–269.
- J. Lintner (1963)。资本成本与企业成长的最优融资。 Journal of Finance, 18, 292–310.
- J. Lintner (1964)。不确定性下的最优股息与企业成长。 Quarterly Journal of Economics, 78, 49–95.
- J. Lintner (1965)。证券价格、风险与多元化的最大收益。 Journal of Finance, 20, 587–615.
- R. H. Litzenberger 和 K. Ramaswamy (1979)。个人税收和股息对资本资产价格的影响：理论与实证证据。 Journal of Financial Economics, 7, 163–195.
- M. H. Miller 和 F. Modigliani (1961)。股息政策、成长与股份估值。 Journal of Business, 34, 411–433.
- M. H. Miller 和 K. Rock (1985)。非对称信息下的股息政策。 Journal of Finance, 40, 1031–1051.
- J. Mossin (1966)。资本资产市场的均衡。 Econometrica, 34, 768–783.
- D. Nissim 和 A. Ziv (2001)。股息变动与未来盈利能力。 Journal of Finance, 56, 2111–2133.
- T. Opler 和 S. Titman (1993)。杠杆收购活动的决定因素：自由现金流 vs. 财务困境成本。 Journal of Finance, 48, 1985–1999.
- M. A. Petersen (2009)。金融面板数据集标准误差的估计：方法比较。 Review of Financial Studies, 22, 435–480.
- J. W. Pratt (1964)。小额与大额的风险厌恶。 Econometrica, 32, 122–136.
- M. S. Rozeff (1982)。成长、贝塔与代理成本作为股息支付率的决定因素。 Journal of Financial Research, 5, 249–259.
- W. F. Sharpe (1964)。资本资产定价：风险条件下的市场均衡理论。 Journal of Finance, 19, 425–442.
- C. W. Smith Jr. 和 R. L. Watts (1992)。投资机会集与企业融资、股息和薪酬政策。 Journal of Financial Economics, 32, 263–292.
- S. B. Thompson (2010)。同时按企业和时间聚类的标准误差的简易公式。 Working paper.
- B. A. Wallingford II (1972a)。预定投资下股息政策优化的跨期方法。 Journal of Finance, 27, 627–635.

因此，

$\dot{p}(t) + p(t)g(t) = \dot{c}(t) \cdot \exp\left(-\int g(t)dt\right). \quad (96A.6)$

由方程 (96A.1) 和 (96A.6) 可得

$\dot{c}(t) \cdot \exp\left(-\int g(t)dt\right) = q(t). \quad (96A.7)$

等价地，

$\dot{c}(t) = q(t) \cdot \exp\left(\int g(t)dt\right). \quad (96A.8)$

因此，

$c(t) = \int q(t) \cdot \exp\left(\int g(t)dt\right) dt. \quad (96A.9)$

将方程 (96A.9) 代入方程 (96A.3)，我们得到方程 (96A.1) 的通解，

$p(t) = \exp\left(-\int g(t)dt\right) \cdot \left[\int q(t) \exp\left(\int g(t)dt\right) dt\right]. \quad (96A.10)$

为求解方程 (96.17)，我们将应用上述结果。令

$g(t) = \delta \frac{\dot{m}(t)}{m(t)} - k$

且

$q(t) = -G(t).$

因为

$\exp\left(\int g(t)dt\right) = \exp\left(\int \left(\delta \frac{\dot{m}(t)}{m(t)} - k\right) dt\right)$
$= \exp\left(\delta \int \frac{\dot{m}(t)}{m(t)}dt - kt\right)$
$= \exp\left(\delta \ln(m(t)) - kt + c\right)$
$= c_1 \cdot m(t)^{\delta} \exp(-kt), \quad (96A.11)$

其中 $c_1 > 0$。则有

$P(t) = c_2 \cdot m(t)^{-\delta} \exp(kt) \cdot \left[ \int q(t) c_3 \cdot m(t)^{\delta} \exp(-kt) dt \right], \quad (96A.12)$

其中 $c_2 > 0$ 且 $c_3 > 0$，或等价地，

$P(t) = c_4 \cdot \frac{e^{kt}}{m(t)^{\delta}} \cdot \left[ \int -G(t) \frac{m(t)^{\delta}}{e^{kt}} dt \right], \quad (96A.13)$

其中 $c_4 > 0$。

最后，我们有

$P(t) = c \frac{e^{kt}}{m(t)^{\delta}} \cdot \int G(t) m(t)^{\delta} e^{-kt} dt. \quad (96A.14)$

由不定积分改为定积分，方程 (96A.13) 可表示为

$p(t) = \frac{e^{kt}}{m(t)^{\delta}} \int_{t}^{T} G(s) m(s)^{\delta} e^{-ks} ds,$

即方程 (96.19)。

## 附录 96B：方程 (96.21) 的推导

本附录详细推导方程 (96.21)。在方程 (96.20) 中，企业的初始价值可表示为

$p(0) = \frac{1}{m(0)^{\delta}} \int_{0}^{T} \left\{ (a + b \bar{I} - h) A(0) e^{th} m(t)^{\delta - 1} - \alpha' A(0)^2 \rho(t)^2 \sigma(t)^2 e^{2th} m(t)^{\delta - 2} \right\} e^{-kt} dt. \quad (96.20)$

为最大化企业价值，需确定每个时点的流通股数；因此目标函数可写为如下形式：

$\max_{\{m(t)\}_{t=0}^{T}} p(0). \quad (96B.1)$

根据欧拉-拉格朗日条件（参见 Chiang, 1984），我们对目标函数关于 $m(t)$ 求一阶条件，其中

t ∈ [0,T] 并令这些一阶条件等于零。

$$\frac{1}{m(0)^{\delta}}\Big\{ (\delta - 1)(a + b\bar{I} - h)A(0)e^{th}m(t)^{\delta-2} - \alpha' A(0)^2 \rho(t)^2 \sigma(t)^2 e^{2th} m(t)^{\delta-3} (\delta - 2) \Big\} e^{-kt} dt = 0, \quad (96B.2)$$

其中 t ∈ [0,T]。

为简化方程 (96B.2)，

$$\begin{aligned} &(\delta - 1)(a + b\bar{I} - h)A(0)e^{th}m(t)^{\delta-2} \\ &-\alpha' A(0)^2 \rho(t)^2 \sigma(t)^2 e^{2th} m(t)^{\delta-3} (\delta - 2) = 0, \quad (96B.3) \end{aligned}$$

其中 t ∈ [0,T]，即方程 (96.21)。

## 附录 96C：方程 (96.28) 和 (96.29) 的推导

本附录详细推导方程 (96.28) 和 (96.29)。在方程 (96.35) 中，在总风险或系统性风险不变的情况下，最优支付率是

$$[\bar{D}(t)/\bar{x}(t)] = \left(1 - \frac{h}{a + b\bar{I}}\right) \left[ \frac{-k + h e^{(h-k)(T-t)}}{h - k} \right]. \quad (96.35)$$

考虑有限增长情形，若 (h − k)(T − t) < 1，则根据麦克劳林展开，e^{(h-k)(T-t)} 可表示为

$$\begin{aligned} e^{(h-k)(T-t)} &= 1 + (h - k)(T - t) + \frac{(h - k)^2 (T - t)^2}{2!} + \frac{(h - k)^3 (T - t)^3}{3!} \\ &\approx 1 + (h - k)(T - t). \quad (96C.1) \end{aligned}$$

因此，方程 (96.31) 可近似写为

$$[\bar{D}(t)/\bar{x}(t)] \approx \left(1 - \frac{h}{a + b\bar{I}}\right) (1 + h(T - t)),$$

即方程 (96.38)。

我们进一步对方程 (96.33) 关于增长率求偏导。则最优支付率关于

增长率的偏导可近似写为

$$\frac{\partial[\bar{D}(t)/\bar{x}(t)]}{\partial h} \approx \left(\frac{(a + b\bar{I})(T - t) - 2h(T - t) - 1}{a + b\bar{I}}\right),$$

即方程 (96.29)。

## 附录 96D：使用移动估计过程寻找方程 (96.36) 中的结构变化点

为估计经验断点，我们首先假设与风险相关的虚拟变量为 $D(g_{i,t} < c \cdot ROA_{i,t})$。我们引入无结构变化模型，方程 (96D.1)，和结构变化模型，方程 (96D.2)。在方程 (96D.2) 中，$c$ 为连续常数变量，取值范围为 0.2 至 1.8 ($c \in [0.2,\ 1.8]$)。结构变化的断点在 $g_{i,t} = c \cdot ROA_{i,t}$ 处。

$$\ln\left(\frac{payout\ ratio_{i,t}}{1 - (payout\ ratio_{i,t})}\right) = \alpha + \beta_1 Risk_{i,t} + \beta_2 Growth_{i,t} + \beta_3 \ln(Size)_{i,t}$$

$$+ \beta_4 ROA_{i,t} + e_{i,t}, \tag{96D.1}$$

$$\ln\left(\frac{payout\ ratio_{i,t}}{1 - (payout\ ratio_{i,t})}\right) = \alpha + \beta'_1 Risk_{i,t} + \beta'_2 D\left(g_{i,t} < c \cdot ROA_{i,t}\right)$$ 

$$\cdot Risk_i + \beta'_3 Growth_{i,t} + \beta'_4 \ln(Size)_{i,t}$$

$$+ \beta'_5 ROA_{i,t} + e_{i,t}. \tag{96D.2}$$

利用移动估计过程，我们计算 $g_{i,t} = 0.2 \times ROA_{i,t}$ 与 $g_{i,t} = 1.8 \times ROA_{i,t}$ 之间所有潜在结构变化点的 $F$ 统计量。$F$ 检验的原假设是支付率与风险之间的关系不存在结构变化，即方程 (96D.1) 与方程 (96D.2) 相同。最后，我们可以在 $F$ 统计量值最高的点处定位结构变化的断点。

由表 96D.1 可知，该过程在使用贝塔风险作为自变量时在 $c = 0.93$ 处出现明显峰值，使用总风险作为自变量时在 $c = 0.96$ 处出现峰值。图 96D.1 也以图形方式展示了在贝塔风险（总风险）方面 $c = 0.93$（0.96）处的峰值 $F$ 统计量。移动估计过程的结果表明，支付率与风险之间的关系存在结构变化。结构变化的断点在 $g_{i,t} = 0.93 \times ROA_{i,t}$ 或 $g_{i,t} = 0.97 \times ROA_{i,t}$ 处。
