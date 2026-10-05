
结合第 4.3 节的 `CCA` 结果，对于大多数在基于邻域和基于最短路径的中心性指标之间表现出强负（正）规范相关性的网络，我们观察到 `CLC` (`BWC`) 指标受同一因子（`Factor-1`）主导，该因子同样主导了 `DEG` 和 `EVC` 指标，而 `BWC` (`CLC`) 指标似乎被不同的因子（`Factor-2`）主导。注意，对于弱-中等规范相关的网络，`CLC` 指标被一个完全不同的因子（`Factor-3`，其主要只主导 `CLC` 指标）主导，而我们观察到 `BWC` 指标要么被 `Factor-1`（配合 `DEG`）或 `Factor-2`（配合 `EVC`）主导。上述关于 `CCA` 和 `EFA` 结果讨论表明，在两个基于最短路径的中心性指标之间，`BWC` 指标是一个相对更有优势的指标，其相对于两个基于邻域的指标的变化贡献了这两类中心性指标之间的整体相关性。

关于特定因子的主导程度，我们观察到 `BWC` 指标是被特定因子强烈主导的指标（主导因子的 `BWC` 载荷远大于非主导因子的 `BWC` 载荷），其次是 `EVC`。尽管 `DEG` 指标的主导因子与非主导因子的载荷值可以明显区分，但我们观察到 `DEG` 指标（在某种程度上也 `CLC` 指标）受特定因子的主导程度相对较低（特别是对于 24 个强负相关网络中的 23 个，两个因子的 `DEG` 载荷值均高于 0.4）。

### 4.6 相关工作

文献中报道了多项涉及真实世界网络数据集中心性指标的相关性分析。然而，这些相关性分析仅涉及两个中心性指标。据我们所知，除了我们在 `[19]` 中报告的早期工作外，尚未有其他涉及中心性指标的规范相关（`CCA`）研究。此外，我们的工作是第一项涉及四个主要中心性指标（`DEG`、`EVC`、`BWC` 和 `CLC`）进行 `EFA`，并结合研究 `CCA`-`EFA` 结果的工作。在本节的其余部分，我们回顾了近期文献中报道的相关性研究。在 `[11]` 中，两个基于邻域的 `DEG` 和 `EVC` 指标之间观察到强相关性，而对于不同领域的真实网络图，两个基于最短路径的 `BWC` 和 `CLC` 指标之间仅观察到中等相关性（这在 `[23]` 中也得到了证实）。`[11]` 使用了 `Pearson` 相关性分析。

在 `[12]` 中，作者使用 `Spearman` 秩相关分析来量化计算轻量的 `DEG` 指标在多大程度上可以代替计算密集型的 `EVC`、`BWC` 和 `CLC` 指标对顶点排名：观察到高度顶点更有可能是高 `BWC` 顶点，且可能更接近其他顶点；另一方面，观察到高度顶点并不一定是高 `EVC` 顶点。`[13]` 中报道的基于中心性的聚类结果表明，可能存在两个不同的节点簇：一个核心簇，其中组成节点在几项测量中具有最大的中心性指标值；和一个边缘簇，其中组成节点的中心性指标值较低。在 `[14]` 中，作者探索了最近提出的 `O(log²n)` 偷盗者游戏 (`GoT`) 节点中心性指标 `[15]` 与使用无标度、小世界和随机网络模型生成的合成网络的四个主要中心性指标之间的相关性（通过 `Pearson's`、`Spearman's` 和 `Kendall's` 相关性分析）：观察到 `GoT` 与 `DEG` 和 `BWC` 之间存在强负相关，而 `GoT` 与 `CLC` 之间存在弱负相关。

文献中报道了以下因子分析研究：在 `[25]` 考虑的五个中心性指标（值中心性 `[24]`、`BWC`、`CLC`、流中心性 `[25]` 和 Jordan 中心性 `[26]`）中，作者使用保留的主成分数量（与我们的方法类似）作为确定因子数量的依据，并将这些中心性指标在特征向量中的项视为因子载荷。相反，我们将特征向量中的视为中心性指标的初始因子载荷，并进行方差极大旋转以最大化共同性得分，同时利用生成的最终因子载荷来识别每个中心性指标的主导因子，并在强正、强负和弱-中等规范相关网络的背景下探索这些结果。此外，与我们的观察相似，`[25]` 中的作者也观察到 `BWC` 和 `CLC` 指标被两个不同的因子表示。同样，`[27]` 关于农业景观图论模型也观察到 `BWC` 和 `CLC` 指标被两个不同的因子表示，第三个因子则代表度和子图中心性指标。

### 4.7 结论与未来工作

典型相关性分析（`CCA`）的结果表明，在 80 个真实网络中，有超过五之四的网络基于邻域（`DEG` 和 `EVC`）与基于最短路径（`BWC` 和 `CLC`）的中心性指标之间存在强正或负典型相关。我们观察到分别有 24 个真实网络的典型相关系数值小于 `-0.90`（强负典型相关性的衡量标准），以及 25 个网络大于 `0.90`（强正典型相关性的衡量标准）。我们得出结论，其余网络（80 个中的 31 个）表现出弱到中等的相关性，其典型相关系数跨越了 `[-0.90, …, 0.90]` 的宽范围。我们还观察到节点度的谱半径比是一个影响性的网络级指标，它与两类中心性指标之间的典型相关性有关：我们的结果表明，如果一个真实网络出现负典型相关系数，它更有可能具有相对较低的节点度变异（节点度谱半径比小于 `3.0`）；相反，如果一个真实网络表现出较大的节点度变异（节点度谱半径比大于 `3.0`），它更有可能产生正典型相关系数。关于网络领域，我们观察到生物网络和交通网络主要呈现正典型相关系数值，而组织网络（如游戏网络、政治网络、大学部门网络等）更有可能呈现负典型相关系数值。

对同一组 80 个真实网络进行探索性因子分析（`EFA`）的结果表明，两个隐含因子（共同性得分高于 `0.98`）就足以代表四个中心性指标（`DEG`、`EVC`、`BWC` 和 `CLC`），适用于强正和负典型相关网络；而对于弱到中等的典型相关网络，则需要三个隐含因子才能在统计上代表这四个中心性指标。我们观察到超过 90% 的网络中 `BWC` 和 `CLC` 指标（尽管两者都是基于最短路径的中心性指标）由两个不同的因子代表；而两个基于邻域的中心性指标（`DEG` 和 `EVC`）在强正和负典型相关网络中由同一因子代表，在弱到中等的典型相关网络中由两个不同因子代表。此外，对于强正（负）典型相关网络，`BWC`（`CLC`）指标受与 `DEG` 和 `EVC` 指标相同的因子主导。

作为未来工作的一部分，我们计划建立一个基于线性典型相关的预测模型，该模型将使用四个中心性指标中的三个（例如 `DEG`、`EVC` 和 `CLC`）作为自变量，并预测第四个指标（例如可能是计算量最大的指标 `BWC`），并将此类预测准确性与现有的基于皮尔逊相关的单变量和多变量线性预测模型进行比较。

## 参考文献

[1] M. E. J. Newman, Networks: An Introduction, 1st Edition, Oxford, UK: Oxford University Press, September 2010. a, b

[2] P. Bonacich, Power and Centrality: A Family of Measures. American Journal of Sociology, vol. 92, no. 5, pp. 1170–1182, March 1987. a, b

[3] L. Freeman, A set of measures based on betweenness. Sociometry, vol. 40, no. 1, pp. 35–41, March 1977. →

[4] L. Freeman, Centrality in social networks. Social Networks, vol. 1, no. 3, pp. 215–239, 1979. →

[5] G. Strang, Linear Algebra and its Applications, 4th Edition, Pacific Grove, CA, 2006. a, b, c, d, e

[6] N. Meghanathan, Spectral radius as a measure of node degree for complex network. In: Proceedings of 3rd International Conference on Digital Contents and Applications, pp. 30–33, Hainan, December 20–23 2014. a, b, c

[7] R. Noldus, and P. Van Mieghem, Assortativity in complex networks. Journal of Complex Networks, vol. 3, no. 4, pp. 507–542, December 2015. a, b, c

[8] N. Meghanathan, Randomness index for complex analysis. Social Network Analysis and Mining, vol. 7, no. 25, pp. 1–15, December 2017. a, b, c

[9] U. Brandes, A faster algorithm for betweenness centrality. The Journal of Mathematical Sociology, vol. 25, no. 2, pp. 163–177, 2001. →

[10] T. H. Cormen, C. E. Leiserson, R. L. Rivest, and C. Stein, Introduction to Algorithms, 4th Edition, Cambridge, MA: MIT Press, 2022. a, b, c

[11] N. Meghanathan, Correlation coefficient of centrality metrics for complex networks. In: Proceedings of the 4th Computer Science Online, Intelligent Systems and Automation, Vol. 34, pp. 11–20, 2015. a, b

[12] C. Shao, P. Cui, P. Xun, Y. Peng, and X. Jiang, Rank correlation between centrality metrics: An empirical study. Open Physics, vol. 16, no. 1, pp. 1009–1023, December 2018. →

[13] S. Oldham, B. Fulcher, L. Park, A. Arnatkevici, C. Suo, and A. Fornitto, Consistency and differences between centrality measures across distinct classes of networks. PLoS ONE, vol. 022061, pp. 1–23, July 2019. →

[14] A. Ficara, G. Fiumara, P. De Meo, and A. Liotta, Correlation analysis of node and edge centrality in artificial complex networks. In: Proceedings of Sixth International Congress on Information and Technology, pp. 901–908, London, UK, September 2021. →

[15] D. C. Mocanu, G. Exarchakos, and A. Liotta, Decentralized dynamic understanding of hidden relations in complex networks. Scientific Reports, vol. 8, no. 1571, pp. 1–15, January 2018. →

[16] H. Hotelling, Relations between two sets of variates. Biometrika, vol. 28, pp. 321–377, 1936. →

[17] R. L. Gorsuch, Factor Analysis, 2nd Edition, Lawrence Erlbaum Associates, November 1983. a, b

[18] J. C. Loehlin, Latent Variable Models: An Introduction to Factor, Path, and Structural Equation Analysis, 4th Edition, Psychology Press, December 2003. a, b

[19] N. Meghanathan, Canonical correlation analysis of neighborhood-based centrality metrics vs. shortest path-based centrality metrics. In: Proceedings of the 19th International Conference on Data Science, Las Vegas, USA, July 24−27 2023. a, b

[20] P. Eaton, B. Frank, K. Johnson, and S. Willoughby, Comparing exploratory factor models of the brief electricity and magnetism assessment and the conceptual survey of electricity and magnetism. Physical Review Physics Education Research, vol. 15, no. 020133, pp. 1–11, 2019. →

[21] H. F. Kaiser, The varimax criterion for analytic rotation in factor analysis. Psychometrika, vol. 23, pp. 187–200, September 1958. →

[22] [`pypi.org/project/factor-analyzer/`](https://pypi.org/project/factor-analyzer/) →

[23] S. T. Hasson, and Z. Hussein, Correlation among network centrality metrics in complex networks. In: Proceedings of the 6th International Engineering Conference – Sustainable Technology and Development, pp. 54–58, Erbil, Iraq, 2020. →

[24] M. Suyudi, S. Firman, and A. T. Bon, Theoretical and simulation approaches centrality in social networks. In: Proceedings of the 11th Annual International Conference on Industrial Engineering and Operations Management, Singapore, March 2021. →

[25] L. C. Freeman, S. P. Borgatti, and D. R. White, Centrality in valued graphs: A measure of betweenness based on network flow. Social Networks, vol. 13, pp. 141–154, 1991. a, b, c

[26] P. Hage, and F. Harary, Eccentricity and centrality in networks. Social Networks, vol. 17, no. 1, pp. 57–63, January 2005. →

[27] E. Estrada, and O. Bodin, Using network centrality to manage connectivity. Ecological Applications, vol. 18, no. 7, pp. 1810–1825, October 2008. →

## 5 导航数据预处理领域：自动化机器学习平台的深度回顾

### 摘要

有效的数据预处理在增强机器学习（`ML`）性能方面起着至关重要的作用，影响着最终结果的准确性。在自动化机器学习（`AutoML`）发展的背景下，数据预处理的重要性变得日益突出。本章旨在探索并调研用于数据预处理的 `AutoML` 平台，重点关注这些工具如何简化 `ML` 模型的构建和训练。我们深入探讨了各种任务及其子任务，提供了如何在整个 `ML` 流程中利用 `AutoML` 的见解。

关键词：`AutoML`，自动化机器学习，数据预处理流水

### 5.1 引言
