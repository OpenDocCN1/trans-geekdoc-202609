

| 安全自我效能感 (SLEF) || 0.3194 || 0.3367 || 0.1922 || 0.3148 || **0.8315** |

| *注*：AVE 的平方根显示在对角线上。 |

虽然已经提出了几种统计补救措施来解决共同方法偏差 (CMV)，但文献中对于如何检测和控制它尚无共识。根据 [Chin, Thatcher, Wright, and Steel (2013, pp. 1)](#ch6.xhtml#ref6_17) 的说法，“迄今为止，方法论专家尚未就检测和控制 CMV 的最佳实践达成一致”。尽管如此，为了检验本研究中潜在的 CMV，我们遵循了 [Liu, Chan, Yang, and Niu (2018)](#ch6.xhtml#ref6_56) 使用的方法，即：(1) 检查潜在变量之间的相关矩阵；(2) 进行 Harman 单因素检验。如 [表 6.7](#ch6.xhtml#table6_7) 所示，最大相关性为 0.4048（`GSOR` 和 `GSCB` 的相关性），远低于表明存在 CMV 的建议极高相关性 0.90。由于潜在变量之间存在低相关性，CMV 的影响微乎其微。我们的 Harman 单因素检验结果显示，单一因素解释了提取的总方差的 20.24%，远低于 50%，表明 CMV 在我们的研究中不是一个问题。

### 步骤 4：回归分析

在本步骤中，我们使用多元线性回归对 Donalds 和 Osei-Bryson 模型中指定的因果链接（即假设）的有效性进行统计分析。这种方法适合我们的研究，因为它非常适合评估多个预测变量和目标变量之间的关系，以及评估包含分类变量和区间变量的模型。读者应注意，该模型中的所有变量均为区间量表，除两个分类变量外，即 `DominantOrientation` (`DomOR`) 和 `DominantDecisionStyle` (`DomDS`)。二元分类变量 `DomOR` (`Idea vs. Action`) 可直接用于回归分析中。按照回归分析中处理非二元分类变量的传统做法，这些变量通过多个二元数字虚拟变量间接表示，如果某个潜在预测变量的任何相关虚拟变量对给定目标变量有统计学显著影响，则认为该潜在预测变量对给定目标变量有统计学显著影响。回顾一下，个人的决策风格要么是 `analytic`（分析型）、`conceptual`（概念型）、`behavioural`（行为型）或 `directive`（指令型）（参见 [图 6.1](#ch6.xhtml#fig6_1)）。因此，如果个人的主导决策风格被识别为 `analytic`，在我们的回归分析中，该变量被赋值为 1，而所有其他决策风格变量（即 `conceptual`、`behavioural` 和 `directive`）被赋值为 0。[表 6.8](#ch6.xhtml#table6_8) 显示了 `DomDS` 变量所有可能取值组合的虚拟变量。然而，应注意对于给定的回归方程，四个二元决策风格变量中只能使用三个进行回归分析，这也是我们实际所做的。[表 6.8](#ch6.xhtml#table6_8) 并不意味着需要所有四个二元变量；相反，[表 6.8](#ch6.xhtml#table6_8) 提供了一种解释回归分析结果的方法，因为它提供了每个二元决策风格变量每个取值含义的信息。

#### 表 6.8 代表主导决策风格的虚拟变量

| **虚拟变量** || **水平** || **主导决策风格** |
| --- | --- | --- |
| `DomDS_A` || 1 || `Analytical`（分析型） |
| || 0 || `Conceptual`（概念型）或 `Behavioural`（行为型）或 `Directive`（指令型） |
| `DomDS_B` || 1 || `Behavioural`（行为型） |
| || 0 || `Analytical`（分析型）或 `Conceptual`（概念型）或 `Directive`（指令型） |
| `DomDS_C` || 1 || `Conceptual`（概念型） |
| || 0 || `Analytical`（分析型）或 `Behavioural`（行为型）或 `Directive`（指令型） |
| `DomDS_D` || 1 || `Directive`（指令型） |
| || 0 || `Analytical`（分析型）或 `Conceptual`（概念型）或 `Behavioural`（行为型） |

Donalds 和 Osei-Bryson 模型包含四个变量（即 `SecuritySelf-Efficacy` (`SLEF`)、`GeneralSecurityOrientation` (`GSOR`)、`GeneralSecurityComplianceBehaviour` (`GSCB`)、`PasswordSecurityComplianceBehaviour` (`PWCB`)`），每个变量都是一个或多个因果链接的目标变量。对于这些目标变量中的每一个，我们都使用单独的回归模型来确定相关因果链接的存在是否得到统计分析的支持。[图 6.4](#ch6.xhtml#fig6_4) 显示了评估的各种回归模型。

![图 6.4 多元回归模型](images/fig6_4_B.jpg)

[图 6.4 多元回归模型](#ch6.xhtml#R_fig6_4)

我们使用 `SAS Enterprise Miner` 软件进行统计分析。[表 6.9](#ch6.xhtml#table6_9) 显示了在 5% 显著性水平下得到支持的因果链接的统计分析结果。值得注意的是，[表 6.9](#ch6.xhtml#table6_9) 中的“水平”列仅适用于分类（二元和多值）变量（`DomOR` 和 `DomDS`）以及前因变量为分类变量的那些因果链接；其他情况显示为 N/A。

#### 表 6.9 假设检验结果

| **回归模型** || **标签** || **路径** || **水平** || **系数** || **p值** || **结果** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || H1 || `DomOR` || ➔ || `SLEF` || `Action` || –0.17148 || 0.021661[\*](#ch6.xhtml#table-fn6_9_1) || 支持 |
| 2 || H2 || `DomDS_D` || ➔ || `GSOR` || 0 || –0.23644 || 0.0004256[\*](#ch6.xhtml#table-fn6_9_1) || 支持 |
| 3 || H3 || `DomDS_B` || ➔ || `GSCB` || 0 || –0.28071 || 0.034210[\*](#ch6.xhtml#table-fn6_9_1) || 支持 |
| || H4 || `GSOR` || ➔ || `GSCB` || N/A || 0.38907 || 0.000000[\*](#ch6.xhtml#table-fn6_9_1) || 支持 |
| || H6 || `GSAW` || ➔ || `GSCB` || N/A || 0.14446 || 0.012527[\*](#ch6.xhtml#table-fn6_9_1) || 支持 |
| || H8 || `SLEF` || ➔ || `GSCB` || N/A || 0.266947 || 0.000153[\*](#ch6.xhtml#table-fn6_9_1) || 支持 |
| 4 || H5 || `GSOR` || ➔ || `PWCB` || N/A || 0.20225 || 0.00398244[\*](#ch6.xhtml#table-fn6_9_1) || 支持 |
| || H7 || `GSAW` || ➔ || `PWCB` || N/A || 0.16623 || 0.00410887[\*](#ch6.xhtml#table-fn6_9_1) || 支持 |
| || H9 || `SLEF` || ➔ || `PWCB` || N/A || 0.23847 || 0.00073900[\*](#ch6.xhtml#table-fn6_9_1) || 支持 |

具体而言，结果显示从 `DominantOrientation (DomOR)` 到 `SecuritySelf-Efficacy (SLEF)` 的路径（即回归模型 1）在统计学上显著。回归模型 1 的结果表明，假设两个人唯一的区别在于他们的主导取向，那么具有 `Idea`（创意型）取向的个体将比具有 `Action`（行动型）取向的个体拥有更高水平的 `SecuritySelf-Efficacy`。这是因为当 `DominantOrientation` 为 `Action` 时，其系数为负（即 -0.17148），而当 `DominantOrientation` 为 `Idea` 时为 0。

读者可能会观察到，对于每个涉及 `DominantDecisionStyle (DomDS)` 作为潜在预测变量的回归模型（即回归模型 2 和 3），至少有一个相关的二元虚拟变量是相关目标变量的统计学显著预测因子，因此 `DominantDecisionStyle` 可被视为相关目标变量的统计学显著预测因子。

更具体地说，模型 2 的结果表明，假设两个人唯一的区别在于他们的主导决策风格，那么具有 `Directive`（指令型）主导决策风格的个体将比具有其他主导决策风格的个体拥有更高水平的 `GeneralSecurityOrientation (GSOR)`。这是因为当 `DominantDecisionStyle_Directive` 为 0 时，其系数为负。

