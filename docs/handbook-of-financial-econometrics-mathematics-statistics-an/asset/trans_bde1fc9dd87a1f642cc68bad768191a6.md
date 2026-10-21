
- A. Lorenzo-Valdes、L. Armenta-Fraire和R. Duran-Vazquez（2016）。石油价格与股市指数条件相依性的Copula-TGARCH方法：以墨西哥为例。Estudios Económicos，31(1)，47–63。

- M.-J. Lu、C. Chen和W. Härdle（2017）。基于Copula的信用风险分析因子模型。Review of Quantitative Finance and Accounting，49(4)，949–971。https://doi.org/10.1007/s11156-016-0613-x。

- T. Lux和A. Papapantoleon（2017）。d-copula的改进Fréchet–Hoeffding界及其在无模型金融中的应用。Annals of Applied Probability，27，3633–3671。

- H. Manner和O. Reznikova（2012）。时变Copula综述：设定、模拟与应用。Econometric Reviews，31(6)，654–687。https://doi.org/10.1080/07474938.2011.608042。

- A. Min和C. Czado（2014）。基于pair-copula构造的SCOMDY模型及其在汇率中的应用。Computational Statistics and Data Analysis，76，523–535。https://doi.org/10.1016/j.csda.2012.08.003。

- N. Naifar（2011）。用阿基米德Copula建模相依结构及其在iTraxx CDS指数中的应用。Journal of Computational and Applied Mathematics，235，2459–2466。https://doi.org/10.1016/j.cam.2010.10.047。

- C. Nguyen和M. Bhatti（2012）。油价与股市之间依赖性的Copula模型：来自中国和越南的证据。Journal of International Financial Markets, Institutions and Money，22(4)，758–773。https://doi.org/10.1016/j.intfin.2012.03.004。

- C. Ning（2010）。股票市场与外汇市场之间的相依结构——一种Copula方法。Journal of International Money and Finance，29(5)，743–759。https://doi.org/10.1016/j.jimonfin.2009.12.002。

- D. Oh和A. Patton（2018）。时变系统性风险：来自CDS利差动态Copula模型的证据。Journal of Business & Economic Statistics，36(2)，181–195。https://doi.org/10.1080/07350015.2016.1177535。

- A. J. Patton（2002）。Copula理论在金融计量经济学中的应用。未发表的博士论文，加州大学圣迭戈分校经济学系。取自 www.amstat.org/sections/bus_econ/papers/patton_dissertation.pdf。

- A. J. Patton（2006）。汇率非对称相依性建模。International Economic Review，47(2)，527–556。

- A. J. Patton（2012）。经济时间序列Copula模型综述。Journal of Multivariate Analysis，110，4–18。https://doi.org/10.1016/j.jmva.2012.02.021。

- J. L. Rossi、R. S. Ehlers和M. G. A. Filho（2011）。Copula-GARCH模型选择的建模：一种贝叶斯方法。巴西圣保罗大学圣卡洛斯校区。取自 http://conteudo.icmc.usp.br/CMS/Arquivos/arquivos_enviados/BIBLIOTECA_113_NSE_88.pdf。

- A. Shamiri、N. A. Hamzah和A. Pirmoradian（2011）。金融市场风险管理中的尾部相依性估计：Clayton-Gumbel Copula方法。Sains Malaysiana，40(8)，927–935。

- A. Sklar（1959）。n维分布函数及其边缘分布。Publications de l'Institut de Statistique de l'Université de Paris，8，229–231。

- M. Tachibana（2018）。美国、英国和欧元区股票市场的避险货币与对冲货币：基于Copula的方法。Global Finance Journal，35，82–96。https://doi.org/10.1016/j.gfj.2017.07.001。

- B. Wang、T. Cao和S. Wang（2014）。基于Copula-GARCH模型的中国商业银行汇率风险研究。Modern Economy，5，541–551。https://doi.org/10.4236/me.2014.55051。

- Z.-R. Wang、X.-H. Chen、Y.-B. Jin和Y.-J. Zhou（2010）。外汇投资组合的风险估计：基于GARCH-EVT-Copula模型使用VaR和CVaR。Physica A，389，4918–4928。https://doi.org/10.1016/j.physa.2010.07.012。

- G. Weiss（2013）。Copula-GARCH与动态条件相关：关于VaR和ES预测准确性的实证研究。Review of Quantitative Finance and Accounting，41(2)，179–202。https://doi.org/10.1007/s11156-012-0311-2。

- G. Weiss和H. Supper（2013）。使用vine copulas预测流动性调整后的日内风险价值。Journal of Banking and Finance，37(9)，3334–3350。https://doi.org/10.1016/j.jbankfin.2013.05.013。

## 附录73A：标准学生氏t分布

设 T 是一个定义域为 D = (-∞,∞) 的连续变量，其分布函数 F 由 F(t) = P(T ≤ t) 给出。若 T 服从自由度为 v 的学生氏 t 分布，则其密度函数为

$$f_v(t) = (v\pi)^{-1/2} \cdot \frac{\Gamma((v+1)/2)}{\Gamma(v/2)} \cdot \left(1 + \frac{t^2}{v}\right)^{-(v+1)/2}$$

其中 Γ 是伽马函数。若定义 X = μ + σT，则 X 服从广义 t 分布，其密度函数如下：

$$f_v(x|\mu,\beta) = (\beta v \pi)^{-1/2} \cdot \frac{\Gamma((v+1)/2)}{\Gamma(v/2)} \cdot \left(1 + \frac{(x-\mu)^2}{\beta v}\right)^{-(v+1)/2}$$

其中 X 的期望为 μ，X 的方差为 σ² = βv(v-2)⁻¹。若 μ = 0 且 βv = v-2（从而 σ² = 1），则 X ∼ t_v(0,1)，标准学生氏 t 分布的密度函数如下：

$$f_v(x) = (\pi(v-2))^{-1/2} \cdot \frac{\Gamma((v+1)/2)}{\Gamma(v/2)} \cdot \left(1 + \frac{x^2}{v-2}\right)^{-(v+1)/2}$$

若自由度较小，与正态分布相比，该分布的峰会更低、尾部更长。当 ν → ∞ 时，该分布趋近于均值为 0、方差为 1 的正态分布。

## 附录73B：椭圆Copula的密度函数

高斯Copula分布无法写成简单的闭式形式，只能表示为积分形式。当 n = 2 时，二元高斯Copula函数为

$$C(u_1, u_2; \varrho) = \Phi_\varrho(\Phi^{-1}(u_1), \Phi^{-1}(u_2)) = \int_{-\infty}^{\Phi^{-1}(u_1)} \int_{-\infty}^{\Phi^{-1}(u_2)} (2\pi)^{-1}(1 - \varrho^2)^{-1/2} \exp\left(-\frac{x_1^2 - 2\varrho x_1 x_2 + x_2^2}{2(1 - \varrho^2)}\right) dx_1 dx_2,$$

其中 $\varrho$ 是两个变量之间的相关系数。对该函数求导，可得二元高斯Copula密度函数为

$$c(u_1, u_2; \varrho) = (1 - \varrho^2)^{-1/2} \exp\left(-\frac{\varrho^2 \xi_1^2 - 2\varrho \xi_1 \xi_2 + \varrho^2 \xi_2^2}{2(1 - \varrho^2)}\right).$$

类似地，学生氏 $t$ Copula分布也无法写成简单的闭式形式。当 $n = 2$ 时，二元学生氏 $t$ Copula函数为

$$C(u_1, u_2; \varrho) = t_{v,\varrho}(t_v^{-1}(u_1), t_v^{-1}(u_2)) = \int_{-\infty}^{t_v^{-1}(u_1)} \int_{-\infty}^{t_v^{-1}(u_2)} (2\pi)^{-1}(1 - \varrho^2)^{-1/2} \left[1 + v^{-1}\frac{x_1^2 - 2\varrho x_1 x_2 + x_2^2}{1 - \varrho^2}\right]^{-(v+2)/2} dx_1 dx_2.$$

对该函数求导，可得二元学生氏 $t$ Copula密度函数为

$$c(u_1, u_2; \varrho) = K (1 - \varrho^2)^{-1/2} \left[1 + v^{-1}(1 - \varrho^2)^{-1} (\xi_1^2 - 2\varrho \xi_1 \xi_2 + \xi_2^2)\right]^{-(v+2)/2} \cdot \left[(1 + v^{-1} \xi_1^2)(1 + v^{-1} \xi_2^2)\right]^{(v+1)/2},$$

其中 $\xi_1 = t_v^{-1}(u_1)$ 和 $\xi_2 = t_v^{-1}(u_2)$ 是学生氏 $t$ 变量的实现值，而 $K$ 为常数，$K = \Gamma(v/2) \cdot \Gamma((v+1)/2)^{-2} \cdot \Gamma((v+2)/2).$

## 附录73C：极大似然估计

可以用完全极大似然估计（MLE）方法来估计Copula参数。设联合密度表示如下：

$$f(x_1, \dots, x_n) = c(F_1(x_1), \dots, F_n(x_n)) \cdot f_1(x_1) \cdots f_n(x_n).$$

将边缘密度和边缘分布分别记为 $f_i(x_i;\alpha_i)$ 和 $F_i(x_i;\alpha_i)$，则联合密度可写为

$$f(x_1,\dots,x_n;\boldsymbol{\alpha},\boldsymbol{\theta}) = c(F_1(x_1;\alpha_1),\dots,F_n(x_n;\alpha_n);\boldsymbol{\theta})\cdot\prod_{i=1}^n f_i(x_i;\alpha_i),$$

其中 $\boldsymbol{\alpha}=(\alpha_1,\dots,\alpha_n)$ 是边缘密度参数的向量，$\boldsymbol{\theta}=(\theta_1,\dots,\theta_n)$ 是Copula参数的向量。因此，对数似然函数为

$$\ln L(\boldsymbol{\alpha},\boldsymbol{\theta},\boldsymbol{X}_1,\dots,\boldsymbol{X}_T) = \sum_{t=1}^T\left(\ln c(F_1(x_{1t};\alpha_1),\dots,F_n(x_{nt};\alpha_n);\boldsymbol{\theta}) + \sum_{i=1}^n \ln f_i(x_{it};\alpha_i)\right),$$

其中 $\boldsymbol{X}_t=(x_{1t},\dots,x_{nt})$ 是时间 $t$ 上 $n$ 个随机变量观测值的行向量。因此，可以分两个独立步骤来最大化对数似然，具体如下：

- （i）使用MLE分别估计每个边缘密度的参数（$\hat{\alpha}_i$）

$$\max_{\alpha_i}\sum_{i=1}^T\ln f_i(x_{it};\alpha_i),\quad\text{for }i=1,\dots,n.$$

- （ii）通过求解下式估计Copula参数

$$\max_{\theta}\sum_{t=1}^T\ln c(F_1(x_{1t};\hat{\alpha}_1),\dots,F_n(x_{nt};\hat{\alpha}_n);\boldsymbol{\theta}).$$

现在考虑用这些步骤来估计Clayton Copula。首先，将两个变量在均值层面进行标准化。然后，使用MLE分别估计每个标准化变量的标准学生氏 $t$ 分布密度的参数（$\hat{v}_i$）。最大化如下函数：

$$\max_{v_i}\sum_{i=1}^T\ln f_i(x_{it};v_i),\quad\text{for }i=1,2,$$

其中 $f_v(x)=(\pi(v-2))^{-(1/2)}\cdot\Gamma(v/2)^{-1}\cdot\Gamma((v+1)/2)\cdot\left(1+\frac{x^2}{v-2}\right)^{-(v+1)/2}$。利用估计出的 $\hat{v}_i$，将学生氏 $t$ 分布拟合到标准化变量。所得序列 $u_1$ 和 $u_2$ 的定义域为 $[0,1]$。随后，
