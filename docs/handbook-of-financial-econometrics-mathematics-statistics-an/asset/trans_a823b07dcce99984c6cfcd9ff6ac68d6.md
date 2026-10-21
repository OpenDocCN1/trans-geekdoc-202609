

![](img/31ee7e6fa5107b22bbf7960ec96106a1_415_0.png)

## 图9.5：银行外国债权网络的图形表示

按LRIC指数之一排名的前十名。建模网络的图形表示如图9.5所示。我们还计算了关键借款人指数，并将结果与我们的方法进行了比较。

指数值最大的国家被认为是市场中最关键/互联度最高的国家。LRIC的五个版本（SumPaths、MaxPath、MaxMin、MaxT、MultT）给出的排名几乎相似，而基于模拟的LRIC（Simul（有关该测度的更多细节，请参见附录9B））则显示出一些差异。然而，主要差异从TOP-10国家的中间部分开始。根据所有方法，TOP-2位置是稳定的，由美利坚合众国（美国）和香港占据。基于模拟的LRIC指数还将一些国家的排名分组，形成区域集群（斯堪的纳维亚、波罗的海国家、澳大利亚和新西兰）。

结果使我们得到两类国家。

首先，最高评级通常出现在大型且强大的经济体，如美国、英国和中国。它们拥有发达的金融体系，具有高度的可信度和主权评级。因此，它们的金融产品（银行存款或证券）吸引了大量投资者。这些结果与（IMF，2015）的发现一致，并可能为“大而不能倒”政策提供良好基础，当这些国家的金融部门可能成为全球系统性风险的来源并应受到更密切监控时。

然而，与上一节相反，我们可以识别出一组经济体量并不算大但也获得了最高LRIC值的国家。像香港、开曼群岛、新加坡和卢森堡这样的国家（地区）是“太互联而不能倒”经济体的典型例子。由于其有吸引力的商业环境、发达的基础设施、人力资本和良好的声誉，这些国家促使投资者将其资产配置到其金融体系中，从而使这些国家成为重要的借款方。这些国家出现在最高排名中乍一看似乎不正常，但这与我们最初的假设一致，即影响力最大的不仅是最庞大的市场参与者，还包括互联度最高的参与者。换言之，对这些国家而言，每一笔单独的现金流并不那么重要，但它们的组合对整个金融体系的稳定可能至关重要。例如，如果一个国家从网络中移除，我们很可能不会看到一连串的级联失败（因为与每个国家的交互量并不大），但这将导致金融流动重新定向到其他国家，从而影响整体金融稳定。

在这方面，有一个有趣的问题：结果对网络结构变化的敏感性如何。根据我们的估计，LRIC方法能够确定任何配置网络中的关键元素，也可用于分析网络配置的动态变化。

我们还使用了一系列现有的中心性度量来估算国家互联程度：加权度中心性、紧密中心性、介数中心性、PageRank和特征向量中心性。这些度量在附录9C中描述。中心性指数计算的结果如表9.14所示。

为了比较排名，我们使用了相关性分析。由于排名中的位置是一个顺序变量，为了评估不同排序的一致性，应使用除传统皮尔逊系数之外的其他秩相关系数。在我们的工作中，我们采用了Kendall度量（Kendall, 1970）的思想，它统计两个排名列表之间两两不一致的数量。此外，我们使用了Goodman和Kruskal γ秩系数，该系数表示数据按每个量排序时排序的相似性（Goodman和Kruskal，1954）。该系数计算为γ = (N_S − N_D)/(N_S + N_D)，其中N_S是在两个变量上按相同顺序排列的案例对数（一致对数量），N_D是在两个变量上按相反顺序排列的案例对数（相反对数量）。

然而，尽管大多数中心性度量和LRIC指数的相关系数相当高，但表9.15显示，与LRIC指数相比，经典中心性度量在识别第二组系统性重要国家（如开曼群岛、卢森堡、香港）方面表现较差。

## 9.5 结论

网络方法可应用于金融体系的不同部分，以刻画系统性风险。在我们的工作中，系统性风险网络模型已被应用于金融市场的一个特定部分——国际信贷市场。

我们探讨了衡量系统性重要性的两种方法：基于路径的远距离相互作用强度测量，以及基于模拟的远距离相互作用强度测量。该网络模型旨在帮助监管机构识别在任何特定危机期间“太大而不能倒”或“太互联而不能倒”的金融元素。所提出的方法能够识别那些乍一看不具有高系统性重要性、但对整个系统稳定性有显著影响的国家。此外，基于模拟的LRIC指数可成为识别区域金融集群的有用工具。

我们对假设示例进行了估算，并展示了跨境国家敞口的实证分析，以证明所提出方法的可行性。基于我们方法的实证结果与国际货币基金组织（IMF）和其他国际金融机构的结论一致。此外，这些结果使我们注意到一些国家的重要性，这些国家因其在全球金融中的中介作用而可能对整个系统的稳定产生强大影响。

## 致谢

我们感谢 Jane M Binner 教授、Logan Kelly 教授、Richard Anderson 教授和 John Duca 博士邀请我们参加由英格兰银行与伯明翰大学金融韧性研究中心于2017年5月23–24日联合主办的“金融服务指数、流动性与经济活动”会议，并感谢该会议的与会者提出的许多有益意见。第9.2–9.3节由俄罗斯科学基金会资助，资助号为№ 17–18-01651，用于国家研究型大学高等经济学院。

## 参考文献

Acharya, V. V., Pedersen, L. H., Philippon, T. and Richardson, M. (2010). Measuring Systemic Risk. Federal Reserve Bank of Cleveland. Working Paper No. 02.

Adrian, T. and Brunnermeier, M. (2010). CoVaR. Federal Reserve Bank of New York, Staff Report No. 348.

Akram, Q. F. and Christophersen C. (2010). Interbank Overnight Interest Rates — Gains from Systemic Importance. Norges Bank. Working Paper No. 11.

Aldasoro, I. and Alves, I. (2017). Multiplex interbank networks and systemic importance An application to European data. BIS. Working Papers No. 603.

Aleskerov, F., Andrievskaya, I. and Permjakova, E. (2016). Key Borrowers Detected By The Intensities of Their Short-Range Interactions. In Models, Algorithms, and Technologies for Network Analysis. From the 4th International Conference on Network Analysis, edited by V. A. Kalyagin, P. Koldanov and P. M. Pardalos, New York: Springer International Publishing.

Aleskerov, F. T., Yuzbashev, D. V. and Yakuba, V. I. (2007). Threshold Aggregation for Three-Graded Rankings. Automation and Remote Control (in Russian). No. 1. 147–152.

Aleskerov, F. T. (2006). Power Indices Taking into Account Agents’ Preferences. Eds. Simeone B. & Pukelsheim, F. Mathematics and Democracy, Springer, Berlin, 1–18.

Allen, F. and Gale, D. (2000). Financial Contagion. Journal of Political Economy, 108(1), 1–33.

Allen, F. and Babus, A. (2009). Networks in Finance. In Network-based Strategies and Competencies. Ed. Kleindorfer, P. & Wind, J. 367–382.

Angelini, P., Maresca, G. and Russo, D. (1996). Systemic risk in the netting system. Journal of Banking and Finance, 20, 853–868.

Barrat, A., Barthelemy, M., Pastor-Satorras R. and Vespignani A. (2004). The Architecture of Complex Weighted Networks. Proceedings of the National Academy of Sciences, 101(11), 3747–3752.

Basel Committee on Banking Supervision (BCBS) (2013). Global Systemically Important Banks: Updated Assessment Methodology and the Higher Loss Absorbency Requirement Consultative Document.

Bech, M. L. and Atalay, E. (2008). The Topology of the Federal Funds Market. Federal Reserve Bank of New York, Staff Report No. 354.

Bernanke, B. (2010). Causes of the Recent Financial and Economic Crisis. Testimony before the Financial Crisis Inquiry Commission (FCIC), September 2, 2010, Washington D.C.

Bluhm, M. and Krahnen, J. P. (2014). Systemic Risk in An Interconnected Banking System with Endogenous Asset Markets. Journal of Financial Stability, 13, 75–94.

Bonacich, P. (1972). Technique for Analyzing Overlapping Memberships. Sociological Methodology, 4, 176–185.

Bruhl, V. (2017). How to Define a Systemically Important Financial Institution — A New Perspective. Intereconomics, March 2017, 52(2), 107–110.

Cajueiro, D. O. and Tabak, B. M. (2008). The Role of Banks in the Brazilian Interbank Market: Does Bank Type Matter? Physica A: Statistical Mechanics and its Applications, 387(27), 6825–6836.

Chan-Lau, J. A. (2010). The Global Financial Crisis and its Impact on the Chilean Banking System. IMF Working Paper No. 108.

Drehmann, M. and Tarashev, N. (2011). Measuring the Systemic Importance of Interconnected Banks. Bank for International Settlements. Working Paper No. 342.

