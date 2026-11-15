

还形式化了\(\text{PL}_D(r)\)中的函数与\(d_r\)中的收敛性（或等价地\(\tilde{d}_r\)）之间的联系。

作为证明定理 B.17 的第一步，建立以下内容是有帮助的。

### 命题 B.16.

存在一个在 \(\mathbb{R}^D\) 上的有界 Lipschitz 函数的可数集合 \(T'_r\)，使得对所有 \(P, Q \in \mathcal{P}(r)\)，都有 \(\tilde{d}_r(P, Q) = \sup_{\psi \in T'_r} | \int_{\mathbb{R}^D} \psi dP - \int_{\mathbb{R}^D} \psi dQ | \in [0, \infty)\)。

我们构造的集合 \(T'_r\) 的一个关键性质是：对任意 \(\psi \in \text{PL}_D(r)\)，都存在一个在 \(T'_r\) 中的序列 \((\psi_\ell)\)，它在 \(\mathbb{R}^D\) 的紧子集上一致收敛到 \(\psi\)。在后续证明中，当 \(Q\) 是 \(\mathbb{R}^D\) 上的有符号 Borel 测度且 \(f : \mathbb{R}^D \to \mathbb{R}\) 是 \(Q\)-可积函数时，我们将写 \(Q(f)\) 作为 \(\int_{\mathbb{R}^D} f dQ\) 的简写。

**证明。** 对 \(N \in \mathbb{N}\)，令 \(B_N \equiv \bar{B}_D(0, N) := \{ x \in \mathbb{R}^D : \|x\| \le N \}\)，并对 \(x \in \mathbb{R}^D\) 定义 \(f_N(x) := (N - \|x\|) \vee 0 \wedge 1\)，因此 \(f_N\) 在 \(\mathbb{R}^D\) 上是 1-Lipschitz 的，\(f_N = 1\) 在 \(B_{N-1}\) 上，且 \(f_N = 0\) 在 \(B_N^c\) 上。在下面的论证中（以及在定理 B.17 的证明中），我们将在多处将 \(f_N\) 作为（不连续的）指示函数 \(\mathbb{1}_{B_N}\) 的替代。特别要注意的是，若 \(\bar{g} : B_N \to \mathbb{R}\) 在 \(B_N\) 上是 Lipschitz 的，那么由 \(g(x) := \bar{g}(x)f_N(x)\) 定义的函数 \(g : \mathbb{R}^D \to \mathbb{R}\) 是 Lipschitz 的，并且支撑在紧集 \(B_N\) 上。

回顾 (1.4) 中 \(\tilde{d}_r, \mathcal{P}(r)\) 的定义，并令 \(\widetilde{\text{PL}}_D(r, 1)\) 表示所有满足 \(\phi(0) = 0\) 的 \(\phi \in \text{PL}_D(r, 1)\) 的集合，从 (1.3) 可得

\(\begin{aligned} \tilde{d}_r(P, Q) &= \sup_{\phi \in \widetilde{\text{PL}}_D(r, 1)} |(P - Q)(\phi)| \le \sup_{\phi \in \widetilde{\text{PL}}_D(r, 1)} (P + Q)(|\phi|) \\ &\le \int_{\mathbb{R}^D} (\|x\| + \|x\|^r) d(P + Q)(x) < \infty \end{aligned} \quad \text{(B.13)}\)

对所有 \(P, Q \in \mathcal{P}(r)\) 成立。若 \(\phi \in \widetilde{\text{PL}}_D(r, 1)\)，则

\(|\phi(x) - \phi(y)| \le \|x - y\|(1 + \|x\|^{r-1} + \|y\|^{r-1}) \le (1 + 2N^{r-1})\|x - y\|\)

对所有 \(x, y \in B_N\) 成立，因此 \(\phi|_{B_N}\) 属于满足 \(g(0) = 0\) 的 \((1 + 2N^{r-1})\)-Lipschitz 函数 \(g : B_N \to \mathbb{R}\) 的集合，我们将其记作 \(\mathcal{G}_N\)。

由于 \(B_N\) 是紧的且 \(\mathcal{G}_N\) 一致有界和一致等连续，

\(\mathcal{G}_N\) 因此根据阿塞利-阿斯柯利定理（例如 Dudley, 2002, Theorem 2.4.7）在 \(B_N\) 上的 supremum 范数下是紧的。因此它是全界的，所以对每个 \(m \in \mathbb{N}\)，我们可以找到一个有限子集 \(\tilde{\mathcal{H}}_{N,m} \subseteq \mathcal{G}_N\)，使得对任意 \(g \in \mathcal{G}_N\)，都存在 \(\tilde{h} \in \tilde{\mathcal{H}}_{N,m}\)，满足 \(\sup_{x \in B_N} |g(x) - \tilde{h}(x)| < 1/m\)。每个 \(\tilde{h} \in \tilde{\mathcal{H}}_{N,m}\) 都可与函数 \(h : \mathbb{R}^D \to \mathbb{R}\) 相关联，该函数由 \(h(x) := \tilde{h}(x)f_N(x)\) 定义。根据上一段的论证，所有这类 \(h\) 的集合 \(\mathcal{H}_{N,m}\) 是支撑在 \(B_N\) 上的有界 Lipschitz 函数的有限集。

因此，\(T'_r := \bigcup_{N,m \in \mathbb{N}} \mathcal{H}_{N,m}\) 是 \(\mathbb{R}^D\) 上一个有界 Lipschitz 函数的可数集合，我们声称它具有所期望的性质，即对任意两个概率测度 \(P, Q \in \mathcal{P}(r)\)，都有 \(\tilde{d}_r(P, Q) = \sup_{\psi \in T'_r} |(P-Q)(\psi)|\)。的确，对固定的 \(P, Q \in \mathcal{P}(r)\)，函数 \(\psi_r: x \mapsto \|x\| + \|x\|^r\) 在 \(\mathbb{R}^D\) 上关于 \(P\) 和 \(Q\) 均可积，因此根据主导收敛定理，当 \(N \to \infty\) 时，有 \(P(\psi_r \mathbf{1}_{B_{N-1}^c}) \to 0\) 和 \(Q(\psi_r \mathbf{1}_{B_{N-1}^c}) \to 0\)。于是，对任意 \(\varepsilon > 0\)，存在足够大的 \(N \equiv N_{\varepsilon, r} \in \mathbb{N}\)，使得 \(P(\psi_r \mathbf{1}_{B_{N-1}^c}) < \varepsilon/4\) 和 \(Q(\psi_r \mathbf{1}_{B_{N-1}^c}) < \varepsilon/4\)。选择 \(m \equiv m_{\varepsilon} \in \mathbb{N}\) 使得 \(1/m < \varepsilon/4\)，我们从前一段推断，对任意 \(\phi \in \widetilde{\text{PL}}_D(r, 1)\)，都存在 \(\tilde{h} \in \tilde{\mathcal{H}}_{N,m}\)，使得 \(\sup_{x \in B_N} |\phi(x) - \tilde{h}(x)| < 1/m < \varepsilon/4\)。令 \(h\) 为 \(\mathcal{H}_{N,m} \subseteq T'_r\) 中的对应函数，则有

\[
\begin{aligned}
|(P-Q)(\phi)| &\le |(P-Q)(\phi(1 - f_N))| + |(P-Q)(\phi f_N - h)| + |(P-Q)(h)| \\
&\le (P + Q)(|\phi|(1 - f_N)) + (P + Q)(|\phi f_N - h|) + \sup_{\psi \in T'_r}|(P-Q)(\psi)| \tag{B.14}
\end{aligned}
\]

由三角不等式得。由于 \(\phi \in \widetilde{\text{PL}}_D(r, 1)\)，对所有 \(x \in \mathbb{R}^D\) 有 \(|\phi(x)| = |\phi(x) - \phi(0)| \le \|x\| + \|x\|^r = \psi_r(x)\)，故

由我们对 \(N\) 的选择以及 \(0 \le 1 - f_N \le \mathbf{1}_{B_{N-1}^c}\) 这一事实可知。此外，

由我们对 \(h\) 的选择可知，因此由 (B.14) 得出 \(|(P - Q)(\phi)| < \varepsilon + \sup_{\psi \in T'_r} |(P - Q)(\psi)|\)。由于这对每个 \(\phi \in \widetilde{\text{PL}}_D(r, 1)\) 和所有 \(\varepsilon > 0\) 均成立，结果得证。

### 定理 B.17.

设 \(P \in \mathcal{P}_D(r)\)，并让 \((P_n)\) 为 \(\mathcal{P}_D(r)\) 中的概率测度序列。则存在一个可数集合 \(T_r \subseteq \text{PL}_D(r)\)，使得以下命题等价：

- (i) 对所有 \(\psi \in T_r\) 有 \(\int_{\mathbb{R}^D} \psi \, dP_n \rightarrow \int_{\mathbb{R}^D} \psi \, dP\);
- (ii) \(\tilde{d}_r(P_n, P) \rightarrow 0\);
- (iii) \(d_r(P_n, P) \rightarrow 0\)。

一个合适的集合 \(T_r \subseteq \text{PL}_D(r)\) 可以通过扩充在命题 B.16（证明中）定义的有界 Lipschitz 函数集合 \(T'_r\) 来构造。

### 注释 B.18.

利用定理 B.17，我们可以验证 \(\tilde{d}_r\) 是在 \(\mathcal{P}(r) \equiv \mathcal{P}_D(r)\) 上的一个度量，它生成与 \(d_r\) 相同的拓扑。确实，从 (1.4) 和 (B.13) 清楚可知，\(\tilde{d}_r\) 取值于 \([0, \infty)\) 并在 \(\mathcal{P}(r)\) 上满足三角不等式。此外，若 \(P, Q \in \mathcal{P}(r)\) 满足 \(\tilde{d}_r(P, Q) = 0\)，则通过在上述 (ii) 中取对所有 \(n\) 的 \(P_n = Q\)，我们推出 \(d_r(P, Q) = 0\)。由于 \(d_r\) 是在 \(\mathcal{P}(r)\) 上的一个度量（例如 Villani, 2003, Theorem 7.3），这就得出 \(P = Q\)，如所要求。事实上，\((\mathcal{P}(r), d_r)\) 是一个可分完备度量空间（例如 Panaretos and Zemel, 2020, Theorem 2.2.7 and Proposition 2.2.8），因此根据定理 B.17 中的等价性 (ii) \(\Leftrightarrow\) (iii)，\((\mathcal{P}(r), \tilde{d}_r)\) 也同样如此。

**证明。** (i) \(\Rightarrow\) (ii)：如同在命题 B.16 的证明中，函数 \(f_N: x \mapsto (N - \|x\|) \vee 0 \wedge 1\) 在下面的论证中再次作为每个 \(N \in \mathbb{N}\) 的 \(B_N \equiv \bar{B}_D(0, N) = \{x \in \mathbb{R}^D : \|x\| \le N\}\) 的指示函数 \(\mathbb{1}_{B_N}\) 的 Lipschitz 替代；注意 \(f_N = 1\) 在 \(B_{N-1}\) 上，\(f_N = 0\) 在 \(B_N^c\) 上，且 \(f_N\) 在 \(\mathbb{R}^D\) 上是 1-Lipschitz 的。鉴于此以及 \(\psi_r: x \mapsto \|x\| + \|x\|^r\) 属于 \(\text{PL}_D(r)\) 这一事实，函数 \(\psi_r(1 - f_N)\) 对每个 \(N \in \mathbb{N}\) 也位于 \(\text{PL}_D(r)\) 中。

令 \(\tilde{\mathcal{H}}_{N,m}\) 和 \(\mathcal{H}_{N,m}\) 为命题 B.16 证明中对每个 \(N, m \in \mathbb{N}\) 构造的有限集合，并令 \(T'_r := \bigcup_{N,m \in \mathbb{N}} \mathcal{H}_{N,m}\)。由于

