
对 $h_{it}$ 的模型。然后，第一阶段的拟似然函数为

$$L_1(\phi|r_t)= -\frac{1}{2}\sum_{t=1}^{T}\big(k\log(2\pi)+\log(|I_k|)+2\log(|D_t|)+r_t' D_t^{-1} I_k D_t^{-1} r_t\big)$$
$$= -\frac{1}{2}\sum_{i=1}^{k}\Big(T\log(2\pi)+\sum_{t=1}^{T}\big(\log(h_{it})+\frac{r_{it}^2}{h_{it}}\big)\Big).$$

设 $\hat\phi = \arg\max L_1(\phi|r_t)$。然后，在第二阶段，方程 (129.6) 中的 DCC 参数是利用 (129.8) 中的原始似然函数在第一阶段 GARCH 参数估计值 $\hat\phi$ 的条件下估计的。而且，拟似然函数为

$$L_2(\psi|\hat\phi, r_t)= -\frac{1}{2}\sum_{t=1}^{T}\big(k\log(2\pi)+2\log(|D_t|)+\log(|R_t|)+r_t' D_t^{-1} R_t^{-1} D_t^{-1} r_t\big)$$
$$= -\frac{1}{2}\sum_{t=1}^{T}\big(k\log(2\pi)+2\log(|D_t|)+\log(|R_t|)+\varepsilon_t' R_t^{-1} \varepsilon_t\big).$$

$L_2(\psi|\hat\phi, r_t)$ 中的估计参数 $\hat\psi$ 为

$$\hat\psi = \arg\max L_2(\psi|\hat\phi, r_t).$$

根据 Engle (2002)，我们知道 $\hat\theta_T = (\hat\phi_T, \hat\psi_T)$ 具有渐近正态性。因此，参数的估计值可以很容易地对其显著性进行检验。

## 129.3 简单平均相关系数和方差在不同阶段差异的检验

从相关系数的图表，尤其是图 129.1 中的简单平均相关系数图，我们注意到相关系数存在一些尖锐值。此外，在第一个尖锐点之前以及两个尖锐点之间，数值变化稳定。这种现象对于简单平均方差更为明显，这启发我们检验不同阶段的平均相关系数和方差是否相同。在本部分中，我们将相关系数数据分为两组，并将其表示为具有未知分布的两个变量 $X_1$ 和 $Y_1$。然后，我们可以通过 Brunner 和 Munzel (2000) 提出的一种有效检验来检验它们的均值是否相同。在他们的论文中，Brunner 和 Munzel (2000) 讨论了如何检验两个分离随机变量之间的差异以及如何计算

概率 p = P(X₁ < Y₁) + ½ P(X₁ = Y₁)。类似地，对于方差数据，我们将其表示为两个随机变量 X₂ 和 Y₂，并计算 p = P(X₂ < Y₂) + ½ P(X₂ = Y₂)。我们使用这种检验方法分别获得相关系数和方差差异的概率。

我们接下来简要讨论 Brunner–Munzel 检验。假设一个一般的非参数模型，如 Brunner 和 Munzel (2000) 中所述，有 N = n₁ + n₂ 个独立随机变量，

$$X_{k_1} \sim F_1(x),\, Y_{k_2} \sim F_2(x),\quad k_1 = 1,\dots,n_1,\,k_2 = 1,\dots,n_2.\tag{129.9}$$

分布函数 F₁(x) 和 F₂(x) 是任意的（除去一个点分布的平凡情况）。此外，无处理效应的假设通常表述为 H₀^F : F₁ = F₂，这在假设下意味着同方差性。为了表述无处理效应的非参数假设，相对处理效应 p = P(X₁ < Y₁) + ½ P(X₁ = Y₁) 被考虑。已知 Fᵢ(x) = ½[Fᵢ⁻(x) + Fᵢ⁺(x)]，其中 Fᵢ⁻(x) 是左连续版本，Fᵢ⁺(x) 是右连续版本。因此，p 可以写成 p = ∫ F₁ dF₂ 且无处理效应的假设写成 H₀^p : p = ∫ F₁ dF₂ = ½，因为 H₀^F : F₁ = F₂ = F 蕴含 H₀^p : p = ½，由 ∫ F dF = ½ 可得。

为了估计 p，分布函数 F₁ 和 F₂ 被其经验对应物 \hat Fᵢ(x) = ½[\hat Fᵢ⁻(x) + \hat Fᵢ⁺(x)] 替代。令

$$\hat H(x) = \sum_{i=1}^{2} \frac{n_i}{N} \hat F_i(x).$$

则 R₁ₖ = N · \hat H(Xₖ) 和 R₂ₖ = N · \hat H(Yₖ) + ½ 是 Xₖ 和 Yₖ 的秩。令 \bar R_{i.} = n_i^{-1} \sum_{k=1}^{n_i} R_{ik}, i = 1,2，表示秩 R_{ik} 的均值。于是

$$\hat p = \int \hat F_1 d\hat F_2 = \frac{1}{n_1} \left( \bar R_{2.} - \frac{n_2 + 1}{2} \right)$$

是 p 的无偏且一致的估计量。

对于任何相关系数或方差数据，已知它们是自相关的。但在 Brunner 和 Munzel (2000) 中，随机变量 X_{k1} 和 Y_{k2} 假定为 N 个独立变量。为了满足独立性，两个分离组的样本量需要足够大，使得它们之间的依赖性可以忽略。在本章中，

样本量超过 700，这足够大以满足变量独立性的要求。

在进行 Brunner–Munzel 检验时，由于我们不知道将样本分为两组的最佳断点，因此需要做出选择。基本思想是我们选择一个起点 x_s 和一个终点 x_e 作为两组的断点。在此过程中，我们需要保持两组的样本量足够大以满足独立性。我们首先在 x_s 和 x_e 之间选取任意点 x_a 作为断点，然后执行 Brunner–Munzel 检验以获得 \hat{p} 的估计。对于所有 \hat{p} 值，我们可以获得局部最大值，可视为最佳断点。如果两个相邻断点之间的距离不足以使这两个相邻断点之间的样本满足独立性，我们就保留 \hat{p} 值更大的断点，舍弃其他断点。实际上，我们可能会得到几个断点，这与本研究中相关系数和方差数据中存在几个尖锐点的事实一致。

我们进一步通过再次对样本及其邻域样本执行 Brunner–Munzel 检验来检验这些断点，以查看这两个样本的均值是否相同。如果我们接受假设，则放弃这两个样本的该断点；否则，保留该断点。最终，在我们得到所有可能的左侧断点后停止，任意两个断点之间的子样本均值与其邻域子样本均值显著不同。然后，得到所有断点。这使我们能够获得结构变化的确切日期。

为简洁起见，我们仅提供关于简单平均相关系数和方差的两个图表。对于其他图表，我们可以进行相同的检验并得到类似结果。在附图中，我们可以看到差异概率在大约 2007 年 2 月和 2008 年 9 月分别达到两个局部最大值点，均大于 90%。这一结果与我们之前观察到的模式一致。对于这两个局部最大值点，它们被视为阶段断点。在简单平均相关系数和方差的图表中，我们用虚线垂直线表示其日期。这两个点在经验实施中非常重要且有用，因为它们为我们提供了将相关系数和方差划分为不同阶段的方法。此外，对于方差差异的概率，如果它非常高，大于 90%，我们需要考虑不同阶段的风险。这也是确定阶段断点很重要的另一个原因。

## 129.4 数据与实证结果

数据包括标准普尔 500 公司的日收益率。样本涵盖 2006 年 1 月 3 日至 2008 年 10 月 31 日期间。股票收益是根据网站上的日收盘价计算的：http://finance.yahoo.com。本章中，我们考虑银行、保险和交易行业公司收益的相关性，以查看次贷危机是否影响了收益的相关性。对于银行业，选择了十家银行，其代码为：AXP、BBT、BK、C、CIT、COF、KEY、NCC、PNC、USB。对于保险业，我们还选择了十家大型保险公司，其代码为：ABK、AET、AIG、ALL、HIG、MET、PRU、ANAT、ASI 和 HCC。此外，我们选择了交易行业的八家公司，其代码为：AMTD、BPSG、CS、GS、JPM、NMR、OPY 和 AMP。

表 129.1 和 129.2 列出了公司名称及其代码。表 129.3 报告了均值、标准差、偏度和峰度的

**表 129.1：** 银行和保险公司的名称及代码。

| 银行名称 | 银行代码 | 保险公司名称 | 保险公司代码 |
|---|---|---|---|
| American Express Co | AXP | Ambac Finl Grp Inc | ABK |
| BB&T Corp | BBT | Aetna Inc | AET |
| Bank of NY Mellon Corp | BK | American International Group | AIG |
| Citigroup Inc | C | Allstate Corp | ALL |
| CIT Group Inc | CIT | Hartford Fin Services Group | HIG |
| Capital One Financial Corp | COF | MetLife Inc | MET |
| KEY Corp | KEY | Prudential Financial Inc | PRU |
| PNC Financial Svcs Group Inc | PNC | American National Insurance Co | ANAT |
| U S Bancorp | USB | American Safety Insurance Holdings Ltd | ASI |
|  |  | HCC Insurance Holdings Inc | HCC |

**表 129.2：** 交易公司的名称及代码。

| 名称 | 代码 |
|---|---|
| TD Ameritrade Holding Corp | AMTD |
| Broadpoint Securities Group Inc | BPSG |
| Credit Suisse Group | CS |
| Goldman Sachs Group Inc | GS |
| JPMorgan Chase & Co | JPM |
| Nomura Holdings Inc | NMR |
| Oppenheimer Holdings Inc | OPY |
| Ameriprise Financial Inc | AMP |

