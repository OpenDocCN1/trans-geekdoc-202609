is conditionally independent of $\mathcal{S}_k$ given $\mathcal{S}_{k-1}$, and is independent of $\mathcal{S}_k$.

**Remark A.10.** To explicitly construct a (random) \(\tilde{U}_k\) with the above properties, consider applying the Gram–Schmidt procedure to \(m^0, \dots, m^{k-1}, e_1, \dots, e_n \in \mathbb{R}^n\) (in that order) and retaining only the non-zero vectors in the output (which are all normalised to have unit Euclidean length). This yields an \(\mathcal{S}_{k-1}\)-measurable orthonormal basis \(\tilde{m}^1, \dots, \tilde{m}^n\) of \(\mathbb{R}^n\), where \(\tilde{m}^1, \dots, \tilde{m}^{r_k}\) are obtained from \(m^0, \dots, m^{k-1}\) and therefore span \(\text{Im}(M_k)\), while \(\tilde{m}^{r_k+1}, \dots, \tilde{m}^n\) span \(V_k = \text{Im}(M_k)^\perp\). Thus, we can take \(\tilde{U}_k = (\tilde{m}^{r_k+1} \dots \tilde{m}^n)\).

The main result of this subsection is Proposition A.11 below, which plays a crucial role in the inductive proof of the AMP master theorems given in Sections A.4 and A.5. For each \(k \in \{1, \dots, n - 1\}\), let

```
\(\alpha^k \equiv \alpha^k(n) \equiv (\alpha_1^k, \dots, \alpha_k^k) := M_k^+ m^k = (M_k^\top M_k)^+ M_k^\top m^k \in \mathbb{R}^k \tag{A.4}\)
```

be a vector of projection coefficients satisfying \(P_k m^k = M_k \alpha^k = \sum_{\ell=1}^k \alpha_\ell^k m^{\ell-1}\). When \(M_k\) has full rank (i.e. when \(r_k = k\)), note that \(\alpha^k = (M_k^\top M_k)^{-1} M_k^\top m^k\) is the unique vector with this property. In addition, let \(B_1 := (0, 0) \in \mathbb{R}^2\) and \(B_k := \text{diag}(b_0, \dots, b_{k-1}) \in \mathbb{R}^{k \times k}\) for \(k \in \{2, \dots, n\}\), so that \(Y_k = H_k + (0 \, M_{k-1})B_k\) for all \(k \in \{1, \dots, n\}\).

**Proposition A.11.** For \(n \in \mathbb{N}\), consider a symmetric AMP recursion (2.1) for which (A0) holds. For \(k \in \{0, 1, \dots, n - 1\}\), let both \(\tilde{W}^k \equiv \tilde{W}^k(n) \sim \text{GOE}(n)\) and \((\tilde{Z}^{k+1}, \tilde{\zeta}^{k+1}) \equiv (\tilde{Z}^{k+1}(n), \tilde{\zeta}^{k+1}(n)) \sim N_n(0, I_n) \otimes N(0, 1/n)\) be independent of \(\mathcal{S}_k\). Then

```
\(W \stackrel{d}{=}_{\mathcal{S}_0} \tilde{W}^0 \quad \text{and} \quad h^1 \stackrel{d}{=}_{\mathcal{S}_0} \|m^0\|_n \tilde{Z}^1 + \tilde{\zeta}^1 m^0 =: h^{1,0}, \tag{A.5}\)
```

and for each \(k \in \{1, \dots, n - 1\}\), we have

```
\(W \stackrel{d}{=}|_{\mathcal{S}_k} W P_k + (W P_k)^\top P_k^\perp + P_k^\perp \tilde{W}^k P_k^\perp = Y_k M_k^+ + (Y_k M_k^+)^\top P_k^\perp + P_k^\perp \tilde{W}^k P_k^\perp\)
\(h^{k+1} \stackrel{d}{=}|_{\mathcal{S}_k} H_k \alpha^k + P_k^\perp (\tilde{W}^k \tilde{m}^k) + \{(M_k^+)^\top H_k^\top \tilde{m}^k - b_k m^{k-1}\)
\(+ (0 \, M_{k-1})B_k \alpha^k\} \tag{A.6}\)
```