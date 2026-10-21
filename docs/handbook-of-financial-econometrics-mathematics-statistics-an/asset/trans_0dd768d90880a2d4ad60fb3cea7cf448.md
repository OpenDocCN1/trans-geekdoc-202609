

## 表112.5：*（续）*

| 公司 | Box-Jenkins | Holt/Winters | 规范化NN | 非规范化NN | 时间序列分解 |
|---|---:|---:|---:|---:|---:|
| JPM | 3.41 | 3.38 | 8.65 | 10.94 | 32.64 |
| KMP | 2.26 | 1.42 | 5.40 | 39.98 | 5.11 |
| KO | 5.49 | 5.36 | 6.39 | 21.53 | 8.48 |
| KYO | 2.02 | 1.75 | 4.61 | 15.47 | 41.40 |
| MCD | 3.34 | 2.71 | 8.77 | 45.55 | 8.93 |
| MMC | 7.20 | 7.27 | 4.46 | 3.96 | 12.48 |
| MS | 3.33 | 3.19 | 4.25 | 85.88 | 23.59 |
| MSFT | 8.05 | 7.85 | 5.55 | 3.78 | 8.73 |
| MU | 10.81 | 10.79 | 1.42 | 46.54 | 41.69 |
| MYL | 5.90 | 5.86 | 8.72 | 14.50 | 5.81 |
| NOK | 4.09 | 4.26 | 2.35 | 97.76 | 40.71 |
| NTT | 1.88 | 1.60 | 2.14 | 41.67 | 4.78 |
| PCAR | 8.35 | 8.27 | 10.93 | 38.99 | 12.80 |
| PG | 4.47 | 4.49 | 5.62 | 5.80 | 4.68 |
| RF | 18.17 | 17.94 | 2.79 | 178.08 | 52.35 |
| RIG | 6.16 | 6.16 | 6.69 | 19.95 | 20.04 |
| SCHW | 9.25 | 9.12 | 2.47 | 25.15 | 9.91 |
| SLB | 15.25 | 15.04 | 12.28 | 18.27 | 1.95 |
| SPG | 3.63 | 3.33 | 8.50 | 39.39 | 17.23 |
| SYMC | 9.74 | 9.73 | 6.24 | 3.27 | 21.19 |
| T | 1.34 | 1.35 | 5.08 | 14.34 | 16.50 |
| USB | 9.30 | 9.23 | 7.79 | 6.90 | 13.39 |
| VCO | 1.34 | 1.27 | 14.77 | 40.52 | 11.90 |
| VMC | 8.74 | 8.73 | 6.85 | 57.03 | 9.10 |
| WHR | 6.18 | 6.18 | 11.19 | 6.02 | 15.05 |
| XOM | 8.32 | 8.13 | 4.51 | 17.72 | 12.15 |
| YHOO | 10.26 | 10.76 | 26.65 | 38.53 | 6.15 |
| **平均值** | **6.62** | **6.50** | **9.30** | **57.11** | **15.00** |
| **标准误差** | **4.16** | **4.17** | **12.83** | **169.92** | **11.93** |

表112.5显示，H/W模型在50个最低MAPE中占16个，规范化NN模型占11个，B-J和TSD各占6个，非规范化NN占5个。然而，正如我们之前指出的，H/W和B-J模型对同一股票的MAPE非常接近且相似。由于NN模型考虑了众多变量，规范化NN模型产生最低MAPE的股票与B-J和H/W模型产生最低MAPE的股票不同。最显著的现象是，非规范化NN的平均MAPE通常非常大，CT的MAPE高达1215.72%，RF的MAPE为178.08%。当我们根据给定模型对所有50家公司计算平均值和标准误差时，H/W模型的平均值最小，但B-J模型的标准差最小。不过，两种模型非常接近。规范化NN紧随其后，TSD与规范化NN的差距也不大。显然，我们应将非规范化NN模型排除在外。这再次清楚地说明了为什么对原始数据进行规范化是神经网络（NN）中的常见做法。对于HIBB，规范化NN也显示出非常高的MAPE，为88.29%。而B-J和H/W模型仅产生相对适中的平均MAPE。从表112.5我们可以得出结论，我们首选的模型是H/W、B-J和规范化NN，它们的表现都非常好。

## 112.6 结论

在本研究中，我们将传统时间序列分解（TSD）、Holt/Winters（H/W）模型、Box-Jenkins（B-J）方法以及神经网络（NN）应用于1998年9月1日至2010年12月31日期间随机挑选的50只股票，每家公司收盘价共有3105个观测值。该样本期间涵盖了高科技繁荣与萧条、历史性的9/11事件、房地产繁荣与萧条，以及近期严重的衰退和当前缓慢的复苏。在此全球经济和金融危机异常不确定的时期，股票价格预计极难预测。所有三种时间序列方法对样本内数据的拟合都非常好，R²约为0.995。对于60个交易日的留出样本或样本外预测，以平均绝对百分比误差（MAPE）衡量的预测误差在B-J、H/W和规范化NN模型中较低，而时间序列分解和非规范化NN模型的预测误差则相当大。

股票市场中充斥着日内交易者、高频交易者、投机者、机构投资者、散户个人投资者、动量追逐者、反向投资者、倾向于发布买入推荐的有影响力的金融分析师，以及其他对当前信息和未来预期持不同看法的多元化市场参与者。信息技术的飞速发展使新闻和谣言以近乎光速传播。即便股票价格极难预测，市场参与者仍必须基于其最佳判断以及所采用的方法和模型作出决策。我们在本研究中讨论的模型和方法的真正价值检验，取决于它们能否在未来的研究中同样适用于其他样本期间和其他样本。

## 参考文献

- Aiken, M. and Bsat, M. (1999). Forecasting Market Trends with Neural Networks. Information Systems Management 16, 42-49.
- Alyuda NeuroIntelligence (2010). Alyuda NeuroIntelligence Manual, http://www.alyuda.com/neural-networks-software.htm.
- Baiyand. A. (2011). The Trading Book: A Complete Solution to Mastering Technical Systems and Trading Psychology. McGraw-Hill, New York.
- Balvers, R., Wu, R. and Gilliand, E. (2000). Mean Reversion Across National Stock Markets and Parametric Contrarian Investment Strategies. Journal of Finance 55, 773-806.
- Box, G. and Jenkins, G. (1976). Time Series Analysis: Forecasting & Control, Revised edn. Holden Day, San Francisco.
- Brock, W., Lakonishok, J. and LeBaron, B. (1992). Simple Technical Trading Rules and Stochastic Properties of Stock Returns. Journal of Finance 47, 1731-1764.
- Corgnet, B., Desantis, M. and Porter, D. (2018). What Makes a Good Trader? On the Role of Intuition and Reflection on Trader Performance. Journal of Finance 73, 1113-1137.
- Cujean, J. and Hasler, M. (2017). Why Does Return Predictability Concentrate in Bad Times. Journal of Finance 72, 2717-2757.
- Daniel, K., Hirshleifer, D. and Subrahmanyam, A. (1998). Investor Psychology and Security Market Under- and Overreactions. Journal of Finance 53, 1839-1885.
- Daniel, K. and Hirshleifer, D. (2015). Overconfident Investors, Predictable Returns, and Excessive Trading. Journal of Economic Perspectives 29, 61-88.
- DeBondt, W. and Thaler, R. (1985). Does the Stock Market Overreact? Journal of Finance 40, 793-805.
- DeBondt, W. and Thaler, R. (1987). Further Evidence on Investor Overreaction and Stock Market Seasonality. Journal of Finance 42, 557-581.
- Dutta, G., Jha, P., Laha, A. and Mohan, N. (2006). Artificial Neural Network Models for Forecasting Stock Price Index in the Bombay Stock Exchange. Journal of Emerging Market Finance 5, 283-295.
- Ferson, W. and Harvey, C. (1993). The Risk and Predictability of International Equity Returns. Review of Financial Studies 6, 527-566.
- Fletcher, D. and Goss, E. (1993). Forecasting with Neural Networks: An Application Using Bankruptcy Data. Information Management 24(3), 159-167.
- Foucault, T., Hombert, J. and Rosu, I. (2016). News Trading and Speed. Journal of Finance 71, 335-381.
- Garleanu, N. and Pedersen, L.H. (2018). Efficiently Inefficient Markets for Assets and Asset Management. Journal of Finance 73, 1663-1712.
- Gazzaz, N.M., Yusoff, M.K., Aris, A.Z., Juahir, H. and Ramli, M.F. (2012). Artificial Neural Network Modeling of the Water Quality Index for Kinta River (Malaysia) Using Water Quality Variables as Predictors. Marine Pollution Bulletin 64(11), 2409-2420.
- Giudici, P. (2001). Bayesian Data Mining, with Application to Benchmarking and Credit Scoring. Applied Stochastic Models in Business & Industry 17, 69-81.
- Glickstein, D. and Wubbels, R. (1983). Dow Theory is Alive and Well! Journal of Portfolio Management 28-32.
- Gordon, W. (1968). The Stock Market Indicators. Investors Press, Palisades, NJ.
- Grudnitski, G. and Osburn, L. (1993). Forecasting S&P and Gold Futures Prices: An Application of Neural Network. Journal of Futures Markets 13, 631-643.
- Gutierrez, R. and Kelly, E. (2008). The Long-Lasting Momentum in Weekly Returns. Journal of Finance 63, 415-447.

