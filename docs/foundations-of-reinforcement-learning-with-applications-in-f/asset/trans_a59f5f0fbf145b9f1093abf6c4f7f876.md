

# 值函数与贝尔曼方程

或许我们想在这整本书中强调的最重要概念是 `Value Function` 的概念，以及如何使用 `Planning` 或 `Learning` 算法高效地计算它。给定（固定）策略 `π` 的值函数 `V^π:𝒮→ℝ` 定义为：

$$
\begin{array}{r} {V^{\pi}(s) = \mathbb{E}_{\pi,p}\lbrack G_{t}|S_{t} = s\rbrack\text{~for~all~}s \in \mathcal{S}} \\ \end{array}
$$

理解值函数的直观方式是，它告诉我们从给定状态可以期望获得多少“累积未来奖励”（即 `Return`）。期望下的随机性来自于基于函数 `p`，Agent 在执行策略 `π` 规定的未来动作时将要看到的不确定的未来状态和奖励。评估给定策略的值函数的关键在于，它可以用下一时间步状态的值函数递�地表示。换句话说，

$$
\begin{array}{r} {V^{\pi}(s) = {\sum\limits_{r,s^{\prime}}p}(r,s^{\prime}|s,\pi(s)) \cdot (r + \gamma \cdot V^{\pi}(s^{\prime}))\text{~for~all~}s \in \mathcal{S}} \\ \end{array}
$$

这个方程表明，当 Agent 遵循确定性策略 `π` 时，在给定状态 `s` 下，它采取动作 `a = π(s)`，然后观察到一个随机的下一状态 `s'` 和一个随机奖励 `r`，因此 `V^π(s)` 可以分解为 `r`（即下一步的即时预期奖励）的期望以及未来预期累积奖励的其余部分（后者可以用 `V^π(s')` 的期望来表示）。本章我们不会深入探讨如何求解这个递�式（将在未来章节中详细介绍），但目前重要的是要认识到，这个递�式是评估给定策略的值函数的关键。

然而，评估给定策略的值函数并不是最终目标——它只是实现评估 `Optimal Value Function`（从中我们得到 `Optimal Policy`）这一最终目标的一种手段。最优值函数 `V*:𝒮→ℝ` 定义为：

$$
\begin{array}{r} {V^{*}(s) = \max_{\pi}V^{\pi}(s)\text{~for~all~}s \in \mathcal{S}} \\ \end{array}
$$

好消息是，即使最优值函数也可以递�地表示，如下所示：

$$
\begin{array}{r} {V^{*}(s) = \max_{a}{\sum\limits_{r,s^{\prime}}p}(r,s^{\prime}|s,a) \cdot (r + \gamma \cdot V^{*}(s^{\prime}))\text{~for~all~}s \in \mathcal{S}} \\ \end{array}
$$

此外，我们可以证明存在一个最优策略 `π*`，它对所有 `s ∈ 𝒮` 都能实现 `V*(s)`（证明是构造性的，它给出了一种从函数 `V*` 获得函数 `π*` 的简单方法）。具体来说，这意味着遵循最优策略 `π*` 所得到的值函数与最优值函数 `V*` 相同，即，

$$
\begin{array}{r} {V^{\pi^{*}}(s) = V^{*}(s)\text{~for~all~}s \in \mathcal{S}} \\ \end{array}
$$

这里有一些术语需要熟悉。计算 `V^π(s)`（给定策略的值函数）的问题被称为 `Prediction` 问题（因为这相当于在遵循策略 `π` 时，对从任何给定状态获得的预期回报进行统计估计）。计算最优值函数 `V*`（以及因此的最优策略 `π*`）的问题被称为 `Control` 问题（因为这需要引导策略，以便从任何状态获得最大预期回报）。求解 Prediction 问题通常是求解（更难的）Control 问题的垫脚石。这些针对 `V^π` 和 `V*` 的递�方程被称为（著名的）Bellman Equations（你将在未来章节中多次听到它们）。在连续时间公式中，Bellman Equation 被称为著名的 `Hamilton-Jacobi-Bellman (HJB)` 方程。

基于 Bellman 方程求解预测和控制问题的算法大致分为：

*   Dynamic Programming，一类（在 A.I. 术语中）`Planning` 算法。

*   Reinforcement Learning，一类（在 A.I. 术语中）`Learning` 算法。

现在让我们谈谈 Dynamic Programming 算法与 Reinforcement Learning 算法之间的区别。Dynamic Programming 算法（本书将大量介绍）假设 Agent 知道转移概率 `p`，并且算法利用这些概率的知识（利用 Bellman Equation 高效计算值函数）。Dynamic Programming 算法被认为是 `Planning` 而不是 `Learning`（在 A.I. 术语中），因为算法不需要与 Environment 交互，也不需要从 Environment 传来的（状态，奖励）数据流中学习。相反，凭借转移概率，算法可以推理未来的概率结果并执行必要的优化计算以推断最优策略。因此，它 `plans` 其成功之路，而不是 `learning` 如何成功。

然而，在典型的现实世界情况中，人们并不真正知道转移概率 `p`。这就是 Reinforcement Learning (RL) 的领域。RL 算法与 Environment 交互，从 Environment 接收到的每个新的（状态，奖励）对中学习，并逐步找出最优值函数（使用我们之前概述的“试错”方法）。然而，请注意，Environment 交互可以是 `real` 交互或 `simulated` 交互。在后一种情况下，我们确实有一个转移模型，但模型的结构非常复杂，以至于我们只能访问下一状态和奖励的样本（而不是概率的显式表示）。这被称为 Environment 的 `Sampling Model`。有了这样的环境采样模型（例如，机器人在模拟地形上学习），我们可以使用与在真实环境中交互时（例如，机器人在实际地形上学习）所使用的相同 RL 算法。事实上，大多数 RL 算法在实践中都是从环境的采样模型中学习的。如前所述，RL 本质上是一种“试错”学习方法，因此非常费力且从根本上效率低下。RL 的最新进展来自于更高效的学习最优值函数的方法，以及更好的近似最优值函数的方法。RL 未来的关键挑战之一是找到更好的方法来平衡动作的“探索”和“利用”。无论如何，RL 最近开始取得良好效果的关键原因之一是得到了 Deep Learning 的帮助（通常使用深度神经网络来近似值函数和/或近似策略函数）。使用这种深度学习近似的 RL 以现代术语 `Deep RL` 而闻名。

我们相信，当前 A.I. 的前景取决于 Deep RL 的成功。未来十年将令人兴奋，因为 RL 研究可能会产生改进的算法，并且它与 Deep Learning 的结合有望使我们能够解决相当复杂的现实世界随机控制问题。

# 1.9 章节大纲

本书的章节组织为 4 个模块，如下所示：

*   Module I: Processes and Planning Algorithms ([Chapters 3](#chapter3.xhtml) – [6](#chapter6.xhtml))

*   Module II: Modeling Financial Applications ([Chapters 7](#chapter7.xhtml) – [10](#chapter10.xhtml))

*   Module III: Reinforcement Learning Algorithms ([Chapters 11](#chapter11.xhtml) – [14](#chapter14.xhtml))

*   Module IV: Finishing Touches ([Chapters 15](#chapter15.xhtml) – [17](#chapter17.xhtml))

