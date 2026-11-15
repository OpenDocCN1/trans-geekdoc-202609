

## 2.1. 对称 AMP

- (iii) 其他抽象 AMP 递归的前驱：通过推广和变换 (2.1)，我们可以得到若干相关抽象 AMP 迭代的极限行为的状态演化描述，包括输入矩阵不必对称的情况（第 2.2 节）和/或迭代本身为矩阵而非向量的情况（第 A.7 节）。这些有助于分析更广泛的 AMP 算法类，而这些算法并不完全由 (2.1) 直接覆盖：参见例如第 4 节关于 GAMP 的内容。

我们将通过下面的定理 2.1 来形式化上述点 (i)。更一般地，在定理 2.3 中，我们将建立每个固定 \(k\) 当 \(n \to \infty\) 时 \(h^1, \dots, h^k, \gamma \in \mathbb{R}^n\) 分量的联合经验分布的 Wasserstein 极限。鉴于 (ii) 和 (iii)，我们将这些结果称为对称 AMP 的“主定理”。

我们将考虑一种概率设置，其中对于每个 \(n \in \mathbb{N}\)，我们都有一个基于随机三元组 \((m^0, \gamma, W) \equiv (m^0(n), \gamma(n), W(n))\) 的 AMP 递归 (2.1)，满足

- (A0) \(W \equiv W(n) \sim \text{GOE}(n)\) 且与 \((m^0, \gamma) \equiv (m^0(n), \gamma(n))\) 独立。

回顾第 1.1 节中的概念和定义，我们假设对于某些 \(r \in [2, \infty)\) 和 \(\tau_1 \in (0, \infty)\)，(2.1) 的输入在 \(n \to \infty\) 时还满足以下条件：

- (A1) 存在概率分布 \(\pi \in \mathcal{P}_1(r)\)，使得 \(\gamma \equiv \gamma(n)\) 分量的经验分布 \(\nu_n(\gamma)\) 满足 \(d_r(\nu_n(\gamma), \pi) \xrightarrow{c} 0\)。

- (A2) \(\|m^0\|_n \equiv (n^{-1} \sum_{i=1}^n |m_i^0|^2)^{1/2} \to \tau_1\) 且 \(\|m^0\|_{n,r} \equiv (n^{-1} \sum_{i=1}^n |m_i^0|^r)^{1/r} = O_c(1)\)。

- (A3) 存在 Lipschitz 函数 \(F_0 : \mathbb{R} \to \mathbb{R}\)，使得取 \(\tilde{\gamma} \sim \pi\)，我们有 \(\mathbb{E}(F_0(\tilde{\gamma})^2) \le \tau_1^2\)，且对于所有 Lipschitz 函数 \(\phi : \mathbb{R} \to \mathbb{R}\)，\(\langle m^0, \phi(\gamma) \rangle_n = n^{-1} \sum_{i=1}^n f_0(h_i^0, \gamma_i) \phi(\gamma_i) \xrightarrow{c} \mathbb{E}(F_0(\tilde{\gamma})\phi(\tilde{\gamma}))\)。

(A1) 若对于每个 \(n\)，\(\gamma \equiv \gamma(n)\) 的条目独立地从 \(\mathbb{R}\) 上具有一个有限 \(r^{th}\) 阶矩的分布 \(\pi\) 中抽取，则 (A1) 成立。一般来说，\(\pi\) 可以被视为统计应用中的“极限先验分布”。(A2) 包含对 \(m^0 \equiv m^0(n)\) 的经验 \(r^{th}\) 阶矩的有界性假设。(A1) 和 (A2) 均比现有 AMP 文献中关于 \((2r-2)^{th}\) 阶矩的类似条件更宽松、更自然；参见备注 A.4，该备注也讨论了 (A3)。

给定 (A1) 中的 \(\pi \in \mathcal{P}_1(r)\) 和 (A2) 中的 \(\tau_1 \in (0, \infty)\)，状态演化参数 \((\tau_k^2 : k \in \mathbb{N})\) 通过归纳定义为

\(\tau_{k+1}^2 := \mathbb{E}(f_k(G_k, \bar{\gamma})^2),\) (2.2)

其中 \(G_k \sim N(0, \tau_k^2)\) 与 \(\bar{\gamma} \sim \pi\) 独立。由于函数 \(f_k\) 是 Lipschitz 的，且在 (A1) 下 \(\mathbb{E}(\bar{\gamma}^2)^{1/2} \le \mathbb{E}(|\bar{\gamma}|^r)^{1/r} < \infty\)，通过归纳可知对于所有 \(k\)，\(\tau_k^2 \in [0, \infty)\)。

我们将再做两个温和的正则性假设。假设如果 \(r > 2\)，那么

- (A4) 对于每个 \(k \in \mathbb{N}\)，\(\pi(\{y \in \mathbb{R} : x \mapsto f_k(x, y) \text{ 非恒定}\}) > 0\)。

这是一个“非退化”条件，它确保对于所有 \(k \in \mathbb{N}\)，\(\tau_k^2 > 0\)；另参见下面的引理 2.2。今后，我们将写 \(\mu \otimes \mu'\) 表示两个测度 \(\mu, \mu'\) 的乘积测度。

- (A5) 对于每个 \(k \in \mathbb{N}\)，\(f'_k\) 的不连续点集合 \(D_k\) 满足 \((\lambda \otimes \pi)(D_k) = 0\)，其中 \(\lambda\) 表示 \(\mathbb{R}\) 上的勒贝格测度。

这保证了对于每个 \(k\)，(2.1) 中 \(b_k \equiv b_k(n)\) 在 \(n \to \infty\) 时存在确定性极限（另参见下面的备注 2.4），并且统计应用中常用的函数 \(f_k\) 满足此条件，例如基于软阈值函数 \(\text{ST}_t : u \mapsto \text{sgn}(u)(|u| - t)_+\)（\(t > 0\)）的函数。关于 (A1)-(A5) 的一些技术性备注见第 A.1 节，初次阅读时可跳过。

我们现在可以陈述第一个主定理，这是随机矩阵理论中的一个重要结果。如上文 (i) 所述，这特别揭示了 AMP 迭代的渐近分布行为由标量递归 (2.2) 控制。

**定理 2.1.** 假设 (A0)-(A5) 对于由 \(n \in \mathbb{N}\) 索引的一系列对称 AMP 递归 (2.1) 成立。那么对于每个 \(k \in \mathbb{N}\)，我们有

$d_r(\nu_n(h^k, \gamma), N(0, \tau_k^2) \otimes \pi) \xrightarrow{c} 0$ as \( n \to \infty \)，或等价地
\(\tilde{d}_r(\nu_n(h^k, \gamma), N(0, \tau_k^2) \otimes \pi)\)
\(= \sup_{\psi \in \text{PL}_2(r,1)} \left| \frac{1}{n} \sum_{i=1}^n \psi(h_i^k, \gamma_i) - \mathbb{E}(\psi(G_k, \bar{\gamma})) \right| \xrightarrow{c} 0 \quad \text{当 } n \to \infty. \quad (2.3)\)
其中 \( G_k \sim N(0, \tau_k^2) \) 与 \( \bar{\gamma} \sim \pi \) 独立。

在 AMP 文献中，此结论通常表述为
\(\frac{1}{n} \sum_{i=1}^n \psi(h_i^k, \gamma_i) \xrightarrow{a.s.} \mathbb{E}(\psi(G_k, \bar{\gamma})) \quad \text{as } n \to \infty, \text{ 对于每个 } \psi \in \text{PL}_2(r). \quad (2.4)\)

实际上，\(\xrightarrow{a.s.}\) 可以增强为 \(\xrightarrow{c}\)，(2.4) 的结果版本与 (2.3) 等价；换句话说，它可以自动升级为关于伪 Lipschitz 测试函数类 \(\text{PL}_2(r, 1)\) 上 *一致* 成立的收敛语句。更多细节见备注 A.1 和 A.2。

为了深入了解递归 (2.1) 的形式及其在定理 2.1 中的渐近表征，为简化起见，假设对于所有 \(n\)，\(\gamma \equiv \gamma(n) = 0 \in \mathbb{R}^n\)，并首先考虑 \(k=1\)。由于 (A0) 中对于每个 \(n\)，\(m^0 \equiv m^0(n)\) 与 \(W \equiv W(n)\) 独立，故 \(h^1 \equiv h^1(n) = W m^0\) 在给定 \(m^0\) 时条件高斯。事实上，给定 \(m^0\) 时，

\( h^1 \text{ and } h^{1,0} := \|m^0\|_n \tilde{Z} + \tilde{\zeta}m^0 = \tau_1 \tilde{Z} + \Delta^1 \)
对每个 \(n\) 服从相同分布，

其中 \(\tilde{Z} \sim N_n(0, I_n)\) 与 \(\tilde{\zeta} \sim N(0, 1/n)\) 独立，且 \(\Delta^1 := (\|m^0\|_n - \tau_1)\tilde{Z} + \tilde{\zeta}m^0\)；参见引理 A.14、(A.5) 和 (A.20)。

由 (A2)，\(\|m^0\|_n \xrightarrow{c} \tau_1\) 且 \(\|m^0\|_{n,r} = O_c(1)\) 当 \(n \to \infty\)，由此（根据 \(\|\cdot\|_{n,r}\) 的三角不等式）可知 \(\|\Delta^1\|_{n,r} \equiv (n^{-1} \sum_{i=1}^n |\Delta_i^1|^r)^{1/r} \xrightarrow{c} 0\)；参见第 A.5 节开头的 \(\mathcal{H}_1(a)\)。这意味着当 \(n \to \infty\) 时，\(\Delta^1\) 对 \(h^{1,0} \stackrel{d}{=} h^1 \in \mathbb{R}^n\) 分项的经验分布的影响渐近消失，而 \(\tau_1 \tilde{Z}\) 分项的经验分布在 \(d_r\) 中完全收敛到 \(N(0, \tau_1^2)\)（基本上由大数定律，或引理 B.12 中的浓度不等式得出）。这得出了定理 2.1 对于 \(h^1\) 的结论，并且还意味着

\(\|m^1\|_n^2 = \|f_1(h^1, 0)\|_n^2 = \frac{1}{n} \sum_{i=1}^n f_1(h_i^1, 0)^2 \xrightarrow{p} \mathbb{E}(f_1(G_1, 0)^2) = \tau_2^2,\)

\(\|m^1\|_{n,r}^r = \|f_1(h^1, 0)\|_{n,r}^r = \frac{1}{n} \sum_{i=1}^n |f_1(h_i^1, 0)|^r \xrightarrow{p} \mathbb{E}(|f_1(G_1, 0)|^r) < \infty.\)

这些极限源自状态演化递归 (2.2) 以及 \(f_1\) 是 Lipschitz 的事实，因此 \(f_1^2, |f_1|^r \in \text{PL}_2(r)\)；参见推论 B.21(b)。沿着此思路继续归纳，我们得出：对于每个固定 \(k \in \mathbb{N}\)，定理 2.1 中的高斯分布 \(N(0, \tau_k^2)\) 是“玩具”递归

\(\breve{h}^1 := \breve{W}^0 m^0, \quad \breve{m}^k := f_k(\breve{h}^k, \gamma), \quad \breve{h}^{k+1} := \breve{W}^k \breve{m}^k \quad \text{对于 } k \in \mathbb{N}, (2.5)\)

中 \(\breve{h}^k \equiv \breve{h}^k(n) \in \mathbb{R}^n\) 分项的经验分布的 \(d_r\) 极限，其中每个 \(\breve{W}^k \equiv \breve{W}^k(n) \sim \text{GOE}(n)\) 与 \(m^0, \gamma\)（此处为 0）及 \(\breve{W}^0, \dots, \breve{W}^{k-1}\) 独立，因而也与 \(\breve{m}^k\) 独立。

另一方面，请注意，在原始递归 (2.1) 中，相同的 GOE(n) 矩阵 \(W \equiv W(n)\) 出现在每次迭代中，因此 \(W\) 与 \(m^k\) 通常不独立（\(k \in \mathbb{N}\)），而且 \(Wm^k\) 并不按上述意义上渐近高斯。为了补偿这一点，Onsager 校正项 \(-b_k m^{k-1}\) 专门设计为去偏项，以确保 \(h^{k+1} = Wm^k - b_k m^{k-1}\) 与上面 (2.5) 中的 \(\breve{h}^{k+1}\) 具有相同的极限行为。确实，定理 2.1 证明中的一个重要技术步骤是表征给定 \(m^0, \gamma\) 及先前迭代 \(h^1, \dots, h^k\) 时 \(Wm^k\) 的条件分布（命题 A.11），然后表明其“非高斯分量”渐近地被 Onsager 项抵消。

这种巧妙的条件技术最初由 Bolthausen (2014) 和 Bayati 与 Montanari (2011) 开发，后来被广泛用于分析各种其他 AMP 迭代，其中 \(W\) 来自旋转不变矩阵集。例如，Berthier et al. (2020) 引入了一种“长 AMP”递归，其中每个迭代 \(h^{k+1}\) 更明确地用 \(W f_k(h^k, \gamma)\) 的条件分布的高斯部分来定义。对于对称 AMP 递归 (2.1)，关于条件分布的相关结果在第 A.2 节中陈述。

