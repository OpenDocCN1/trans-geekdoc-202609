
80日上证50指数收益对低流动性上证50ETF期权的影响最大。高流动性子样本与低流动性子样本的比较表明，高流动性子样本的结果通常显示出更大的回归系数。这一发现表明，过去股票收益对高流动性期权价格的影响相对大于对低流动性期权价格的影响。

## 103.4.3 价格压力的来源

### 103.4.3.1 市场动量假说

到目前为止，我们已经确定过去股票市场收益会影响指数期权价格。这两种价格变化都会导致边界条件违背，这与无摩擦、无套利市场不一致。对于我们的发现，存在多种可能的解释。目前记录在案的结果的一个可能解释是，投资者只是将过去的股票收益外推到未来股票收益中。正如 Lo 和 Mackinlay (1988) 所记载，市值加权市场指数在不到 1 年的中期区间内表现出强烈的正自相关。因此，给定过去正的股票市场收益，投资者预期正收益将持续，并推高看涨期权价格。给定过去负的股票市场收益，投资者预期负收益将持续，并推高看跌期权价格。这种现象被称为市场动量假说。该假说预测，过去股票收益对波动率价差具有独立的正向影响。

大量文献指出股票市场存在动量收益，例如 Grinblatt et al. (1995)、Jegadeesh 和 Titman (1993) 以及 Lewellen (2002)。大多数投资者是“动量投资者”，买入过去上涨的股票，卖出过去下跌的股票。因此，在本节中，我们研究标的股票动量作为期权市场价格压力来源的影响。

### 103.4.3.2 动量收益模式

我们首先采用动量收益 WML 作为动量因子，以捕捉上证50指数成分股平均收益中的动量模式。WML 最初用于 Carhart (1997) 的四因子模型，随后广泛应用于实证分析，最著名的是用来详细说明平均股票收益中的动量模式，如 Fama 和 French (2012)。我们没有使用过去一年赢家与输家多元化投资组合的月度收益之差，而是使用上个月赢家与输家多元化投资组合的日收益之差，记为 WML。这样做是为了方便后续的时间序列回归。

具体来说，WML 的计算基于按规模和动量进行 2 × 3 分组构建的投资组合（Carhart 1997, Fama and French 2012）。首先，在 2014 年和 2015 年 12 月底，所有成分股根据每只股票的市值被分配到两个规模投资组合。大股票是市值前 50% 的股票，小股票是市值后 50% 的股票。这一描述确定了 2015 年和 2016 年的规模投资组合。然后，在独立排序中，同一组股票根据滞后动量收益的后 30%、中间 40% 和前 30% 的分界点被分配到三个动量投资组合。对于在第 t 天末的每只股票，滞后动量收益是其从 t − 20 到 t − 1 的累计收益（在中国，每个月大约有 21 个工作日，跳过排序日是动量测试的标准做法）。赢家是滞后动量收益前 30% 的股票，中性是中间 40% 的股票，输家是后 30% 的股票。独立 2 × 3 分组的交集产生了六个市值加权的规模-动量投资组合：SL、SN、SW、BL、BN 和 BW。我们计算每个投资组合在第 t + 1 天的日市值加权收益。然后，动量因子 WML(t) 是高滞后动量股票（赢家）的日收益的等权平均值减去低滞后动量股票（输家）的日收益的等权平均值，如方程 (103.9) 所示。

基于按规模和动量进行 2 × 3 分组所构建的投资组合，我们报告了 WML 的汇总统计量，如表 103.6 所示。具体如下：

表 103.6：动量因子的汇总统计量：2015年2月9日至2016年5月26日，316天。

|  | **WML_S** | **WML_B** | **WML** | **WML_S-B** |
|---|---|---|---|---|
| 均值 (%) | 20.58 | 15.81 | 36.40 | 4.77 |
| 标准差 (%) | 10.91 | 7.47 | 16.10 | 9.50 |
| t-mean | 7.55 | 8.47 | 9.04 | 2.01 |

注：WML_S 是小盘股中上个月赢家与输家多元化投资组合日收益之差；WML_B 是大盘股中上个月赢家与输家多元化投资组合日收益之差；WML 是 WML_S 和 WML_B 的等权平均值。WML_S-B 是 WML_S 与 WML_B 之差。所有收益均以人民币计。表中均值和标准差分别表示收益的均值和标准差，t-mean 是均值与其标准误之比。

## 中国的期权价格与股票市场动量

表 103.7：样本期间隐含波动率价差对动量收益的回归结果。

IVS_t=β0+β1 WML_t +ε_t

| 高流动性 | 低流动性 |
| --- | --- |
| β0 | -0.11 (-5.54)*** | -0.21 (-11)*** |
| β1 | 0.08 (1.65)** | 0.35 (7.40)*** |
| R² | 0.008 | 0.15 |

注：**和***分别表示相应系数在5%和1%的显著性水平下显著。

动量效应对低流动性期权组的影响远高于对高流动性期权组的影响。

在本章中，我们研究了中国期权价格与过去股票市场收益之间的关系。利用上证50ETF期权价格，我们分别构建了具有相同到期日和行权价的高流动性和低流动性看涨期权与看跌期权配对的隐含波动率价差，以衡量看涨期权相对于看跌期权的相对价值。我们的实证结果有力地证明，过去股票收益对高流动性和低流动性指数期权的定价都有影响。过去正的股票收益会提高看涨期权价格，而过去负的股票收益会提高看跌期权价格。具体而言，过去60日和80日股票收益分别对高流动性和低流动性期权价格产生最显著的正向影响。因此，我们的发现在经济意义上和统计意义上均显著。

利用 Carhart (1997) 提出的动量因子 WML，我们进一步研究了标的股票动量作为期权市场价格压力来源的影响。回归结果表明，标的股票中的动量效应对低流动性期权的影响大于对高流动性期权的影响。这一发现在一定程度上验证了市场动量假说，该假说预测在股价大幅上涨后，看涨期权价格往往相对较高；在股价大幅下跌后，看跌期权价格往往相对较高。

## 参考文献

Amin, K., Coval, J.D. and Seyhun, H.N. (2004). Index Option Prices and Stock Market Momentum. *Journal of Business* **77**, 835–874.

Ball, C.A. and Torous, W.N. (1986). Futures Options and the Volatility of Futures Prices. *Journal of Finance* **41**, 857–870.

Barberis, N., Mukherjee, A. and Wang, B. (2016). Prospect Theory and Stock Returns: An Empirical Test. *Review of Financial Studies* **29**, 3068–3107.

Black, F. and Scholes, M. (1973). The Pricing of Options and Corporate Liabilities. *Journal of Political Economy* **81**, 637–654.

Bodurtha, J.N. and Courtadon, G.R. (1986). Efficiency Tests of the Foreign Currency Options Market. *Journal of Finance* **41**, 151–162.

Brenner, M. and Galai, D. (1986). Implied Interest Rates. *Journal of Business* **59**(3), 493–507.

Brenner, M. and Subrahmanyam, M.G. (1988). A Simple Formula to Compute the Implied Standard Deviation. *Financial Analysts Journal* **44**, 80–83.

Campbell, J.Y., Grossman, S.J. and Wang, J. (1992). Trading Volume and Serial Correlation in Stock Returns. Working Paper, National Bureau of Economic Research.

Chance, D.M. (1996). A Generalized Simple Formula to Compute the Implied Volatility. *Financial Review* **31**, 859–867.

Carhart, M.M. (1997). On Persistence in Mutual Fund Performance. *Journal of Finance* **52**, 57–82.

Choe, H., Kho, B.C. and Stulz, R.M. (1999). Do Foreign Investors Destabilize Stock Markets? The Korean Experience in 1997. *Journal of Financial Economics* **54**, 227–264.

Conrad, J. and Kaul, G. (1998). An Anatomy of Trading Strategies. *Review of Financial Studies* **11**, 489–519.

Cox, J.C. and Ross, S.A. (1976). A Survey of Some New Results in Financial Option Pricing Theory. *Journal of Finance* **31**, 383–402.

Cremers, M. and Weinbaum, D. (2010). Deviations from Put–Call Parity and Stock Return Predictability. *Journal of Financial and Quantitative Analysis* **45**, 335–367.

Drew, M.E., Naughton, T. and Veeraraghavan, M. (2003). Firm Size, Book-to-Market Equity and Security Returns: Evidence from the Shanghai Stock Exchange. *Australian Journal of Management* **28**, 119–139.

Evnine, J. and Rudd, A. (1985). Index Options: The Early Evidence. *Journal of Finance* **40**, 743–756.

Fama, E.F. and French, K.R. (1993). Common Risk Factors in the Returns on Stocks and Bonds. *Journal of Financial Economics* **33**, 3–56.

Fama, E.F. and French, K.R. (2012). Size, Value, and Momentum in International Stock Returns. *Journal of Financial Economics* **105**, 457–472.

Figlewski, S. (1989). Options Arbitrage in Imperfect Markets. *Journal of Finance* **44**, 1289–1311.

Figlewski, S. and Webb, G.P. (1993). Options, Short Sales, and Market Completeness. *Journal of Finance* **48**, 761–777.

Follmer, R.A. and Helms, B.P. (1990). Put–call–Futures Parity and Arbitrage Opportunity in the Market For Options on Gold Futures Contracts. *Journal of Futures Markets* **10**, 339–352.

Galai, D. (1977). Tests of Market Efficiency of the chicago Board Options Exchange. *Journal of Business* **50**, 167–197.
