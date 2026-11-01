
### Action-utility learning
我们在[第16章](#Chapter16-00.xhtml)中引入了动作-效用函数。动作-效用学习最常见的形式是Q学习，其中智能体学习一个`Q-function`，或质量函数，`Q(s, a)`，表示如果在状态 s 中采取动作 a，则从状态 s 开始的奖励总和。给定一个`Q-function`，智能体可以通过找到具有最高`Q-value`的动作来选择在 s 中做什么。

*动作-效用强化学习* *Q学习* *Q函数*

### Policy search
智能体学习一个策略`π(s)`，它直接将状态映射到策略搜索动作。在[第2章](#Chapter02-00.xhtml)的术语中，这是一个反射智能体。

*策略搜索*

我们从[第23.2节](#Chapter23-02.xhtml#sec23-2)开始介绍被动强化学习，其中智能体的策略是固定的，任务是学习状态（或状态-动作对）的效用；这也可能涉及学习环境的模型。（对马尔可夫决策过程的理解，如[第16章](#Chapter16-00.xhtml)所述，对本节至关重要。）[第23.3节](#Chapter23-03.xhtml#sec23-3)涵盖主动强化学习，其中智能体还必须弄清楚该做什么。主要问题是探索：智能体必须尽可能多地体验其环境，以便学习如何在其中行为。[第23.4节](#Chapter23-04.xhtml#sec23-4)讨论了智能体如何使用归纳学习（包括深度学习方法）从其经验中更快地学习。我们还讨论了其他可以帮助扩展RL以解决实际问题的方法，包括提供中间伪奖励来指导学习者以及将行为组织成动作层次结构。[第23.5节](#Chapter23-05.xhtml#sec23-5)涵盖策略搜索的方法。在[第23.6节](#Chapter23-06.xhtml#sec23-6)中，我们探索学徒学习：使用演示而不是奖励信号训练学习智能体。最后，[第23.7节](#Chapter23-07.xhtml#sec23-7)报告了强化学习的应用。

*被动强化学习* *主动强化学习*

## 23.2 Passive Reinforcement Learning
我们从一个简单的完全可观察环境开始，该环境具有少量动作和状态，其中智能体已经有一个固定的策略`π(s)`来确定其动作。智能体试图学习效用函数`Uπ(s)`——如果从状态 s 开始执行策略`π`，则期望的总折扣奖励。我们称之为被动学习智能体。

*被动学习智能体*

被动学习任务类似于策略评估任务，是[第16.2.2节](#Chapter16-02.xhtml#sec16-2-2)中描述的策略迭代算法的一部分。不同之处在于，被动学习智能体不知道转移模型`P(s' | s,a)`，它指定了在执行动作 a 后从状态 s 到达状态 s' 的概率；它也不知道奖励函数`R(s,a,s')`，它指定了每次转移的奖励。

我们将以[第16章](#Chapter16-00.xhtml)中介绍的4 × 3世界作为示例。[图23.1](#Chapter23-02.xhtml#fig23-1)显示了该世界的最佳策略及其对应的效用。智能体使用其策略`π`在环境中执行一系列试验。在每次试验中，智能体从状态(1,1)开始，并经历一系列状态转移，直到到达其中一个终止状态，(4,2)或(4,3)。它的感知同时提供当前状态和到达该状态时刚刚发生的转移所获得的奖励。典型的试验可能如下所示：

×![](images/Fig-329.jpg)

图23.1(a) 对于随机环境中`R(s, a, s')` = –0.04 的非终止状态之间的转移的最优策略。因为在状态(3,1)中 Left 和 Up 都是最优的，所以有两个策略。我们之前在[图16.2.(b)](#Chapter16-01.xhtml#fig16-2)中看到过。给定策略`π`时，4 × 3 世界中各状态的效用。

*试验*

$\\begin{array}{l} {(1,1)\\underset{Up}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(1,2)\\underset{Up}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(1,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(1,2)\\underset{Up}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(1,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(2,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(3,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(4,3)} \\\\ {(1,1)\\underset{Up}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(1,2)\\underset{Up}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(1,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(2,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(3,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(3,2)\\underset{Up}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(3,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(4,3)} \\\\ {(1,1)\\underset{Up}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(1,2)\\underset{Up}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(1,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(2,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(3,3)\\underset{Right}{\\overset{\\mathbf{\\text{-}}\\mathbf{.04}}{\\rightarrow}}(3,2)\\underset{Up}{\\overset{\\mathbf{\\text{-}}1}{\\rightarrow}}(4,2)} \\\\ \\end{array}$

请注意，每个转移都标注了所采取的动作和在下一个状态收到的奖励。目标是利用有关奖励的信息来学习与每个非终止状态 s 相关的期望效用`Uπ(s)`。效用定义为如果遵循策略`π`所获得的（折扣）奖励的期望总和。如[公式(16.2)](#Chapter16-01.xhtml#eq16-2)中[第557页](#Chapter16-01.xhtml#page_557)所述，我们写

$\\begin{matrix} {U^{\\pi}(s) = E\\left\\lbrack {\\sum\\limits\_{t = 0}^{\\infty}{\\gamma^{t}R\\text{(}S\_{t},\\pi\\,(S\_{t}),\\, S\_{t + 1}\\text{)}}} \\right\\rbrack,} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(23.1)} \\\\ \\end{matrix}$

其中`R(St, π(St), St+1)`是在状态`St`中采取动作`π(St)`并到达状态`St+1`时收到的奖励。请注意，`St`是一个随机变量，表示执行策略`π`时在时间 t 到达的状态，从状态`S0` = s 开始。我们将在所有方程中包含折扣因子`γ`，但对于4 × 3世界，我们将设置`γ` = 1，这意味着不进行折扣。

### 23.2.1 Direct utility estimation
直接效用估计的思想是，状态的效用定义为从该状态开始的期望总奖励（称为期望奖励到终点），并且每次试验为每个访问的状态提供该量的一个样本。例如，前面显示的三个试验中的第一个为状态(1,1)提供了0.76的总奖励样本，为(1,2)提供了0.80和0.88两个样本，为(1,3)提供了0.84和0.92两个样本，依此类推。因此，在每个序列结束时，算法计算每个状态的观察到的奖励到终点，并相应地更新该状态的估计效用，只需在表中为每个状态保持一个运行平均值。在无限多次试验的极限下，样本平均值将收敛于[公式(23.1)](#Chapter23-02.xhtml#eq23-1)中的真实期望。

*直接效用估计 奖励到终点*
