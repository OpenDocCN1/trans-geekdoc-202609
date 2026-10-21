
利用更多数据进行样本外预测。Shumway（2001）证明多期 Logit 模型等价于离散时间风险模型。因此，他的模型对每个样本公司使用多年数据，并将每个公司视为单一观测值。

此外，Shumway（2001）还纠正了传统破产预测方法中的问题，即先前的研究仅使用了先前破产研究中使用的大多数会计比率，而这些比率被发现并不显著。Shumway（2001）不仅纳入了财务比率，还纳入了市场变量，如市场规模、过去股票回报和特有回报波动性，作为破产预测因子。

预测模型中的因变量是给定样本年度中每个公司-年度的破产状态（0，1）。在风险分析中，对于破产公司，因变量在申请破产的年份等于 1，而在破产申请年份之前的全部样本年度中因变量等于 0。非破产公司在样本中每一年都被编码为 0。

Shumway（2001）研究采用了广泛行业中所有可用的公司，形成了 1962–1992 年期间 300 家破产公司的样本。研究发现，多期 Logit 模型优于 MDA 和单期 Logit 模型，并且市场基础和会计基础自变量的组合优于仅基于会计的模型。纳入市场基础和会计基础预测因子的 Shumway 模型表示如下：

Y = -13.303 - 1.982 X₁ + 3.593 X₂ - 0.467 X₃ - 1.809 X₄ + 5.79 X₅,      (78.9)

其中 Y 为 log[P/(1 - P)]，P 为破产概率；
- X₁ = 净利润/总资产；
- X₂ = （总负债/总资产）；
- X₃ = （观察年度前一年末各公司市值/纽约证券交易所和美国证券交易所总市值）的对数；
- X₄ = 过去超额回报，即公司在 t − 1 年的回报减去 t − 1 年价值加权 CRSP 纽约证券交易所/美国证券交易所指数回报；以及
- X₅ = 各公司股票回报的特有标准差。其定义为回归残差的标准差，该回归将 t − 1 年各股票的月度回报对同年价值加权纽约证券交易所/美国证券交易所指数回报进行回归。

为评估方程（78.9）中给出的风险模型预测准确性，Shumway（2001）根据模型预测的破产概率将测试样本分为 10 组。风险模型将几乎 70% 的所有破产案例归类在破产概率最高的十分位中，并在中位数概率以上归类了 96.6% 的破产公司。继 Shumway（2001）之后，破产预测研究人员一直在使用多期 Logit 回归。例如，Sun（2007）开发了多期 Logistic 回归模型，并发现该模型在预测破产方面优于审计师的持续经营意见。4

## 78.7.2 KMV–Merton 模型

KMV 公司开发了 KMV–Merton 模型，该模型现在在实践和学术研究中都频繁使用。该模型是 Merton 模型的应用，其中公司的股权是对公司底层价值的看涨期权，行权价等于公司债务的面值。KMV–Merton 模型通过应用 Merton（1974）债券定价模型来估计债务的市场价值。Merton 模型做出了两个特别重要的假设。第一个假设是公司的总价值遵循几何布朗运动。第二个关键假设是公司仅发行了一只在 T 期间到期的贴现债券。基于这些假设，公司的股权是对公司底层价值的看涨期权，行权价等于公司债务的面值，到期时间为 T。Black–Scholes–Merton 公式可以描述股权价值作为公司总价值的函数。根据 put-call 平价，公司债务的价值等于无风险贴现债券的价值减去针对公司发行的看跌期权的价值，同样行权价等于债务面值，到期时间为 T。如果 Merton 模型的假设成立，KMV–Merton 模型应能给出准确的违约预测。

Bharath 和 Shumway（2004）检验了两个假设：（i）Merton 模型隐含的违约概率是预测破产的充分统计量；以及（ii）Merton 模型是预测违约时需要考虑的重要数量。

本研究假设，一组合理的简单变量无法完全替代 Π_KMV（KMV–Merton 概率）中的信息，或者违约概率的充分统计量不能忽视 Π_KMV。

## 78.7.3 实证比较

Bharath 和 Shumway（2004）将 Π_KMV 纳入到一个从 1980 年到 2003 年预测违约的风险模型中。使用该风险模型，他们将 Π_KMV 与一个天真的替代方案 Π_Naive 进行比较，后者计算起来要简单得多，但保留了 Π_KMV 的部分函数形式。

总之，他们检验了 KMV–Merton 违约预测模型的准确性和贡献。观察预测违约的风险模型，KMV–Merton 模型并未产生违约概率的充分统计量，并且似乎可以在不求解 KMV–Merton 模型所需的联立非线性方程的情况下构建充分统计量。

Mai 的博士论文（2010）重新审视了四种最常用的违约预测模型：z-score 模型（Altman（1968））、Logit 模型（Ohlson（1980））、Probit 模型（Zmijewski（1984））和风险分析（Shumway（2001））。她的实证结果表明，Shumway（2001）采用的离散时间风险模型，结合一套新的会计比率和市场驱动变量，提高了破产预测能力。

通过使用来自 Compustat 年度工业数据库的手工收集的企业违约事件和公开可获得的新闻报道，Mai（2010）构建了 1991 年至 2006 年间在美国三大证券市场之一上市的公司的样本。以谨慎选择的 0.021 隐含破产概率水平为截断点，采用逐步方法的样本外风险模型将 82.7% 的违约公司和 82.8% 的非违约公司分类。相比之下，Shumway（2001）中的最佳结果提供了 76.5% 的违约公司分类，Altman（1993）为 55.2%，Ohlson（1980）为 66.1%，Zmijewski（1984）为 65.4%，可以得出结论，她的博士论文结果优于其他四种模型。

Logit 和 Probit 模型的设定可在附录 78B 中找到，破产预测中风险模型的 SAS 代码可在附录 78C 中找到。

## 78.8 摘要

在本章中，我们讨论了判别分析和因子分析中两种多元统计方法的应用。详细讨论了使用两组判别函数进行信用分析、预测公司破产以及确定问题银行和困境 P-L 保险公司的示例。介绍了因子分析的基本概念，展示了其在确定有用财务比率中的应用。此外，还讨论了因子分析和判别分析结合分析工业债券评级。最后，讨论了 Ohlson 和 Shumway 估计违约概率的方法。

总之，本章表明多元统计方法可用于为管理者和研究人员执行实用的财务分析。

## 注释
- 1. 这三个判别函数的缩放系数可在附录 78A 中找到。
- 2. 为验证其 MDA 模型，PSJ 使用 Lachenbruch 的（1967）jackknife 程序进行实证分析。他们得出结论，MDA 分析在确定电力公用事业行业的债券评级预测方面相对有效。Jackknife 方法及其对 MDA 的应用在附录 78A 中讨论。
- 3. Saunders 和 Allen（2002）以及 Saunders 和 Cornett（2006）讨论了确定信用风险的替代方法。

## 参考文献
E. I. Altman (1968). Financial Ratios, Discriminant Analysis, and the Prediction of Corporate Bankruptcy. Journal of Finance, 23, 589–609.
E. I. Altman, R. Haldeman, and P. Narayanan (1977). ZETA Analysis, a New Model for Bankruptcy Classification. Journal of Banking and Finance, 1, 29–54.
E. I. Altman, and T. P. McGough (1974). Evaluation of a Company as a Going-Concern. Journal of Accounting, (December), 50–57.
E. I. Altman (1982). Accounting Implications of Failure Prediction Models. Journal of Accounting, Auditing, Finance (Fall), 4–19.
E. I. Altman (1984). The Success of Business Failure Prediction Models. An International Survey. Journal of Banking and Finance, 8(2), 171–198.
E. I. Altman (1989). Measuring Corporate Bond Mortality and Performance. Journal of Finance, 44(4), 909–922.
E. I. Altman (1993). Corporate financial distress and bankruptcy: A complete guide to predicting and avoiding distress and profiting from bankruptcy, New York: Wiley.
E. I. Altman (2000). Predicting financial distress of companies revisiting the z-score and ZETA models. Working Paper.
E. I. Altman, G. Marco, and F. Varetto (1994). Corporate Distress Diagnosis: Comparisons Using Linear Discriminant Analysis and Neural Networks. Journal of Banking & Finance, 18, 505–529.
T. Amemiya (1981). The Qualitative Response Models: A Survey. The Journal of Economic Literature, (December), 1483–1536.
