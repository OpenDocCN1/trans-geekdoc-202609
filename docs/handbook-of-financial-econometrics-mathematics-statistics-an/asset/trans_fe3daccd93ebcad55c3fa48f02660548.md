
- Manove, M., Padilla, A. J. and Pagano, M. (2001). Collateral Versus Project Screening: A Model of Lazy Banks. The RAND Journal of Economics, 32, 726–744.
- Manove, M. and Padilla, A. J. (1999). Banking (Conservatively) with Optimists. RAND Journal of Economics, 30, 324–350.
- Ongena, S. and Yu, Y. (2017). Firm Industry Affiliation and Multiple Bank Relationships. Journal of Financial Services Research, 51, 1–17.
- Rajan, R. and Winton, A. (1995). Covenants and Collateral as Incentives to Monitor. Journal of Finance, 50, 1113–1146.
- Rajan, R. G. and Zingales, L. (1995). What Do We Know About Capital Structure? Some Evidence from International Data. Journal of Finance, 50, 1421–1460.
- Rajan, R. G. (1992). Insiders and Outsiders: The Choice Between Informed and Arm's-Length Debt. Journal of Finance, 1367–1400.
- Ramakrishnan, R. T. S. and Thakor, A. V. (1984). Information Reliability and A Theory of Financial Intermediation. Review of Economic Studies, 51, 415–432.
- Sharpe, S. A. (1990). Asymmetric Information, Bank Lending and Implicit Contracts: A Stylized Model of Customer Relationships. Journal of Finance, 45, 1069–1087.
- Sheard, P. (1989). The Main Bank System and Corporate Monitoring and Control in Japan. Journal of Economic Behavior & Organization, 11, 399–422.
- Slovin, M. B., Sushka, M. E. and Ferraro, S. R. (1995). A Comparison of the Information Conveyed by Equity Carve-Outs, Spin-Offs, and Asset Sell-Offs. Journal of Financial Economics, 37, 89–104.
- Szewczyk, S. H., Tsetsekos, G. P. and Zantout, Z. (1996). The Valuation of Corporate R&D Expenditures: Evidence from Investment Opportunities and Free Cash Flow. Financial Management, 25, 105–110.
- von Rheinbaben, J. and Ruckes, M. (1998). A Firm’s Optimal Number of Bank Relationships and the Extent of Information Disclosure. University of Mannheim, Working Paper.
- Wu, Wei-Hsiung (2008). The Second Financial Reform and the Development of Financial Industry in Taiwan. Review of Pacific Basin Financial Markets and Policies, 11(1), 75–97.
- Xu, Y. (2011). Towards a More Accurate Measure of Foreign Bank Entry and its Impact on Domestic Banking Performance: The Case of China. Journal of Banking and Finance, 35(4), 886–901.
- Yosha, O. (1995). Information Disclosure Costs and the Choice of Financing Source. Journal of Financial Intermediation, 4, 3–20.
- Yu, Hai-Chin, Sopranzetti, B. and Lee, C. F. (2012). Multiple Banking Relationships, Managerial Ownership Concentration and Firm Value: A Simultaneous Equations Approach. Quarterly Review of Economics and Finance, 52(3), 286–297.

- 参考文献 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1016
- 附录26A：季节性序列的Holt–Winters预测模型 . . . . . . . . . . . . . . . 1016
- 附录26B：组合预测法 . . . . . . . . . . . . . . . 1021

## 摘要

在本章中，我们首先讨论经典的时间序列成分模型，然后讨论移动平均和经过季节性调整的时间序列。接着讨论线性和对数线性时间趋势回归。我们还回顾了自回归预测模型以及ARIMA模型。最后，讨论了组合预测。

## 关键词

- 自回归预测模型
- 同步指标
- 横截面数据
- 周期性成分
- 指数平滑
- 指数平滑常数
- Holt–Winters预测模型
- 不规则成分
- 滞后指标
- 领先指标
- 均方误差
- 移动平均百分比
- 季节性成分
- 季节性指数
- 季节性指数法
- 时间序列数据
- 趋势成分
- 趋势-周期成分
- 交易日成分
- X-11模型

## 26.1 引言

时间序列分析是金融研究中最重要的工具之一。在本章中，我们将讨论传统的时间序列分析技术。在下一章中，我们将讨论处理异方差性并应用于估计期货合约套期保值比率的现代时间序列分析模型。

我们可以同时纳入时间序列和横截面数据，并在经济和商业决策中应用统计分析技术。时间序列数据是来自某个可量化（或定性）事件、随时间记录的任何数据集。例如，我们每天阅读报纸，可以获得随时间变化的道琼斯工业平均指数（DJIA）。按时间顺序排列的DJIA指数值序列就构成了时间序列数据。其他类型的时间序列数据包括通货膨胀率、消费者价格指数、贸易差额以及公司年度利润等。

**横截面数据**是对个体、个体群体、物体或地理区域*在某一特定时间*的观测。例如，1991年*N*家公司的每股价格就是一组横截面数据。另一方面，通用汽车公司随时间变化的每股价格*P_t*（*t* = 1, 2, …, *T*）则是一组时间序列数据。

本章的目的是描述时间序列分析的各个组成部分，并讨论基于时间序列数据的经济和商业预测的替代方法。26.2节讨论时间序列三种成分的经典描述。26.3节讨论移动平均和经过季节性调整的时间序列。26.4节讨论线性和对数线性时间趋势回归。26.5节讨论指数平滑与预测。26.6节将讨论自回归预测模型。26.7节讨论ARIMA模型。26.8节讨论组合预测。最后，26.9节对本章进行总结。附录26A介绍季节性序列的Holt–Winters预测模型。附录26B讨论组合预测。

## 26.2 经典时间序列成分模型

多种因素导致了时间序列数据随时间的相互依存性；这些因素是趋势因素、季节性因素和商业周期因素。例如，一家成长型公司当前的收益往往高于其刚结束期间的收益，当然，下一期的预期收益也会高于当前收益。因此，任何相邻收益之间的相关性都是正的，这是由于趋势因素造成的。季节性因素也促成了时间序列数据的相互依存性。第四季度的零售额占百货公司全年总销售额的很大一部分。这一季节性因素使得每年第四季度的销售额与任何其他年份第四季度的销售额高度相关。商业周期是时间序列模型中相互依存性的另一个原因。简而言之，传统上认为时间序列的总变动由四个基本成分组成：趋势成分、季节性成分、周期性成分和不规则成分。我们现在将详细讨论这四个成分。

### 26.2.1 趋势成分

趋势是一种随时间相当稳定地增长或下降的模式。例如，强生公司（Johnson & Johnson）的每股收益（EPS）随时间呈现出两个独立的趋势（或二次趋势）（见表26.1和图26.1）。其中一个趋势是从2001年到2007年，另一个是从2008年到2010年。

表26.1：强生公司每股收益。

| 年份 | 每股收益（EPS） |
|------|-----|
| 2001 | 1.87 |
| 2002 | 2.2 |
| 2003 | 2.42 |
| 2004 | 2.87 |
| 2005 | 3.5 |
| 2006 | 3.76 |
| 2007 | 3.67 |
| 2008 | 4.62 |
| 2009 | 4.45 |
| 2010 | 4.85 |

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1024_0.png)

图26.1：强生公司每股收益。

### 26.2.2 季节性成分

季节性现象在商业世界中十分普遍。零售商可以指望12月份的销售额高于任何其他月份；股票回报率通常在1月份高于大多数其他月份——这就是“一月效应”。

表26.2和图26.2显示了IBM公司在44个季度（2000年第一季度至2010年第四季度）的每股收益。该表为所有季度的季节性行为提供了证据。第四季度的数值往往相对较高，而第一季度的数值相对较低。这种季节性行为在图26.2中表现得相当明显，图中一个明显的模式几乎每年都会重复出现。

### 26.2.3 周期性成分与商业周期

周期模式是与季节性行为无关的长期振荡模式。它们不一定是规则的，而是遵循相当平滑的上升和下降模式，每次波动持续超过2或3年。图26.3展示了2000—2010年期间标普500综合指数的周期模式，该模式将在后文讨论

