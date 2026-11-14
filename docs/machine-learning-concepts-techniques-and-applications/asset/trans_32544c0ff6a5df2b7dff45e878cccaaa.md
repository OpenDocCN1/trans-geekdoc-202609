
参数 `α`、`γ` 和初始条件 `Q(S[0], a[0])` 极大地影响 `Q` 值并决定结果。`SARSA` 隐式假设一个低（无限）初始值，也称为“乐观初始条件”。首次采取行动时，奖励被用来设定 `Q` 的值。这在固定确定性奖励的情况下允许即时学习。

### 11.4.3.3 深度 Q 网络

Google DeepMind 在 2014 年为“深度强化学习”或“深度 Q 学习”申请了专利，这是 `Q-learning` 在深度学习中的一种应用，能够以人类专家水平玩 Atari 2600 游戏。

深度神经网络被认为是处理 `Q-tables` 中高维连续状态的最佳解决方案。深度神经网络可以自动提取复杂特征（将在后续章节中详细讨论）。

`Deep Q-Network` 是一种结合了深度学习和强化学习的算法。这种集成方法帮助 `DQN` 直接从高维原始数据中学习策略。事实上，`DQN` 通过将 `convolutional neural network (CNN)` 与 `Q-Learning` 相结合，扩大了强化学习的范围及其应用领域。`CNN` 的输入是原始视觉数据（作为状态），其输出是对应于每个动作的价值评估（`Q value`）。

在 `deep Q-learning` 中，`Q-value` 函数使用神经网络进行近似。作为输入，提供状态；作为输出，计算所有可行动作的 `Q-values`。`Q-learning` 和 `deep Q-learning` 之间的对比在随后得到完美体现。神经网络将输入状态映射到 `Q-value–action` 对，而不是将 `state–action` 对映射到 `Q` ([Figure 11.8](#ch11.xhtml#fig11_8))。

![图 11.8 Q-learning 与 Deep Q-learning 对比。](images/fig11_8_B.jpg)

[图 11.8 Q-learning 与 Deep Q-learning 对比。](#ch11.xhtml#R_fig11_8)

在 `deep Q-Learning` 中，神经网络将输入状态映射到 (`action`, `Q-value`) 对。深度 Q 网络学习算法涉及的步骤总结如下 ([Figure 11.9](#ch11.xhtml#fig11_9))：

1. 初始化主神经网络和次要神经网络。
2. 使用 `epsilon–greedy` 探索策略，选择一个行动方案。
3. 使用 `Bellman equation`，修订网络的权重。

**步骤 1：** 初始化网络。`Deep Q-learning` 在学习过程中使用两个神经网络，即 `main network` 和 `target network`。这两个网络具有相同的架构但使用不同的权重。`main network` 的权重每 `N` 步复制一次到 `target network`。使用两个网络可提高稳定性和学习效率。两个神经网络的设计如下 ([Figure 11.9](#ch11.xhtml#fig11_9))：

1. **Target or prediction network（目标或预测网络）：** `target network` 的输入是当前状态，即第一个样本元素 `s`。每个动作的输出是 `q`。每个输出的 `q` 值决定智能体的下一个状态。该网络的参数始终可更新。
2. **Q-network or evaluation network（Q 网络或评估网络）：** 样本序列中的下一个状态 `s′` 是 `main network` 的输入。输出每个动作的 `Q` 值 (`Q[next]`)。`Bellman equation` 确定状态 `s` 下动作 `a` 的目标 `Q` 值 (`q_target = r + * max(q_next)`)。`evaluation network` 的输出通过 `Bellman equation` 传递，目标 `q` 值被用作 `prediction network` 的标签。

在 `DQL` 中，智能体记住其所有过去的交互，然后采取由 `Q-output` 决定的下一步。状态 `S[t]` 处的 `Q-value` 由 `Q-network` 获得。同时 `target network`（神经网络）计算状态 `S[t+1]`（下一状态）的 `Q-value`。这是为了实现稳定训练。通过将其作为训练数据复制到 `Q-network` 的每次迭代 `Q-value` 中，阻止了 `Q-value` 计数的任何突然增加。该过程如 [Figure 11.10](#ch11.xhtml#fig11_10) 所示。

**步骤 2：** 使用 `epsilon–greedy` 探索策略选择行动方案。在 `epsilon–greedy` 探索策略中，智能体以概率 `epsilon` 选择随机动作，然后以概率 1 – `epsilon` 利用最佳已知动作。两个网络的输出动作都映射到输入状态。模型的预测 `Q-value` 真正由这些输出动作表示。在这种情况下，该状态下最佳已知动作是具有最大预测 `Q-value` 的动作。

**步骤 3：** 使用 `Bellman equation` 修订网络权重。智能体执行选定的动作，并根据 `Bellman equation` 更新 `main` 和 `target networks`。`deep Q-learning` 使用 `Replay`，即保存和回放游戏状态（如状态、动作、奖励和下一状态）的行为，随后由强化学习算法用于学习。为了提高智能体的性能水平，`deep Q-learning` 使用 `experience replay` 以小批量方式学习。`Experience replay` 实际上是存储先前的经验以供学习。

![图 11.9 深度 Q 学习步骤。](images/fig11_9_B.jpg)

[图 11.9 深度 Q 学习步骤。](#ch11.xhtml#R_fig11_9)

![图 11.10 DQL 过程。](images/fig11_10_B.jpg)

[图 11.10 DQL 过程。](#ch11.xhtml#R_fig11_10)

这种学习方法将确保避免神经网络将看到的偏斜数据集分布。重要的是，智能体不需要在每一步之后进行训练。神经网络使用 `Bellman equation` 通过新的时序差分目标进行更新。`deep Q-learning` 的主要目标是使用神经网络复制时序差分目标操作，而不是使用 `Q-table`。以下公式说明了如何使用 `target network` 而不是 `main network` 来计算时序差分目标（公式 11.16）。

```
(11.16)
Q[target] = (R[t] + λ^(*) max[a] Q(S[t+1], a))
```

`target network` 使用 `experience replay` 进行训练，`Q-network` 使用它进行 `Q-value` 计算。损失根据前面的公式，由目标 `Q-value` 和预测 `Q-value` 的平方差计算得出。这仅在将参数复制到 `target network` 之前，针对 `Q-network` 的训练执行。`DQN` 损失期望可以使用 `stochastic gradient descent` 来最小化。如果仅使用最后一个转移，则使用 `Q-learning`。

## 11.5 异步强化学习

`Online RL` 算法依赖于当前时刻的预期数据。这意味着奖励取决于对数据采取的动作，并且这些算法的更改是增量发生的。研究人员试图通过引入称为 `experience replay` 的阶段来改进此过程。然而，这对内存和处理能力等计算资源产生负面影响，以及其他困难，如较旧的 `RL` 策略数据。

为了解决这个问题，开发了 `asynchronous`（独立、并行计算机进程）解决方案。在这种情况下，该方法使多个智能体能够行动，而不依赖于现实生活中的多个实例。它还促进了输入和输出数据的关联。在前文提到的论文中，`asynchronous` 技术被应用于常见的 `RL` 算法，如 `SARSA`（state–action–reward–state–action）、`n-step Q-learning` 和 `actor–critic` 方法。此外，通过证明它们能在常规多核 `CPU` 上运行，而不是通常在深度学习环境中使用的强大 `GPU` 上运行，展示了 `asynchronous` 方法的计算优势。

### 11.5.1 异步强化学习过程
