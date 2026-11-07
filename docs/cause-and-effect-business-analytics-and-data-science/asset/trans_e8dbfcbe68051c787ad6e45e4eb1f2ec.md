
* 第 251 页 Michalewicz, Z., and D. B. Fogel. 2002. 如何解决它：现代启发式方法。纽约 纽约州：Springer。 [⏎](#chapter8.xhtml#b8ref8_26)
* Papadimitriou, Christos H., and Kenneth Steiglitz. 1998. 组合优化：算法与复杂性。花园城，纽约州：Dover。 [⏎](#chapter8.xhtml#b8ref8_27)
* Pisinger, David. 1995. “Algorithms for Knapsack Problems,” *博士论文*，哥本哈根大学计算机科学系。 [⏎](#chapter8.xhtml#b8ref8_28)
* Ravindran, A., Don T. Phillips, and James J. Solberg. 1987. 管理科学：原理与实践，第 2 版。霍博肯，新泽西州：Wiley。 [⏎](#chapter8.xhtml#b8ref8_29)
* Shapiro, Alexander, Darinka Dentcheva, and Andrzej Ruszczynski. 2014. 随机规划讲义：建模与理论。费城，宾夕法尼亚州：SIAM。 [⏎](#chapter8.xhtml#b8ref8_30)
* Storey, A., and M. Cohen. 2002. “利用响应模型：优化银行中的交叉销售和追加销售机会，” *第 8 届 ACM SIGKDD 国际知识发现与数据挖掘会议论文集*。 ACM's SIGKDD 325–331。 [⏎](#chapter8.xhtml#b8ref8_31)
* Taha, Hamdy A. 2010. 管理科学，第 9 版。伦敦，英格兰：Prentice Hall。 [⏎](#chapter8.xhtml#b8ref8_32)
* Trivedi, Pravin K., and David M. Zimmer. 2005. “面向从业者的 sn 简介”。 计量经济学基础与趋势，1(1): 1–111。 [⏎](#chapter8.xhtml#b8ref8_33)
* Tutuncu, R. H., and M. Koenig. 2004. “稳健资产配置”。 运筹学年刊，132: 157–187。 [⏎](#chapter8.xhtml#b8ref8_34)
* Wallace, Stein W. 2000. “不确定性下的决策：敏感性分析是否有用？” 运筹学，48(1): 20–25。 [⏎](#chapter8.xhtml#b8ref8_35)
* Wallace, Stein W., and William T. Ziemba (eds.). 2005. 随机规划的应用。费城，宾夕法尼亚州：MPS-SIAM Series on Optimization。 [⏎](#chapter8.xhtml#b8ref8_36)
* Williams, H. Paul. 2003. 数学规划中的模型构建，第 4 版。霍博肯，新泽西州：Wiley。 [⏎](#chapter8.xhtml#b8ref8_37)
* Zenios, Stavros A. 2007. 实用金融优化：金融工程师的决策。牛津，英格兰：Blackwell Publishing。 [⏎](#chapter8.xhtml#b8ref8_38)

第 252 页

# 9 提升分析 IV：随机与非随机实验的高级建模技术

DOI: [10.1201/9780429172588-9](https://doi.org/10.1201/9780429172588-9)

## 9.1 引言

本章讨论了提升/真实提升建模的高级主题。 [第 6 章](#chapter6.xhtml) 介绍了两种易于应用的基本建模方法。 本章的 [第 9.2 节](#chapter9.xhtml#sec9_2) 考虑了更高级的建模技术，这些技术可能看起来不太直接，但仍然非常实用。

此外，[第 3 章](#chapter3.xhtml)–[第 5 章](#chapter5.xhtml) 中关于因果推断的讨论介绍了在 *观察性* 或 *非随机/非实验性* 数据中衡量因果关系的方法论。 [第 6 章](#chapter6.xhtml)–[第 8 章](#chapter8.xhtml) 关注的是在 *随机实验* 中在个体层面衡量或估计因果效应（或定位）并优化处理分配。 通过 *随机* 实验，我们是指处理组和对照组之间存在随机划分，因此它们之间的任何差异都可以归因于处理。 [第 9.4 节](#chapter9.xhtml#sec9_4) 结合了这些前几章的方法论，以解决两个问题的交集：（1）在个体层面衡量因果效应或定位，以及（2）在 *非随机实验或观察性* 数据中。

在某些商业情况下，随机实验可用且易于执行，例如直接营销（纸质邮件、电子邮件或在线）。 然而，在某些情况下，随机实验不可行。 如前所述，提升分析（在随机实验中）仍是一个新兴领域，而非随机实验中的提升分析在文献中受到的关注有限。 [第 9.4 节](#chapter9.xhtml#sec9_4) 提供了一些方法论细节来解决这个问题。

[第 9.5 节](#chapter9.xhtml#sec9_5) 讨论了“直接响应”的存在，这意味着我们直接知道单个客户是否实际响应（例如通过点击或优惠券扫描）以及如何通过最先进的方法将提升建模与直接响应建模集成。

第 253 页

## 9.2 高级提升/真实提升建模技术

[第 6 章](#chapter6.xhtml) 描述了提升建模的两种简单方法。 本节介绍了一种更高级的方法，由 [Kane 等人（2014）](#chapter9.xhtml#ref9_20) 提出。 考虑 [表 9.1](#chapter9.xhtml#tbl9_1)，其中样本数据中的所有个体都被分类到一个 2 × 2 表中。 响应与否是个人采取的行动，而处理/对照划分由活动设计者决定。

表 9.1 处理与响应 2 × 2 表格 [⏎](#chapter9.xhtml#b9tbl9_1)

|  || 响应 || 未响应 |
| --- | --- | --- |
| 处理 || `Treatment Responders (TR)` || `Treatment Non-responders (TN)` |
| --- | --- | --- |
| 对照 || `Control Responders (CR)` || `Control Non-responders (CN)` |

定义我们的估计目标（即提升）为协变量 `x` 的函数，给出：

`Z`(`x`) = `P`(`R`|`T`,`x`) – `P`(`R`|`C`,`x`), where `R` = event of response

这里 `Z`(`x`) 是在给定一组特征 `x` 的情况下，处理组和对照组之间的响应概率差异（即提升）。 与 [第 6 章](#chapter6.xhtml) 一样，我们的目标是找到一组个体，使其提升值之和最大化。 使用概率论中的贝叶斯法则，[附录 9.1](#chapter9.xhtml#app9_1) 显示上述提升函数 `Z`(`x`) 可以重新表示为：

$$Z\\left( x \\right) = \\frac{1}{2}\\left\\lbrack {\\frac{P\\left\\lbrack {TR} \\middle| x \\right\\rbrack}{P\\left\\lbrack T \\right\\rbrack} + \\frac{P\\left\\lbrack {CN} \\middle| x \\right\\rbrack}{P\\left\\lbrack C \\right\\rbrack} - \\frac{P\\left\\lbrack {TN} \\middle| x \\right\\rbrack}{P\\left\\lbrack T \\right\\rbrack} - \\frac{P\\left\\lbrack {CR} \\middle| x \\right\\rbrack}{P\\left\\lbrack C \\right\\rbrack}} \\right\\rbrack.$$

(9.1)

在公式 (9.1) 中，分子的 `P(TR|x)`、`P(CN|x)`、`P(TN|x)` 和 `P(CR|x)` 分别是个体为处理响应者、对照非响应者、处理非响应者或对照响应者的概率。 因此，我们称之为 *四象限方法* 或 *KLZ*（以 [Kane 等人 2014](#chapter9.xhtml#ref9_20) 命名）。 这些概率可以通过具有四个分类结果的模型使用统计和数据挖掘技术进行预测，例如多项逻辑模型、`CART/CHAID/C4.5`（决策树算法）、`random forest`、`boosted tree`（`MART` 也称为 `TreeNet`）或 `neural network`。 关键要求是能够估计与多个分类结果相关的概率。 公式 (9.1) 中的分母 `P(T)` 和 `P(C)` 分别只是处理和对照概率或比例，即分配给处理和对照的个体百分比，它们是已知量，因为它们由活动设计者决定。

公式 (9.1) 本质上是 [Lai (2006)](#chapter9.xhtml#ref9_23) 提出的一种修改（或校正）版本，他提出了以下评分方程：

`P(TR|x)` + `P(CN|x)` – `P(TN|x)` – `P(CR|x)`,

这可以简单表示为：

`P(TR or CN|x)` – `P(TN or CR|x)`

(9.2).
