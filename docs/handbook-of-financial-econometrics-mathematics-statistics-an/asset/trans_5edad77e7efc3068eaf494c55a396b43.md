

## 表59.3： (59.4) 的拟合AG复发生存模型

| 协变量 | β_j | exp(β_j)^2 | SE(β_j)^3 | z | p值^4 | L^5 | p值^5 |
|---|---|---|---|---|---|---|---|
| A. 命题1：无风险利率对λ^1(t)^1有正向影响 |  |  |  |  |  |  |  |
| X1 | 0.770 | 2.160 | 0.138 | 5.580 | 0.0000 | 32.40 | 0.0000 |
| B. 命题2：股息对λ^2(t)^1有正向影响 |  |  |  |  |  |  |  |
| X2 | -0.044 | 0.957 | 0.034 | -0.919 | 0.3600 | 1.71 | 0.1920 |
| C. 命题3a：资本支出对λ^3(t)^1有负向影响 |  |  |  |  |  |  |  |
| X3 | 1.520 | 4.580 | 0.310 | 4.903 | 0.0000 | 22.20 | 0.0000 |
| D. 命题3b：投资支出对λ^4(t)^1有负向影响 |  |  |  |  |  |  |  |
| X4 | 1.270 | 3.580 | 0.275 | 4.618 | 0.0000 | 18.90 | 0.0000 |
| E. 命题4：回购比率对λ^5(t)^1有负向影响 |  |  |  |  |  |  |  |
| X5 | -0.003 | 0.997 | 0.001 | -3.414 | 0.0003 | 13.20 | 0.0003 |
| F. 命题5：百分比价差对λ^6(t)^1有正向影响 |  |  |  |  |  |  |  |
| X6 | -0.114 | 0.893 | 0.038 | -2.969 | 0.0029 | 7.83 | 0.0051 |
| G. 命题6：机构持股对λ^7(t)^1有正向影响 |  |  |  |  |  |  |  |
| X7 | 0.005 | 1.010 | 0.002 | 2.127 | 0.0334 | 4.28 | 0.0386 |
| H. 命题7：总资产对λ^8(t)^1有正向影响 |  |  |  |  |  |  |  |
| X8 | 0.100 | 1.110 | 0.031 | 3.226 | 0.0012 | 10.20 | 0.0014 |

注：¹ λ^j(t) = λ₀(t) exp{β_j X_j(t)} 是瞬时转换率，1 ≤ j ≤ 8，其中 X₁ 是无风险利率；X₂ 表示股息收益率；X₃ 和 X₄ 表示按上一年末总资产标准化后的“资本支出”和“投资支出”；X₅ 表示回购比率；X₆ 表示转换价格与当前股票价格之间的百分比价差；X₇ 表示“机构持股比例”，即非管理层持有的股份比例；X₈ 表示“总资产”；² exp(β_j) 表示 X_j 对瞬时转换率 λ^j(t) 的边际贡献；³ SE 表示基于 AG 模型的 β_j 估计量的标准差。⁴ 假设 H₀: β_j = 0 对 H₁: β_j ≠ 0 的 p 值；⁵ L 和 p 值是假设 H₀: λ^j(t) = λ₀(t) exp{β_j X_j(t)} 的似然比统计量和 p 值。

对于息票，到期前转换的激励增加。与 Asquith 和 Mullins (1991) 不同，Constantinides (1984) 通过推导连续转换路径表明，较高的股息收益率会导致较低的转换率。

对于资本支出和投资支出的比率（X₃i 和 X₄i），系数 β₃ 和 β₄ 显著为正（p 值为 0.0000）。因此，命题3未得到验证。这表明，伴随投资融资的可转换债券发行并不具有 Constantinides 和 Grundy (1989) 所建议的那种预期的债务类信号效应。相反，由于 β₃ 和 β₄ 均为正，伴随投资融资的可转换债券发行提供了股权类信号效应。股票回购的回购比率（X₅i）的系数 β₅ 显著为负，p 值为 0.0003。因此，命题4得到验证，这与 Spatt 和 Sterbenz (1988) 及 Constantinides 和 Grundy (1989) 关于股票回购比率的债务类信号作用一致。对于转换价格与股票价格之间的百分比价差（X6i），系数 β6 显著为负，p 值为 0.0029。因此，命题5未得到验证。这一结果与 Davidson *等人* (1995) 和 Kim (1990) 关于可转换债券的股权类信号作用相矛盾，但另一方面，它与 Asquith 和 Mullins (1991) 的现金流优势原则一致，即较高的转换价值会引发债券持有人的转换。

最后，命题6和命题7被接受，因为非管理层机构持股比例（X7）和总资产价值（X8）的系数 β7 和 β8 均显著为正，p 值分别为 0.0334 和 0.0012。这意味着对于非管理层机构持股比例较高的公司，发行可转换债券是一种股权类信号。这与 Lee *等人* (2009) 的观点一致，即股东权利较高的公司会发行股权类可转换债券。此外，总资产价值越高，信息不对称程度越低，发行可转换债券就越可能成为股权类信号。

## 59.4.3 可转换债券的风险转移潜力

对于命题8-9，考虑 AG 模型

λ_{ik}^j(t) = λ0(t) exp{β_{j,1} X_{ji}(t) * X_{11,i}(t) + ⋯ + β_{j,7} X_{ji}(t) * X_{16,i}(t)} , (59.5),

其中 9 ≤ j ≤ 10，X9i 是可自由支配资产与总资产之比，X10,i 是自由现金流与总资产之比，X11,i,...,X16,i 是债券评级类别4-9的虚拟变量。表59.4展示了 9 ≤ j ≤ 10 的两个估计 AG 模型（59.5）。对于 j = 9，项 (X9i * X11,i),..., (X9i * X15,i) 的系数 β9,11,...,β9,14 不显著，而项 (X9i * X15,i) 和 (X9i * X16,i) 的系数 β9,15 和 β9,16 显著为负，p 值分别为 0.0005 和 0.0000。也就是说，较高的可自由支配资产比率仅在评级为8和9的债券（X15,i = 1 和 X16,i = 1）中降低转换率。这表明，当风险企业的风险转移潜力较高时，可转换债券的连续转换率并未如预期那样加快，反而放缓，从而维持了风险缓解效应。因此，命题8未得到验证。

对于 j = 10，项 (X10,i * X11,i), (X10,i * X12,i) 的系数 β10,11, β10,12 不显著。另一方面，协变量 (X10i * X13,i),..., (X10,i * X16,i) 的系数 β10,13,...,β10,16 显著为负，p 值分别为 0.001、0.000、0.003 和 0.000。

信号传递更高的预期未来盈利，并作为 Kim (1990) 和 Davidson *等人* (1995) 所称的股权类信号。此外，较高的股票回购比率是可转换债券发行的债务类信号。这一结果支持了 Constantinides 和 Grundy (1989) 的信号均衡模型，该模型为可转换债券发行与股票回购相结合提供了债务配给的理由，这与可转换套利者进行的与套利相关的卖空有关（例如，参见 de Jong *等人*, 2011；Brown *等人*, 2012）。

最后，企业的风险转移潜力不会削弱可转换债券的风险缓解效应。对于风险较高的企业，较高的风险转移潜力，无论是较高的可自由支配资产比率还是较高的自由现金流，都会降低连续转换率。这意味着，对于风险较高的企业，可转换债券的风险缓解效应得以维持。

## 参考文献

Allison, P. D. (2010). *Survival Analysis Using the SAS System: A Practical Guide.* 2nd ed. Cary, NC: SAS Institute.

Andersen, P. K. and Gill, R. D. (1982). Cox’s Regression Model for Counting Processes: A Large Sample Study. *Annals of Statistics*, 10, 1100–1120.

Asquith, P. and Mullins, D. W. (1991). Convertible Debt: Corporate Call Policy and Voluntary Conversion. *Journal of Finance*, 46, 1273–1289.

Banko, J. C. and Zhou, L. (2010). Callable Bonds Revisited. *Financial Management*, 39(2), 613–641.

Billingsley, R. S. and Smith, D. M. (1996). Why Do Firms Issue Convertible Debt? *Financial Management*, 25, 93–99.

Brennan, M. J. and Schwartz, E. S. (1977). Convertible Bonds: Valuation and Optimal Strategies for Call and Conversion. *Journal of Finance*, 32, 1699–1716.

Brennan, M. J. and Schwartz, E. S. (1980). Analyzing Convertible Bonds. *Journal of Financial and Quantitative Analysis*, 15(4), 907–929.

Brennan, M. J. and Schwartz, E. S. (1988). The Case for Convertibles. *J. Appl. Corp. Finance*, 1, 55–64.

Brennan, M. J. and Kraus, A. (1987). Efficient Financing Under Asymmetric Information. *Journal of Finance*, 42, 1225–1243.

Box-Steffensmeier, J. M. and Boef, S. D. (2006). Repeated Events Survival Models: The Conditional Frailty Model. *Statistics in Medicine*, 25, 3518–3533.

Brown, S. J., Grundy, B. D., Lewis, C. M. and Verwijmeren, P. (2012). Convertibles and Hedge Funds as Distributors of Equity Exposure. *Rev. Financ. Stud.*, 25, 3077–3112.

Brounen, D., de Jong, A. and Koedijk, K. (2006). Capital Structure Policies in Europe: Survey Evidence. *J. Bank. Finance*, 30, 1409–1442.

Bühler, W. and Kosiol, C. (2004). Valuation of Convertible Bonds with Sequential Conversion. *Schmalenbach Business Review*, 54, 302–334.

Chang, S. C., Chen, S. S. and Liu, Y. (2004). Why Firms Use Convertibles: A Further Test of the Sequential-Financing-Hypothesis. *J. Bank. Finance*, 28, 1163–1183.

Constantinides, G. M. (1984). Warrant Exercises and Bond Conversion in Competitive Markets. *Journal of Financial Economics*, 13(1), 371–397.

