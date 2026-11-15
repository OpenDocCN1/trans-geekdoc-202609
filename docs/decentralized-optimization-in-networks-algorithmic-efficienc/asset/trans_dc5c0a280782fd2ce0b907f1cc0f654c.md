

+ \frac{1}{\gamma(k)}\varphi(x^*) + \langle \bar{h}(1), x^* \rangle
= \varphi^\dagger(-\bar{h}(k+1), \gamma(k)) + \frac{1}{\gamma(k)}\varphi(x^*) + \langle \bar{h}(1), x^* \rangle. \quad (7.21)

此外，我们可以推导出

\varphi^\dagger(-\bar{h}(s+1), \gamma(s))
\le \varphi^\dagger(-\bar{h}(s+1), \gamma(s-1))
= \varphi^\dagger(-\bar{h}(s) - \hat{g}(s), \gamma(s-1))
\le \varphi^\dagger(-\bar{h}(s), \gamma(s-1)) - \langle \hat{g}(s), \varsigma(s) \rangle + \frac{1}{2}\gamma(s-1)\|\hat{g}(s)\|^2, \quad (7.22)

其中不等式源自 [17, Lemma 2]。然后，(7.22) 进一步表明

\langle \hat{g}(s), \varsigma(s) \rangle \le \varphi^\dagger(-\bar{h}(s), \gamma(s-1)) - \varphi^\dagger(-\bar{h}(s+1), \gamma(s))
+ \frac{1}{2}\gamma(s-1)\|\hat{g}(s)\|^2. \quad (7.23)

对 (7.23) 两边关于 \(s\) 从 1 到 \(k\) 求和并整理所得不等式，我们得到

\sum_{s=1}^k \langle \hat{g}(s), \varsigma(s) \rangle \le \varphi_{\gamma(0)}^\dagger(-\bar{h}(1)) - \varphi_{\gamma(k)}^\dagger(-\bar{h}(k+1))
+ \frac{1}{2} \sum_{s=1}^k \gamma(s-1) \|\hat{g}(s)\|^2. \quad (7.24)

结合 (7.21) 和 (7.24)，我们最终得到

\sum_{s=1}^k \langle \hat{g}(s), \varsigma(s) - x^* \rangle \le \frac{1}{2} \sum_{s=1}^k \gamma(s-1) \|\hat{g}(s)\|^2 + \frac{1}{\gamma(k)} \varphi(x^*)
+ \varphi^\dagger(-\bar{h}(1), \gamma(0)) + \langle \bar{h}(1), x^* \rangle,

这证明了所需结果。

**注释 7.6.** 引理 7.4(b) 对于任何双变量 \(h_i\) 的初始条件均成立，对于算法 1 的收敛性分析至关重要。它比假设 \(h_i\) 零初始条件的结果（如 [25,26,28] 所示）更为一般。

## 7.4.3 主要结果

在本小节中，我们基于先前的结果建立了算法 1 的收敛性。

**定理 7.1.** 在假设 7.1 和 7.2 下。设 $\{\hat{x}_i(k)\}_{k=1}^{\infty}$ 由算法 1 生成，其中 $\gamma(k) = \gamma(0)/\sqrt{k+1}, \gamma(0) > 0$。则，我们有

$f(\hat{x}_i(k)) - f(x^*) \le \frac{\Theta_1}{\sqrt{k}} + \frac{\Theta_2}{k},$

其中 $x^* = \arg \min_{x \in \Omega} f(x), \Theta_1 = 6vL\Theta\gamma(0) + vL^2\gamma(0) + \frac{v}{\gamma(0)}\varphi(x^*)$ 和 $\Theta_2 = v\varphi^\dagger(-\bar{h}(1), \gamma(0)) + v\langle\bar{h}(1), x^*\rangle$ 为正常数。

_证明._ 根据凸函数的 Jensen 不等式，我们有

$f(\hat{x}_i(k)) - f(x^*)
\le \frac{1}{k} \sum_{s=1}^k (f(x_i(s)) - f(x^*))
= \frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v (f_j(x_i(s)) - f_j(x_j(s)) + f_j(x_j(s)) - f_j(x^*))
= O_1 + O_2,$

其中

$O_1 = \frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v (f_j(x_i(s)) - f_j(x_j(s))),$
$O_2 = \frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v (f_j(x_j(s)) - f_j(x^*)).$

基于假设 7.1 和引理 7.1，我们得到

$O_1 \le \frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v L \| x_i(s) - x_j(s) \|
\le \frac{1}{k} \sum_{s=1}^k vL\gamma(s-1) \| \frac{h_i(s)}{q_i(s)} - \bar{h}(s) \|
+ \frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v L\gamma(s-1) \| \bar{h}(s) - \frac{h_j(s)}{q_j(s)} \|.$

然后，根据子梯度不等式和由 (7.19) 给出的 $\{\varsigma(k)\}_{k=1}^{\infty}$ 的定义，有

$O_2 \le \frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v \langle g_j(s), x_j(s) - \varsigma(s) \rangle + \frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v \langle g_j(s), \varsigma(s) - x^* \rangle,$

这在考虑引理 7.1、假设 7.1 和引理 7.4(b) 的情况下，进一步表明

\(\frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v \langle g_j(s), x_j(s) - \varsigma(s) \rangle\)
\(\le \frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v L \| \Pi_\Omega^\varphi(\frac{h_j(s)}{q_j(s)}, \gamma(s-1)) - \Pi_\Omega^\varphi(\bar{h}(s), \gamma(s-1)) \|\)
\(\le \frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v L \gamma(s-1) \| \frac{h_j(s)}{q_j(s)} - \bar{h}(s) \|\)

和

\(\frac{1}{k} \sum_{s=1}^k \sum_{j=1}^v \langle g_j(s), \varsigma(s) - x^* \rangle\)
\(= \frac{v}{k} \sum_{s=1}^k \langle \frac{1}{v} \sum_{j=1}^v g_j(s), \varsigma(s) - x^* \rangle\)
\(\le \frac{v \varphi^\dagger(-\bar{h}(1), \gamma(0)) + v \langle\bar{h}(1), x^*\rangle}{k} + \frac{v L^2}{2k} \sum_{s=1}^k \gamma(s-1)\)
\(+ \frac{v \varphi(x^*)}{\gamma(k) k}.\)

最后，结合 (7.26)-(7.29)，我们可以得到

\(f(\hat{x}_i(k)) - f(x^*)\)
\(\le \frac{1}{k} \sum_{s=1}^k v L \gamma(s-1) \| \frac{h_i(s)}{q_i(s)} - \bar{h}(s) \| + \frac{v L^2}{2k} \sum_{s=1}^k \gamma(s-1)\)
\(+ \frac{2}{k} \sum_{s=1}^k \sum_{j=1}^v L \gamma(s-1) \| \bar{h}(s) - \frac{h_j(s)}{q_j(s)} \|\)
\(+ \frac{v \varphi(x^*)}{\gamma(k) k} + \frac{v \varphi^\dagger(-\bar{h}(1), \gamma(0)) + v \langle\bar{h}(1), x^*\rangle}{k}.\)

由于 \(\gamma(k) = \frac{\gamma(0)}{\sqrt{k+1}}\)，有

\(\sum_{s=1}^k \gamma(s-1) \le \gamma(0)(1 + \int_1^{k+1} \frac{1}{\sqrt{s}} ds) \le 2 \gamma(0) \sqrt{k+1}.\)

因此从引理 7.3 得出

\( f(\hat{x}_i(k)) - f(x^*) \)
\(\le \frac{3vL\Theta}{k} \sum_{s=1}^k \gamma(s-1) + \frac{vL^2}{2k} \sum_{s=1}^k \gamma(s-1) \)
\( + \frac{v\varphi(x^*)}{\gamma(k)k} + \frac{v\varphi^\dagger(-\bar{h}(1), \gamma(0)) + v\langle\bar{h}(1), x^*\rangle}{k} \)
\(\le \frac{(6vL\Theta\gamma(0) + vL^2\gamma(0))}{\sqrt{k}} + \frac{v\varphi(x^*)}{\sqrt{k}\gamma(0)} \)
\( + \frac{v\varphi^\dagger(-\bar{h}(1), \gamma(0)) + v\langle\bar{h}(1), x^*\rangle}{k}, \quad (7.31) \)

这推导出所需结果。

**注释 7.7.** 基于定理 7.1 和 \(\Theta_1\) 的定义，我们推断，向我们的算法引入相关扰动会导致与不考虑隐私保护的类似算法 [27] 相比收敛速度略有下降。参数 \(\delta\)（扰动的上界）与收敛性能成反比。然而，这种权衡是合理的，因为我们只需比 [27] 略微降低收敛速度，就能实现隐私保护这一重要目标。此外，定理 7.1 表明，在较不严格的初始条件下，我们的算法仍可达到与不采取隐私措施的算法 [27] 类似的 \(\mathcal{O}(1/\sqrt{K})\) 收敛速度。而且，我们的方法在不产生高计算复杂度和通信开销的情况下，匹配了 [27] 中的收敛精度，凸显了我们边缘相关扰动策略相对于同态加密 [32,33] 和差分隐私 [36,37] 等其他隐私保护方法的优势。

**注释 7.8.** 可以通过提高算法 1 的通信或计算效率来进一步增强其性能。在机器学习中，每个节点计算其所有样本的本地完整梯度，当样本量较大时会导致显著的计算成本。因此，使用无偏随机梯度（方差减小技术）[50,51] 代替传统的确定性梯度，可以显著降低节点的计算负担而不影响算法收敛。受最近文献 [2,3,42,46] 启发，我们也可以将事件触发策略纳入算法 1，允许每个节点通过测试特定的触发条件来在线决定何时向其外邻居广播当前估计值，从而减少通信负载并提高效率。这些改进将在未来的研究中探讨。

## 7.5 隐私保护分析

本节重点展示算法 1 如何通过边缘相关扰动策略确保隐私保护。我们先介绍一些预备知识，随后给出关于算法 1 隐私保护特性的主要结果。

### 7.5.1 预备知识

由于算法 1 集成了边缘相关扰动，恶意节点关于其入邻居所获得的信息是不准确的。尽管如此，正常节点仍可从其入邻居处接收准确信息，并用其更新变量。然而，恶意节点可能会合作以推断发送者的私有信息。因此，确保恶意节点无法利用算法 1 的边缘相关扰动策略来区分正常节点的真实和虚假子梯度至关重要。

我们将 \(\mathcal{D}_H\) 和 \(\mathcal{D}_E\) 分别定义为正常节点和恶意节点的集合。此外，关于恶意节点的能力，我们作出如下假设。

**假设 7.3.** 恶意节点完全了解邻接矩阵及其入邻居传输的所有信息。具体而言，节点 \(j \in \mathcal{D}_E\) 可观测 \(h_j(k), \tau_{ij}(k), \tilde{h}_{ji}(k)\)，其中 \(i \in \mathcal{N}_j^{\text{in}}(k)\)，以及所有 \(k \ge 1\) 的 \(P(k)\)。

假设 7.3 使恶意节点能够拥有全面的网络信息，这比现有文献 [31,36] 中的假设更现实。我们定义节点 \(j \in \mathcal{D}_E\) 的观测为算法 1 输出的 \(S(\{h_i(1), g_i(k), \tau_{ji}(k)\}_{i,j \in \mathcal{V}, k \ge 1}) = \{ \tilde{h}_{ji}(k) \}_{j \in \mathcal{D}_E, k \ge 1}\)，其取决于输入 \(\{h_i(1), g_i(k), \tau_{ji}(k)\}_{i,j \in \mathcal{V}, k \ge 1}\)。以下定义描述了算法 1 的隐私保护。

**定义 7.1.** 若存在 \(\hat{h}_i(1) \in \mathbb{R}^d\)，\(\{\hat{g}_i(k) : \hat{g}_i(k) \neq g_i(k)\}\)，以及对所有 \(j \in \mathcal{D}_E\) 的 \(\{\hat{\tau}_{ij}(k) : \hat{\tau}_{ij}(k) = \tau_{ij}(k)\}\)，使得对所有 \(k \ge 1\) 都有 \(S(\{\hat{h}_i(1), \hat{g}_i(k), \hat{\tau}_{ji}(k)\}_{i,j \in \mathcal{V}} = S(\{h_i(1), g_i(k), \tau_{ji}(k)\}_{i,j \in \mathcal{V}})\)，则子梯度 \(g_i(k)\)，\(i \in \mathcal{D}_H\) 受到保护。

根据定义 7.1，如果恶意节点从实际子梯度 \(\{g_i(k)\}\) 和伪子梯度 \(\{\hat{g}_i(k)\}\) 中获得相同的观测，则它们无法区分任意 \(i \in \mathcal{D}_H\) 的 \(g_i(k)\) 和 \(\hat{g}_i(k)\)。因此，正常节点的隐私得到保障。

### 7.5.2 主要结果

以下定理展示了算法 1 的隐私保护能力。

**定理 7.2.** 假设假设 7.3 成立。算法 1 可以保护所有 \(i \in \mathcal{D}_H\) 的私有局部子梯度 \(g_i(k)\)。

