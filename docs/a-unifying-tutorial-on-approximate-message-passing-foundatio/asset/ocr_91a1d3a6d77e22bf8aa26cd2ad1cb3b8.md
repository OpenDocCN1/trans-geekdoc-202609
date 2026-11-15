# A.2. Conditional Distributions for Symmetric AMP

where \(y^j \equiv y^j(n) := Wm^j = h^{j+1} + b_j m^{j-1}\) for \(j = 0, 1, \dots, k - 1\). For convenience, we also define \(M_0(n) = Y_0(n) := 0 \in \mathbb{R}^n\). Then the symmetric AMP recursion (2.1) can be rewritten as \(WM_k = Y_k\) for \(k \in \mathbb{N}\).

For each \(0 \le k \le n - 1\), let \(P_k := M_k M_k^+ = M_k(M_k^\top M_k)^+ M_k^\top\) and \(P_k^\perp := I_n - P_k\) be the \(n \times n\) matrices representing the orthogonal projections onto \(\text{Im}(M_k) := \text{span}\{m^j : 0 \le j \le k - 1\}\) and \(V_k := \text{Im}(M_k)^\perp\) respectively, and define \(r_k := \text{rank}(M_k) = \text{dim Im}(M_k)\). Let \(\dot{m}^k := P_k^\perp m^k\) for \(0 \le k \le n - 1\), so that the span of \(\dot{m}^k\) is the orthogonal complement of \(V_{k+1}\) within \(V_k\). Furthermore, define \(\mathcal{S}_{-1} := \{\emptyset, \Omega\}\) to be the trivial \(\sigma\)-algebra, and for \(k \in \mathbb{N}_0\), let

\(\mathcal{S}_k := \sigma(\gamma, m^0, h^j : 1 \le j \le k).\)

Then since \(b_k, m^k\) are measurable functions of \(h^k\) and \(\gamma\), we see from (2.1) that

\(\mathcal{S}_k = \sigma(\gamma, m^0, y^j : 0 \le j \le k - 1),\) (A.3)

and that \(m^0, \dots, m^k\) and \(r_0, \dots, r_{k+1}\) are \(\mathcal{S}_k\)-measurable for each \(-1 \le k \le n - 1\). (It is not true in general that \(\mathbb{P}(r_k = k) = 1\) for all \(1 \le k \le n - 1\), even in recursions (2.1) with non-pathological \(f_k\).)

Our first task is to establish an important fact (Proposition A.8) that will be used to derive the (regular) conditional distributions of \(W\) and \(h^{k+1}\) given \(\mathcal{S}_k\) in Proposition A.11 below, for each fixed \(k \in \{0, 1, \dots, n - 1\}\). We will use the symbol ‘\(\stackrel{d}{=} |_{\mathcal{S}_k}\)’ to indicate (almost-sure) equality of conditional distributions given \(\mathcal{S}_k\), a notion that is defined formally in Section B.2.

**Proposition A.8.** Fix \(0 \le k \le n - 1\) and suppose as in (A0) that \(W \sim \text{GOE}(n)\) is independent of \((m^0, \gamma)\). If \(\tilde{U}_k\) is any \(\mathcal{S}_{k-1}\)-measurable \(n \times (n - r_k)\) matrix whose columns form an orthonormal basis of \(V_k\), then given \(\mathcal{S}_{k-1}\), the matrix \(\tilde{U}_k^\top W \tilde{U}_k\) has conditional distribution \(\text{GOE}(n - r_k)\) and is conditionally independent of \(\mathcal{S}_k\). Consequently, \(\tilde{U}_k^\top W \tilde{U}_k\) has conditional distribution \(\text{GOE}(n - r_k)\) given \(\mathcal{S}_k\), and if \(\tilde{W} \sim \text{GOE}(n)\) is independent of \(\mathcal{S}_k\), then \(\tilde{U}_k^\top W \tilde{U}_k \stackrel{d}{=}|_{\mathcal{S}_k} \tilde{U}_k^\top \tilde{W} \tilde{U}_k\).

**Remark A.9.** Consider the important special case where \(\mathbb{P}(r_k = k) = 1\). Then under the hypotheses of the proposition, \(\tilde{U}_k^\top W \tilde{U}_k \sim \text{GOE}(n - k)\)