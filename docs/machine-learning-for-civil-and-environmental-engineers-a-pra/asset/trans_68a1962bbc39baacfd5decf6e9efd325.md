

## 表 8.2 用于因果发现的算法和 ML 包（每个包的完整描述和所包含的算法可在其原始来源中找到）。

| 用于因果发现的包 | |
|---|---|
| **CausalNex** | [https://causalnex.readthedocs.io/en/latest/index.html] 一个结合 ML 和领域专业知识的 Python 库，用于因果推理。 |
| **Pcalg** | [https://cran.r-project.org/web/packages/pcalg/index.html] 一个用于因果发现的 R 包，包含：基于约束的结构学习算法：• PC • FCI • 真正快速的因果推断 (RFCI) • 贪婪干预等价搜索 (GIES) 基于得分的结构学习算法：• GES • 贪婪干预等价搜索 (GIES) 混合结构学习算法：自适应受限 GES (ARGES) |
| **bnlearn** | [https://www.bnlearn.com] • 一个用于因果发现的 Python 包，包含：基于约束的结构学习算法：• PC（稳定版） • Grow-Shrink (GS) • Incremental Association Markov Blanket (IAMB) • Fast Incremental Association (Fast-IAMB) 基于得分的结构学习算法：• Hill Climbing (HC) • Tabu Search (Tabu) 混合结构学习算法：• Max-Min Hill Climbing (MMHC) • Hybrid HPC (H2PC) • General 2-Phase Restricted Maximization (RSMAX2) 局部发现算法：• Chow-Liu • ARACNE 贝叶斯网络分类器：• Naive Bayes • Tree-Augmented naive Bayes (TAN) |
| **Tetrad Py-causal R-causal** | [https://www.ccd.pitt.edu/data-science] 由匹兹堡大学因果发现中心创建的软件、Python 和 R 包。 |
| **Causal discovery toolbox** | [https://fentechsolutions.github.io/CausalDiscoveryToolbox/html/data.html] 用于因果发现的 Python 和 R 包。 |
| **TIGRAMITE** | [https://github.com/jakobrunge/tigramite] 一个用于时间序列数据集因果发现的 Python 包。 |

最简单的方法是对 *Group A* 的抗弯承载力结果取平均值，对 *Group B* 做同样的处理，并比较每组的平均值（或期望值（*E*））。从数学上看，这将导致以下结果：
*Group A* 与 *Group B* 之间的平均值（期望值）差 = *E* [ Y<sub>1</sub> - Y<sub>0</sub> ] (8.4)
同样，可以使用 Pearlian 方法（即，*do*-微积分）通过应用 do-算子（参见公式 8.5）。<sup>88</sup>
[ Y | do (T = 1)] - *E* [ Y | do (T = 0)] (8.5)
公式 8.4 和 8.5 均估计平均处理效应（ATE）。

## 表 8.3 用于因果发现分析的指标 [28, 29]。

| 指标 | 描述 |
| :--- | :--- |
| 缺失或多余的边 | 原始模型中缺失或存在但生成模型中不存在的边的数量。 |
| 错误的邻接 | 生成模型中存在但原始模型中不存在的无向边的数量。 |
| 错误和正确的有向边 | 生成模型中缺失或存在的有向边的数量，这些边的方向正确。 |
| 结构海明距离 | 缺失的边、多余的边和方向错误的边之和。 |
| 邻接精度 | 正确预测的邻接 / 预测的邻接。 |
| 邻接召回率 | 正确预测的邻接 / 真实的邻接。 |
| 箭头精度 | 正确预测的箭头 / 预测的箭头。 |
| 箭头召回率 | 正确预测的箭头 / 真实的箭头。 |
| 曲线上方面积 | AOC = 1 – AUC，其中 AUC（曲线下方面积）衡量假正率和真正率图形下方的面积。 |

这并非我们能推断的唯一量度。事实上，还有其他因果效应，例如条件平均处理效应（CATE）<sup>89</sup>、对处理组的平均处理效应（ATT）<sup>90</sup>，以及单元个体处理效应（ITE）<sup>91</sup> 等。

要找到 ATT，只检查 Group B 中的梁是合乎逻辑的。

为了继续我们的示例以估计 ATT，我们只想返回到 Group B。然后，ATT 将是 E[Y1 - Y0] | T = 1 <sup>92</sup>。

有许多 ML 包可用于因果推断研究。这些包在表 8.4 中列出。

### 8.4.10 因果方法

在以下页面中，我将介绍一种因果发现和因果推断的方法，我将在本章的后续示例中采用该方法。

让我们先介绍该方法。<sup>93</sup>

提出的因果方法自然包含三个步骤：因果发现 [通过因果图（例如 DAG<sup>94</sup>）揭示潜在结构]、因果推断 [推断通过干预<sup>95</sup>观察到的现象 / 输出将如何变化]、以及（在可能时）将因果发现与同行或独立分析（例如，来自 ML、统计分析、领域知识等）进行比较。图 8.9 更详细地展示了所提方法。

- 89 简单来说，这是对人口子集条件下的 ATE。
- 90 它回答了以下问题：对处理组中个体的治疗预期因果效应是什么？
- 91 它回答了以下问题：治疗对特定单元结果的预期因果效应是什么？很明显，ITE 在这个例子中可能不容易或不可能估计，因为我们只能对每根精确的梁测试一次。一种变通方法是估计每根相同梁之间期望值的差异，以获得 ITE 的接近估计。
- 92 PO 方法扩展以涵盖广泛的应用和条件（例如，倾向得分、混杂性、缺失数据、匹配等）。请随意查阅 [19]。
- 93 或者，心智地图！
- 94 我们也将利用领域知识！
- 95 请记住，干预等同于设置 X = x，而不是观察 X = x。前者涉及因果关系（如果 RC 板的厚度增加到 200 mm，其耐火性是多少？），后者涉及预测（给定同一板的宽度为 200 mm，其耐火性是多少？）。

## 表 8.4 用于因果推断的算法和 ML 包（每个包的完整描述和所包含的算法可在其原始来源中找到）。

| 包 | 详细信息 |
|---|---|
| DoWhy | [https://microsoft.github.io/dowhy] 一个用于从观测或实验数据中推断因果关系的 Python 包。 |
| CausalGAM | [https://cran.r-project.org/web/packages/CausalGAM/index.html] 一个 R 包，通过广义加性模型实现平均处理效应的估计器和标准回归估计器。 |
| FLAME | [https://cran.r-project.org/web/packages/FLAME/index.html] 一个用于因果推断的 R 包。 |
| CausalNex | [https://causalnex.readthedocs.io/en/latest] 一个用于因果推理（发现和推断）的 Python 包。 |
| Causal ML | [https://causalml.readthedocs.io/en/latest/about.html] 一个用于因果推断的 Python 包。 |

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_471_0.png)

图 8.9 所提方法的流程图 [35, 36]。

## 8.5 示例

本节描述了本作品中将重点介绍的五个示例。前三个围绕因果发现（通过基于约束和基于得分的算法），最后两个涵盖因果推断。

### 8.5.1 因果发现

前两个示例利用 Tetrad 的图形界面来发现已知和未知 DGP 的可能因果结构。第三个示例通过 Python 展示。

### **示例 1** 发现已知 DGP 的因果结构 (Tetrad)

第一个案例研究很简单，希望验证我们对已知 DGP 的领域知识。感兴趣的 DGP 涉及 W 形钢梁的弯矩承载力 M。根据公式 8.1，弯矩承载力通过将塑性模量 Z 与钢材的屈服强度 fy 相乘来估计。换言之，M 是 Z 和 fy 的效应，因此将 M 标记为碰撞器，Z → M ← fy。

为执行此分析，根据美国钢结构学会（AISC）手册[98] [37]提供的所有 W 形结构钢截面创建了一个数据库。该数据库包含每根梁的两个独立特征（Z 和 fy）以及 M（作为因变量）。简单来说，由于我们知道 DGP（即，公式 8.1），我将每种钢截面的塑性模量乘以两种钢材等级（A992 和 A36）。

编译后的数据库用于我通过 Tetrad[99] 软件进行的分析，并使用两种算法（即，PC 算法，一种基于约束的算法，以及 FGES 算法，一种基于得分的算法）。下面展示了使用 Tetrad[100] 的过程和本分析的结果。可以看到，生成的 DAG 与我们的领域知识相似，并且与 PC 和 FGES 算法的结果一致。这既是预料之中的，也令人欣慰。如所述，只有基于得分的算法具备计算开发的 DAG 的适配度得分的能力（基于默认的贝叶斯信息准则 (BIC)[101] 估计为 –19,236.4）。

以下是复制我分析的步骤：

### 步骤 1：选择数据

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_472_0.png)

- 98 如果您不知道，AISC 提供许多有用的（且免费）工具，例如包含所有标准钢截面的 Excel 电子表格。和往常一样，我将在我的网站上提供所用的数据。
- 99 下载 Tetrad 的链接在表 8.2 中提供。让我花一分钟时间也感谢因果发现中心，该中心由 U54HG008540 资助项目支持。
- 100 版本 6.9.0 [最后修改：2021 年 5 月 3 日星期一 20:18:40 EDT]，可在 [71] 中找到。
- 101 BIC 分数计算为卡方统计量 - 自由度 × log(样本量)。BIC 值越低，表示模型越好。

