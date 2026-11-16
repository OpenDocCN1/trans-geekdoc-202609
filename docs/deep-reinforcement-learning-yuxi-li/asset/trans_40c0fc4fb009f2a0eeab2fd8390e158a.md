

关于空间不变性、非马尔可夫特征和目标检测的浅层特征 DQN，以及基本瓦片编码特征。Zahavy et al. (2018) 研究动作消除。

参阅博客 `https://deepmind.com/research/dqn/`。参阅 Sutton and Barto (2018) 第 16 章，了解深度 Q 网络的详细直观描述。参阅 Sutton and Barto (2018) 第 11 章，了解关于致命三元组的更多细节。

## 双 DQN

van Hasselt et al. (2016) 提出双 DQN (D-DQN) 以解决 Q-learning 中的高估问题 (van Hasselt, 2010)。在标准 Q-learning 以及 DQN 中，参数按以下方式更新：

```
$$\theta_{t+1} = \theta_t + \alpha(y_t^Q - Q(s_t, a_t; \theta_t))\nabla_{\theta_t} Q(s_t, a_t; \theta_t), \quad (31)$$
```

其中

```
$$y_t^Q = r_{t+1} + \gamma \max_a Q(s_{t+1}, a; \theta_t), \quad (32)$$
```

这样 max 算子既用于选择动作也用于评估动作时使用相同的值。因此，更有可能选择高估的值，并导致过于乐观的值估计。van Hasselt et al. (2016) 提议根据在线网络评估贪婪策略，但使用目标网络来估计其值。这可以通过对 DQN 算法进行微小更改来实现，将 $y_t^Q$ 替换为

```
$$y_t^{D-DQN} = r_{t+1} + \gamma Q(s_{t+1}, \arg \max_a Q(s_{t+1}, a; \theta_t); \theta_t^-), \quad (33)$$
```

其中 $\theta_t$ 是在线网络的参数，$\theta_t^-$ 是目标网络的参数。供参考，$y_t^Q$ 可写为

```
$$y_t^Q = r_{t+1} + \gamma Q(s_{t+1}, \arg \max_a Q(s_{t+1}, a; \theta_t); \theta_t). \quad (34)$$
```

## 优先经验重放

在 DQN 中，经验转移从重放内存中均匀采样，而不考虑经验的重要性。Schaul et al. (2016) 提议对经验重放进行优先级排序，以便重要的经验转移可以更频繁地重放，从而更高效地学习。经验转移的重要性由 TD 误差衡量。作者设计了一种基于 TD 误差的随机优先级排序，使用重要性采样以避免更新分布中的偏差。作者在 DQN 和 D-DQN 中使用优先经验重放，并提高了它们在 Atari 游戏上的性能。在规划中，优先扫除 (Moore and Atkeson, 1993) 用于根据 TD 误差为状态-动作对设置优先级，以实现更高效的更新。

## 决斗架构

Wang et al. (2016b) 提出决斗网络架构来估计状态值函数 $V(s)$ 及其相关优势函数 $A(s, a)$，然后将它们结合以估计动作值函数 $Q(s, a)$，以比 Q-learning 更快地收敛。在 DQN 中，CNN 层后跟一个全连接 (FC) 层。在决斗架构中，CNN 层后跟两个 FC 层流，分别估计值函数和优势函数；然后将两个流结合以估计动作值函数。通常我们使用以下公式将 $V(s)$ 和 $A(s, a)$ 结合以得到 $Q(s, a)$，

```
$$Q(s, a; \theta, \alpha, \beta) = V(s; \theta, \beta) + (A(s, a; \theta, \alpha) - \max_{a'} A(s, a'; \theta, \alpha)) \quad (35)$$
```

其中 $\alpha$ 和 $\beta$ 是两个 FC 层流的参数。Wang et al. (2016b) 提议将 max 算子替换为平均值，如下所示，以获得更好的稳定性，

```
$$Q(s, a; \theta, \alpha, \beta) = V(s; \theta, \beta) + (A(s, a; \theta, \alpha) - \frac{1}{|\mathcal{A}|} A(s, a'; \theta, \alpha)) \quad (36)$$
```

与 D-DQN 和优先经验重放结合实现的决斗架构改进了之前的工作，即 DQN 和带有优先经验重放的 D-DQN，在 Atari 游戏上。

## Rainbow

Hessel et al. (2018) 提出 Rainbow 以结合 DQN、双 Q-learning、优先重放、决斗网络、多步学习、值分布（下文第 3.2 节中讨论）和噪声网络 (Fortunato et al. (2018)，一种通过向网络权重添加参数噪声的探索技术)，并在 Atari 游戏上取得更好的数据效率和性能。消融研究表明，移除优先级或多步学习中的任何一个都会使大多数游戏的性能变差；然而，各组件的贡献在不同游戏间差异显著。

## Retrace

Munos et al. (2016) 提出 Retrace(\(\lambda\))，这是一种安全高效的基于回报的非策略控制 RL 算法，具有低方差、可安全使用任何行为策略的样本，并且对接近行为策略的样本使用高效。作者分析了收敛到最优动作值 \(Q^*\) 的性质，无需假设无限探索极限中的贪婪性 (GLIE) (Singh et al., 2000) 以及 Watkins’ \(Q(\lambda)\) 的收敛性。作者在 Atari 游戏上进行了实验。Gruslys et al. (2017) 将 Retrace (Munos et al., 2016) 扩展到 actor-critic。

## 3.2 分布值函数

通常，基于值的 RL 方法使用期望值，例如 TD 学习和 Q-learning。然而，期望值通常不能表征一个分布，关于值分布的更多信息可能有益。考虑通勤者示例。在 5 天中的 4 天，她花 15 分钟通勤上班，而在其余 5 天中的 1 天，她花 30 分钟。平均而言，她花 18 分钟上班。然而，通勤时间要么是 15 分钟，要么是 30 分钟，从来不是 18 分钟。

Bellemare et al. (2017) 提出一种值分布方法来解决 RL 问题。值分布是 RL 代理接收到的随机回报的分布。与动作值函数的 Bellman 方程形成对比，并且与之类似，

```
\(Q(s, a) = \mathbb{E}R(s, a) + \gamma \mathbb{E}Q(S', A')\) (37)
```

Bellemare et al. (2017) 建立了分布式 Bellman 方程，

```
\(Z(s, a) = R(s, a) + \gamma Z(S', A')\) (38)
```

这里，$Z$ 是随机回报，其期望是值 $Q$。三个随机变量表征 $Z$ 的分布：奖励 $R$、下一个状态-动作对 $(S', A')$ 和随机回报 $Z(S', A')$。

Bellemare et al. (2017) 证明了值分布的策略评估 Bellman 算子的收缩性，因此，对于固定策略，Bellman 算子在 Wasserstein 度量的最大形式下收缩。值分布的 Bellman 算子 \(\mathcal{T}^\pi : \mathcal{Z} \to \mathcal{Z}$ 定义为，

```
\(\mathcal{T}^\pi Z(s, a) = R(s, a) + \gamma P^\pi Z(s, a)\) (39)
```

其中 \(P^\pi Z(s, a) = Z(S', A')\)，$S' \sim P(\cdot|s, a)$，$A' \sim \pi(\cdot|S')$。作者还表明在控制设置中存在不稳定性，即在值分布的 Bellman 最优方程中。作者认为，值分布近似相比期望近似具有优势，可保持值分布的多模态性，并减轻非平稳策略对学习的影响，并从理论和实证上用 Atari 游戏展示了值分布对 RL 的重要性。

Bellemare et al. (2017) 提出一种用于近似分布式强化学习的分类算法。值分布使用离散分布建模，以一组原子作为支持，\(\{z_i = V_{MIN} + i \Delta z : 0 \le i < N\}$，\(\Delta z = \frac{V_{MAX} - V_{MIN}}{N - 1}$，其中 \(N \in \mathbb{N}, V_{MIN} \in \mathbb{R}, V_{MAX} \in \mathbb{R}\) 是参数。原子概率随后由以下公式给出，

```
\(Z_\theta(s, a) = z_i, \text{ with probability, } p_i(s, a) = \frac{e^{\theta_i(s, a)}}{\sum_j e^{\theta_j(s, a)}}\). (40)
```

为解决 Bellman 更新 \(\mathcal{T} Z_\theta$ 导致的不连续支持问题以及样本转移学习问题，Bellemare et al. (2017) 将样本更新 \(\hat{\mathcal{T}} Z_\theta$ 投影到 \(Z_\theta$ 的支持上，通过为每个原子 \(z_j$ 计算 Bellman 更新 \(\hat{\mathcal{T}}z_j = r + \gamma z_j$，然后将其概率分配给更新 \(\hat{\mathcal{T}}z_j\) 的直接邻居。使用 \(\Phi\hat{\mathcal{T}}Z_\theta(s,a)$ 表示样本 Bellman 算子的操作，遵循分配概率的投影。样本损失函数是 KL 散度的交叉熵项，可以通过梯度下降优化，

\(\mathcal{L}_{s,a}(\theta) = D_{KL}(\hat{\Phi}\mathcal{T}Z_\theta(s,a)||Z_\theta(s,a)).\) (41)

算法 9 给出了分类算法的伪代码，它为单个转移样本计算采样 Bellman 算子，随后跟随分配概率的投影。

```
Input: a transition \(s_t, a_t, r_t, s_{t+1}, \gamma_t\)
Output: cross-entropy loss
// \{z_i\} are atom support, p_i(s,a) are atom probabilities, \(i \in \{0, \dots, N - 1\}\)
\(Q(s_{t+1}, a) = \sum_i z_i p_i(s_{t+1}, a)\)
\(a^* \leftarrow \arg \max_a Q(s_{t+1}, a)\)
\(m_i = 0, i \in \{0, \dots, N - 1\}\)
for \(j \in \{0, \dots, N - 1\}\) do
  //compute the projection of \(\hat{\mathcal{T}}z_j\) onto the support of \{z_i\}
// \([\cdot]^b_a\) bounds the argument in the range of \([a, b]\)
  \(\hat{\mathcal{T}}z_j \leftarrow [r_t + \gamma z_j]^{V_{MAX}}_{V_{MIN}}\)
// \(b_j \in [0, N - 1]\)
  \(b_j \leftarrow (\hat{\mathcal{T}} - V_{MIN}) / \Delta z\)
  \(l \leftarrow \lfloor b_j \rfloor, u \leftarrow \lceil b_j \rceil\)
//distribute probability of \(\hat{\mathcal{T}}z_j\)
  \(m_l \leftarrow m_l + p_j(s_{t+1}, a^*)(u - b_j)\)
  \(m_u \leftarrow m_u + p_j(s_{t+1}, a^*)(b_j - l)\)
end
output \(- \sum_i m_i \log p_i(s_t, a_t)\)

Algorithm 9: Categorical Algorithm, adapted from Bellemare et al. (2017)
```

Morimura et al. (2010a;b) 提出风险敏感算法。Rowland et al. (2018) 分析了 Bellemare et al. (2017) 提出的分类分布式强化学习。Doan et al. (2018) 提出用于分布式 RL 的 GAN Q-learning。Dabney et al. (2018) 提议利用分位回归来处理状态-动作回报分布。

观看 Marc Bellemare 的演讲 https://vimeo.com/235922311。阅读博客 https://deepmind.com/blog/going-beyond-average-reinforcement-learning/，其中包含关于 Atari 游戏实验的视频。

## 3.3 通用值函数

### HORDE

Sutton et al. (2011) 讨论了值函数为预测知识和面向目标（控制）知识提供语义，并提出使用通用值函数来表示知识，其中策略、终止函数、奖励函数和终止奖励函数是参数。作者随后提出 Horde，这是一种可扩展的实时架构，用于从无监督传感器运动交互（即非奖励信号和观测）中并行学习独立子代理的通用值函数。Horde 可以使用通用值函数学习预测许多传感器的值以及最大化这些传感器值的策略，并回答预测性或面向目标的问题。Horde 是非策略的，即在遵循其他行为策略的同时实时学习，并使用基于梯度的时序差分学习方法，每个时间步的时间和内存复杂度为常数。

