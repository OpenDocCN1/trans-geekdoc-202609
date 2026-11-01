
# 规划演进

20世纪70年代初的规划器通过为每个子目标计算一个子计划，然后以某种顺序将子计划串联起来来分解问题。这种方法由 Sacerdoti（1975）称为线性规划，很快被发现是不完备的。它无法解决一些非常简单的问题，例如由 Allen Brown 在使用 `HACKER` 系统进行实验时发现的 Sussman 异常（参见练习 11.SUSS），found by Allen Brown during experimentation with the `HACKER` system (Sussman, 1975)。完备的规划器必须允许在单个序列中交错来自不同子计划的操作。Warren（1974）的 `WARPLAN` 系统实现了这一点，并展示了逻辑编程语言 `Prolog` 如何生成简洁的程序；`WARPLAN` 只有 100 行代码。

### 线性规划

部分顺序规划主导了接下来 20 年的研究，其中理论工作描述了冲突的检测（Tate, 1975a）和已实现条件的保护（Sussman, 1975），实现包括 `NOAH`（Sacerdoti, 1977）和 `NONLIN`（Tate, 1977）。这导致了形式化模型（Chapman, 1987；McAllester and Rosenblitt, 1991），允许对各种算法和规划问题进行理论分析，并产生了广泛分发的系统 `UCPOP`（Penberthy and Weld, 1992）。

Drew McDermott 怀疑对部分顺序规划的强调挤占了其他技术，而这些技术或许应该在计算机的内存是 Shakey 时代 100 倍的现在重新考虑。他的 `UN POP`（McDermott, 1996）是一种采用 `ignore-delete-list` 启发式的状态空间规划程序。`HSP`，即启发式搜索规划器（Bonet and Geffner, 1999；Haslum, 2006）使状态空间搜索对于大型规划问题变得实用。`FF` 或 Fast Forward 规划器（Hoffmann, 2001；Hoffmann and Nebel, 2001；Hoffmann, 2005）以及 `FAST DOWNWARD` 变体（Helmert, 2006）在 2000 年代赢得了国际规划竞赛。

双向搜索（参见 [第 3.4.5 节](#Chapter03-04.xhtml#sec3-4-5)）也已知会因缺乏启发式而受苦，但通过使用反向搜索在目标周围创建边界，然后细化启发式向前搜索该边界，已取得了一些成功（Torralba et al., 2016）。`SYMBA*` 双向搜索规划器（Torralba et al., 2016）赢得了 2016 年的竞赛。

研究人员转向 `PDDL` 和规划范式，以便他们可以使用领域无关的启发式。Hoffmann（2005）分析了 `ignore-delete-list` 启发式的搜索空间。Edelkamp（2009）和 Haslum et al.（2007）描述了如何为规划启发式构建模式数据库。Felner et al.（2004）展示了使用模式数据库解决滑动拼图问题的令人鼓舞的结果，滑动拼图可以被视为一个规划领域，但 Hoffmann et al.（2006）显示了抽象在经典规划问题中的一些局限性。（Rintanen, 2012）讨论了用于 SAT 求解的规划特定变量选择启发式。

Helmert et al.（2011）描述了 Fast Downward Stone Soup（`FDSS`）系统，这是一种投资组合规划器，正如石汤寓言中所说，它邀请我们尽可能多地投入规划算法。该系统维护一组训练问题，并为每个问题和每个算法记录问题解决方案的运行时间和所得计划成本。然后在面对新问题时，它利用过去的经验来决定尝试哪些算法、时间限制是多少，并采用成本最小的解决方案。`FDSS` 是 2018 年国际规划竞赛的获胜者（Seipp and Röger, 2018）。Seipp et al.（2015）描述了一种机器学习方法，用于在给定新问题时自动学习一个良好的投资组合。Vallati et al.（2015）概述了投资组合规划。算法投资组合在组合搜索问题中的思想可追溯至 Gomes and Selman（2001）。

Sistla and Godefroid（2004）涵盖了对称性约简，而 Godefroid（1990）涵盖了部分排序的启发式。Richter and Helmert（2009）展示了使用首选动作进行前向剪枝的效率提升。

Blum and Furst（1997）凭借其 `Graphplan` 系统使规划领域焕发活力，该系统比当时的部分顺序规划器快数个数量级。Bryce and Kambhampati（2007）概述了规划图。情况演算在规划中的应用由 John McCarthy（1963）引入，并由 Ray Reiter（2001）完善。

Kautz et al.（1996）研究了将动作模式命题化的各种方法，发现最紧凑的形式并不一定导致最快的求解时间。Ernst et al.（1997）进行了系统分析，并开发了一个自动“编译器”，用于从 `PDDL` 问题生成命题表示。结合了 `Graphplan` 和 `SATPLAN` 思想的 `BLACKBOX` 规划器由 Kautz and Selman（1998）开发。基于约束满足的规划器包括 `CPLAN` van Beek and Chen（1999）和 `GP-CSP`（Do and Kambhampati, 2003）。

人们也对将计划表示为二元决策图（`BDD`）感兴趣，二元决策图是硬件验证社区广泛研究的布尔表达式的紧凑数据结构（Clarke and Grumberg, 1987；McMillan, 1993）。有用于证明二元决策图属性的技术，包括其作为规划问题解的属性。Cimatti et al.（1998）提出了一种基于此方法的规划器。其他表示方法也被使用，例如整数规划（Vossen et al., 2001）。

### 二元决策图（BDD）

各种规划方法之间存在一些有趣的比较。Helmert（2001）分析了几类规划问题，并表明诸如 `Graphplan` 和 `SATPLAN` 之类的基于约束的方法最适合 NP-hard 领域，而基于搜索的方法在可行解无需回溯即可找到的领域中表现更好。`Graphplan` 和 `SATPLAN` 在包含许多对象的领域中遇到困难，因为这意味着它们必须创建许多动作。在某些情况下，可以通过动态生成命题化动作，仅在需要时生成，而不是在搜索开始前全部实例化，从而推迟或避免该问题。

### 宏操作

层次规划的第一个机制是 `STRIPS` 程序中用于学习 macrops 的设施——“宏操作符”，由一系列原始步骤组成（Fikes et al., 1972）。`ABSTRIPS` 系统（Sacerdoti, 1974）引入了抽象层次的概念，其中在较高层级的规划被允许忽略动作的低层级前提条件，以便推导出可行计划的总体结构。Austin Tate 的博士论文（1975b）和 Earl Sacerdoti（1977）的工作发展了 `HTN` 规划的基本思想。Erol、Hendler 和 Nau（1994、1996）提出了一个完整的层次分解规划器以及纯 `HTN` 规划器的复杂性结果范围。我们对 `HLAs` 和天使语义的介绍归功于 Marthi et al.（2007、2008）。

### 抽象层次

层次规划的目标之一是以广义计划的形式重用之前的规划经验。基于解释的学习技术已被用作在诸如 `SOAR`（Laird et al., 1986）和 `PRODIGY`（Carbonell et al., 1989）等系统中泛化先前计算的计划的手段。一种替代方法是以原始形式存储先前计算的计划，然后通过类比原始问题来重用它们以解决新的相似问题。这是被称为案例式规划（Carbonell, 1983；Alterman, 1988）的领域所采用的方法。Kambhampati（1994）认为案例式规划应被分析为一种细化规划的形式，并为基于案例的部分顺序规划提供了形式化基础。

### 基于案例的规划
