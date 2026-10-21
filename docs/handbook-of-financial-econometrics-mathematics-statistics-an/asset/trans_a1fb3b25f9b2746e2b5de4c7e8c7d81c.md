
## 参考文献

- Hu, L. (2006). 跨金融市场的依赖模式：混合 Copula 方法。 *应用金融经济学*, 16(10), 717–729.
- Hua, L. (2017). 关于具有上下全范围尾部依赖的双变量 Copula。 *保险：数学与经济学*, 73, 94–104.
- Hull, J. C. (2012). *风险管理与金融机构*, 第3版. Hoboken: John Wiley & Sons.
- Imbierowicz, B. and Rauch, C. (2014). 银行中流动性风险与信用风险之间的关系。 *银行与金融杂志*, 40, 242–256.
- Inanoglu, H. and Jacobs, M. (2009). 风险聚合与敏感性分析模型：银行经济资本的应用。 *风险与金融管理杂志*, 2, 118–189.
- International Financial Risk Institute Foundation and Chief Risk Officer Forum (2007). 来自联合 IFRI/CRO 论坛关于经济资本实践与应用调查的见解。 KPMG Business Advisory Services.
- Jaworski, P., Durante, F., Härdle, W. and Rychlik, T. (2009). Copula 理论及其应用。 Springer-Verlag Berlin Heidelberg.
- Jorion, P. (2007). *风险价值：管理金融风险的新基准*, 第3版. New York: McGraw-Hill.
- Kole, E., Koedijk, K. and Verbeek, M. (2007). 风险管理中的 Copula 选择。 *银行与金融杂志*, 31(8), 2405–2423.
- Kolia, L. (2016). 极端风险建模：金融压力测试的 EVT-配对 Copulas 方法。 *银行与金融杂志*, 70, 1–22.
- Kretzschmar, G., McNeil, A. J. and Kirchner, A. (2010). 资本充足率的综合模型：银行为何资本不足。 *银行与金融杂志*, 34(12), 2838–2850.
- Kuritzkes, A. and Schuermann, T. (2007). 我们对银行风险的了解、未知和无法得知的：来自前线的视角。 In Diebold, F. X., Doherty, N. and Herring, R. J. (eds.), *金融风险管理中的已知、未知与不可知*, Princeton: Princeton University Press.
- Lai, Y. and Tseng, J. C. (2010). 中国股票市场在全球股票市场中的作用：避风港还是对冲工具？ *国际经济学与金融评论*, 19, 211–218.
- Li, D. X. (2000). 关于违约相关性：Copula 函数方法。 *固定收益杂志*, 9(4), 43–54.
- Li, J., Zhu, X., Wu, D., Lee, C. F., Feng, J. and Shi, Y. (2015). 关于信用、市场和操作风险的聚合。 *定量金融与会计评论*, 44(1), 161–189.
- Li, J., Wei, L., Lee, C. F., Zhu, X. and Wu, D. (2018). 基于财务报表的银行风险聚合。 *定量金融与会计评论*, 50(3), 673–694.
- Maciag, J., Hesse, F., Boeve, R. and Pfingsten, A. (2016). 使用不同 Copulas 聚合市场风险和信用风险时风险度量的比较。 *风险杂志*, 18(5), 101–136.
- Nelsen, R. B. (1999). Copulas 导论。 Springer, New York.
- Nikoloulopoulos, A. K., Joe, H. and Li, H. (2009). 多元 t Copulas 的极值性质。 *Extremes*, 12(2), 129–148.
- Rodriguez, J. C. (2007). 衡量金融传染：Copula 方法。 *实证金融杂志*, 14(3), 401–423.
- Rosenberg, J. V. and Schuermann, T. (2006). 具有偏态、厚尾风险的综合风险管理的一般方法。 *金融经济学杂志*, 79(3), 569–614.
- Sklar, A. (1959). n 维分布函数及其边缘。 *巴黎大学统计研究所出版物*, 8, 229–231.
- Tang, A. and Valdez, E. A. (2006). 经济资本与使用 Copulas 的风险聚合。 Paper presented at the 28th International Congress of Actuaries, Paris, France.
- Turgutlu, E. and Ucer, B. (2010). 全球多元化是否合理？通过混合 Copula 方法从新兴股票市场获得的证据。 *应用经济学*, 42, 647–658.
- Viebig, J. and Poddig, T. (2010). 使用极值理论和 Copula 理论对对冲基金策略的极端回报和不对称依赖结构建模。 *风险杂志*, 13(2), 23–55.
- Weiß, G. N. F. (2014). 使用异常值检测方法和拟合优度检验识别混合 Copula 分量。 *风险杂志*, 16(4), 61–101.
- Weiß, G. N. F. and Scheffer, M. (2015). 混合配对 Copula 构造。 *银行与金融杂志*, 54, 175–191.

## 附录 38A：单个 Copula

假设 $u_1, u_2, \dots, u_N$ 服从一元标准均匀分布，然后，本章提到的五种流行 Copula 如下介绍。

- (1) 高斯 Copula 表示为

  $C_{\text{Gaussian}}(u_1, u_2, \dots, u_N | R) = \Phi_R(\Phi^{-1}(u_1), \Phi^{-1}(u_2), \dots, \Phi^{-1}(u_N)), \quad (38A.1)$

  其中 $\Phi_R$ 表示相关系数矩阵为 $R$ 的标准多元高斯分布函数，$\Phi^{-1}$ 表示标准一元高斯分布的逆函数。 高斯 Copula 具有零尾部相关性，通常被视为比较的基准。

- (2) $t$ Copula 表示为

  $C_t(u_1, u_2, \dots, u_N | \nu, R) = t_{\nu,R}(t_{\nu}^{-1}(u_1), t_{\nu}^{-1}(u_2), \dots, t_{\nu}^{-1}(u_N)), \quad (38A.2)$

  其中 $t_{\nu,R}$ 表示自由度为 $\nu$ 且相关系数矩阵为 $R$ 的 $t$ 分布函数，$t_{\nu}^{-1}$ 表示 $t$ 分布函数的逆函数。 $t$ Copula 在右尾和左尾表现出相同的依赖性。 自由度越大，$t$ Copula 的尾部相关性越弱。 事实上，高斯 Copula 是当自由度趋近于 $\infty$ 时 $t$ Copula 的极限情况。

- (3) Gumbel Copula 表示为

  $C_{\text{Gumbel}}(u_1, u_2, \dots, u_N | \alpha) = \exp\left\{ -\left[\sum_{n=1}^{N}(-\ln u_n)^{\alpha}\right]^{\frac{1}{\alpha}}\right\}, \quad \alpha \in [1, \infty), \quad (38A.3)$

  其中 $\alpha$ 越大，依赖性越重。 具体而言，$\alpha = 1$ 表示独立 Copula，而当 $\alpha$ 趋近于 $\infty$ 时，我们得到完全依赖 Copula。 Gumbel Copula 在右尾的依赖性大于左尾。

- (4) Clayton Copula 表示为

  $C_{\text{Clayton}}(u_1, u_2, \dots, u_N|\beta) = \left(\sum_{n=1}^{N} u_n^{-\beta} - N + 1\right)^{-\frac{1}{\beta}}, \quad \beta \in (0,\infty),$ (38A.4)

  其中 $\beta$ 越大，依赖性越重。 具体而言，当 $\beta$ 趋近于 0 时，我们得到独立 Copula，而当 $\beta$ 趋近于 $\infty$ 时，我们得到完全依赖 Copula。 Clayton Copula 在左尾的依赖性大于右尾。

- (5) Frank Copula 表示为

  $C_{\text{Frank}}(u_1, u_2, \dots, u_N|\lambda) = -\frac{1}{\lambda} \ln\left(1 + \frac{\prod_{n=1}^{N} (e^{-\lambda u_n} - 1)}{(e^{-\lambda} - 1)^{N-1}}\right), \quad \lambda \neq 0,$ 当 $N \ge 3, \lambda \in (0,\infty),$ (38A.5)

  其中 Frank Copula 在 $\lambda$ 等于 $-\infty$ 时显示完全负相关，在 $\lambda$ 等于 $\infty$ 时显示完全正相关，在 $\lambda$ 等于 0 时显示独立。 Frank Copula 只能捕捉对称依赖性，对左尾或右尾依赖性不敏感。

## 附录 38B：边缘分布

本章边际风险拟合的三种分布如下介绍。

- (1) 偏斜广义误差分布 Skewed Generalized Error Distribution (SGED) 表示为

  $f(x|\mu,\sigma,k,\lambda)=\frac{C}{\sigma}\exp\left\{-\frac{1}{[1+\operatorname{sgn}(x-\mu+\delta\sigma)\lambda]^{k}\theta^{k}\sigma^{k}}|x-\mu+\delta\sigma|^{k}\right\},$ (38B.1)

  其中 $C = \frac{k}{2\theta}\Gamma\left(\frac{1}{k}\right)^{-1}, \quad \theta = \Gamma\left(\frac{1}{k}\right)^{\frac{1}{2}}\Gamma\left(\frac{3}{k}\right)^{-\frac{1}{2}} S(\lambda)^{-1}, \quad \delta = 2\lambda A S(\lambda)^{-1},$ $S(\lambda)=\sqrt{1+3\lambda^{2}-4A^{2}\lambda^{2}}, \quad A = \Gamma\left(\frac{2}{k}\right)\Gamma\left(\frac{1}{k}\right)^{-\frac{1}{2}}\Gamma\left(\frac{3}{k}\right)^{-\frac{1}{2}},$ (38B.2)

  $\mu = E(x)$ 和 $\sigma$ 分别是随机变量 $x$ 的期望值和标准差，sgn 是符号函数，Γ 是 Gamma 函数。 形状参数 $k$ 决定密度函数的高度和尾部，约束条件为 $k > 0$，而 $\lambda$ 是密度的偏度参数，约束条件为 $-1 < \lambda < 1$。 特别地，当 $k = 2$ 且 $\lambda = 0$ 时，SGED 分布变为标准正态分布。

- (2) 学生 $t$ 分布表示为

  $$f(x) = \frac{\Gamma\left(\frac{\nu+1}{2}\right)}{\sqrt{\nu\pi}\,\Gamma\left(\frac{\nu}{2}\right)} \left(1 + \frac{x^2}{\nu}\right)^{-\frac{\nu+1}{2}}, \qquad (38B.3)$$

  其中 $\nu$ 是自由度，$\Gamma$ 是 Gamma 函数。 学生 $t$ 分布是统计学中常见的分布，其形状由参数 $\nu$ 决定。

- (3) 对数正态分布表示为

  $$f(x|\mu,\sigma) = \frac{1}{\sqrt{2\pi}\,\sigma x} \exp\left\{ -\frac{(\ln x - \mu)^2}{2\sigma^2} \right\}, \; x > 0, \mu > 0, \sigma > 0, \qquad (38B.4)$$

  其中 $\mu$ 和 $\sigma$ 分别是 $\ln x$ 的均值和标准差。 对数正态分布是保险和操作风险中用于建模较大索赔和操作风险损失的标准分布之一。
