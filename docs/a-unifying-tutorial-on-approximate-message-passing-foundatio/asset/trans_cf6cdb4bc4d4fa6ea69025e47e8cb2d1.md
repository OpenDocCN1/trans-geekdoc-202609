

\(||W||_{2\to 2}:=\sup_{u\neq 0}||Wu||_2/||u||_2=O_c(1)\) 对于 \(W\sim\text{GOE}(n)\) 当 \(n\to\infty\)（例如 Anderson et al., 2010; Knowles and Yin, 2013）；有关更多详情，请参见 Javanmard and Montanari (2013, 第 4.2.1 节)、Berthier et al. (2020, 第 5.4 节) 和 Fan (2022, 附录 D)。

这些扰动论证并不能简单地推广到 \(r\neq 2\) 的 \(d_r\) 收敛结果，因为 \(||W||_{r\to r}:=\sup_{u\neq 0}||Wu||_r/||u||_r\) 对于 \(r\in[1,2)\cup(2,\infty]\) 不是 \(O_c(1)\) 甚至不是 \(O_p(1)\)。事实上，给定 \(r\in[1,2)\) 和独立的 \(Z\sim N_n(0,I_n)\) 及 \(\zeta\sim N(0,1/n)\)，Lemma A.14 得出

\(||W||_{r\to r}\ge||We_1||_r\stackrel{d}{=}||n^{-1/2}Z+\zeta e_1||_r=n^{1/r-1/2}||Z||_{n,r}+o_p(1),\)

其中 \(||Z||_{n,r}\stackrel{\mathcal{L}}{=}E(|Z_1|^r)^{1/r}\in(0,\infty)\)。此外，当 \(1/r+1/r'=1\) 时，\(||W||_{r\to r}=||W||_{r'\to r'}\)。

**Remark A.7.** (A5) 是一个非空虚但非常温和的条件。对于任何 Lipschitz \(f:\mathbb{R}^2\rightarrow\mathbb{R}\)，偏导数 \(\frac{\partial f}{\partial x}\) 在其定义域上是有界的，该定义域是勒贝格测度满集的 Borel 集。尽管如此，仍存在一些 Lipschitz \(f:\mathbb{R}^2\rightarrow\mathbb{R}\) 的示例，其中 \(\frac{\partial f}{\partial x}\) 不能扩展为在 \((\lambda\otimes\pi)\)-几乎处处连续的 \(\mathbb{R}^2\) 上的函数（参见 Remark B.15）。尽管如此，在任何实际 AMP 程序中，做出这种病态的 \(f_k\) 选择是不可想象的，在这些程序中，函数 \(f'_k\) 通常具有这样的性质：对于每个 \(y\in\mathbb{R}\)，\(\{x\in\mathbb{R}:(x,y)\in D_k\}\) 是有限的，因而满足 (A5)。

## A.2 对称 AMP 的条件分布

在本小节中，我们固定 \(n\in\mathbb{N}\)，并且在大多数地方，我们省略了所有量（如 \(W\equiv W(n)\) 和 \(h^k\equiv h^k(n)\)）对 \(n\) 的依赖。当我们提到 *标准正交* 集时，隐含的意思是组成向量具有单位欧几里得范数，即底层内积是 \(\langle\cdot,\cdot\rangle\) 而不是 \(\langle\cdot,\cdot\rangle_n\)。关于条件分布的所有陈述都可以正式地理解为正则条件概率的严格定义，如第 B.2 节所述。下面结果的证明见第 A.3 节。

在第 2.1 节的设置下，定义 \(n\times k\) 矩阵

\(H_k\equiv H_k(n):=(h^1\cdots h^k),\) \(M_k\equiv M_k(n):=(m^0m^1\cdots m^{k-1}),\)
\(Y_k\equiv Y_k(n):=(y^0y^1\cdots y^{k-1}),\)

其中 \(y^j \equiv y^j(n) := Wm^j = h^{j+1} + b_j m^{j-1}\) 对 \(j = 0, 1, \dots, k - 1\)。为方便起见，我们还定义 \(M_0(n) = Y_0(n) := 0 \in \mathbb{R}^n\)。那么对称 AMP 递归 (2.1) 可以重写为 \(WM_k = Y_k\)，其中 \(k \in \mathbb{N}\)。

对于每个 \(0 \le k \le n - 1\)，令 \(P_k := M_k M_k^+ = M_k(M_k^\top M_k)^+ M_k^\top\) 和 \(P_k^\perp := I_n - P_k\) 为分别表示正交投影到 \(\text{Im}(M_k) := \text{span}\{m^j : 0 \le j \le k - 1\}\) 和 \(V_k := \text{Im}(M_k)^\perp\) 的 \(n\times n\) 矩阵，并定义 \(r_k := \text{rank}(M_k) = \text{dim Im}(M_k)\)。对于 \(0 \le k \le n - 1\)，令 \(\dot{m}^k := P_k^\perp m^k\)，这样 \(\dot{m}^k\) 的张成就是 \(V_k\) 内 \(V_{k+1}\) 的正交补。此外，定义 \(\mathcal{S}_{-1} := \{\emptyset, \Omega\}\) 为平凡 \(\sigma\)-代数，并对 \(k \in \mathbb{N}_0\)，令

\(\mathcal{S}_k := \sigma(\gamma, m^0, h^j : 1 \le j \le k).\)

由于 \(b_k, m^k\) 是 \(h^k\) 和 \(\gamma\) 的可测函数，从 (2.1) 我们可知

\(\mathcal{S}_k = \sigma(\gamma, m^0, y^j : 0 \le j \le k - 1),\) (A.3)

并且对于每个 \(-1 \le k \le n - 1\)，\(m^0, \dots, m^k\) 和 \(r_0, \dots, r_{k+1}\) 都是 \(\mathcal{S}_k\)-可测的。（一般来说，对所有 \(1 \le k \le n - 1\) 都有 \(\mathbb{P}(r_k = k) = 1\) 并不成立，即使是在具有非病态 \(f_k\) 的递归 (2.1) 中也是如此。）

我们的首要任务是建立一个重要事实（命题 A.8），它将用于在下面的命题 A.11 中推导给定 \(\mathcal{S}_k\) 下的 \(W\) 和 \(h^{k+1}\) 的（正则）条件分布，针对每个固定 \(k \in \{0, 1, \dots, n - 1\}\)。我们将使用符号 ‘\(\stackrel{d}{=}|_{\mathcal{S}_k}\)’ 来表示给定 \(\mathcal{S}_k\) 下的（几乎处处）条件分布相等，这一概念在第 B.2 节中有正式定义。

**Proposition A.8.** 固定 \(0 \le k \le n - 1\) 并假设如 (A0) 中所述 \(W \sim \text{GOE}(n)\) 与 \((m^0, \gamma)\) 独立。如果 \(\tilde{U}_k\) 是任何 \(\mathcal{S}_{k-1}\)-可测的 \(n\times(n-r_k)\) 矩阵，其列构成 \(V_k\) 的一组标准正交基，那么给定 \(\mathcal{S}_{k-1}\) 时，矩阵 \(\tilde{U}_k^\top W \tilde{U}_k\) 具有条件分布 \(\text{GOE}(n-r_k)\) 且与 \(\mathcal{S}_k\) 条件独立。因此，给定 \(\mathcal{S}_k\) 时，\(\tilde{U}_k^\top W \tilde{U}_k\) 具有条件分布 \(\text{GOE}(n-r_k)\)，并且如果 \(\tilde{W} \sim \text{GOE}(n)\) 与 \(\mathcal{S}_k\) 独立，则 \(\tilde{U}_k^\top W \tilde{U}_k \stackrel{d}{=}|_{\mathcal{S}_k} \tilde{U}_k^\top \tilde{W} \tilde{U}_k\)。

**Remark A.9.** 考虑重要的特例 \(\mathbb{P}(r_k = k) = 1\)。那么在命题假设下，\(\tilde{U}_k^\top W \tilde{U}_k \sim \text{GOE}(n - k)\) 在给定 \(\mathcal{S}_{k-1}\) 时与 \(\mathcal{S}_k\) 条件独立，并且与 \(\mathcal{S}_k\) 独立。

**Remark A.10.** 为了显式构造具有上述性质的（随机）\(\tilde{U}_k\)，考虑对 \(m^0, \dots, m^{k-1}, e_1, \dots, e_n \in \mathbb{R}^n\)（按此顺序）应用 Gram–Schmidt 过程，并仅保留输出中的非零向量（这些向量均已归一化为单位欧几里得长度）。这得到 \(\mathbb{R}^n\) 的一个 \(\mathcal{S}_{k-1}\)-可测标准正交基 \(\tilde{m}^1, \dots, \tilde{m}^n\)，其中 \(\tilde{m}^1, \dots, \tilde{m}^{r_k}\) 由 \(m^0, \dots, m^{k-1}\) 得到，因而张成 \(\text{Im}(M_k)\)，而 \(\tilde{m}^{r_k+1}, \dots, \tilde{m}^n\) 张成 \(V_k = \text{Im}(M_k)^\perp\)。因此，我们可以取 \(\tilde{U}_k = (\tilde{m}^{r_k+1} \dots \tilde{m}^n)\)。

本小节的主要结果是下面的命题 A.11，它在第 A.4 节和第 A.5 节给出的 AMP 主定理的归纳证明中起着关键作用。对于每个 \(k \in \{1, \dots, n - 1\}\)，令

\(\alpha^k \equiv \alpha^k(n) \equiv (\alpha_1^k, \dots, \alpha_k^k) := M_k^+ m^k = (M_k^\top M_k)^+ M_k^\top m^k \in \mathbb{R}^k \tag{A.4}\)

成为投影系数向量，满足 \(P_k m^k = M_k \alpha^k = \sum_{\ell=1}^k \alpha_\ell^k m^{\ell-1}\)。当 \(M_k\) 满秩（即当 \(r_k = k\)）时，请注意 \(\alpha^k = (M_k^\top M_k)^{-1} M_k^\top m^k\) 是具有此性质的唯一向量。此外，令 \(B_1 := (0, 0) \in \mathbb{R}^2\) 且对于 \(k \in \{2, \dots, n\}\)，\(B_k := \text{diag}(b_0, \dots, b_{k-1}) \in \mathbb{R}^{k \times k}\)，这样对于所有 \(k \in \{1, \dots, n\}\) 都有 \(Y_k = H_k + (0 \, M_{k-1})B_k\)。

**Proposition A.11.** 对于 \(n \in \mathbb{N}\)，考虑满足 (A0) 的对称 AMP 递归 (2.1)。对于 \(k \in \{0, 1, \dots, n - 1\}\)，令 \(\tilde{W}^k \equiv \tilde{W}^k(n) \sim \text{GOE}(n)\) 和 \((\tilde{Z}^{k+1}, \tilde{\zeta}^{k+1}) \equiv (\tilde{Z}^{k+1}(n), \tilde{\zeta}^{k+1}(n)) \sim N_n(0, I_n) \otimes N(0, 1/n)\) 都与 \(\mathcal{S}_k\) 独立。那么

\(W \stackrel{d}{=}_{\mathcal{S}_0} \tilde{W}^0 \quad \text{and} \quad h^1 \stackrel{d}{=}_{\mathcal{S}_0} \|m^0\|_n \tilde{Z}^1 + \tilde{\zeta}^1 m^0 =: h^{1,0}, \tag{A.5}\)

并且对于每个 \(k \in \{1, \dots, n - 1\}\)，有

\(W \stackrel{d}{=}|_{\mathcal{S}_k} W P_k + (W P_k)^\top P_k^\perp + P_k^\perp \tilde{W}^k P_k^\perp = Y_k M_k^+ + (Y_k M_k^+)^\top P_k^\perp + P_k^\perp \tilde{W}^k P_k^\perp\)

\(h^{k+1} \stackrel{d}{=}|_{\mathcal{S}_k} H_k \alpha^k + P_k^\perp (\tilde{W}^k \tilde{m}^k) + \{(M_k^+)^\top H_k^\top \tilde{m}^k - b_k m^{k-1} + (0 \, M_{k-1})B_k \alpha^k\} \tag{A.6}\)

