

且 \( t \ge 0 \)，有

\(\begin{aligned} \tilde{P}(n, t, v) &:= \mathbb{P}\left(\left|\frac{1}{n}\sum_{i=1}^n \phi_{v_i, y_i}(\tilde{Z}_i^1)\right| \ge t\right) \le \exp\left\{1 - \left(\frac{nt}{CL\tau_1\|v\|_2}\right)^2\right\} \\ &\le \exp\left\{1 - \left(\frac{n^{1/2}t}{CL\tau_1\|v\|_n}\right)^2\right\} \\ &=: \tilde{E}_r(n, t, L\tau_1\|v\|_n), \end{aligned}\)

(A.34)

其中 \( C > 0 \) 是一个合适的普适常数。再次回顾 \(\tilde{Z}^1\) 与 \(\mathcal{S}_0 = \sigma(\gamma, m^0)\) 独立，根据引理 B.7 可知，对于所有 \( 1 \le i \le n \)，有 \(m_i^0\{\phi(\tilde{h}_i^1, \gamma_i) - \mathbb{E}(\phi(\tilde{h}_i^1, \gamma_i) \mid \mathcal{S}_0)\} = \phi_{m_i^0, \gamma_i}(\tilde{Z}_i^1)\)。因此，对于每个 \( n \) 和 \( \varepsilon > 0 \)，有

\(\begin{aligned} \mathbb{P}(|T'_{n1}| > \varepsilon \mid \mathcal{S}_0) &= \mathbb{P}\left(\left|\frac{1}{n}\sum_{i=1}^n \phi_{m_i^0, \gamma_i}(\tilde{Z}_i^1)\right| \ge \varepsilon \mid \mathcal{S}_0\right) = \tilde{P}(n, \varepsilon, m^0) \\ &\le \tilde{E}_r(n, \varepsilon, L\tau_1\|m^0\|_n). \end{aligned}\)

(A.35)

由于根据 (A2) \(\|m^0\|_n \xrightarrow{c} \tau_1\)，命题 1.2 保证事件 \(\tilde{A}_0(n) := \{\|m^0\|_n \le \tau_1 + 1\} \in \mathcal{S}_0(n)\) 满足 \(\sum_{n=1}^\infty \mathbb{P}(\tilde{A}_0(n)^c) < \infty\)。此外，对于每个 \( n \) 和 \( \varepsilon > 0 \)，由 (A.34) 可得

\(\begin{aligned} \mathbb{P}(|T'_{n1}| > \varepsilon \cap \tilde{A}_0(n) \mid \mathcal{S}_0) &= \mathbb{P}(|T'_{n1}| > \varepsilon \mid \mathcal{S}_0)\mathbb{1}_{\tilde{A}_0(n)} \le \tilde{P}(n, \varepsilon, m^0)\mathbb{1}_{\tilde{A}_0(n)} \\ &\le \tilde{E}_r(n, \varepsilon, L\tau_1 C_0)\mathbb{1}_{\tilde{A}_0(n)} \le \tilde{E}_r(n, \varepsilon, L\tau_1 C_0), \end{aligned}\)

(A.36)

其中我们利用了 \(\tilde{A}_0(n) \in \mathcal{S}_0(n)\) 这一事实来得到上述第一个等式。回顾 (A.34) 中 \(\tilde{E}_r(n, \varepsilon, C_0)\) 的表达式，我们看到 \(\sum_{n=1}^\infty \tilde{E}_r(n, \varepsilon, L\tau_1 C_0) < \infty\)。因此，对于每个 \( \varepsilon > 0 \)，如同在 (A.29) 中一样，我们得出

\(\begin{aligned} \sum_{n=1}^\infty \mathbb{P}(|T'_{n1}| > \varepsilon) &\le \sum_{n=1}^\infty \mathbb{P}(\{|T'_{n1}| > \varepsilon\} \cap \tilde{A}_0(n)) + \sum_{n=1}^\infty \mathbb{P}(\tilde{A}_0(n)^c) \\ &\le \sum_{n=1}^\infty \tilde{E}_r(n, \varepsilon, L\tau_1 C_0) + \sum_{n=1}^\infty \mathbb{P}(\tilde{A}_0(n)^c) < \infty, \end{aligned}\)

(A.37)

这在考虑命题 1.2 的情况下蕴含了 (A.33)，从而得出 (A.31) 中 \( T_{n1} \xrightarrow{c} \tilde{\tau} \mathbb{E}(\phi(\tilde{G}_1))\)。

关于 (A.31) 中的 \( T_{n2} \)，令 \( L > 0 \) 如上文所述，使得 \( \phi \in \text{PL}_2(1, L) \)。对于每个 \( n \)，回顾由 (A.23) 得 \( h^{1,0} = \tilde{h}^1 + \Delta^1 \)，我们现在应用柯西-施瓦茨不等式可知

\( |T_{n2}| \le \frac{1}{n} \sum_{i=1}^n |m_i^0| |\phi(h_i^{1,0}, \gamma_i) - \phi(h_i^{1,0} - \Delta_i^1, \gamma_i)| \ \ \le \frac{L}{n} \sum_{i=1}^n |m_i^0| |\Delta_i^1| \le L \|m^0\|_n \|\Delta^1\|_n. \)

由于根据 (A2) \(\|m^0\|_n \xrightarrow{c} \tau_1\)，并且根据 \(\mathcal{H}_1(a)\) 有 \(\|\Delta^1\|_n \le \|\Delta^1\|_{n,r} = o_c(1)\)，我们得出 \( T_{n2} = O_c(1) o_c(1) = o_c(1) \)。这完成了对 \(\mathcal{H}_1(d)\) 的证明。

转向归纳步骤，我们考虑一般的 \( k \in \mathbb{N} \) 并假设 \(\mathcal{H}_k(b, c, d)\) 已经建立。断言 \(\mathcal{H}_k(e, \dots, j)\) 和 \(\mathcal{H}_{k+1}(a, b, c, d)\) 将按此顺序证明。注意由于 \( r \ge 2 \)，有 \(\text{PL}_{k+1}(2) \subseteq \text{PL}_{k+1}(r)\)。

### $\mathcal{H}_k(e)$

在 \( j = \ell = 1 \) 的情况下，根据 (A2) 有 \( |||m^0||_n - \tau_1| \xrightarrow{c} 0 \)，因此根据 (A.17) \(\langle m^0, m^0 \rangle_n \xrightarrow{c} \tau_1^2 = \bar{T}_{1,1} = \mathbb{E}(\bar{G}_1^2)\)。现在固定 \( j, \ell \in \{2, \dots, k+1\} \)。那么，根据引理 B.22 以及 AMP 递归 (2.1) 中 \( f_{j-1}, f_{\ell-1} \) 为 Lipschitz 的事实，\(\tilde{\psi}_{j\ell}: (x_1, \dots, x_k, y) \mapsto f_{j-1}(x_{j-1}, y) f_{\ell-1}(x_{\ell-1}, y)\) 属于 \(\text{PL}_{k+1}(2) \subseteq \text{PL}_{k+1}(r)\)。因此，在 \(\mathcal{H}_k(c)\) 中取 \( \psi = \tilde{\psi}_{j\ell} \)，我们看到

\(\langle m^{j-1}, m^{\ell-1} \rangle_n = \frac{1}{n} \sum_{i=1}^n f_{j-1}(h_i^{j-1}, \gamma_i) f_{\ell-1}(h_i^{\ell-1}, \gamma_i) \ \ \xrightarrow{c} \mathbb{E}(f_{j-1}(\bar{G}_{j-1}, \bar{\gamma}) \cdot f_{\ell-1}(\bar{G}_{\ell-1}, \bar{\gamma})) = \bar{T}_{j,\ell} = \mathbb{E}(\bar{G}_j \bar{G}_\ell),\)

其中最后的等式取自 (A.17)。为处理剩余情况 \( \{j, \ell\} = \{1, k+1\} \)，注意由于 \( f_k \) 是 Lipschitz，映射 \( \phi_{k+1}: (x_1, \dots, x_k, y) \mapsto f_k(x_k, y) \) 属于 \(\text{PL}_{k+1}(1)\)。因此，在 \(\mathcal{H}_k(d)\) 中取 \( \phi = \phi_{k+1} \)，我们推断出

\(\langle m^0, m^k \rangle_n = \frac{1}{n} \sum_{i=1}^n m_i^0 f_k(h_i^k, \gamma_i) \xrightarrow{c} \mathbb{E}(F_0(\bar{\gamma}) \cdot f_k(\bar{G}_k, \bar{\gamma})) \ \ = \bar{T}_{1, k+1} = \mathbb{E}(\bar{G}_1 \bar{G}_{k+1}),\)

其中最后的等式同样取自 (A.17)。

### $\mathcal{H}_k(f)$

此证明与 \(\mathcal{H}_k(e)\) 的证明非常相似。首先固定 \(1 \le j, \ell \le k\)。根据引理 B.22，函数 \((x_1, \dots, x_k, y) \mapsto x_j f_\ell(x_\ell, y)\) 属于 \(\text{PL}_{k+1}(2) \subseteq \text{PL}_{k+1}(r)\)，因此再次应用 \(\mathcal{H}_k(c)\)，我们推断出

\(\langle h^j, m^\ell \rangle_n = \frac{1}{n} \sum_{i=1}^n h_i^j f_\ell(h_i^\ell, \gamma_i) \xrightarrow{\text{Law}} \mathbb{E}(\bar{G}_j f_\ell(\bar{G}_\ell, \bar{\gamma})) = \mathbb{E}(f'_\ell(\bar{G}_\ell, \bar{\gamma})) \mathbb{E}(\bar{G}_j \bar{G}_\ell) = \bar{b}_\ell \bar{T}_{j,\ell},\)

其中最后的等式取自 (A.19)。对 \(\mathcal{H}_k(f)\) 的第二部分，我们固定 \(1 \le j \le k\) 并应用 \(\mathcal{H}_k(d)\)，使用 \(\text{PL}_{k+1}(1)\) 函数 \((x_1, \dots, x_k, y) \mapsto x_j\)，可以看到

\(\langle h^j, m^0 \rangle_n = \frac{1}{n} \sum_{i=1}^n m_i^0 h_i^j \xrightarrow{\text{Law}} \mathbb{E}(F_0(\bar{\gamma}) \bar{G}_j) = 0\)

这是由于 \(\bar{G}_j \sim N(0, \tau_j^2)\) 与 \(\bar{\gamma} \sim \pi\) 独立。

### $\mathcal{H}_k(g)$

根据定义 1.1 中完全收敛的定义，仅需证明：若 \((\beta_n)\) 是任意随机变量序列，且对每个 \(n\) 满足 \(\beta_n \overset{d}{=} \langle f'_k(h^k, \gamma) \rangle_n\)，则 \(\beta_n \xrightarrow{a.s.} \mathbb{E}(f'_k(\bar{G}_k, \bar{\gamma}))\)。对于任意这样的序列 \((\beta_n)\)，我们首先寻求构造一个随机序列 \(((\eta_n, \theta_n) \in \mathbb{R}^n \times \mathbb{R}^n : n \in \mathbb{N})\)，使得对每个 \(n\) 有 \((\eta_n, \theta_n) \overset{d}{=} (h^k(n), \gamma(n))\)，且作为随机序列几乎处处有 \(((f'_k(\eta_n, \theta_n))_n : n \in \mathbb{N}) = (\beta_n : n \in \mathbb{N})\)。这可以通过应用引理 B.10 来完成，其中我们对每个 \(n\) 取 \(g_n : \mathbb{R}^n \times \mathbb{R}^n \to \mathbb{R}\) 为可测函数 \((x, y) \mapsto \langle f'_k(x, y) \rangle_n = n^{-1} \sum_{i=1}^n f'_k(x_i, y_i)\)。

由构造可知对每个 \(n\) 有 \((\eta_n, \theta_n) \overset{d}{=} (h^k(n), \gamma(n))\)，根据归纳假设 \(\mathcal{H}_k(c)\)，对于每个 \(\varphi \in \text{PL}_2(r)\)，都有 \(n^{-1} \sum_{i=1}^n \varphi(\eta_{ni}, \theta_{ni}) \overset{d}{=} n^{-1} \sum_{i=1}^n \varphi(h_i^k, \gamma_i) \xrightarrow{\text{Law}} \mathbb{E}(\varphi(\bar{G}_k, \bar{\gamma}))\)，其中 \((\bar{G}_k, \bar{\gamma}) \sim N(0, \tau_k^2) \otimes \pi =: \bar{\mu}^k\)。因此，记 \(\hat{\mu}_n^k := \nu_n(\eta_n, \theta_n) = n^{-1} \sum_{i=1}^n \delta_{(\eta_{ni}, \theta_{ni})}\) 为每个 \(n\) 中 \(\eta_n\) 和 \(\theta_n\) 分量的联合经验分布，根据推论 B.21(a) 可得 \(d_r(\hat{\mu}_n^k, \bar{\mu}^k) \xrightarrow{a.s.} 0\)，从而 \((\hat{\mu}_n^k)\) 以概率 1 弱收敛于 \(\bar{\mu}^k\)。根据 (A5)，\(f'_k\) 是有限的、Borel 可测且在 \(\bar{\mu}^k\)-几乎处处连续的，因此我们可以应用引理 B.14 得出 \(\beta_n = \langle f'_k(\eta_n, \theta_n) \rangle_n = \int_{\mathbb{R}^2} f'_k \, d\hat{\mu}_n^k \to \int_{\mathbb{R}^2} f'_k \, d\bar{\mu}^k = \mathbb{E}(f'_k(\bar{G}_k, \bar{\gamma}))\) 几乎处处成立。这完成了对 \(\mathcal{H}_k(g)\) 的证明。

