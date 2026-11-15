

\( h^k \equiv h^k(n) \) 是 \( m^0(n), \gamma(n) \) 和 \( W(n) \) 的一个确定性Borel可测函数。而且对于所有 \( x, x' \in \mathbb{R}^n \) 及其对应的分量经验分布 \( \nu_n(x), \nu_n(x') \)，有

\( |d_r(\nu_n(x), \bar{\mu}^k) - d_r(\nu_n(x'), \bar{\mu}^k)| \le d_r(\nu_n(x), \nu_n(x')) \le (n^{-1} \sum_{i=1}^n |x_i - x'_i|^r)^{1/r} = \|x - x'\|_{n,r} \)

因为 \( d_r \) 是一个度量，所以 \( x \mapsto d_r(\nu_n(x), \bar{\mu}^k) \) 在 \( \mathbb{R}^n \) 上是连续的。

因为 \( \{(a_1, a_2, \dots) \in \mathbb{R}^{\mathbb{N}} : \lim_{n \to \infty} a_n = 0\} \) 是 \( \mathbb{R}^{\mathbb{N}} \) 的一个Borel子集，我们得出结论：\( g : (u, v) \mapsto \mathbb{P}\{\lim_{n \to \infty} g_n(u(n), v(n), W(n)) = 0\} \) 是 \( E \times E \) 上一个定义良好的Borel可测函数，且对所有 \( (u, v) \in E^* \) 满足 \( g(u, v) = 1 \)。

现在更一般地假设 \( (\Upsilon, \Gamma) \) 和 \( (W(n) : n \in \mathbb{N}) \) 是独立的。如果 \( (\Upsilon, \Gamma) \in E^* \) 几乎必然成立，那么对来自 (2.1) 的相应AMP迭代序列 \( (h^k(n) : n \in \mathbb{N}) \),

\( \mathbb{P}\left( \lim_{n\to\infty} d_r(\mu_n^k, \bar{\mu}^k) = 0 \right) = \mathbb{P}\left( \lim_{n\to\infty} g_n(m^0(n), \gamma(n), W(n)) = 0 \right) = \mathbb{E}\left\{ \mathbb{P}\left( \lim_{n\to\infty} g_n(m^0(n), \gamma(n), W(n)) = 0 \mid \Upsilon, \Gamma \right) \right\} = \mathbb{E}(g(\Upsilon, \Gamma)) \ge \mathbb{E}(g(\Upsilon, \Gamma) \mathbb{1}_{\{(\Upsilon, \Gamma) \in E^*\}}) = 1, \)

其中第三个等号来自独立性假设和Lemma B.7。因此，\( d_r(\mu_n^k, \bar{\mu}^k) \xrightarrow{a.s.} 0 \) 当 \( n \to \infty \)，并且根据Corollary B.21(a)，此外 \( \tilde{d}_r(\mu_n^k, \bar{\mu}^k) \xrightarrow{a.s.} 0 \)。

## A.6 第二节的辅助结果与证明

_Lemma 2.2 的证明._ 我们对 \( k \) 进行归纳证明，首先注意基例 \( k=1 \) 是平凡的，因为根据 (A4) 有 \( \bar{T}^{[1]} = \tau_1^2 > 0 \)。现在对于 \( k \ge 2 \) 和 \( a \equiv (a_1, \dots, a_k) \in \mathbb{R}^k \)，回顾 \( a^\top \bar{T}^{[k]}a \) 的表达式 (2.7)。如果 \( a_1 \neq 0 = a_2 = \cdots = a_k \)，则 \( a^\top \bar{T}^{[k]}a = (a_1 \tau_1)^2 > 0 \)，与基例的情况相同。另一方面，如果存在某个 \( 2 \le L \le k \) 使得 \( a_L \neq 0 \)，那么根据 (A4)，我们可以找到满足 \( \pi(B_L) > 0 \) 的 \( B_L \subseteq \mathbb{R} \)，使得只要 \( y \in B_L \)，映射 \( x_{L-1} \mapsto a_L f_{L-1}(x_{L-1}, y) \) 就是非恒定的。对于所有这样的 \( y \)，注意 \( (x_1, \dots, x_{k-1}) \mapsto \sum_{\ell=2}^k a_\ell f_{\ell-1}(x_{\ell-1}, y) \) 在 \( \mathbb{R}^{k-1} \) 上是非恒定的。现在根据归纳假设，\( (G_1, \dots, G_{k-1}) \) 拥有一个正定协方差矩阵 $\bar{\mathrm{T}}^{[k-1]}$，因此随机变量 $a_1 F_0(y) + \sum_{\ell=2}^k a_\ell f_{\ell-1}(G_{\ell-1}, y)$ 在任何 $y \in B_L$ 时都是非退化的。由于 $\bar{\gamma} \sim \pi$ 与 $G_1, \dots, G_{k-1}$ 独立，且 $\mathbb{P}(\bar{\gamma} \in B_L) = \pi(B_L) > 0$，可知 $a_1 F_0(\bar{\gamma}) + \sum_{\ell=2}^k a_\ell f_{\ell-1}(G_{\ell-1}, \bar{\gamma})$ 也是非退化的。因此，在所有情况下，根据 (2.7) 和 (A3)，当 $a \neq 0$ 时有 $a^\top \bar{\mathrm{T}}^{[k]} a > 0$，正如所声称的。

_Remark A.5 的证明._ 由于 $\tilde{f}_0$ 是Lipschitz连续且 $\bar{\eta}, \bar{\gamma} \in \mathcal{P}_1(2)$，我们有 $\mathbb{E}\{\|(\tilde{f}_0(\bar{\eta}, \bar{\gamma}), \bar{\gamma})\|^2\} < \infty$，因此 $\mu^0 \in \mathcal{P}_2(2)$。根据Corollary B.21(b)，(A1$^+$) 的一个等价表述为

$\frac{1}{n} \sum_{i=1}^n \psi(m_i^0, \gamma_i) \xrightarrow{\mathcal{L}} \mathbb{E}\{\psi(\tilde{f}_0(\bar{\eta}, \bar{\gamma}), \bar{\gamma})\}$

对所有 $\psi \in \text{PL}_2(2)$ 均成立。特别是，映射 $(x, y) \mapsto x^2$ 属于 $\text{PL}_2(2)$，因此 $\|m^0\|_n^2 = n^{-1} \sum_{i=1}^n |m_i^0|^2 \xrightarrow{\mathcal{L}} \mathbb{E}(\tilde{f}_0(\bar{\eta}, \bar{\gamma})^2) =: \tau_1^2$，这给出了 (A2) 的第一部分。此外，函数 $F_0: \mathbb{R} \to \mathbb{R}$ 由 $F_0(y) := \mathbb{E}(\tilde{f}_0(\bar{\eta}, y))$ 定义，它是Lipschitz连续的，并且由于 $\bar{\eta}, \bar{\gamma}$ 独立，根据Lemma B.7和Jensen不等式，

$\mathbb{E}(F_0(\bar{\gamma})^2) = \mathbb{E}\{\mathbb{E}(\tilde{f}_0(\bar{\eta}, \bar{\gamma}) | \bar{\gamma})^2\} \leq \mathbb{E}\{\mathbb{E}(\tilde{f}_0(\bar{\eta}, \bar{\gamma})^2 | \bar{\gamma})\} = \tau_1^2$.

对于每个Lipschitz函数 $\phi: \mathbb{R} \to \mathbb{R}$，Lemma B.22 保证 $(x, y) \mapsto x \phi(y)$ 属于 $\text{PL}_2(2)$，因此

$\langle m^0, \phi(\gamma) \rangle_n = \frac{1}{n} \sum_{i=1}^n m_i^0 \phi(\gamma_i) \xrightarrow{\mathcal{L}} \mathbb{E}(\tilde{f}_0(\bar{\eta}, \bar{\gamma}) \cdot \phi(\bar{\gamma})) = \mathbb{E}\{\mathbb{E}(\tilde{f}_0(\bar{\eta}, \bar{\gamma}) | \bar{\gamma}) \phi(\bar{\gamma})\} = \mathbb{E}(F_0(\bar{\gamma}) \phi(\bar{\gamma}))$，

其中最后一个等号再次来自Lemma B.7。因此，(A3) 也成立。

下面的辅助结果用于控制 Proposition A.16(a) 证明中在 (A.22) 定义的偏差项 $\Delta^{k+1}$ 中的第三个求和项。

**Lemma A.18.** 对于 $n \in \mathbb{N}$ 和 $k \in \{0, 1, \dots, n-1\}$，设 $\tilde{Z}^{k+1} \equiv \tilde{Z}^{k+1}(n)$ 如 Proposition A.11 所示，使得 $\tilde{Z}^{k+1} \sim N_n(0, I_n)$ 与 $\mathcal{S}_k$ 独立。如果 $\xi_1, \dots, \xi_k \stackrel{\text{iid}}{\sim} N(0, 1)$ 且 $r \geq 1$，则 $\| P_k \tilde{Z}^{k+1} \|_{n, r}$ 在随机意义上被 $\sum_{i=1}^k |\xi_i| / n^{1/(r \vee 2)}$ 支配。

证明. 注意 \( P_k \) 是一个秩为 \( r_k \le k \) 的 \( \mathcal{S}_k \)-可测投影矩阵。由于 \( \tilde{Z}^{k+1} \) 与 \( \mathcal{S}_k \) 独立，因此根据 Remark B.4，它在给定 \( \mathcal{S}_k \) 下的条件分布为 \( N_n(0, I_n) \)。现在设 \( \xi_1, \dots, \xi_k \stackrel{\text{iid}}{\sim} N(0,1) \) 与 \( \mathcal{S}_k \) 独立，并让 \( \{\tilde{m}^1, \dots, \tilde{m}^{r_k}\} \) 成为 \( \text{Im}(M_k) = \text{Im}(P_k) \) 的任意一个 \( \mathcal{S}_k \)-可测正交归一基，如同 Remark A.10 所述。回顾如果 \( Z \sim N_n(0, I_n) \) 且 \( P \in \mathbb{R}^{n \times n} \) 是一个秩为 \( p \) 的确定性投影矩阵，则 \( PZ \sim N(0, P) \)，这也是当 \( \zeta_1, \dots, \zeta_p \stackrel{\text{iid}}{\sim} N(0,1) \) 且 \( \{u_1, \dots, u_p\} \) 是 \( \text{Im}(P) \) 的任意正交归一基时 \( \sum_{i=1}^p \zeta_i u_i \) 的分布。由此及Lemma B.6(b) 推断，\( P_k \tilde{Z}^{k+1} \) 和 \( \sum_{i=1}^{r_k} \xi_i \tilde{m}^i \) 在给定 \( \mathcal{S}_k \) 下都具有条件分布 \( N_n(0, P_k) \)。这意味着 \( \|P_k \tilde{Z}^{k+1}\|_{n,r} \stackrel{d}{=} \|\sum_{i=1}^{r_k} \xi_i \tilde{m}^i\|_{n,r} \)。

现在对于所有 \( x \in \mathbb{R}^n \)，根据 Hölder 不等式以及 \( \|\cdot\|_{p'} \le \|\cdot\|_p \)（当 \( 1 \le p \le p' \)）的事实，我们有 \( \|x\|_{n,r} = n^{-1/r} \|x\|_r \le n^{-1/(r \vee 2)} \|x\|_2 \)。由于根据定义对所有 \( i \) 有 \( \|\tilde{m}^i\|_2 = 1 \)，由此及 \( \|\cdot\|_{n,r} \) 的三角不等式可得 \( \|\sum_{i=1}^{r_k} \xi_i \tilde{m}^i\|_{n,r} \le \sum_{i=1}^{r_k} |\xi_i| \|\tilde{m}^i\|_{n,r} \le \sum_{i=1}^{r_k} |\xi_i| / n^{1/(r \vee 2)} \le \sum_{i=1}^k |\xi_i| / n^{1/(r \vee 2)} \)。将这与上一段的结论结合即可得到结果。

## A.7 带矩阵值迭代的AMP

如前文第2.1节所述，对于更一般的抽象AMP递归（其中迭代为矩阵而非向量），可以得到状态演化表征。在此，我们将简要描述非对称迭代 (2.10) 的扩展版本，它被用于在第4.1节中建立GAMP的主定理。

对于 \( n, p \in \mathbb{N} \)，设 \( W \in \mathbb{R}^{n \times p} \)、\( \beta \in \mathbb{R}^p \) 和 \( \gamma \in \mathbb{R}^n \) 如 (B0) 所示。对于 \( \ell_E, \ell_H \in \mathbb{N} \)，设 \( (g_k, f_{k+1} : k \in \mathbb{N}_0) \) 为两个Lipschitz函数序列 \( g_k: \mathbb{R}^{\ell_E} \times \mathbb{R} \to \mathbb{R}^{\ell_H} \) 和 \( f_{k+1}: \mathbb{R}^{\ell_H} \times \mathbb{R} \to \mathbb{R}^{\ell_E} \)，它们按行应用于矩阵。给定 \( Q^{-1} := 0 \in \mathbb{R}^{n \times \ell_H} \)、\( B_0 \in \mathbb{R}^{\ell_E \times \ell_H} \) 和 \( M^0 \in \mathbb{R}^{p \times \ell_E} \)，归纳式定义

\[
E^k := W M^k - Q^{k-1} B_k^\top, \qquad Q^k := g_k(E^k, \gamma),
\]

\[
C_k := n^{-1} \sum_{i=1}^n g_k'(E_i^k, \gamma_i), \qquad H^{k+1} := W^\top Q^k - M^k C_k^\top,
\]

\[
M^{k+1} := f_{k+1}(H^{k+1}, \beta),
\]

\[
B_{k+1} := n^{-1} \sum_{j=1}^p f_{k+1}'(H_j^{k+1}, \beta_j)
\]

(A.52)

