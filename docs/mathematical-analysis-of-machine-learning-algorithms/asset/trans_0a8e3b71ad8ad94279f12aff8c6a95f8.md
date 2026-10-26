
因此我们可以采用一个更容易满足的不等式来定义见证损失的分解假设。这导致了一个基于不等式的定义，称为见证 Bellman 分解，它比无模型 RL 中定义 18.28 中的 Bellman 分解更弱。

### Definition 18.58 (见证 Bellman 分解)

设 $\mathcal{H} = \{\mathcal{H}^h\}$ 为 $h = 1, \dots, H$ 的内积向量空间序列。MDP 相对于 $\mathcal{H}$ 具有见证 Bellman 分解，如果满足以下条件。对于所有 $h \ge 2$ 和模型 $M \in \mathcal{M}$，存在 $u^{h-1}(M) \in \mathcal{H}^{h-1}$，并且对于所有策略 $\pi'$，存在 $\phi(\pi') \in \mathcal{H}^{h-1}$ 使得以下分解成立：$\left| \mathbb{E}_{\tilde{x}^h \sim \pi'} \mathcal{E}^h(M, \tilde{x}^h, \pi_M(\tilde{x}^h)) \right| \le \left| \langle u^{h-1}(M), \phi^{h-1}(\pi') \rangle \right| \le \kappa \mathbb{E}_{\tilde{x}^h \sim \pi'} \sup_{f \in \mathcal{F}} \left| \mathcal{E}^h(M, f, \tilde{x}^h, \pi_M(\tilde{x}^h)) \right|$，其中 $\kappa \ge 1$ 为某个常数。

类似命题 18.29，我们对见证 Bellman eluder 系数有以下结果。证明留作练习。

### Proposition 18.59

考虑定义 18.58 中的见证 Bellman 分解的 MDP。假设 $x_i^1$ 是从同一底层分布中抽取的独立同分布样本，并且对于 $h \ge 2$，$\sup_{f \in \mathcal{F}} \|u^{h-1}(M)\|_{\mathcal{H}^{h-1}} \le B$。假设 $r^h + f^{h+1}(x^h, a^h) \in [0,1]$，则 $\mathrm{EC}_{V\text{-Wit}}^1(0, \mathcal{M}, \mathcal{F}, T) \le 1 + \ln T$，$\mathrm{EC}_{V\text{-Wit}}^h(1, \mathcal{M}, \mathcal{F}, T) \le 2\kappa^2 \mathrm{entro}\!\left(1/(\kappa^2 B^2 T), \phi^{h-1}(\cdot)\right), \quad (h \ge 2)$，其中 $\mathrm{entro}(\cdot)$ 在命题 15.8 中定义。

命题 18.57 和命题 18.59 表明 $V$ 型 Hellinger Bellman eluder 系数可利用见证 Bellman 分解进行界定。因此模型基于 RL 的一般方法是采用 Hellinger eluder 系数，它将在线 Bellman 误差化为训练数据上的 Hellinger 损失。后者可利用标准似然准则进行界定。所得过程在算法 18.6 中给出，该算法已在 (Agarwal and Zhang, 2022a) 中利用解耦系数进行分析。还可通过使用 Bellman eluder 系数分析算法 18.5 的技术，为该算法推导出与定理 18.34 可比的遗憾界。

模型基于方法相对于无模型方法的优势之一是探索在模型基于方法中通常更容易。这是模型基于见证 eluder 系数小于无模型 eluder 系数的直接推论。事实上，容易验证以下结果成立。

### Proposition 18.60

考虑模型类 $\mathcal{M}$ 和候选 $Q$ 函数类 $\mathcal{F}$，使得 $\{f_M : M \in \mathcal{M}\} \subset \mathcal{F}$。则 $\mathrm{EC}_{Q\text{-Wit}}(\epsilon, \mathcal{M}, \mathcal{F}, T) \le \mathrm{EC}_Q(\epsilon, \mathcal{F}, T)$，$\mathrm{EC}_{V\text{-Wit}}^h(\epsilon, \mathcal{M}, \mathcal{F}, T) \le \mathrm{EC}_V^h(\epsilon, \mathcal{F}, T) \quad (h \ge 2)$。

### Algorithm 18.6 V-type 模型基于后验采样算法

**输入:** $\lambda, \eta, \tilde{\eta}, \tilde{\pi}, T, p_0, \mathcal{M}$

1. **for** $t = 1, 2, \ldots, T$ **do**
2. &nbsp;&nbsp;&nbsp;&nbsp;观察 $x_t^1$
3. &nbsp;&nbsp;&nbsp;&nbsp;抽取
   \[
   M_t \sim p_t(M \mid x_t^1, S_{t-1})
   \]
   根据
   \[
   p_t(M \mid x_t^1, S_{t-1}) \propto p_0(M) \exp\left(\lambda \sum_{s=1}^{t} f_M(x_s^1) + \sum_{s=1}^{t-1} L_s^{h_s}(M)\right),
   \]
   其中
   \[
   L_s^{h}(M) = -\tilde{\eta}(R_M^h(x_s^h, a_s^h) - r_s^h)^2 + \eta \ln P_M^h(x_s^{h+1} \mid x_s^h, a_s^h).
   \]
4. &nbsp;&nbsp;&nbsp;&nbsp;令 $\pi_t = \pi_{M_t}$
5. &nbsp;&nbsp;&nbsp;&nbsp;执行策略 $\pi_t$ 并观察轨迹 $(x_t, a_t, r_t)$ 直至 $x_t^{h_t}$，其中 $h_t$ 均匀随机
6. &nbsp;&nbsp;&nbsp;&nbsp;执行随机策略 $\alpha_t^{h_t} \sim \tilde{\pi}^{h_t}(\cdot \mid x_t^{h_t})$，并观察 $(r_t^{h_t}, x_t^{h_t+1})$
7. **return** 从 $t = 1$ 到 $t = T$ 中随机选择的 $\pi_t$

命题 18.60 显示一般而言，模型基于 RL 问题比无模型问题更容易求解。事实上，对于某些问题如因子 MDP，无模型方法和模型基于方法之间可能存在显著分离。

### Example 18.61 (因子 MDP (Kearns and Koller, 1999))

设 $d \ge 1$ 且 $\Omega$ 为一个小的有限集合。定义上下文空间 $\mathcal{X} = \Omega^d$，按时间自然划分。对于状态 $x^h \in \mathcal{X}$，我们用 $x^h[i] \subset \Omega$ 表示 $x^h$ 的第 $i$ 个分量，$i \in [d]$，以及状态变量的子集。对于每个 $i \in [d]$，$i$ 的父节点 $pa_i \subset [d]$ 是直接影响 $i$ 的状态变量子集。在因子 MDP 中，转移概率 $P$ 根据以下方式分解

\[
P^h(x^{h+1} \mid x^h, a^h) = \prod_{i=1}^{d} P_{(i)}^h[x^{h+1}[i] \mid x^h[pa_i], a^h].
\]

已知因子 MDP 可利用模型基于方法在多项式时间内学习，具有良好的见证 Bellman 分解。然而任何无模型方法在 $H$ 上具有指数复杂度 (Sun et al., 2019)。

## 18.9 历史和文献评述

强化学习 (Sutton and Barto, 2018) 有着悠久的历史，诸如用于基于值函数方法的 $Q$-learning (Watkins and Dayan, 1992) 以及用于基于策略方法的策略梯度 (REINFORCE) (Williams, 1992) 等重要算法在 1990 年代初期就已开发。本章考虑的理论分析仅涵盖基于值函数的方法。强化学习的数学基础与动态规划和最优控制 (Bertsekas, 2012) 密切相关。虽然 Q-learning 的收敛分析在算法提出后不久就出现了 (Jaakkola et al., 1993)，但早期的理论结果并未考虑探索，并且研究了更简单的表格设定。

带探索的强化学习的理论分析在更近期的研究中才得到研究，主要结果是利用基于值函数的方法开发的。本章介绍了近年来为分析强化学习而开发的主要技术工具。我们主要考虑了各种算法的统计行为，而未考虑其计算复杂度。事实上，本章研究的许多算法不一定在计算上有效。早期的考虑探索的强化学习结果研究了表格情形 (Kearns and Singh, 2002; Auer et al., 2008; Bartlett and Tewari, 2009; Dann and Brunskill, 2015)。特别是，Azar 等 (2017) 得到了与 minimax 率相匹配的尖锐结果。

Jin 等 (2018) 考虑了用于表格问题的 Q-learning 风格的无模型算法，其扩展到线性 MDP，称为带 UCB 的最小二乘值迭代 (LSVI-UCB)，在 Jin 等 (2020) 中进行了分析。算法 18.2 可视为 Jin 等 (2020) 中 LSVI-UCB 的变体。该算法与实际使用的 Q learning 非常相似，但在回归目标中额外加入了奖励项。该算法的遗憾界对 d 的依赖略有次优。通过使用加权回归，如 Zhou 和 Gu (2022) 所做，可以在主导阶上改善对 H 和 d 的依赖。虽然算法 18.2 可以处理一些非线性，但由于需要在回归目标中显式地纳入奖励函数 b_h^i(·)，它比算法 18.1 更复杂。这种复杂性可在其他变体中看到，例如 Wang 等 (2020)，他们提出了一种通用的奖励函数设计程序。

对于线性 MDP，Zanette 等 (2020) 提出了一种不同的方法，改进了 Jin 等 (2020) 中对 d 的依赖。Zanette 等 (2020) 中使用的 minimax 目标由 Antos 等 (2008) 引入。该方法推广到非线性 Q 函数类时变为算法 18.1。该方法相对于 LSVI-UCB 的优势在于，非线性推广仅要求 Q 函数类 F 相对于另一个函数类 G 完备，这相对容易满足。这里使用 Bellman eluder 系数概念提出的扩展也已被 Jin 等 (2021) 考虑，他们采用了类似的 Bellman eluder 维度的概念。Dann 等 (2021) 研究了后验采样方法，其中引入了 Bellman eluder 系数的概念。

Bellman 分解（和 Bellman rank）的思想由 Jiang 等 (2017) 提出，该论文提出了 V 型算法 OLIVE 以解决低 Bellman rank 的问题。定理 18.11 中的遗憾分解也在那里提出。OLIVE 相对于算法 18.3 的优势在于它不需要完备性假设。然而，它仅适用于有限动作的情况（没有简单的方法将 OLIVE 推广以处理
