
这里 `f(S)` 是通过公式 (16.2) 计算的样本 `S` 的适应度。分母汇总了种群中所有样本的适应度函数值——这使得概率和为 1。

一旦选定父母对，通过双点交叉对染色体进行重组。由于每个样本由一对染色体定义，且每个染色体具有不同的含义，我们分别对它们应用重组算子。假设一个父母染色体的长度标记为 `N1`，另一个父母染色体的长度标记为 `N2`。使用均匀分布，算法从闭区间 `[1; N1]` 中选择一对整数，从闭区间 `[1; N2]` 中选择另一对整数。这些整数中的每对都定义了各自染色体中的一个子字符串。然后，交叉算子将其中一个父母染色体的子字符串与另一个父母的子字符串进行交换。注意，由于这些子字符串的大小可能不同，后代的长度可能与父母的长度不同。

### 图示

该原理在图 16.7 中所示，其中染色体 `A` 和 `B` 的中间部分已经交换。注意 `A` 和 `B` 的长度是如何受到影响的。工程师必须决定是否允许交换段的大小为 0 的情况；在另一个极端情况下，一段可以代表整个父母。

变异算子应该防止种群过早退化，并确保种群代表搜索空间的代表性部分。

一种可能性是从新创建的种群中随机选择一个预设百分比的位置，并为每个该位置添加一个为该位置单独生成的随机整数。然后将结果对示例/属性的数量取模。假设原始示例/属性的数量为 100，被选定进行变异包含的位置为 95。如果随机生成的整数是 22，则变异后的值为 `.95 C 22/ mod 100 D 17`。

### 你学到了什么？

为了确保你理解了这一主题，请尝试回答以下问题。如果有困难，请返回前文中对应的部分。

* 通过选择最佳属性和最具代表性的示例可以实现什么？
* 使用两个染色体而不是仅用一个的优点是什么？
* 所选的适应度函数如何反映了属性与示例集与高分类准确率之间的竞争需求？
* 为什么我们使用交换不同长度子串的重组算子？变异是如何实现的？

| ![image](img/chapter_title_corner_decoration_left.png)  ||  || ![image](img/chapter_title_corner_decoration_right.png)  |

| --- | --- | --- |

![image](img/chapter_title_above.png) 

# 16.8 总结与历史说明

![image](img/chapter_title_below.png) 

* 遗传算法受达尔文进化论的启发，是经典人工智能搜索技术的一种流行替代方案。最简单的实现是基于二进制字符串的。
* 该算法对个体种群进行三种基本操作：基于适应度函数的生存、染色体对的重组以及变异。此外，有时也会使用字符串的反转。
* 遗传算法实际应用中经常遇到的问题之一是种群的过早退化。检测此问题的方法是考虑种群中染色体的多样性。一种解决方案是在种群中添加人工创建的染色体。在这里，反转算子也是有效的。
* 遗传算法的替代实现可以使用数字字符串、符号、混合字符串甚至树形结构。
* 本章通过近邻分类器领域的一个简单问题说明了遗传算法的实际用途。

历史说明：将生物演化原理转化为遗传算法形式的想法归于 Holland [37]，尽管其他一些作者稍早就提过类似的观点。其中，或许 Rechenberg [80] 值得被提及，而 Fogel 等人 [29] 则被归功为遗传编程思想的先驱。将遗传算法具体应用于 `k` 分类器选择中的方法来自 Rozsypal 和 Kubat [82]。

| ![image](img/chapter_title_corner_decoration_left.png)  ||  || ![image](img/chapter_title_corner_decoration_right.png)  |

| --- | --- | --- |

![image](img/chapter_title_above.png) 

# 16.9 巩固知识

![image](img/chapter_title_below.png) 

这些练习题旨在巩固所学知识。建议的思维实验将帮助读者从不同的角度看待本章的思想，并引发独立思考。计算机作业将迫使读者注意那些他们可能会忽略的看似微不足道的细节。

––––––––

![image](img/scene_break.png) 

### 练习题

1. 使用纸和笔以类似于表 16.2 的方式对遗传算法进行人工模拟。使用你自行选择的适应度函数、不同的初始种群以及用于单点交叉的随机点。然后用两点交叉重复该练习。

––––––––

![image](img/scene_break.png) 

### 思考一下

1. 解释不同的种群规模如何影响达到良好解所需的代数。详细阐述种群规模与过早退化问题之间的关系。还要讨论适应度函数形状的影响。
2. 哪些类型的搜索问题遗传算法可能比经典搜索算法更高效地解决？
3. 识别适用于遗传算法的具体工程问题（除前文中提到的之外）。建议哪些问题最适合用二进制或数字字符串表示染色体，建议哪些问题更适合树。
4. 列出自然进化与其计算机模型之间的一些差异。推测是否可以从自然中获得更多灵感。你认为与生物演化相比，计算机程序的优势在哪里？

1. 巩固知识 329

### 计算机作业

1. 实现一个在二进制字符串染色体上运行的基础遗传算法。确保你有用于生存函数、幸运轮、重组和变异的独立模块，并且这些模块具有足够的通用性以便于修改。
2. 为第 1 章中的“饼”（pies）和“圆形”（circles）领域创建初始种群，并将它们作为上一个任务开发的程序的输入。注意，在“圆形”领域的情况下，你可能需要对原始程序进行微调，以便处理数字字符串染色体。
3. 对于你选择的领域，实现几种可选的配配策略。运行系统实验以找出哪种策略能最快找到解决方案。速度可以通过评估适应度值的染色体数量来衡量。
4. 对于你选择的领域，尝试使用不同重组算子的替代“组合”，以及不同的重组、变异和反转频率。绘制图表显示搜索速度（如上一个任务所示）如何取决于这些参数的具体设置。

# N 臂老虎机问题

图 17.1 显示了五台老虎机。每台机器的平均回报率都不同，但我们不知道这些平均回报率有多大。如果我们想收益最大化，就需要找出这些平均回报率是多少，然后一直选择最有希望的那台机器。这就是机器学习中所谓的“N 臂老虎机问题”的本质，该名称暗示了老虎机臭名昭著的掠夺金钱倾向。

![image](img/scene_break.png)

![image](img/image696.png)![image](img/image150.png)![image](img/image491.png)![image](img/image426.png)![image](img/image666.png)

图 17.1 通用问题：哪台老虎机提供的平均回报率最高？

在理论上，这应该是很容易的。为什么简单地多尝试每台机器几次，观察回报，然后选择回报最高的那台机器呢？但在现实中，这不是一个好主意。在对最佳机器做出可靠决策之前，可能需要浪费大量的硬币。

## 一种考虑到成本的简单策略

考虑到所产生的成本，务实的工程师会限制实验，并仅根据几次尝试做出初始选择。由于这种早期的决策是不可靠的，她并不会墨守成规。她会偶尔对其他机器进行实验：如果其中某些机器确实更好怎么办？如果是这样，将“之前的最佳”替换为这台新机器是完全合理的。这种策略非常自然。人们不需要成为机器学习科学家也能想出这种方法。

![image](img/image112.png)这正是强化学习范式寻求模拟的行为。在图 17.1 的特定情况下，有五种动作可以选择。上述原理结合了对当前认为最好的机器的**利用（exploitation）**以及对备选方案的**探索（exploration）**。利用占主导地位；探索则少之又几。在最简单的实现中，探索步骤的频率由用户指定的参数 `E` 控制。例如，`E = 0.1` 意味着“最佳”机器（根据之前的试验看起来最好的机器）有 90% 的时间被选中；在剩下的 10% 的情况下，会给随机选择的其他机器一个机会。

## 累计奖励

“最佳动作”被定义为导致最高平均回报的动作。对于每个动作，学习者都会对之前的回报进行计数；这些回报的平均值被视为该动作的质量。例如，让我们用整数 `1`、`2`、`3`、`4` 和 `5` 来表示图 17.1 中的机器。

1. ![image](img/image166.png)动作 `ai` 代表选择第 `i` 台机器。假设最左侧的被选择了三次，这些选择导致了以下回报 `r1 = 0`、`r2 = 9` 和 `r3 = 3`。该特定选择的质量就是 `Q(a1)`。

![image](img/image311.png).r1 + r2 + r3 / 3 = (0 + 9 + 3) / 3 = 4。为了避免必须存储所有之前采取动作的回报，实现该程序的工程师可以利用以下公式，其中 `Qka` 是根据 `k` 个回报计算出的动作 `a` 的质量，而 `rk` 是最新的回报。

![image](img/image605.png)在此，让我们注意到回报可以是负的——与其说是“惩罚”。

## 如何选择回报最高的动作

![image](img/image473.png)表 17.1 E-greedy 强化学习算法

输入：用户指定的参数 `E`，例如 `E = 0.1`；一组动作 `ai` 及其初始值估计值 `Q0i`；
对于每个动作 `ai`，令 `ki = 0`（该动作被采取的次数）；

1. ![image](img/image470.png)从均匀分布 `[0; 1]` 中生成一个随机数 `p`。
2. ![image](img/image381.png)如果 `p < E`，选择值最高的动作（利用）。否则，选择一个随机的动作（探索）。
3. 将上一步选择的动作标记为 `ai`。观察回报 `ri`。
4. ![image](img/image592.png)使用以下公式更新 `ai` 的值：`Qai = Qai + 1/(ki + 1) * (ri - Qai)`
5. 设置 `ki = ki + 1` 并返回 1。

![image](img/scene_break.png)1

![image](img/image229.png)Qai = Qai + (ri - Qai) / (ki + 1) (17.1)

![image](img/scene_break.png)

![image](img/image422.png)k + 1

![image](img/image182.png)多亏于这个公式，每个动作只需要记住 `k` 和 `Qka`——结合最新的回报即可更新 `k+1` 步动作的值。上述过程有时被称为 E-greedy 策略。为了方便用户，表 17.1 用伪代码总结了该算法。

![image](img/image112.png)初始化过程 为了能够使用公式 (17.1)，我们需要一个起点：我们需要为每个动作设置一个初始值。一种优雅的可能性是选择一个远高于任何单次回报的值。例如，如果已知所有回报来自 `[0; 10]`，那么以下值是合理的：`Q0i = 50`。

![image](img/image602.png)在每个时刻，系统以 `(1-E)` 的概率选择值最高的动作，随机打破平。在开始时，所有动作都有相同的概率。假设选择了 `ai`。根据收到的回报，该动作的质量通过公式 (17.1) 被降低。因此，在选择下一个动作时（如果使用利用），必须是另一个动作——其值也会被降低。简而言之，读者可以看到将所有动作值初始化为同一个大数字可以确保在游戏早期尝试所有的动作。

### 你学了什么？

为了让你理解这个主题，请尝试回答以下问题。如果有困难，请回到前面的对应部分。

- 描述在 N 臂老虎机问题中寻找最佳机器时使用的 E-greedy 策略。解释动作及其值的含义。什么是利用和探索？
- 描述维护平均回报的简单机制。该机制如何更新动作的值？
- 为什么本节建议将所有动作的初始值 `Q0i` 设置为典型回报的倍数？

# 17.2 中的状态和动作

老虎机的例子是一个简化，便于解释基本术语。它的主要局限性是只有一个可以选择适当动作的状态。

在现实中，情况要复杂得多。通常有很多状态，每个状态都有几个动作可以选择。可以通过井字游戏来阐明本质。

# 井棋游戏

其原理如图 17.2 所示，这是针对棋盘大小为三乘三格子的简单情况给出的说明。两名玩家交替进行，一人在棋盘上画“叉”，另一人画“圈”。目标是形成三个“叉”或三个“圈”——无论是列、行还是对角线。谁先成功谁获胜。如果在左侧所示的情况下，轮到画“叉”的玩家操作，他可以通过在左下角画一个“叉”来获胜。相反，如果是对手的操作，对手将通过在那里画一个“圈”来阻止这一点。

## 状态与动作

每个棋盘位置代表一个状态。在每个状态下，玩家需要选择一个具体的动作。因此，在左侧所示的状态下，有三个空格，因此有三个动作可供选择（一个是获胜的动作）。整个情况可以用一个查找表来表示，其中每个状态-动作对都有一个特定的值，`Q(s; a)`。

![image](img/image330.png)

![image](img/image043.png)![image](img/image709.png)

––––––––

![image](img/scene_break.png)

图 17.2 在井棋中，两名玩家交替放置他们的“叉”和“圈”。获胜者是获得直线三连（垂直、水平或对角线）的人。

基于这些值，$\epsilon$-greedy 策略决定了在特定状态下应该采取哪种动作。动作产生一个奖励 `r`，然后该奖励将通过公式 (17.1) 更新状态-动作对的值。

实现学习场景最典型的方法是让程序与自己进行长系列游戏，从对动作的随机性选择开始（仅基于 `Q(s; a)` 的初始值），然后逐渐改进它们，直到达到非常高的竞技水平。

主要问题在于如何确定具体动作的奖励。原则上，可以考虑三种替代方案。

![image](img/image602.png)

### 回归化表述

这可能是处理奖励分配问题最简单的方法。进行一整场游戏。如果赢了，学习智能体在整个游戏中遇到的所有状态-动作对都被处理为收到了奖励 1。如果输了，它们被处理为都收到了奖励 1。

这种方法的主要缺点是它忽略了这样一种情况：游戏中采取的所有动作对最终结果的贡献并不是平等的。玩家输掉可能是因为是因为在一系列精彩动作之后的单次失误。在这种情况下，惩罚良好的动作当然是不公平的，甚至是不实际的。反之亦如此：弱的动作实际上可能获得奖励，仅仅是因为由于对手意之外的失误而最终赢得了游戏。然而，人们认为，从长远来看，这些微小的“不公”会被抵消，因为在大多数时候，胜者的动作都是好的。

回归化表述的优点在于其简单性。

### 连续化表述

上述回归化表述中存在的问题（即它可能会因为单次失误而惩罚一系列良好的动作）在假设我们知道如何确定每个动作后的奖励的情况下，可以被消除。这确实是可能的；即使在无法做到此点的领域，至少也可以进行估计。然而，大多数时候，在游戏结束之前尝试确定给定动作的奖励是推测性的——因此具有误导性。这就是为什么这种方法很少使用的原因。

### 折中方案：折扣回报

这本质上是一种改进的回归化表述，其根据游戏的长度来确定奖励。例如，获胜所需的时间越长，奖励就越高。

## 你学了什么？

为了确保你理解这一主题，请尝试回答以下问题。如果你有困难，请回到前文中对应的部分。

- 描述强化学习中 `SARSA` 方法的原理。这个名字是从哪里来的？

表 17.2 SARSA 算法——使用 `E-greedy` 策略和任务的阶段性表述

![image](img/image731.png)

输入：用户指定的参数 `E`；`ϵ`；`γ`

所有动作值对的初始化值，`Q0(si, aj)`；对于每个状态-动作对 `si, aj`，初始化 `kij(D) = 0`；

1. 选择一个初始状态 `s`。
2. 使用表 17.1 中的 `E-greedy` 策略选择动作 `a`。
3. 执行动作 `a`。这产生了一个新状态 `s⁰` 和奖励 `r`。
4. ![image](img/image335.png)在状态 `s⁰` 下，使用 `E-greedy` 策略选择动作 `a⁰`。更新 `Q(s, a) = Q(s, a) + ϵ[r + γQ(s⁰, a⁰) - Q(s, a)]`。
5. ![image](img/image530.png)令 `s=s⁰` 且 `a=a⁰`。如果 `s` 是终止状态，跳转到 1 开始一个新阶段；否则跳转到 3。

![image](img/image731.png)

![image](img/chapter_title_above.png)

| --- | --- | --- |
![image](img/chapter_title_above.png)

# 17.4 总结与历史说明

![image](img/chapter_title_below.png)

- 与前面章节中的分类问题不同，强化学习假设智能体通过对其试图控制的系统进行直接实验来学习。
- 在 `多臂老虎机`（N-armed bandit）的高度简化的形式中，智能体寻求识别最有前景的动作——提供最高平均回报的动作。最简单的实际实现依赖于所谓的 `E-greedy` 策略。
- 更现实的任务实现假设存在一个状态集。对于每个状态，智能体需要从一组备动作中进行选择。这种选择可以通过 `E-greedy` 策略实现，该策略依赖于状态动作对的质量 `Q(s, a)`。
- 将奖励分配给状态-动作对的问题可以通过其阶段性表述、连续表述或带折扣的阶段性表述来解决。
- 在强化学习较高级的方法中，本章简要提到了 `SARSA` 方法。

### 历史说明
Bellman [3] 提供了“老虎机”问题最早的系统性处理之一，而他反过来是在更早的工作基础上构建的。重要的是，同一位作者后来开发了动态规划原理，这可以被认为是强化学习的直接先驱 [4]。强化学习的基本原理的发展可能归功于 Sutton [7]。

| --- | --- | --- |
![image](img/chapter_title_above.png)

# 17.5 巩固你的知识

![image](img/chapter_title_below.png)

练习是为了巩固所学知识。建议的思维实验将帮助读者以不同的角度看待本章的观点，并引发独立思考。计算机作业将迫使读者注意他们原本可能会忽略的看似微不足道的细节。

### 练习
计算图 17.2 中跳井棋示例中状态-动作对的数量。

### 思考一下
1. 该策略的 `E-greedy` 有什么局限性？你能建议如何克服它们吗？强化学习的原理已经使用一些简单的玩具玩具领域进行了解释。你能想出一个有趣的现实世界应用吗？主要的困难将在于如何将具体问题转化为强化学习的形式。解决图 17.2 所示的简单版跳井棋可能需要多少个阶段（episodes）？

2. 编写一个计算机程序来实现 17.1 节描述的 `多臂老虎机`。考虑图 17.4 所示的迷宫问题。任务是找到从起点 `S` 到目标 `G` 的最短路径。计算机可以利用强化学习原理，通过多次训练来学习这条最短路径。建议用于捕捉该游戏状态和动作的数据结构。编写一个计算机程序，在处理此任务时依赖阶段性表述和 `E-greedy` 策略。

![image](img/image407.png)图 17.4 智能体从 `S` 开始；任务是找到到 `G` 的最短路径

| --- | --- | --- |
![image](img/chapter_title_above.png)

# 参考文献

1. Ash, T. (1989). 反向传播神经网络。人工智能、认知与研究期刊, 1, 365–375。
2. Ball, G. & Hall, D. (1965). 一种新型数据分析方法。斯坦福大学技术报告。
1. Bellman, R. (1956). 实验的原理。Sankhya, 16, 221–229。
2. Bellman, R. (1957). 动态规划。普林顿出版社。
3. Chow, C. K. (1957). 使用决策函数的字符识别系统。IRE Transactions on Computers, EC-6, 247–254.
4. Cover, T. M. (1965). 线性不等式系统的几何与统计特性及其模式识别中的应用。IEEE Transactions on Electronic Computers, EC-14, 326–334.
5. Cover, T. M. (1968). 最近邻域规则估计。IEEE Transactions on Information Theory, IT-14, 50–55.
6. Breiman, L. (1996). 袋法（Bagging）。Machine Learning, 24, 123–140.
7. Breiman, L. (2001). 随机森林。Machine Learning, 45, 5–32.
8. Breiman, L., Friedman, J., Olshen, R., & Stone, C. (1984). 分类与回归树。Belmont: Wadsworth International Group.
9. Broomhead, D. S. & Lowe, D. (1988). 多变量函数插值与自适应网络。Complex Systems, 2, 321–355.
10. Bryson, A. E. & Ho, Y.-C. (1969). 应用最优控制。New York: Blaisdell.
11. Clare, A. & King, R. D. (2001). 多标签表型数据的知识发现。在第五届欧洲数据挖掘与知识发现原理会议论文集中，PKDD’01，德国弗兰克福（页 42–53）。
12. Clark, P. & Niblett, R. (1989). CN2 归纳算法。Machine Learning, 3, 261–284.
13. Blumer, W., Ehrenfeucht, A., Haussler, D., & Warmuth, M. (1989). 可学习性与 Vapnik-Chervonenkis 维。Journal of the ACM, 36, 929–965.
14. Boutell, M., Luo, J., Shen, X., & Brown, C. (2004). 多标签场景识别。Pattern Recognition, 37, 1757–1771.
15. ing, B. (2004). 人工智能启蒙。Sudbury: Jones and Bartlett.

1. Cover, T. M. & Hart, P. E. (1967). 最近邻域模式分类. IEEE Transactions on Information Theory, IT-13, 21–27.
2. Dasarathy, B. V. (1991). 最近邻类分类技术. Los Alomitos: IEEE Computer Society Press.
3. Dietterich, T. (1998). 用于比较监督分类学习算法的近似统计检验. Neural Computation, 10, 1895–1923.
4. Dudani, S. A. (1975). 距离加权的 k-最近邻类规则. IEEE Transactions on Systems, Man, and Cybernetics, SMC-6, 325–327.
5. Fayyad, U. M. & Irani, K. B. (1992). 论决策树生成中连续值属性的处理. Machine Learning, 8, 87–102.
6. Fisher, R. A. (1936). 分类学问题中多次测量的使用. Annals of Eugenics, 7, 111–132.
7. Fisher, D. (1987). 通过增量式概念聚类获取知识. Machine Learning, 2, 139–172.
8. Fix, E. & Hodges, J. L. (1951). 判别分析，非参数判别. USAF 航空医学学院, Randolph Field, TX, Project 21-49-004, Report 4, Contract AF41(128)-3.
9. Freund, Y. & Schapire, R. E. (1996). 新型提升算法的实验. In Machine Learning: Proceedings of the Thirteenth International Conference, Bari (pp. 148–156).
10. Fogel, L. J., Owens, A. J., & Walsh, M. J. (1966). 模拟演化的人工智能. New York: Wiley.
11. Friedman, J. H., Bentley, J. L., & Finkel, R. A. (1977). 在对数期望时间内寻找最佳匹配的算法. ACM Transactions on Mathematical Software, 3(3), 209–226.
12. Gennari, J. H., Langley, P., & Fisher, D. (1990). 增量概念形成模型. Artificial Intelligence, 40, 11–61.
13. Godbole, S. & Sarawagi, S. (2004). 多标签分类的判别方法. In H. Dai, R. Srikant, & C. Zhang (Eds.), Lecture Notes in Artificial Intelligence (Vol. 3056, pp. 22–30). Berlin/Heidelberg: Springer.
14. Good, I. J. (1965). 概率的估计：关于现代贝叶斯方法的论文. Cambridge: MIT.
15. Gordon, D. F. & desJardin, M. (1995). 机器学习中偏的评估与选择. Machine Learning, 20, 5–22.
16. Hart, P. E. (1968). 压缩最近邻规则. IEEE Transactions on Information Theory, IT-14, 515–516.
17. Hellman, M. E. (1970). 带有拒绝选项的最近邻分类规则. IEEE Transactions on Systems Science and Cybernetics, 6, 179–185.
18. Holland, J. H. (1975). 自然与人工系统中的适应. Ann Arbor: University of Michigan Press.
19. Holte, R. C. (1993). 极简单的分类规则在大多数常用数据库上表现良好. Machine Learning, 11, 63–90.
20. Hunt, E. B., Marin, J., & Stone, P. J. (1966). 归纳实验. New York: Academic Press.
21. Katz, A. J., Gately, M. T., & Collins, D. R. (1990). 无鲁棒特征的鲁棒分类器. Neural Computation, 2, 472–479.
22. Kearns, M. J. & Vazirani, U. V. (1994). 计算学习理论导论. Cambridge, MA: MIT Press.
23. Kodratoff, Y. (1988). 机器学习导论. London: Pitman.
24. Kodratoff, Y. & Michalski, R. S. (1990). 机器学习：人工智能方法（第 3 卷）. San Mateo: Morgan Kaufmann.
25. Kohavi, R. (1997). 特征选择的包装器. Artificial Intelligence, 97(1–2), 273–324.
26. Kohonen, T. (1982). 拓扑结构正确特征图的自组织形成. Biological Cybernetics, 43, 59–69.
27. Kohonen, T. (1990). 自组织映射. Proceedings of the IEEE, 78(9), 1464–1480.
28. Koller, D. & Sahami, M. (1997). 使用少量单词对文档进行分层分类. In Proceedings of the 14th International conference on machine learning, `ICML'07`, San Francisco (pp. 170–178).
29. Kononenko, I., Bratko, I., & Kukar, M. (1998). 机器学习在医学诊断的应用. In Michalski, I., Bratko, & Kubat (Eds.), Machine learning and data mining: Methods and applications. Chichester: Wiley.
30. Kubat, M. (1989). 时变知识库中的浮点近似. Pattern Recognition, 10, 223–227.
31. Kubat, M., & Flotinger D. (1994). 基于 AI 的自动分类. Biological Cybernetics, 79, 443–448.
32. Kubat, M., Holte, R., & Matwin, S. (1997). 学习负样本. In Proceedings of 17th annual SIGIR conference on research and development, `SIGIR'94`, Dublin (pp. 3–12).
33. Kubat, M., Koprinska, I., & Pfurtschell, G. (1998). 海面图像中的溢油检测. Machine Learning, 30, 195–215.
34. Kubat, M., Koprinska, I., & Pfurtschell, G. (1998). 学习信号. In Michalski, I., Bratko, & Kubat (Eds.), Machine learning and data mining: Methods and applications. Chichester: Wiley.
35. Littlestone, N. (1987). 快速学习无关属性：一种线性阈值算法. Machine Learning, 2, 285–318.
36. Lewis, D. D. & Gale, W. A. (1994). 分类器的序列算法. In Proceedings of 17th annual SIGIR conference on research and development, `SIGIR'94`, Dublin (pp. 3–12).
37. Louizou, G. & Maybank, S. J. (1987). 最近邻与贝叶斯误差. IEEE Transactions on Pattern Analysis and Machine Intelligence, 9, 254–262.
38. McCallum, A. (1999). 用 EM 训练的多标签文本分类. In Proceedings of the workshop on text learning, `AAAI'99` (pp. 1–7).
39. McQueen, J. (1967). 多变量观测分类与分析的方法. In Proceedings of 5th Berkeley symposium on mathematical statistics and probability, Berkeley (pp. 281–297).
40. Michalski, R. S. (1969). 通覆盖问题的准最小解. In Proceedings of 5th international symposium on information processing, `FCIP'69`, Bled (Vol. A3, pp. 125–128).
41. Michalski, R. S. & Tecu, G. (1994). 机器学习：多策略方法. Palo Alto: Morgan Kaufmann.
42. Michalski, R. S., Carbonell, J. G., & Mitchell, T. M. (1983). 机器学习：人工智能方法. Palo Alto: Tioga Publishing Company.
43. Michalski, R. S., Carbonell, J. G., & Mitchell, T. M. (1986). 机器学习：人工智能方法（第 2 卷）. Palo Alto: Tioga Publishing Company.
44. Michalski, R., Bratko, I., & Kubat, M. (1998). 机器学习与数据挖掘：方法与应用. New York: Wiley.
45. Michell, M. (1998). 遗传算法导论. Cambridge, MA: MIT.
46. Mill, J. S. (1865). 逻辑体系. London: Longmans.
47. Minsky, M. & Papert, S. (1969). 感知机. Cambridge, MA: MIT.
48. Mitchell, T. M. (1982). 泛化即搜索. Artificial Intelligence, 18, 203–226.
49. Mitchell, T. M. (1997). 机器学习. New York: McGraw-Hill.
50. Mori, S., Suen, C. Y., & Yamamoto, K. (1992). OCR 研发的历史性. Proceedings of IEEE, 80, 1029–1058.
51. Muggleton, S. & Buntine, W. (1988). 通过反转解析进行一阶谓的机器发明. In Proceedings of 5th international machine learning conference, Ann Arbor, Michigan (pp. 339–352).
52. Murty, M. N. & Krishna, G. (1980). 一种计算高效的数据聚类技术. Pattern Recognition, 12, 153–158.
53. Neyman, J. & Pearson E. S. (1928). 用于统计推断的某些检验标准的使用与解释. Biometrica, 20A, 175–240.
54. Ogden, C. K. & Richards, I. A. (1923). 意义的意义（第 8 版，1946 年）. New York: Harcourt, Brace, and World.
55. Parzen E. (1962). 概率密度函数与模式的估计. Annals of Mathematical Statistics, 33, 1065–1076.

# 参考文献

4. Quinlan, J. R. (1979). 从大规模样本集中归纳出规则。在 D. Michie (编) 微电子时代的专家系统。爱丁堡：爱丁堡大学。
1. Quinlan, J. R. (1986). 决策树的归纳。Machine Learning, 1, 81–106.
2. Quinlan, R. (1990). 从关系中学习逻辑定义。Machine Learning, 5, 239–266.
1. Quinlan, J. R. (1993). `C4.5`: 用于机器学习的程序。圣马特奥：Morgan Kaufmann。
2. Read, J., Pfahringer, B., Holmes, G., & Frank, E. (2011). 多标签分类分类器链。Machine Learning, 85, 333–359.
3. Rechenberg, I. (1973). 进化策略：根据生物进化原理优化技术系统。斯图加特：Holzmann。
4. Rosenblatt, M. (1958). 感知机：大脑信息存储和组织的概率模型。Psychological Review, 65, 386–408.
5. Roskopf, A. & Kubat, M. (2001). 使用遗传算法减少最近邻分类器的规模并选择相关属性。在第 18 次国际机器学习会议上。威廉斯顿 (449–456)。
6. Rumelhart, D. E. & McClelland, J. L. (1986). 并行分布式处理。剑桥：MIT Press。
7. Russell, S. & Norvig, P. (2003). 人工智能：现代方法（第 2 版）。英格尔利夫：Prentice Hall。
8. Schapire, R. E. (1990). 弱学习器的强度。Machine Learning, 5, 190–227.
9. Shawe-Taylor, J., Anthony, M., & Biggs, N. (1993). 用 Vapnik-Chervonenkis 维数限制样本量。Discrete Applied Mathematics, 42(1), 65–73.
10. Sutton, R. S. (1984). 强化学习中的时间信用分配。马萨诸塞大学博士论文。
11. Thrun, S. & Mitchell, T. M. (1995). 终身学习。Robotics and Autonomous Systems, 15, 24–46.
12. Tukey, I. (1976). CNN 的两种改进。IEEE Transactions on Systems, Man and Communications, 6, 769–772.
13. Turney, P. D. (1993). 上上下文特征的鲁棒分类。在第六次人工智能与专家系统应用会议上。爱丁堡 (268–276)。
14. Valiant, L. (1984). 可学习理论。Communications of the ACM, 27, 1134–1142.
15. Vapnik, V. N. (1992). 基于数据的依赖估计。纽约：Springer。
16. Vapnik, V. N. (1995). 统计学习理论本质。纽约：Springer。
17. Vapnik, V. N. & Chervonenkis, A. Y. (1971). 事件频率到概率的均匀收敛。Theory of Probability and its Applications, 16, 264–280.
18. Werbos, P. (1974). 超回归：预测与分析的新工具。哈佛大学博士论文。
19. Whewell, W. (1858). 科学思想史。伦敦。
20. Widmer, G. & Kubat, M. (1996). 概念漂下的学习。Machine Learning, 23, 69–101.
1. Widrow, B. & Hoff, M. E. (1960). 自适应开关电路。IRE WESCON 记录，纽约 (96–104)。
2. Wolpert, D. (1992). 叠加泛化。Neural Networks, 5, 241–259.
3. Wolpert, D. (1996). 学习算法缺乏区别。Neural Computation, 8, 1341–1390.
4. Zhang, M.-L. & Zhou, Z.-H. (2007). `ML-KNN`: 多标签学习的惰学习方法。Pattern Recognition, 40, 203–248.

# 索引

### A
- 应用，151, 167
- 属性，连续，30, 38, 45–47, 84, 122, 145
- 离散，8, 22, 44, 137
- 无关，13, 49, 74, 75, 118, 144, 156
- 选择，204, 205, 324
- 未知，202

### B
- 反向传播，98
- 偏置，67, 143, 191, 193

### C
- 聚类
- 分层聚合，283
- 簇间距离，275, 284
- k-means，277, 281
- 归一化，278
- 原理，273
- 上下文，191, 199, 201

### D
- 决策树
- 作为分类器，113
- 转换为规则，130
- 归纳，117
- 数值，122
- 距离，275

### G
- 高斯函数在贝叶斯中，33
- 在 RBF 网络中，107

### I
- 不平衡类，78, 194, 215, 225, 255
- 可解释性，114, 126

### L
- 线性分类器
- 在 RBF 网络中，108
- 感知机，69
- WINNOW，73
- 线性序类，207

### M
- 多标签分类-二元相关性，254
- 类别聚合，263
- 分类器链，256
- 最近邻分类器，253
- 神经网络，252
- 堆叠，258

### N
- 最近邻
- 危险样本，57
- 加权，55
- 神经网络反向传播，97
- MLP 架构，100
- MLP 作为分类器，91
- RBF 网络，106
- 噪声
- 在属性中，14, 45
- 在类别标签中，14
- 归一化，51, 278, 279

### P
- 性能评价标准
- 错误率，15
- 宏平均，265
- 微平均，266
- 精率，215
- 召回率，215
- 敏感性，220
- 特异性，220
- 多项式分类器，79
- 备选搜索运算符，305
- 非正式定义，303
- 递归规则，303
- 概率，199
- 决策树，127, 128, 184, 192
- 规则，130, 131

### R
- 回归，207
- 强化 sarsa，337
- 状态与动作，334
- 规则归纳谓词，303
- 递归，303
- 规则集，130, 298
- 顺序覆盖，300

### S
- 搜索
- 遗传，309
- 爬山算法，1, 5, 6, 8, 97, 309
- 相似性，43
- 统计评估，241
- 间隔或错误，239
- I 型错误，243
- 线性支持支持机，84
- 基于 RBF 的，108

### T
- 随时间类，200

### V
- 投票
- 简单，174, 176
- 加权多数决，179, 181
