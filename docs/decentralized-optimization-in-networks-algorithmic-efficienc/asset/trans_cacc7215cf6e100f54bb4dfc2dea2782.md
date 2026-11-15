

- a) 存在正常数 \( C \) 和 \( \alpha \in (0, 1) \)，使得 \( r_{s,t}^{i,j} \) 与 \( \theta_t^j \) 之间的绝对差被 \( C\varsigma^{s-t} \) 上界界定。此外，\( \theta_t \) 的转置等于 \( \theta_{t+1} \) 的转置与矩阵 \( R_t \) 的乘积。

- b) 令 \( \{\mu_t^i\}_{t \ge 1} \) 表示由公式 (6.9) 得出的序列。随后，对于预定的时间跨度 \( T \)，\( \frac{\mu_{t+1}^i}{n} \) 与 \( \theta_{t+1}^i \) 之差的大小被 \( Q\lambda^{T-t-1} \) 上界界定。此外，元素 \( \mu_{t+1}^i \) 被限制在区间 \( [\varpi^{-1}, \varpi] \) 内，其中 \( \varpi \) 和 \( \omega \) 是正常数。

在展示随后的关键引理之前，我们定义一个共轭类型的函数，记为 \( \mathcal{G}_\Omega^\varphi(u, \beta) \)，适用于任意向量 \( u \in \mathbb{R}^m \) 和正步长参数 \( \beta \)，其中

\(\mathcal{H}_\Omega^\varphi(v, \alpha) = \sup_{u \in \Omega} \{ \langle v, u \rangle - \frac{1}{\alpha} \phi(u) \}.\)

随后，我们制定一个关键引理以支撑我们的主要发现，其验证可追溯至 [47]。

**引理 6.3.** [47] 基于 \( \Pi_\Omega^\varphi(\cdot) \) 和 \( \mathcal{G}_\Omega^\varphi(\cdot) \) 的定义，我们断言，对于任意 \( v, u \in \mathbb{R}^m \) 和正 \( \alpha \)，以下关系成立：

- a) \( \nabla \mathcal{H}_\Omega^\varphi(-v, \alpha) = \Pi_\Omega^\varphi(v, \alpha) \)，且 \( ||\nabla \mathcal{H}_\Omega^\varphi(-v, \alpha) - \nabla \mathcal{H}_\Omega^\varphi(-u, \alpha)|| = ||\Pi_\Omega^\varphi(v, \alpha) - \Pi_\Omega^\varphi(u, \alpha)|| \le \alpha ||v - u|| \).

- b) \( \mathcal{H}_\Omega^\varphi(-v - u, \alpha) \le \mathcal{H}_\Omega^\varphi(-v, \alpha) - \langle \nabla \mathcal{H}_\Omega^\varphi(-v, \alpha), u \rangle + (\alpha/2)||u||^2 \).

## 6.4.2 收敛性分析

在本小节中，我们提出一个关于协商偏差上界的关键引理，具体为 \( \sup_{t \in \mathcal{V}} \{ \mathbb{E}[||q_t^i - \bar{q}_t||] \} \)，以便更全面地理解算法 1 的有效性。随后，我们制定关于遗憾上界（记为 \( \bar{R}_T^i \)）的主要结果，从而实现算法 1 的收敛性分析。

我们引入辅助向量 \( \bar{q}_t \)，作为 \( i \) 从 1 到 \( n \) 的所有索引上 \( \theta_t^i \) 与 \( q_t^i \) 乘积之和。为简化随后的收敛性分析，我们对集合 \( \mathcal{V} \) 中所有节点 \( i \) 和所有时间步 \( t \ge 1 \) 将 \( \hat{g}_t^i(x_t^i) \) 简写为 \( \hat{g}_t^i \)。因此，我们得到：

\(\bar{q}_{t+1} = \sum_{i=1}^n \theta_{t+1}^i \sum_{j=1}^n r_t^{ij} q_t^j + \sum_{i=1}^n \theta_{t+1}^i \sum_{j=1}^n r_t^{ij} \vartheta_t^j\)
\( + \sum_{i=1}^n \theta_{t+1}^i \frac{\hat{g}_t^i}{v_{t+1}^i} \)
\( = \bar{q}_t + \sum_{i=1}^n \theta_t^i \vartheta_t^i + \sum_{i=1}^n \theta_{t+1}^i \frac{\hat{g}_t^i}{v_{t+1}^i} ,\) (6.12)

该等式源自关于归一化向量序列的引理 6.2。通过对公式 (6.12) 两边在所有 \( t \) 值上求和，随后重组所得等式，可得：

\(\bar{q}_{t+1} = \bar{q}_1 + \sum_{s=1}^t \sum_{i=1}^n \theta_s^i \vartheta_s^i + \sum_{s=1}^t \sum_{i=1}^n \theta_{s+1}^i \frac{\hat{g}_s^i}{v_{s+1}^i}.\) (6.13)

此外，我们引入符号 \( b_{\max} \) 表示 \( t \in \{1, \dots, T\} \) 范围内 \( b_t \) 的最大值。随后，提出以下引理。

**引理 6.4.** 考虑到序列 \(\{q_t^i\}_{t=1}^T\) 和 \(\{v_t^i\}_{t=1}^T\) 根据算法 1 迭代更新，并在假设 6.1 和 6.2 的前提下，我们得到对所有 \( t = 1, \cdots, T \)，\(\max_{i \in \mathcal{V}} \{\mathbb{E}[||q_t^i - \bar{q}_t||]\} \le O_1\)，其中

\(O_1 = \frac{n Q(\sqrt{2m}b_{\max} + \omega m K)}{1 - \lambda} + Q \sum_{i=1}^n ||q_1^i|| + 2\omega m K.\)

**证明。** 作为公式 (6.8) 和 (6.12) 的结果，我们推导出

\(q_{t+1}^i = \sum_{j=1}^n r_{t+1:1}^{ij} q_1^j + \sum_{s=1}^t \sum_{j=1}^n r_{t+1:s}^{ij} \vartheta_s^j\)
\(+ \sum_{s=1}^{t-1} \sum_{j=1}^n r_{t+1:s+1}^{ij} \frac{\hat{g}_s^j}{v_{s+1}^j} + \frac{\hat{g}_t^i}{v_{t+1}^i}.\) (6.14)

随后，我们从公式 (6.13) 和 (6.14) 得出以下结论：

\(q_{t+1}^i - \bar{q}_{t+1} = \tau_1 + \tau_2 + \tau_3,\) (6.15)

其中

\(\tau_1 = \sum_{j=1}^n r_{t+1:1}^{ij} q_1^j - \sum_{j=1}^n \theta_1^j q_1^j,\)
\(\tau_2 = \sum_{s=1}^t \sum_{j=1}^n r_{t+1:s}^{ij} \vartheta_s^j - \sum_{s=1}^t \sum_{j=1}^n \theta_s^j \vartheta_s^j,\)
\(\tau_3 = \sum_{s=1}^{t-1} \sum_{j=1}^n r_{t+1:s+1}^{ij} \frac{\hat{g}_s^j}{v_{s+1}^j} - \sum_{s=1}^t \sum_{j=1}^n \theta_{s+1}^j \frac{\hat{g}_s^j}{v_{s+1}^j} + \frac{\hat{g}_t^i}{v_{t+1}^i}.\)

以引理 6.2 为基础，我们从参数 \( \tau_1 \) 推断出

\(\mathbb{E}[||\tau_1||] \le \mathbb{E}[\sum_{j=1}^n ||r_{t+1:1}^{ij} - \theta_1^j|| ||q_1^j||] \le Q \lambda^t \sum_{i=1}^n ||q_1^i||.\) (6.16)

鉴于 \( \vartheta_t^j \) 源自以参数 \( b_t \) 为特征的拉普拉斯分布，可以推断出其期望范数的平方 \( \mathbb{E}[||\vartheta_t^j||^2] \) 被其平方范数期望 \( \mathbb{E}[||\vartheta_t^j||^2] \) 上界界定，而后者又不大于 \( 2mb_{max}^2 \)。因此，我们继续推导：

\(\begin{aligned} \mathbb{E}[||\tau_2||] \le \mathbb{E}[\sum_{s=1}^t \sum_{j=1}^n ||r_{t+1:s}^{ij} - \theta_s^j|| ||\vartheta_s^j||] \\ \le n Q \sum_{s=1}^t \lambda^{t+1-s} \mathbb{E}[||\vartheta_s^j||] \\ \le n Q \sum_{s=1}^t \lambda^{t+1-s} \sqrt{2m} b_{max}. \end{aligned} \quad (6.17)\)

根据引理 6.1(c) 和引理 6.2，可以推导出

\(\begin{aligned} \mathbb{E}[||\tau_3||] \le \mathbb{E}[\sum_{s=1}^{t-1} \sum_{j=1}^n ||r_{t+1:s+1}^{ij} - \theta_{s+1}^j|| ||\frac{\hat{g}_s^j}{v_{s+1}^j}||] \\ + \mathbb{E}[\sum_{i=1}^n ||\theta_{t+1}^i - \frac{\hat{g}_t^i}{v_{t+1}^i}||] + \mathbb{E}[||\frac{\hat{g}_t^i}{v_{t+1}^i}||] \\ \le n Q \omega m K \sum_{s=1}^{t-1} \lambda^{t-s} + 2 \omega m K. \end{aligned} \quad (6.18)\)

最终，我们可以推断出

\(\mathbb{E}[||q_{t+1}^i - \bar{q}_{t+1}||] \le \mathbb{E}[||\tau_1||] + \mathbb{E}[||\tau_2||] + \mathbb{E}[||\tau_3||] \le O_1,\) (6.19)

这得出了预期结果。\(\square\)

为实现 \(\bar{R}_T^i\) 的目标遗憾上界，我们必须为预期最优性差异（由 \( \mathbb{E}[f_t^i(x_t^j) - f_t^i(x^*)] \) 表示）建立上界。然而，最优点 \( x^* \) 可能位于 \( (1 - \xi)\Omega \) 范围之外，而 \( x_t^i \) 则是将 \( q_t^i \) 投影到约束集 \( (1 - \xi)\Omega \) 上所得。因此，我们无法像以往的去中心化双平均法 [27,39,40] 中那样直接应用假设 6.2(b) 进行进一步审视。这在我们的分析工作中带来了一个新的障碍。为绕过这一难点，我们引入 \( \check{x} \) 作为 \( (1 - \xi)x^* \)，其中 \( x^* \) 是 \( \sum_{t=1}^T \sum_{i=1}^n f_t^i(x) \) 在 \( \Omega \) 上的最小化器，并将差异 \( \mathbb{E}[f_t^i(x_t^j) - f_t^i(x^*)] \) 等价地重构为

\(\begin{aligned} \mathbb{E}[f_t^i(x_t^j) - f_t^i(x^*)] &= \mathbb{E}[f_t^i(x_t^j) - f_t^i(x_t^i)] + \mathbb{E}[f_t^i(x_t^i) - f_t^i(\check{x})] \\ &+ \mathbb{E}[f_t^i(\check{x}) - f_t^i(x^*)]. \end{aligned}\)

鉴于 \( x_t^j \) 属于 \( (1-\xi)\Omega \)，且 \( \check{x} \) 和 \( x^* \) 均位于 \( \Omega \) 内，其中 \( \check{x} \) 具体位于 \( (1-\xi)\Omega \)，我们可以利用函数 \( f_t^j \) 的 Lipschitz 连续性为上述等式中的每个分量建立界。随后，这使我们能够获得 \( \bar{R}_T^j \) 的所求遗憾上界。为明确起见，让我们定义 \( \bar{x}_t \) 为使用步长 \( \alpha_{t-1} \) 的映射函数 \( \phi \) 将 \( \bar{q}_t \) 投影到 \( (1-\xi)\Omega \) 上所得。考虑预定的时间跨度 \( T \)，我们设定 \( \delta = \frac{d}{\sqrt{T}} \) 和 \( \xi = \frac{1}{\sqrt{T}} \)，随后提出下一个定理。

**定理 6.1.** *考虑到序列* \(\{x_t^i\}_{t=1}^T\) *由算法 1 迭代优化，采用步长* \(\alpha_t = \frac{\alpha_0}{\sqrt{t+1}}\) *且* \(\alpha_0 > 0\)。*鉴于假设 6.1 和 6.2 的有效性，存在分别记为* \(\Delta_1\) *和* \(\Delta_2\) *的正有限值，满足以下条件：*

\(\bar{R}_T^j \le \Delta_1 \sqrt{T} + \Delta_2,\)

*对所有* \(j \in \mathcal{V}\)，*其中*

\(\Delta_1 = (4+m)\alpha_0 n K O_1 + \frac{2n\phi(\check{x})}{\alpha_0} + 2\alpha_0 n^2 m^2 K^2 \omega^2\)
\(+ 4\alpha_0 n^2 m b_{\max}^2 + n K (d+D),\)
\(\Delta_2 = \frac{n^2 \omega m K D Q}{1 - \lambda} + n \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_1, \alpha_0) + n \langle \bar{q}_1, \check{x} \rangle.\)

**证明。** 回顾，对于所有 \(i\)，\( x_t^i \) 位于集合 \( (1-\xi)\Omega \) 内，同样，\( \check{x} \) 也属于此约束集。引入符号 \( \check{x} \) 的目的是为了间接促进期望 \( \mathbb{E}[f_t^i(x_t^i) - f_t^i(x^*)] \) 上界的推导，如前所述。鉴于假设 6.1 和 6.2，我们可以推断出

\(\bar{R}_T^j = \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^j) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x^*)]\)
\(=\mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^j) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^i)]\)
\(+ \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(\check{x}) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x^*)]\)
\(+ \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^i) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(\check{x})].\) (6.20)

随后，我们深入探讨公式 (6.20) 的各个组成部分。利用 \( f_t^i \) 的凸性，我们可从假设 6.2 推断出

\(\mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^j) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^i)]\)

