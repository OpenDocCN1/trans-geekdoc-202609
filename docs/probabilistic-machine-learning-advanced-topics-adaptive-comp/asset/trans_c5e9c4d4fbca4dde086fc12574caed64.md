

![](img/ca72c1626f4850f058a9edc138c1ac73_1163_0.png)

图 34.19: BALD 和 BatchBALD 的直觉。$D_{pool}$ 是一个未标记数据集（从中取出 $\boldsymbol{x}_{1:b}$），$D_{train}$ 是当前训练集，$\boldsymbol{w}$ 是模型参数集，$p(\boldsymbol{y}|\boldsymbol{x}, \boldsymbol{w}, D_{train})$ 是数据点 $\boldsymbol{x}$ 的输出预测。BALD 高估了联合互信息，而 BatchBALD 会考虑变量之间的重叠。各自得分的贡献区域以灰色显示，重复计算的区域以深灰色显示。来源：[KAG19] 的图 3。感谢 Andreas Kirsch 许可使用。

### 34.7.4.3 计算 BatchBALD

计算联合（条件）互信息是不可行的，因此在本节中，我们讨论如何对其进行近似。为简洁起见，我们省略对 $\boldsymbol{x}$ 和 $\mathcal{D}$ 的条件。采用此新记法后，目标变为

$\alpha_{\text{BALD}}(\boldsymbol{x}_{1:B}, p(\boldsymbol{w}|\mathcal{D})) = \mathbb{H}(y_1, \dots, y_B) - \mathbb{E}_{p(\boldsymbol{w})}[\mathbb{H}(y_1, \dots, y_B|\boldsymbol{w})]$ (34.105)

注意，给定 $\boldsymbol{w}$ 时，$y_i$ 条件独立，因此 $\mathbb{H}(y_1, \dots, y_B|\boldsymbol{w}) = \sum_{i=1}^B \mathbb{H}(y_i|\boldsymbol{w})$。故我们可以用蒙特卡罗法近似第二项：

$\mathbb{E}_{p(\boldsymbol{w})}[\mathbb{H}(y_1, \dots, y_B|\boldsymbol{w})] \approx \frac{1}{S} \sum_{i=1}^n \sum_s \mathbb{H}(y_i|\hat{\boldsymbol{w}}_s)$ (34.106)

其中 $\hat{\boldsymbol{w}}_s \sim p(\boldsymbol{w}|\mathcal{D})$。

第一项 $\mathbb{H}(y_1, \dots, y_B)$ 是联合熵，因此更难计算。[KAG19] 提出如下近似方法：对批次中所有可能的标签序列求和，并利用 $p(\boldsymbol{y}) = \mathbb{E}_{p(\boldsymbol{w})}[p(\boldsymbol{y}|\boldsymbol{w})]$ 这一事实：

$\mathbb{H}(\boldsymbol{y}_{1:B}) = \mathbb{E}_{p(\boldsymbol{w})p(\boldsymbol{y}_{1:B}|w)} [-\log p(\boldsymbol{y}_{1:B}|\boldsymbol{w})]$ (34.107)

$\approx \sum_{\hat{\boldsymbol{y}}_{1:B}} \left( \frac{1}{S} \sum_{s=1}^S p(\hat{\boldsymbol{y}}_{1:B}|\hat{\boldsymbol{w}}_s) \right) \log \left( \frac{1}{S} \sum_{s=1}^S p(\hat{\boldsymbol{y}}_{1:B}|\hat{\boldsymbol{w}}_s) \right)$ (34.108)

通过注意到 $p(\boldsymbol{y}_{1:n}|\boldsymbol{w}) = p(y_n|\boldsymbol{w})p(\boldsymbol{y}_{1:n-1}|\boldsymbol{w})$，可以使对所有可能标签序列的求和更加高效，因此在实现贪心算法时，可以递增式地更新概率，复用之前的计算。详情见 [KAG19]。

![](img/ca72c1626f4850f058a9edc138c1ac73_1164_0.png)

图 34.20: 从 MNIST 池中查询的三个批次（每个大小为 4），分别由 (a) BALD 和 (b) BatchBALD 查询。(c) 准确度与查询点数量的图。BALD 可能会选择单个信息性数据点的副本，而 BatchBALD 选择多样化的点，从而提高数据效率。由 batch_bald_mnist.ipynb 生成。

### 34.7.4.4 MNIST 上 BALD 与 BatchBALD 的实验比较

在本节中，我们展示了将 BALD 和 BatchBALD 应用于在标准 MNIST 数据集上训练 CNN 的一些实验结果。我们使用批量大小为 4，并使用 MC dropout（第 17.3.1 节）近似参数后验 p(w|D)。在图 34.20(a) 中，我们看到 BALD 选择彼此非常相似的示例，而在图 34.20(b) 中，我们看到 BatchBALD 选择了更大多样性的点。在图 34.20(c) 中，我们看到 BatchBALD 的学习效率高于 BALD，而 BALD 又高于随机采样数据。

## 35 强化学习

本章与 Lihong Li 合著。

### 35.1 引言

**强化学习**或**RL**是一种学习范式，其中代理人与最初未知的环境顺序交互。交互通常会产生一个**轨迹**或多个轨迹。设 $\tau = (s_0, a_0, r_0, s_1, a_1, r_1, \dots, s_T)$ 为长度 $T$ 的轨迹，由状态序列 $s_t$、动作 $a_t$ 和奖励 $r_t$ 组成。代理人的目标是优化其动作选择策略，使得对于某个给定的**折扣因子** $\gamma \in [0, 1]$，折扣累积奖励 $G_0 \triangleq \sum_{t=0}^{T-1} \gamma^t r_t$ 最大化。

一般来说，$G_0$ 是一个随机变量。我们将专注于最大化其期望，受最大预期效用原则（第 34.1.3 节）的启发，但请注意其他可能性，例如**条件风险价值**，在风险敏感型应用中可能更合适。

我们将专注于马尔可夫决策过程，其中轨迹 $\tau$ 的生成模型可以分解为单步模型。当这些模型参数已知时，求解最优策略称为**规划**（见第 34.6 节）；否则，可以使用 RL 算法从轨迹中获得最优策略，该过程称为**学习**。

在**无模型 RL**中，我们试图在不明确表示和学习模型的情况下学习策略，而是直接从轨迹中学习。在**基于模型 RL**中，我们首先从轨迹中学习一个模型，然后在所学模型上使用规划算法来求解策略。请参见图 35.1 以获取概述。本章将介绍一些关键概念和技术，并将主要遵循 [SB18] 的记法。更多细节可参阅 [Sze10; SB18; Ber19; Aga+21a; Mey22; Aga+22] 等教科书，以及 [WO12; Aru+17; FL+18; Li18] 等综述。

### 35.1.1 方法概述

在本节中，我们简要概述当 MDP 模型未知时如何计算最优策略。相反，代理人与环境交互并从观察到的轨迹中学习。这是 RL 的核心焦点。我们将在后续章节中深入探讨，但首先提供此路线图。

我们可以根据代理人表示和学习的量对 RL 方法进行分类：值函数、策略和模型；或者根据动作如何选择：在策略上（动作必须由代理人的当前策略选择）和非策略上。表 35.1 列出了几个具有代表性的示例。后续章节将给出更多细节。我们还将在第 35.5 和第 35.6 节中更深入地讨论非策略学习和基于推理的控制这两个重要主题。

![](img/ca72c1626f4850f058a9edc138c1ac73_1167_0.png)

图 35.1: RL 方法概述。缩写：DQN = 深度 Q 网络（第 35.2.6 节）；MPC = 模型预测控制（第 35.4 节）；HJB = Hamilton-Jacobi-Bellman 方程；TD = 时序差分学习（第 35.2.2 节）。改编自 Steve Brunton 的幻灯片。

| 方法 | 学习的函数 | On/Off | 章节 |
| :--- | :--- | :--- | :--- |
| SARSA | $Q(s, a)$ | On | 第 35.2.4 节 |
| Q-learning | $Q(s, a)$ | Off | 第 35.2.5 节 |
| REINFORCE | $\pi(a|s)$ | On | 第 35.3.2 节 |
| A2C | $\pi(a|s), V(s)$ | On | 第 35.3.3.1 节 |
| TRPO/PPO | $\pi(a|s), A(s, a)$ | On | 第 35.3.4 节 |
| DDPG | $a = \pi(s), Q(s, a)$ | Off | 第 35.3.5 节 |
| Soft actor-critic | $\pi(a|s), Q(s, a)$ | Off | 第 35.6.1 节 |
| Model-based RL | $p(s'|s, a)$ | Off | 第 35.4 节 |

表 35.1: 流行 RL 方法摘要。On/off 指在策略 vs 非在策略方法。

### 35.1.2 基于值的方法

在基于值的方法中，我们通常试图从经验中学习最优 Q-函数，然后使用公式 (34.84) 从中推导策略。通常，使用函数近似器（例如神经网络）Qw 来表示 Q-函数，并进行迭代训练。给定转移 (s, a, r, s')，我们将时序差分（也称为 TD 误差）定义为

$r + \gamma \max_{a'} Q_w(s', a') - Q_w(s, a)$

显然，预期 TD 误差是在 (s, a) 处评估的 Bellman 误差。因此，如果 Qw = Q∗，则根据 Bellman 最优性方程，TD 误差平均为 0。否则，该误差为代理人提供了一个信号，以更改 w 使 Qw(s, a) 更接近 R(s, a) + γ maxa' Qw(s', a')。对 Qw 的更新是基于使用 Qw 计算的目标。这种更新在 RL 中称为自举，不应与统计自助法（第 3.3.2 节）混淆。基于值的方法，如 Q-learning 和 SARSA，在第 35.2 节中讨论。

### 35.1.3 策略搜索方法

在策略搜索中，我们试图直接最大化关于策略参数 $\theta$ 的 $J(\pi_\theta)$。如果 $J(\pi_\theta)$ 关于 $\theta$ 可微，我们可以使用随机梯度上升来优化 $\theta$，这被称为策略梯度，如第 35.3.1 节中所述。基本思想是执行**蒙特卡罗模拟**，其中我们通过与环境交互来采样轨迹，然后使用评分函数估计器（第 6.3.4 节）来估计 $\nabla_\theta J(\pi_\theta)$。在这里，$J(\pi_\theta)$ 定义为期望，其分布取决于 $\theta$，因此在计算梯度时交换 $\nabla$ 和 E 是无效的，可以使用评分函数估计器代替。策略梯度的一个例子是 **REINFORCE**。

策略梯度方法的优点是，对于许多常见的策略类，它们被证明可以收敛到局部最优，而当使用近似时 Q-learning 可能会发散（第 35.5.3 节）。此外，策略梯度方法可以轻松应用于连续动作空间，因为它们不需要计算 $\arg\max_a Q(s, a)$。不幸的是，$\nabla_\theta J(\pi_\theta)$ 的评分函数估计器可能具有很高的方差，因此结果方法可能收敛缓慢。

降低方差的一种方法是学习近似值函数 $V_w(s)$，并在评分函数估计器中将其用作基线。我们可以使用类似于 Q-learning 的值函数方法来学习 $V_w(s)$。或者，我们可以学习优势函数 $A_w(s, a)$ 并使用它来估计梯度。这些策略梯度变体被称为 **演员-评论家** 方法，其中演员指的是策略 $\pi_\theta$，评论家指的是 $V_w$ 或 $A_w$。详情见第 35.3.3 节。

### 35.1.4 基于模型的 RL

基于值的方法（如 Q-learning）和策略搜索方法（如策略梯度）可能非常 **样本效率低**，这意味着它们在找到良好策略之前可能需要多次与环境交互。如果代理人对 MDP 模型有先验知识，那么先学习模型，然后计算模型的最优（或近似最优）策略而无需再与环境交互，可能更具样本效率。

这种方法称为 **基于模型 RL**。第一步是学习 MDP 模型，包括 $p_T(s'|s, a)$ 和 $R(s, a)$ 函数，例如使用 DNN。给定一组 $(s, a, r, s')$ 元组，这样的模型可以使用标准监督学习方法学习。第二步可以

