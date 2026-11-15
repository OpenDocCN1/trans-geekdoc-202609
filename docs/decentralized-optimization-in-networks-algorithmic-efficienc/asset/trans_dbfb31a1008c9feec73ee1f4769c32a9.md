

文献 [18,19,27,28] 利用欧几里得范数进行理论分析，尽管一般范数及其对偶范数更为合适，但这并不影响最终的理论结果。

## 7.4 收敛保证

本节对算法 1 的收敛行为进行了理论分析。首先，介绍了与投影运算和矩阵 \( P(k) \) 相关的两个预备结果。随后，通过定义多个辅助向量引入了两个关键引理，这些引理对主要结果有显著影响。最后，基于这些发现建立了算法 1 的收敛性。

### 7.4.1 预备结果

我们首先介绍两个有用的预备结果。

**引理 7.1.** [17] 对于任意 \(\vartheta, \sigma \in \mathbb{R}^d\)，以下不等式成立：

\(\left\|\Pi_\Omega^\vartheta(\vartheta, \gamma) - \Pi_\Omega^\sigma(\sigma, \gamma)\right\| \le \gamma \|\vartheta - \sigma\|.\)

定义状态转移矩阵 \(\psi(k_1, k_2) = [\psi_{ij}(k_1, k_2)] \in \mathbb{R}^{d \times d}\)，其满足：

\(\psi(k_1, k_2) = \begin{cases} P(k_2 - 1)P(k_2 - 2) \cdots P(k_1), & k_2 > k_1, \\ I_n, & k_2 \le k_1. \end{cases}\)

基于 [11, Corollary 2]，我们得到关于 \(\psi(k_1, k_2)\) 的以下结果。

**引理 7.2.** [11] 在假设 7.2 下，对于任意 \(k_2 \ge k_1 > 0\)，存在一组随机向量序列 \(\phi(k) = [\phi_1(k), ..., \phi_v(k)]^\mathrm{T} \in \mathbb{R}^v\)（即，\(\phi_i(k) \ge 0\)，\(\sum_{i=1}^v \phi_i(k) = 1\)），使得

\(|\phi_i(k) - \psi_{ij}(s, k)| \le C \lambda^{k-s}, \forall i, j \in \mathcal{V},\)

其中 \(C > 0\) 为常数，\(\lambda \in (0, 1)\)。此外，以下不等式成立：

\(\mu \le \sum_{j=1}^v \psi_{ij}(1, k) \le \kappa, \forall i \in \mathcal{V},\)

其中 \(\mu\) 和 \(\kappa\) 为正常数。

### 7.4.2 支撑结果

本小节介绍两个关键引理，以进一步说明算法 1 的性能。

**引理 7.3.** 给定假设 7.1 和 7.2 满足，定义辅助向量 \(\bar{h}(k+1) = \frac{1}{v}\sum_{i=1}^v h_i(k+1)\)。存在常数 \(\Theta > 0\)，使得对所有 \(k \ge 1\) 和 \(i \in \mathcal{V}\)，以下不等式成立：

\(\left\| \frac{h_i(k)}{q_i(k)} - \bar{h}(k) \right\| \le \Theta,\)

其中

\(\Theta = \frac{1}{\mu}(\delta Q + (1 + v)L + \kappa \sum_{j=1}^v ||h_j(1)||) + \frac{Cv(2L + \delta Q)}{\mu(1 - \lambda)} + ||\bar{h}(1)||.\)

_证明._ 由 (7.4) 和 (7.5a) 可得

\(h_i(k+1) = \sum_{s=1}^{k-1} \sum_{j=1}^v \psi_{ij}(s+1, k+1) \sum_{l=1}^v P_{jl}(s)\tau_{jl}(s) + g_i(k) + \sum_{s=1}^{k-1} \sum_{j=1}^v \psi_{ij}(s+1, k+1) g_j(s) + \sum_{j=1}^v P_{ij}(k)\tau_{ij}(k) + \sum_{j=1}^v \psi_{ij}(1, k+1)h_j(1).\) (7.8)

同样，根据 (7.5b)，我们可以得到

\(q_i(k+1) = \sum_{j=1}^v P_{ij}(k)q_j(k) = \sum_{j=1}^v \psi_{ij}(1, k+1),\) (7.9)

该结果源于条件 \(q_j(1) = 1\) 对所有 \(j \in \mathcal{V}\) 成立。利用 (7.7) 和 \(\bar{h}(k+1)\) 的定义，我们得到

\(\bar{h}(k+1) = \frac{1}{v} \sum_{i=1}^v (\sum_{j=1}^v P_{ij}(k)h_j(k) + \sum_{j=1}^v P_{ij}(k)\tau_{ij}(k) + g_i(k)) = \frac{1}{v} \sum_{j=1}^v h_j(k) + \frac{1}{v} \sum_{i=1}^v \sum_{j=1}^v P_{ij}(k)\tau_{ij}(k) + \frac{1}{v} \sum_{i=1}^v g_i(k) = \bar{h}(k) + \frac{1}{v} \sum_{i=1}^v g_i(k),\) (7.10)

其中第二个等式成立是因为 \(P(k)\) 是列随机矩阵。因此

\(\bar{h}(k+1) = \bar{h}(k) + \frac{1}{v} \sum_{i=1}^v g_i(k) = \frac{1}{v} \sum_{i=1}^v h_i(1) + \frac{1}{v} \sum_{s=1}^k \sum_{i=1}^v g_i(s). \tag{7.11}\)

由此 (7.8)–(7.10) 可得

\(\bar{h}(k+1) - \frac{h_i(k+1)}{q_i(k+1)} = \frac{\omega_1 + \omega_2 + \omega_3}{q_i(k+1)} + \omega_4, \tag{7.12}\)

其中

\(\omega_1 = \frac{1}{v} \sum_{s=1}^k \sum_{j=1}^v g_j(s) q_i(k+1) - \sum_{s=1}^k \sum_{j=1}^v \psi_{ij}(s+1, k+1) g_j(s), \\ \omega_2 = \sum_{s=1}^{k-1} \sum_{j=1}^v \psi_{ij}(s+1, k+1) \sum_{l=1}^v P_{jl}(s) \tau_{jl}(s) + \sum_{j=1}^v P_{ij}(k) \tau_{ij}(k), \\ \omega_3 = \sum_{j=1}^v g_j(k) - g_i(k) - \sum_{j=1}^v \psi_{ij}(1, k+1) h_j(1)\)

且 \(\omega_4 = \bar{h}(1)\)。接下来，我们分别分析 \(\omega_1, \omega_2\) 和 \(\omega_3\)。定义随机向量序列 \(\phi(k) = [\phi_1(k), \dots, \phi_v(k)]^T \in \mathbb{R}^d\)，如引理 7.2 所示，我们得到

\(\omega_1 = \sum_{s=1}^k \sum_{j=1}^v g_j(s) (\frac{q_i(k+1)}{v} - \phi_i(k+1)) + \sum_{s=1}^k \sum_{j=1}^v g_j(s) (\phi_i(k+1) - \psi_{ij}(s+1, k+1)) = \frac{1}{v} \sum_{s=1}^k \sum_{j=1}^v g_j(s) \sum_{j=1}^v (\psi_{ij}(1, k+1) - \phi_i(k+1)) + \sum_{s=1}^k \sum_{j=1}^v g_j(s) (\phi_i(k+1) - \psi_{ij}(s+1, k+1)). \tag{7.13}\)

根据引理 7.2，可得

\[
\|\omega_1\| \le \frac{1}{v} \sum_{s=1}^k \sum_{j=1}^v \|g_j(s)\| |\sum_{j=1}^v (\psi_{ij}(1, k+1) - \phi_i(k+1))| + \sum_{s=1}^k \sum_{j=1}^v \|g_j(s)\| |\phi_i(k+1) - \psi_{ij}(s+1, k+1)| \le vLC \sum_{s=1}^k \lambda^k + vLC \sum_{s=1}^k \lambda^{k-s} \le \frac{2vLC}{1 - \lambda},
\]

其中第二个不等式使用了 \(\|g\| \le L\)。类似地，对于 \(\omega_2\)，我们有

\(\omega_2 = \sum_{s=1}^{k-1} \sum_{j=1}^v [\psi_{ij}(s+1, k+1) - \phi_i(k+1)] \sum_{l=1}^v P_{jl}(s) \tau_{jl}(s) + \phi_i(k+1) \sum_{s=1}^{k-1} \sum_{j=1}^v \sum_{l=1}^v P_{jl}(s) \tau_{jl}(s) + \sum_{j=1}^v P_{ij}(k) \tau_{ij}(k).\)

由 (7.7) 可知，对于任意 \(s\)，\(\sum_{j=1}^v \sum_{l=1}^v P_{jl}(s) \tau_{jl}(s) = 0\)。然后，根据引理 7.2，可得

\(\|\omega_2\| \le \sum_{s=1}^{k-1} \sum_{j=1}^v |\psi_{ij}(s+1, k+1) - \phi_i(k+1)| \delta Q + \delta Q \le \sum_{s=1}^{k-1} v \max_j |\psi_{ij}(s+1, k+1) - \phi_i(k+1)| \delta Q + \delta Q = \frac{vC\delta Q}{1 - \lambda} + \delta Q,\)

其中第一个不等式源于 \(\sum_{l=1}^v \|P_{jl}(s) \tau_{jl}(s)\| \le \delta Q\)（对 \(\|\tau_{ij}(k)\| \le \delta, \forall i, j \in \mathcal{V}\)），且 \(\sum_{j=1}^v \|P_{ij}(k)\| < Q, \forall k \ge 1\)。此外，我们还推导出

\(\|\omega_3\| \le \|\sum_{j=1}^v g_j(k) - g_i(k)\| + \|\sum_{j=1}^v \psi_{ij}(1, k+1) h_j(1)\| \le (1 + v)L + \kappa \sum_{j=1}^v \|h_j(1)\|.\)

结合 (7.12)、(7.14)、(7.16) 和 (7.17)，我们可以推导出

\(\left\| \frac{h_i(k+1)}{q_i(k+1)} - \bar{h}(k+1) \right\| \leq \frac{\|\omega_1\| + \|\omega_2\| + \|\omega_3\|}{q_i(k+1)} + \|\omega_4\| \leq \frac{2vLC + vC\delta Q}{\mu(1-\lambda)} + \frac{\delta Q + (1+v)L + \kappa \sum_{j=1}^v \|h_j(1)\|}{\mu} + \|\bar{h}(1)\|.\)

至此，证明完成。

接下来，我们为随后的支撑引理提供必要的定义。对于每个 \(k \ge 1\)，定义辅助变量如下：

\(\varsigma(k) = \Pi_\Omega^\omega(\bar{h}(k), \gamma(k-1)).\)

此外，对于任何向量 \(\sigma \in \mathbb{R}^d\) 和 \(\gamma > 0\)，与函数 \(\varphi(\cdot)\) 相关的共轭型函数由以下给出

\(\varphi^\dagger(\sigma, \gamma) = \sup_{x \in \Omega} \{ \langle \sigma, x \rangle - \frac{1}{\gamma} \varphi(x) \}.\)

此外，我们定义 \(\hat{g}(s) = (1/v) \sum_{i=1}^v g_i(s)\)。使用上述定义，我们现在建立一个关键引理以支持主要结果。

**引理 7.4.** 考虑由 (7.2) 和 (7.20) 分别给出的函数 \(\Pi_\Omega^\omega(\sigma, \gamma)\) 和 \(\varphi^\dagger(\sigma, \gamma)\)。对于非递增且为正的序列 \(\{\gamma(k)\}_{k=1}^\infty\)，以下陈述成立：

- (a) \(\nabla \varphi^\dagger(-\sigma, \gamma) = \Pi_\Omega^\omega(\sigma, \gamma);\)
- (b) \(\sum_{s=1}^k \langle \hat{g}(s), \varsigma(s) - x^* \rangle \leq \frac{1}{2} \sum_{s=1}^k \gamma(s-1) \|\hat{g}(s)\|^2 + \frac{1}{\gamma(k)} \varphi(x^*) + \varphi^\dagger(-\bar{h}(1), \gamma(0)) + \langle h(1), x^* \rangle, \forall x^* \in \Omega.\)

证明. 使用 (7.2) 和 (7.20)，引理 7.4(a) 可以轻松证明。基于引理 7.4(a) 和 (7.20)，我们有

\(- \sum_{s=1}^k \langle \hat{g}(s), x^* \rangle \leq \sup_{x \in \Omega} \{ - \sum_{s=1}^k \langle \hat{g}(s), x \rangle - \bar{h}(1), x \rangle - \frac{1}{\gamma(k)} \varphi(x) \}\)

