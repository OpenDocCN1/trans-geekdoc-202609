

\(T'_r\) 是一组有界 Lipschitz 函数，我们当然有 \(T'_r \subseteq \mathrm{PL}_D(r)\)。我们声称 \(T_r := T'_r \cup \{\psi_r(1 - f_N) : N \in \mathbb{N}\}\) 是 \(\mathrm{PL}_D(r)\) 的一个可数子集，具有所需性质。要看这一点，假设 (i) 对于这个集合 \(T_r\) 成立，即对于所有 \(\psi \in T_r\) 有 \(P_n(\psi) \to P(\psi)\)。正如在 (B.13) 中所述，我们有 \(\tilde{d}_r(P_n, P) = \sup_{\phi \in \widetilde{\mathrm{PL}}_D(r, 1)} |(P_n - P)(\phi)|\) 对所有 \(n\) 成立，其中 \(\widetilde{\mathrm{PL}}_D(r, 1)\) 表示所有满足 \(\phi(0) = 0\) 的 \(\phi \in \mathrm{PL}_D(r, 1)\) 的集合，因此只需证明后者趋于 0。

我们将考虑一个分解 (B.15)，类似于命题 B.16 证明中的 (B.14)，在此例中特别要注意，以确保随后的界在 \(\phi \in \widetilde{\mathrm{PL}}_D(r, 1)\) 上一致成立。注意，由于当 \(N \to \infty\) 时 \(\psi_r(1 - f_N) \to 0\) 在 \(\mathbb{R}^D\) 上逐点收敛，并且对于每个 \(N\)，\(\psi_r(1 - f_N)\) 被 \(\mathbb{R}^D\) 上的 \(P\)-可积函数 \(\psi_r\) 支配，根据主导收敛定理，我们有当 \(N \to \infty\) 时 \(P(\psi_r(1 - f_N)) \to 0\)。因此，对于任意 \(\varepsilon > 0\)，存在一个足够大的 \(N \equiv N_{\varepsilon, r} \in \mathbb{N}\)，使得 \(P(\psi_r(1 - f_N)) < \varepsilon/4\)，并且我们还固定 \(m \equiv m_\varepsilon \in \mathbb{N}\) 使得 \(1/m < \varepsilon/4\)。选择这样的 \(N\) 和 \(m\)，根据 \(\tilde{\mathcal{H}}_{N,m}\) 的定义性质，对于任何 \(\phi \in \widetilde{\mathrm{PL}}_D(r, 1)\)，都存在 \(\tilde{h}_\phi \in \tilde{\mathcal{H}}_{N,m}\)，使得 \(\sup_{x \in B_N} |\phi(x) - \tilde{h}_\phi(x)| < 1/m < \varepsilon/4\)。令 \(h_\phi\) 为如上所述在 \(\mathcal{H}_{N,m}\) 中对应的函数，则有

```
|(P_n - P)(\phi)|
\le |(P_n - P)(\phi(1 - f_N))| + |(P_n - P)(\phi f_N - h_\phi)| + |(P_n - P)(h_\phi)|
\le (P_n + P)(|\phi(1 - f_N)|) + (P_n + P)(|\phi f_N - h_\phi|) + \max_{\psi \in \mathcal{H}_{N,m}} |(P_n - P)(\psi)|
```

根据三角不等式。现在，对于每一个 \(\phi \in \widetilde{\mathrm{PL}}_D(r, 1)\)，我们有对于所有 \(x \in \mathbb{R}^D\)，\(|\phi(x)| = |\phi(x) - \phi(0)| \le \|x\| + \|x\|^r = \psi_r(x)\)。由于根据假设，当 \(n \to \infty\) 时 \(P_n(\psi_r(1 - f_N)) \to P(\psi_r(1 - f_N))\)，这意味着

```
\limsup_{n \to \infty} \sup_{\phi \in \widetilde{\mathrm{PL}}_D(r, 1)} (P_n + P)(|\phi|(1 - f_N))
\le \limsup_{n \to \infty} \sup (P_n + P)(\psi_r(1 - f_N))
= 2P(\psi_r(1 - f_N)) < \varepsilon/2.
```

此外，对于任何 \(\phi \in \widetilde{\mathrm{PL}}_D(r, 1)\)，函数 \(\phi f_N\) 和 \(h_\phi\) 都支撑于 \(B_N\) 上，并且在 $B_N$ 上 \(|\phi f_N - h_\phi| = |\phi - \tilde{h}_\phi| f_N \le |\phi - \tilde{h}_\phi| < \varepsilon/4\)，所以

\(\limsup_{n\to\infty} \sup_{\phi \in \widetilde{\text{PL}}_D(r,1)} (P_n + P)(|\phi f_N - h_\phi|)\)

\(\le 2 \sup_{\phi \in \widetilde{\text{PL}}_D(r,1)} \sup_{x \in B_N} |\phi(x) f_N(x) - h_\phi(x)| < \varepsilon/2.\) (B.17)

最后，由于 \(\mathcal{H}_{N,m}\) 是有限的，并且根据假设对所有 \(\psi \in \mathcal{H}_{N,m} \subseteq T_r\) 有 \(P_n(\psi) \to P(\psi)\)，因此 \(\max_{\psi \in \mathcal{H}_{N,m}} |(P_n - P)(\psi)| \to 0\)。将其与 (B.15)、(B.16) 和 (B.17) 结合，我们得出

\(\limsup_{n\to\infty} \tilde{d}_r(P_n, P) = \limsup_{n\to\infty} \sup_{\phi \in \widetilde{\text{PL}}_D(r,1)} |(P_n - P)(\phi)| < \varepsilon/2 + \varepsilon/2 = \varepsilon.\)

由于 \(\varepsilon > 0\) 是任意的，所需结论成立。

(ii) \(\Rightarrow\) (iii)：假设 \(\tilde{d}_r(P_n, P) \to 0\)，令 \(\psi: \mathbb{R}^D \to \mathbb{R}\) 为某个 \(L > 0\) 的（有界）\(L\)-Lipschitz 函数。则 \(\tilde{\psi}(\cdot) := \psi(\cdot)/L \in \text{PL}_D(r,1)\)，所以 \(P_n(\psi) = L P_n(\tilde{\psi}) \to L P(\tilde{\psi}) = P(\psi)\)。因此 \(P_n \xrightarrow{d} P\)。此外，函数 \(x \mapsto \|x\|^r\) 属于 \(\text{PL}(r, (r/2) \vee 1)\)，因为根据下文的 Lemma B.20，

\(|\|x\|^r - \|y\|^r| \le \frac{r \vee 2}{2} |\|x\| - \|y\|| (\|x\|^{r-1} + \|y\|^{r-1})\)

\(\le \frac{r \vee 2}{2} \|x - y\| (\|x\|^{r-1} + \|y\|^{r-1})\) (B.18)

对于所有 \(x, y \in \mathbb{R}^D\)，所以 \(\int_{\mathbb{R}^D} \|x\|^r dP_n(x) \to \int_{\mathbb{R}^D} \|x\|^r dP(x)\)。我们得出 \(d_r(P_n, P) \to 0\)。

(iii) \(\Rightarrow\) (i)：我们将证明，如果 (iii) 成立，则对于所有 \(\psi \in \text{PL}_D(r)\) 有 \(P_n(\psi) \to P(\psi)\)。确实，假设 \(P_n \xrightarrow{d} P\) 且 \(\int_{\mathbb{R}^D} \|x\|^r dP_n(x) \to \int_{\mathbb{R}^D} \|x\|^r dP(x)\)。现在，对于 \(L > 0\) 和任何 \(\psi \in \widetilde{\text{PL}}_D(r,L)\)，我们有对于所有 \(x \in \mathbb{R}^D\)，\(|\psi(x)| \le L \|x\| (1 + \|x\|^{r-1}) \le 2L(1 + \|x\|^r)\)。因此，由于 \(\psi\) 在 \(\mathbb{R}^D\) 上连续，且 \(x \mapsto |\psi(x)| / (1 + \|x\|^r)\) 在 \(\mathbb{R}^D\) 上有界，根据 (iii) 和 Dümbgen et al. (2011, Lemma 4.5)，可得 \(P_n(\psi) \to P(\psi)\)。

**注 B.19.** 定理 B.17 中蕴含 (i) \(\Rightarrow\) (ii) 的证明与 Dudley (2002) 中的论证类似，该论证表明其定理 11.3.3 中 (b) 蕴含 (c)，在此确立了有界 Lipschitz 度量诱导弱收敛拓扑（概率度量在可分度量空间上的）。

### Lemma B.20. 如果 \( a, b \ge 0 \) 且 \( r \ge 1 \)，则 \( |a^r - b^r| \le \max(1, r/2) |a - b| (a^{r-1} + b^{r-1}) \)。

证明。不妨假设 \( 0 \le b \le a \)。若 \( r \ge 2 \)，则 \( t \mapsto rt^{r-1} \) 在 \( [0, \infty) \) 上凸，所以

```
a^r - b^r = \int_a^b r t^{r-1} dt \le \int_a^b r \left( \frac{t-b}{a-b} a^{r-1} + \frac{a-t}{a-b} b^{r-1} \right) dt = \frac{r}{2}(a - b)(a^{r-1} + b^{r-1}).
```

若 \( r \in [1, 2] \)，则 \( 0 \le (ab)^{r-1}(a^{2-r} - b^{2-r}) = ab^{r-1} - ba^{r-1} \)，所以 \( a^r - b^r \le (a - b)(a^{r-1} + b^{r-1}) \)。

当我们有一个在 \(\mathbb{R}^D\) 上的可能随机概率测度序列 \( P_n \equiv P_n(\omega) \) 时，可以应用确定性定理 B.17 来获得下面的推论 B.21，在其中我们为 \(\mathcal{P}(r)\) 配备与 \( d_r \)（或等价地，\(\tilde{d}_r\)）度量相关的博雷尔 \(\sigma\)-代数 \(\mathcal{B}_r \equiv \mathcal{B}(\mathcal{P}(r))\)。注意，根据命题 B.16，对于每个 \( n \)，\(\tilde{d}_r(P_n, P)\) 是可测的（即一个真随机变量）。\( d_r(P_n, P) \) 的可测性由 Villani (2009, Corollary 5.22) 保证；另见 Panaretos 和 Zemel (2020, Lemma 2.4.6)。

### 推论 B.21. 固定 \( P \in \mathcal{P}(r) \equiv \mathcal{P}_D(r) \)，令 \( (P_n) \) 为随机元素序列 \( P_n: \Omega \to \mathcal{P}(r) \)。

- (a) 则以下各项等价：

- (i) 对于每个 \(\psi \in \text{PL}_D(r)\)，\(\int_{\mathbb{R}^D} \psi \, dP_n \xrightarrow{a.s.} \int_{\mathbb{R}^D} \psi \, dP\)；
- (ii) \(\tilde{d}_r(P_n, P) \xrightarrow{a.s.} 0\)；
- (iii) \(d_r(P_n, P) \xrightarrow{a.s.} 0\)。

- (b) 如果 (i)–(iii) 中的收敛模式改为概率收敛或完全收敛，则同样的等价性成立。

因此，为了建立对随机分布序列 \(P_n\)、一个拟议的极限 \(P \in \mathcal{P}_D(r)\) 以及上述任何随机收敛模式中 (ii) 和 (iii) 中看似更强的结论，证明对每个 \(\psi \in \text{PL}_D(r)\) 依次成立 (i) 的适当版本即为充分（有时也更方便）。这是我们在对称 AMP 的主定理（定理 2.1 和 2.3）证明中采取的方法。

证明。(a) 蕴含 (ii) \(\Rightarrow\) (iii) \(\Rightarrow\) (i) 直接由定理 B.17 得出。至于 (i) \(\Rightarrow\) (ii)，请注意，对于 (i) 中的每个 \(\psi \in \text{PL}_D(r)\)，概率为 1 的事件 \(\Omega(\psi)\)，在其上 \(\int_{\mathbb{R}^D} \psi dP_n \to \int_{\mathbb{R}^D} \psi dP\)，可能（先验上）依赖于 \(\psi\)。关键在于，在 (i) 下，定理 B.17 保证了这种收敛实际上在这样的一系列事件 \(\Omega(\psi)\) 的可数交汇上在 \(\text{PL}_D(r, 1)\) 上是一致的。更准确地说，令 \(T_r \subseteq \text{PL}_D(r)\) 如定理 B.17 中所示，我们看到 \(\cap_{\psi \in T_r} \Omega(\psi)\) 是概率为 1 的事件，在其上 (ii) 和 (iii) 成立。

### (b) 概率收敛：

(i) \(\Rightarrow\) (ii)：首先，我们证明，如果对于每个 \(\psi \in \text{PL}_D(r)\) 有 \(P_n(\psi) \xrightarrow{p} P(\psi)\)，则 \(\tilde{d}_r(P_n, P) \xrightarrow{p} 0\)，或等价地，序列 \((\tilde{d}_r(P_n, P) : n \in \mathbb{N})\) 的每个子序列都有一个更短的子序列几乎处处收敛于 0。只需证明，对于任何子序列 \((Q_k) \equiv (P_{n_k})\)，存在一个更短的子序列 \((Q_{k_\ell})\)，使得概率为 1 时，对所有 \(\psi \in T_r \subseteq \text{PL}_D(r)\) 有 \(Q_{k_\ell}(\psi) \to P(\psi)\)；确实，所需结论随即直接由 (a) 得出。为此，将可数集合 \(T_r\) 的元素枚举为 \(\psi_1, \psi_2, \dots\) 并采用对角线论证：由于 \(Q_k(\psi_1) \xrightarrow{p} P(\psi_1)\)，我们可以从 \((Q_k)\) 中提取一个子序列 \((Q_{k_{1,\ell}})\)，使得当 \(\ell \to \infty\) 时 \(Q_{k_{1,\ell}}(\psi_1) \xrightarrow{a.s.} P(\psi_1)\)。继续归纳，我们看到对于每个 \(J \in \mathbb{N}\)，存在 \((Q_{k_{J-1,\ell}})\) 的一个子序列 \((Q_{k_{J,\ell}})\) 和一个概率为 1 的事件，在其上当 \(\ell \to \infty\) 时，对所有 \(1 \le j \le J\) 有 \(Q_{k_{J,\ell}}(\psi_j) \to P(\psi_j)\)。最后，令 \(\ell \in \mathbb{N}\) 时 \(Q_{k_\ell} := Q_{k_{\ell,\ell}}\)，并观察到概率为 1 时，对所有 \(j \in \mathbb{N}\) 有 \(Q_{k_{J,\ell}}(\psi_j) \to P(\psi_j)\) 当 \(\ell \to \infty\)，正如所要求的那样。

