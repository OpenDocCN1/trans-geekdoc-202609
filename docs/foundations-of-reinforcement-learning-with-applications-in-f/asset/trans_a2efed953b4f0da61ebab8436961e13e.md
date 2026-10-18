

所以 AI Agent 有 `T` 次动作选择机会（按顺序进行），每次选择仅基于该时间步之前观察到的奖励（具体而言，AI Agent 并不知道概率分布 `ℛ^(*a*)`）。任何旨在最大化预期累积奖励的选择策略，既存在探索时浪费时间在“ dud”上的风险，也存在利用时错失未开发的“gem”的风险。

可以立即观察到，环境没有 `State` 的概念。当 AI Agent 选择一个 arm 时，环境只是从该 arm 的概率分布中采样。然而，AI Agent 可能会维护历史（已采取的动作和获得的奖励）的相关特征作为其 `State`，这将有助于 AI Agent 做出 arm-选择（动作）决策。arm-选择动作随后基于代理 `State` 的 `Policy` 函数。因此，代理的 arm-选择策略基本上就是这个 `Policy`。因此，即使 MAB 不被表述为 MDP，代理也可以将其建模为 MDP，并使用合适的规划或学习算法来求解。然而，许多 MAB 算法并不采用这种正式的 MDP 方法。相反，它们依赖于不旨在 `optimize` 的启发式方法——它们只是努力争取 `good` 的累积奖励（期望意义下）。请注意，即使在简单的启发式算法中，`A[t]` 也是一个随机变量，仅仅因为它是过去（随机）奖励的函数。

### 15.1.3 Regret

`Regret` 的概念在为 MAB 设计算法时非常基础。在本节中，我们阐明这一想法。

我们将 `Action Value` `Q(a)` 定义为动作 `a` 的（未知）平均奖励，即，

```
$$\begin{array}{r} {Q(a) = \mathbb{E}\lbrack r|a\rbrack} \\ \end{array}$$  
```

我们将 `Optimal Value V^*` 和 `Optimal Action a^*`（请注意可能存在多个最优动作）定义为：

```
$$\begin{array}{r} {V^{\*} = \max\_{a \in \mathcal{A}}Q(a) = Q(a^{\*})} \\ \end{array}$$  
```

我们将 `Regret l[t]` 定义为单个时间步 `t` 的机会损失，如下所示：

```
$$\begin{array}{r} {l\_{t} = \mathbb{E}\lbrack V^{\*} - Q(A\_{t})\rbrack} \\ \end{array}$$  
```

我们将 `Total Regret L[T]` 定义为总的机会损失，如下所示：

```
$$\begin{array}{r} {L\_{T} = {\sum\limits\_{t = 1}^{T}l\_{t}} = {\sum\limits\_{t = 1}^{T}\mathbb{E}}\lbrack V^{\*} - Q(A\_{t})\rbrack} \\ \end{array}$$  
```

最大化 `Expected Cumulative Rewards` 等同于最小化 `Total Regret`。

### 15.1.4 Counts and Gaps

设 `N[t](a)` 为前 `t` 个时间步中动作 `a` 被选择的（随机）次数。我们将给定动作选择策略下的 `𝔼[N[t](a)]` 称为动作 `a` 在前 `t` 步上的 `Count`，记为 `Count[t](a)`。我们将动作 `a` 与最优动作 `a^*` 之间的值差称为 `a` 的 `Gap`，记为 `Δ[a]`，即，

```
$$\begin{array}{r} {\Delta\_{a} = V^{\*} - Q(a)} \\ \end{array}$$  
```

我们将 Total Regret 定义为（动作上的）`Count`s 和 `Gap`s 的乘积之和，如下所示：

```
$$\begin{array}{rlll} L\_{T} & {= {\sum\limits\_{t = 1}^{T}\mathbb{E}}\lbrack V^{\*} - Q(A\_{t})\rbrack} & {= {\sum\limits\_{a \in \mathcal{A}}\mathbb{E}}\lbrack N\_{T}(a)\rbrack \cdot (V^{\*} - Q(a))} & {= {\sum\limits\_{a \in \mathcal{A}}C}ount\_{T}(a) \cdot \Delta\_{a}} \\ \end{array}$$  
```

一个好的算法确保大 `Gap`s 对应小 `Count`s。然而，核心挑战在于 `we don't know the Gaps`。

在本章中，我们将（在代码中）实现几种不同的 MAB 问题算法。因此，让我们投资于一个抽象基类，其接口可以由我们开发的每个算法实现。这个抽象基类 `MABBase` 的代码如下所示。其构造函数接受 3 个输入：

*   `arm_distributions` 它是 `Distribution[float]`s 的 Sequence，每个 arm 对应一个。

*   `time_steps` 它表示时间步数 `T`

*   `num_episodes` 它表示我们可以运行算法的 episode 数量（每个 episode 有 `T` 个时间步），以生成指标来评估算法在期望意义下（跨 episode 平均）的表现。

我们想要编写的每个算法只需实现 `@abstractmethod get_episode_rewards_actions`，其旨在返回算法在 `T` 个时间步内采取的动作的一维 ndarray（针对单个 episode），以及对这些动作产生的奖励的一维 ndarray。

![](images/comp15_1.jpg)

我们为抽象基类 `MABBase` 编写以下不言自明的方法：

![](images/comp15_2.jpg)

上述代码位于文件 `rl/chapter14/mab_base.py` 中。

接下来，我们介绍一些简单的启发式算法。

## 15.2 Simple Algorithms

我们考虑对每个 `a ∈ 𝒜` 估计 Q-Value `Q̂[t](a)` 的算法，作为真实 Q-Value `Q(a)` 的近似。`Q̂[t]` 中的下标 `t` 指的是这是在 `t` 个时间步后的估计，考虑了直到 `t` 个时间步为止的所有可用信息。

估计 `Q̂[t](a)` 的一种自然方法是 `rewards-averaging`，即，

```
$$\begin{array}{r} {{\hat{Q}}\_{t}(a) = \frac{1}{N\_{t}(a)}{\sum\limits\_{s = 1}^{t}R\_{s}} \cdot \mathbb{I}\_{A\_{s} = a}} \\ \end{array}$$  
```

其中 `𝕀` 指示指示函数。

### 15.2.1 Greedy and ϵ-Greedy

首先，考虑一个 `never` 探索（即 `always` 利用）的算法。这被称为 `Greedy Algorithm`，它选择估计值最高的动作，即，

```
$$\begin{array}{r} {A\_{t} = \text{arg}\,\text{max}\_{a \in \mathcal{A}}{\hat{Q}}\_{t - 1}(a)} \\ \end{array}$$  
```

与往常一样，arg max 平局通过任意规则打破以优先处理动作。我们在 [第 12 章](#chapter12.xhtml) 中指出，此类算法可能会永远锁定在次优动作上（次优 `a` 是 `Δ[a] > 0` 的动作）。这导致某些次优 `a` 的 `Count[T](a)` 是 `T` 的线性函数，这意味着 Total Regret 是 `T` 的线性函数（我们将其称为 `Linear Total Regret`）。

现在让我们考虑 `ϵ`-greedy 算法，它永远在探索。在每个时间步 `t`：

*   以概率 `1 − ϵ`，选择动作等于 arg max`[a ∈ 𝒜]Q̂[t − 1](a)`

*   以概率 `ϵ`，从 `𝒜` 中随机选择一个动作（均匀分布）

`ϵ` 的常数值确保最小遗憾与平均差距成正比，即，

```
$$\begin{array}{r} {l\_{t} \geq \frac{\epsilon}{|\\mathcal{A}|}{\sum\limits\_{a \in \mathcal{A}}\Delta\_{a}}} \\ \end{array}$$  
```

因此，`ϵ`-Greedy 算法也具有 Linear Total Regret。

### 15.2.2 Optimistic Initialization

接下来，我们考虑一个简单且实用的想法：对所有 `a ∈ 𝒜` 将 `Q̂[0](a)` 初始化为高值，并通过增量平均更新 `Q̂[t]`。从所有 `a ∈ 𝒜` 的 `N[0](a) ≥ 0` 开始，每个时间步 `t` 的更新如下：

```
$$\begin{array}{r} {N\_{t}(A\_{t}) = N\_{t - 1}(A\_{t}) + 1} \\ \end{array}$$  
```

```
$$\begin{array}{r} {{\hat{Q}}\_{t}(A\_{t}) = {\hat{Q}}\_{t - 1}(A\_{t}) + \frac{R\_{t} - {\hat{Q}}\_{t - 1}(A\_{t})}{N\_{t}(A\_{t})}} \\ \end{array}$$  
```

