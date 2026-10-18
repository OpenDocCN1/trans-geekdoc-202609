

# mdp: `MarkovDecisionProcess[S, A]`

这表示抽象马尔可夫决策过程的接口。我们要提醒的是，这个接口不提供任何访问转移概率或奖励函数的途径。通过此接口可用的核心功能是两个 `@abstractmethods` `step` 和 `actions`。`step` 方法仅允许我们在给定当前状态和动作的情况下访问下一个状态和奖励对的样本（因为它返回一个抽象的 `Distribution` 对象）。`actions` 方法为给定状态提供可执行的动作。

# states: `NTStateDistribution[S]`

这表示非终止状态的任意分布，进而允许我们为每个轨迹体验从该分布中采样起始状态。

# approx\_0: `QValueFunctionApprox[S, A]`

这表示 Q-值函数的初始函数近似（旨在在算法过程中，在每次原子体验后以不可变方式更新）。

# gamma: `float`

这表示在估计 Q-值函数时使用的折扣因子。

# epsilon\_as\_func\_of\_episodes: `Callable[[int], float]`

这表示探索程度（`ϵ`）作为集数的函数。

# max\_episode\_length: `int`

这表示我们将截断轨迹体验并开始新体验的时间步数。正如我们所解释的，TD 控制不需要完整的轨迹体验，因此我们可以在轨迹体验中进行尽可能少或尽可能多的时间步数（`max_episode_length` 为我们提供了这种控制）。

`glie_sarsa` 产生一个生成器（`Iterator`），即在每次原子体验结束时的 Q-值函数估计。`while True` 循环遍历轨迹体验。内部的 `while` 循环遍历时间步——这些步骤中的每一个都涉及以下内容：

* 给定当前状态和动作，我们获取 `next_state` 和 `reward` 对的样本（使用从 `mdp.step(state, action)` 获得的 `Distribution` 的 `sample` 方法）。
* 使用函数 `epsilon_greedy_action` 从 `next_state` 获取 `next_action`，该函数利用当前 Q-值函数估计（由 `q` 引用）推导的 `ϵ`-贪婪策略。
* 根据公式 (12.5) 更新 Q-值函数（使用 `q` 的 `update` 方法：`QValueFunctionApprox[S, A]`）。请注意，这是一个不可变更新，因为我们在每次时间步后生成 Q-值函数估计的 `Iterable`（生成器）。

在 `glie_sarsa` 的代码之前，让我们先了解 `epsilon_greedy_action` 的代码，它返回从 `ϵ`-贪婪策略概率分布中采样的动作，该分布由 Q-值函数估计推导，输入为非终止状态、Q-值函数估计、允许动作的集合以及 `ϵ`。

![](images/comp12_10.jpg)

上述代码位于文件 `rl/td.py` 中。

让我们在我们之前测试 GLIE MC 控制的简单库存 MDP 上测试此方法（我们使用相同的 `si_mdp`：`SimpleInventoryMDPCap` 对象以及之前测试 GLIE MC 控制时设置的相同参数值）。

![](images/comp12_11.jpg)

现在让我们获取 Q-值函数更新 `num_episodes * max_episode_length` 次后的最优 Q-值函数最终估计，并从中提取最优状态-值函数和最优策略的估计（使用我们之前编写的函数 `get_vf_and_policy_from_qvf`）。

![](images/comp12_12.jpg)

这将打印：

![](images/comp12_13.jpg)

我们可以看到，这合理地收敛到真实的值函数（并达到真实的最优策略），如值迭代所产生的（当我们测试 GLIE MC 控制时显示了其结果）。

上述代码位于文件 `rl/chapter11/simple_inventory_mdp_cap.py` 中。另请参见 `rl/chapter11/control_utils.py` 中的辅助函数，您可以使用它们来运行自己的实验和测试 RL 控制算法。

对于表格式 GLIE MC 控制，我们陈述了一个关于收敛到真实最优值函数（因此也是真实最优策略）的理论保证定理。对于表格式 GLIE SARSA 是否存在类似的东西？答案是肯定的，但附加条件是我们根据 Robbins-Monro 计划降低学习率。我们陈述以下定理，不作证明。

现在让我们比较 GLIE MC 控制和 GLIE SARSA。这种比较类似于 [第 11 章](#chapter11.xhtml) 中 [第 11.5.2 节](#chapter11.xhtml#sec11_5_2) 关于它们的偏差、方差和收敛特性的比较。与 GLIE MC 控制的无偏估计相比，GLIE SARSA 对 Q-值函数带有偏差的估计。另一方面，TD 目标 `R[t + 1] + γ ⋅ Q(S[t + 1], A[t + 1]; w)` 的方差远低于 `G[t]`，因为 `G[t]` 依赖于许多随机状态转移和随机奖励（轨迹体验的其余部分），其方差会累积，而 TD 目标仅依赖于下一个随机状态转移 `S[t + 1]` 和下一个随机奖励 `R[t + 1]`。GLIE SARSA 的坏消息（由于其更新中的偏差）是，在使用函数近似时，它并不总是收敛到最优值函数/策略。

如前所述 [第 11 章](#chapter11.xhtml)，由于 MC 和 TD 在数据使用、更新性质和更新频率方面存在显著差异，因此在比较 MC 和 TD 的收敛速度或有限体验数据使用效率时，甚至不清楚如何创建一个公平的竞争环境。MC 和 TD 之间的典型比较是使用恒定学习率进行的，并且已确定在实践中，GLIE SARSA 在恒定学习率下比 GLIE MC 控制学习得更快。我们通过在 `SimpleInventoryMDPCap` 上运行 GLIE MC 控制和 GLIE SARSA，并绘制 Q-值函数估计的均方根误差（RMSE）作为批次集数的函数（即可视化 Q-值函数的 RMSE 随两种算法进展而演变的方式）来说明这一点。这是通过调用位于文件 `rl/chapter11/control_utils.py` 中的函数 `compare_mc_sarsa_ql` 完成的。

[图 12.3](#chapter12.xhtml#fig12_3) 描绘了我们对 GLIE MC 控制和 GLIE SARSA 的实现的收敛情况，学习率恒定为 `α = 0.05`。我们使用从之前创建的同一个 `SimpleInventoryMDPCap` 对象生成的 500 个集数的数据生成了此图（具有相同的折扣因子 `γ = 0.9`）。我们在每批 10 个集数后绘制了 RMSE，因此图中显示的两条曲线都绘制了 50 个 RMSE 数据点。首先，我们清楚地看到 MC 控制的方差显著更大，这从断断续续的 MC 控制 RMSE 进展曲线中可以看出。其次，我们注意到 MC 控制 RMSE 曲线在最初几个集数批次中进展相当快，但在最初几个集数批次后收敛较慢（相对于 SARSA 的进展）。这导致 SARSA 达到相当小的 RMSE 比 MC 控制更快。GLIE SARSA 优于可比的 GLIE MC 控制（恒定学习率）的这种行为在大多数 MDP 控制问题中是典型的。

![图 12.3 GLIE MC 控制和 GLIE SARSA 对 SimpleInventoryMDPCap 的收敛](images/fig12_3.jpg)

[图 12.3](#chapter12.xhtml#b12fig12_3) GLIE MC 控制和 GLIE SARSA 对 SimpleInventoryMDPCap 的收敛

最后，重要的是认识到 MC 控制对初始值函数不太敏感，而 SARSA 对初始值函数更敏感。我们鼓励您尝试此 `SimpleInventoryMDPCap` 示例的初始值函数，并评估它如何影响收敛速度。

