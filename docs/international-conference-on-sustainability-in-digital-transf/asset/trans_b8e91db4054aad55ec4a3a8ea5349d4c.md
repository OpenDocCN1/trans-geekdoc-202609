
| 3 || \- || \- || 0-82 || \- || \- || 82-91 || 126-135 |
| 4 || \- || \- || \- || \- || 0-34 || 91-101 || 135-145 |
| 5 || 53-70 || \- || \- || \- || 34-71 || 101-112 || 145-156 |
| 7 || \- || \- || \- || 36-60 || \- || 112-122 || 156-166 |
| 6 || \- || 54-90 || 82-121 || \- || 71-78 || 122-131 || 166-175 |
| 8 || \- || \- || \- || \- || 78-140 || 140-145 || 175-180 |
| 9 || \- || \- || 121-180 || \- || \- || 180-186 || 180-186 |

![图 44.1 甘特图](images/fig44_1_C.jpg)

[图 44.1 甘特图](#ch44.xhtml#R_fig44_1)

来自 `BB` 方法，而红色条形显示修改后的进出时间。甘特图使用 `MATLAB R2014a` 生成。

## 结论

`BB` 方法提供了比其他方法更精确的解决方案，用于使用等势机器解决流水车间调度问题（`FSSP`）。然而，本文进一步优化了 `BB` 方法，以获得租赁机器的更实际解决方案。`BB` 方法可以减少完工时间，但有时无法减少机器利用时间。因此，在这些情况下，建议的方法更有帮助。

## 参考文献

1.  [Gupta, D. and Goel, S.](#ch44.xhtml#R_ref44_1) (2020). Nx2 流水车间调度问题，每阶段有并行机器，处理时间与概率相关。Advances in Mathematics: Scientific Journal, 9, 1061–1069.
2.  [Gupta, D. and Goel, S.](#ch44.xhtml#R_ref44_2) (2022). 分支定界技术用于每阶段具有等势机器的两阶段流水车间调度模型。International Journal of Operational Research, 44(4), 462‑472.
3.  [Gupta, D., Goel, S., and Mangla, N.](#ch44.xhtml#R_ref44_3) (2022). 在第一阶段具有 m 台等势机器的两阶段流水车间调度问题中生产调度的优化。International Journal of System Assurance Engineering and Management, 13 (6), 1162–1169.
4.  [Ignall, E., and Schrage, L.](#ch44.xhtml#R_ref44_4) 将分支定界技术应用于某些流水车间调度问题。Operations research 13, 3 (1965), 400–412. 4
5.  [Johnsons, S. M.](#ch44.xhtml#R_ref44_5) 包含设置时间的最佳两阶段和三阶段生产计划。Naval research logistics quarterly 1, 10 61–68.
6.  [Kianpour, P., Gupta, D., Krishnan, K., and Gopalakrishnan, B.](#ch44.xhtml#R_ref44_6) (2023). 基于 Doe 的增强遗传算法用于无关并行机调度以最小化提前/迟到成本。Journal of Optimization in Industrial Engineering, 16(2), 99-114.
7.  [Lomniciki, Z.](#ch44.xhtml#R_ref44_7) (1965). 三机调度问题的精确解的分支定界算法。Journal of the Operational Research Society, 16, (1), 89–100.
8.  [Maggu, P. L., Das, G., and Kumar, R.](#ch44.xhtml#R_ref44_8) 关于 2× n 排序问题中带运输时间的工件块的等效工件。Journal of the operations research society of japan 24, 2 (1981), 136–146.
9.  [Malhotra, K., Gupta, D., Goel, S., and Tripathi, A. K.](#ch44.xhtml#R_ref44_9) (2022). 具有等势并行机器的双目标流水车间调度。Malaysian Journal of Mathematical Sciences, 16(9), 451–470.
10.  [Mansouri, M., Bahmani, Y., and Smadi, H.](#ch44.xhtml#R_ref44_10) (2023). 并行流水车间调度问题的混合方法 †。Computer Sciences & Mathematics Forum, 7(1), 14413.
11.  [Mokotoff, E.](#ch44.xhtml#R_ref44_11) (2001). 并行机调度问题：综述。Asia-Pacific Journal of Operational Research, 18, 2, 193.
12.  [Singh, T. and Gupta, S.](#ch44.xhtml#R_ref44_12) (2008). 包括运输时间的并行机器三阶段流水车间租赁成本最小化。Acta Cinencia Indica, 34, 2, 629–634.

# 45 基于遗传算法的预防性维护下系统可靠性优化

Shakuntla Singla^([^(44)](#fn44))

Department of Mathematics and Humanities, MMEC, Maharishi Markandeshwar (Deemed to be University) Mullana,Ambala, India

DOI: [10.1201/9781003534136-45](https://dx.doi.org/10.1201/9781003534136-45)

## 摘要

任何行业的生产完全依赖于用于制造产品的机械，而机器即系统的可靠性对于提高生产具有至关重要的意义。本文使用 Chapman Kolmogorov 前向方程方法，在预防性维护的影响下，对串联系统的可靠性参数如系统平均失效时间和可用运行时间进行了计算。研究对象是一个由两个串联子系统组成的系统，其中一个具有预防性维护设施。注意到了故障率和修复率方面的变化。遗传算法（`GA`）被应用于在最佳参数值下获得 `ATTF` 和可用性的最优值。结果表明，良好的维护在提高系统的整体可用性方面发挥着至关重要的作用。

**关键词：** 平均失效时间（`ATTF`）、故障率、修复率、遗传算法（`GA`）

## 引言

可靠性可以解释为在时间 `t` 时的成功概率，即机器在给定外部条件下在规定时间内成功实现预期目的的概率。设备或系统如果能够在运行过程中正常执行功能而不发生故障或没有障碍，则可认为其更可靠或可靠性较高。任何系统都不能始终表现良好，因为系统持续使用会导致部件的撕裂和磨损。这导致系统部件失效，从而降低可靠性和效率。

本文讨论了由两个单元 `A` 和 `B` 组成的串联系统的可靠性参数，如平均失效时间（`ATTF`）和可用运行时间，其中 `B` 具有直接失效并具备完善维修设施的特性，而单元 `A` 则首先降级到较小程度，导致产量减少。预防性维护的应用可逆转这一情况，使其恢复到完全工作状态 [[1](#ch45.xhtml#ref45_1)]。已使用半马尔可夫过程在冷备用影响下对热电厂引风机可靠性进行了分析。使用 `RPGT` 对造纸工业中擦拭单元的工作效率进行了研究 [[2](#ch45.xhtml#ref45_2), [3](#ch45.xhtml#ref45_3)]。讨论了使用振动监测实验的涡轮发电机维护和可用性 [[4](#ch45.xhtml#ref45_4)]。具有可单独修复部件的多部件系统已在强化学习方法下进行分析，以找到最佳维护措施 [[5](#ch45.xhtml#ref45_5)] 使用两种不同技术提出了在劣化条件下优化系统可靠性的方案 [[6](#ch45.xhtml#ref45_6)]。讨论了两种类型的故障，并检查了两种故障类型的结果并描绘了结果以获得系统可靠性。马尔可夫方法概念已被应用于获得燃煤热电厂不同子系统的可用性和可执行性 [[7](#ch45.xhtml#ref45_7), [8](#ch45.xhtml#ref45_8)]。半马尔可夫过程与再生点技术已被用于理解由主单元与在失效后按需并联排列的两个子单元替代组成的系统的行为。讨论了自然启发算法粒子群优化以优化橡胶厂成本 [[9](#ch45.xhtml#ref45_9)]。

## 模型描述与符号

### 系统描述

两个单元 `A` 和 `B` 以串联方式排列，任何单元的故障都会导致整个系统失效。

![图 45.1 给定系统的状态转换图](images/fig45_1_C.jpg)

图 45.1 给定系统的状态转换图

