
```
=^d \, | \mathcal{S}_k \sum_{\ell=1}^k \alpha_{\ell k} h^\ell + \| \hat{m}^k \|_n (P_{k\perp} \bar{Z}^{k+1}) + \tilde{\zeta}^{k+1} \hat{m}^k + M_k(M_k^\top M_k)\\ + \left( v^{k,k} - \sum_{\ell=1}^k \alpha_\ell^k v^{k, \ell-1} \right)\\ =: h^{k+1, k},\tag{A.7}
```

where $v^{k,\ell} \equiv v^{k,\ell}(n) := H_k^\top m^\ell - b_\ell M_k^\top m^{\ell-1} \in \mathbb{R}^k$ for $\ell \in \{0, \dots, k\}$.

The crux of the proof of Proposition A.11 is to establish (A.6), which characterises the conditional distribution of $W$ given $\mathcal{S}_k$. It is intuitively helpful to think of this as being obtained by conditioning $W$ on the 'linear constraints' $Wm^0 = y^0, \dots, Wm^{k-1} = y^{k-1}$. However, since $m^1, \dots, m^{k-1}$ are random and depend on $W$, this heuristic argument is not sufficient on its own to constitute a formal proof of Proposition A.11. For the benefit of readers interested in the technicalities, we give a more detailed explanation below.

Observe that for fixed $k \in \mathbb{N}$ and deterministic $y, a^0, a^1, \dots, a^k \in \mathbb{R}^n$, the event $\Omega_{y, a^0, \dots, a^k} := \{ \gamma = y, m^0 = a^0, h^1 = a^1, \dots, h^k = a^k \}$ can be expressed as

```
\Omega_{y, a^0, \dots, a^k} = \{ \gamma = y, m^0 = a^0, W t^j = z^j \text{ for all } 0 \le j \le k-1 \}\\ = \{ \gamma = y, m^0 = a^0, W T_k = Z_k \},\tag{A.8}
```

where $t^j := f_j(a^j, y) \in \mathbb{R}^n$ and $z^j := a^{j+1} + \langle f_j'(a^j, y) \rangle_n f_{j-1}(a^{j-1}, y)$ for $0 \le j \le k-1$, and $T_k := (t^0 \ t^1 \ \dots \ t^{k-1})$ and $Z_k := (z^0 \ z^1 \ \dots \ z^{k-1})$ are fixed $n \times k$ matrices. Now for $W \sim \text{GOE}(n)$ and any fixed $T \in \mathbb{R}^{n \times k}$ of rank $p$, we can derive the conditional distribution of $W$ given $WT$ by writing

```
W = WP + (P + P^\perp)^\top W P^\perp = WP + (WP)^\top P^\perp + P^\perp W P^\perp,\tag{A.9}
```

where $P := TT^+$ and $P^\perp := I_n - TT^+$ represent the orthogonal projections onto $\text{Im}(T)$ and $\text{Im}(T)^\perp$ respectively. The first two terms on the right hand side of (A.9) are measurable functions of $WP = (WT)T^+$ (and hence $WT$), while the third term $P^\perp W P^\perp$ is independent of $WT$. Thus, $\mathbb{E}(W \mid WT) = WP + (WP)^\top P^\perp$. Moreover, we can write $P^\perp = \tilde{U} \tilde{U}^\top$, where the columns of $\tilde{U}$ form an orthonormal basis for $\text{Im}(T)^\perp$, so that $P^\perp W P^\perp = \tilde{U}(\tilde{U}^\top W \tilde{U})\tilde{U}^\top$, and $\tilde{U}^\top W \tilde{U} \sim \text{GOE}(n - p)$ is independent of $WT$. For $Z \in \mathbb{R}^{n \times k}$, this enables us to interpret ‘the conditional distribution of $W$ given $WT = Z$’ as the distribution of

$ZT^\perp + (ZT^\perp)^\top P^\perp + \tilde{U}^\top W \tilde{U}$,

where $\tilde{W} \sim \text{GOE}(n - p)$. We denote this distribution by $\mathcal{L}_Z(T)$.

In view of (A.8) and the assumption that $W$ is independent of $(m^0, \gamma)$ in (A0), it is then tempting to argue heuristically that

$W \mid \{\gamma = y, m^0 = a^0, h^1 = a^1, \dots, h^k = a^k\}$

\(\overset{d}{=} W \mid \{\gamma = y, m^0 = a^0, WT_k = Z_k\}\)

\(\overset{d}{=} W \mid \{WT_k = Z_k\} \sim \mathcal{L}_{Z_k}(T_k)\),

and conclude on this basis that $W$ has (regular) conditional distribution $\mathcal{L}_\omega \equiv \mathcal{L}_{Y_k(\omega)}(M_k(\omega))$ given $\mathcal{S}_k = \sigma(\gamma, m^0, h^1, \dots, h^k)$, noting that $M_k(\omega) = T_k$ and $Y_k(\omega) = Z_k$ for $\omega \in \Omega_{y, a^0, \dots, a^k}$. However, this line of reasoning appears to involve conditioning explicitly on an event of potentially zero probability, and is not formally justified by the above argument; cf. the Borel paradox (Dudley, 2002, pp. 350–351) for the associated hazards.

As mentioned above, the issue is that $M_k$ is random and is in general not independent of $W$, whereas the distributional claims in the previous paragraph relied on the fact that $T$ was fixed. Nevertheless, the key point is that the randomness of $M_k$ and its dependence on $W$ turn out not to cause irreconcilable difficulties, due to the conditional independence established in Proposition A.8. It follows from this result that $\mathbb{E}(W \mid \mathcal{S}_k) = W P_k + (W P_k)^\top P_k^\perp$, so the conditional distributional equality (A.6) in Proposition A.11 and the decomposition (A.11) in its proof are the appropriate analogues of (A.9).

## A.3 Proofs of Results in Section A.2

A key ingredient in the proof of Proposition A.8 is Lemma A.12 below, which extends the orthogonal invariance property of the GOE($n$) distribution. Given a finite collection of disjoint measurable spaces $(\mathcal{X}_1, \mathcal{A}_1), \dots, (\mathcal{X}_m, \mathcal{A}_m)$, we equip the disjoint union $\sqcup_{k=1}^m \mathcal{X}_k$ with the $\sigma$-algebra $\{\sqcup_{k=1}^m A_k : A_k \in \mathcal{A}_k \text{ for all } k\}$.

### Lemma A.12.

Let \(\mathcal{G} \subseteq \mathcal{F}\) be a sub-\(\sigma\)-algebra and let \(X : (\Omega, \mathcal{F}, \mathbb{P}) \to \sqcup_{k=1}^n \mathbb{R}^{k \times k}\) be a measurable function. Suppose that there is a partition of \(\Omega\) into disjoint events \(\Omega_1, \dots, \Omega_m \in \mathcal{G}\) such that for each \(k = 1, \dots, m\), the map \(X\) takes values in \(\mathbb{R}^{n_k \times n_k}\) on \(\Omega_k\) and has conditional distribution \(\text{GOE}(n_k)\) given \(\mathcal{G}\) on \(\Omega_k\), for some (deterministic) \(n_k \in \{1, \dots, n\}\). Moreover, let \(Q = (Q_1 \ Q_2) : (\Omega, \mathcal{F}, \mathbb{P}) \to \sqcup_{k=1}^n \mathbb{O}_k\) be a \(\mathcal{G}\)-measurable function such that on each event \(\Omega_k\), the map \(Q\) takes values in \(\mathbb{O}_{n_k}\), and \(Q_1, Q_2\) have \(\ell_k\) and \(n_k - \ell_k\) columns respectively, for some (deterministic) \(\ell_k \in \{1, \dots, n_k - 1\}\). Then, given \(\mathcal{G}\), we have the following:

- (a) \(Q^\top X Q\) has conditional distribution \(\text{GOE}(n_k)\) on \(\Omega_k\) for every \(k = 1, \dots, m\);
- (b) \(Q_2^\top X Q_2\) has conditional distribution \(\text{GOE}(n_k - \ell_k)\) on \(\Omega_k\) for every \(k = 1, \dots, m\);
- (c) \(Q^\top X Q_1\) and \(Q_2^\top X Q_2\) are conditionally independent.

### Remark A.13.

Note that if \(n_1 = \dots = n_m = n\), then under the first condition of the lemma, it follows from Remark B.4 that \(X\) has unconditional distribution \(\text{GOE}(n)\) and is independent of \(\mathcal{G}\). Thus, in the instructive special case where \(m=1\) and \(1 \le \ell_1 < n = n_1\), the result above simplifies to the following: suppose that \(X \sim \text{GOE}(n)\), and is independent of \(\mathcal{G}\), and moreover that \(Q = (Q_1 \ Q_2) : (\Omega, \mathcal{F}, \mathbb{P}) \to \mathbb{O}_n\) is a \(\mathcal{G}\)-measurable map such that \(Q_1, Q_2\) have \(\ell_1\) and \(n - \ell_1\) columns respectively. Then

- (a) \(Q^\top X Q \sim \text{GOE}(n)\) and is independent of \(\mathcal{G}\);
- (b) \(Q_2^\top X Q_2 \sim \text{GOE}(n - \ell_1)\) and is independent of \(\mathcal{G}\);
- (c) \(Q^\top X Q_1\) and \(Q_2^\top X Q_2\) are independent, and also conditionally independent given \(\mathcal{G}\).

### Proof of Lemma A.12.

(a) For \(\ell = 1, \dots, n\), let \(\mathcal{A}_\ell\) and \(\mathcal{B}_\ell\) be the Borel \(\sigma\)-algebras on \(\mathcal{X}_\ell := \mathbb{R}^{\ell \times \ell}\) and \(\mathcal{Y}_\ell := \mathbb{O}_\ell\) respectively. Define \(\phi_\ell : \mathcal{X}_\ell \times \mathcal{Y}_\ell \to \mathcal{X}_\ell\) by \(\phi_\ell(M, J) := J^\top M J\), and for \(J \in \mathbb{O}_\ell\), let \(\iota_J : \mathcal{X}_\ell \to \mathcal{X}_\ell \times \mathcal{Y}_\ell\) be the map \(M \mapsto (M, J)\). Then the orthogonal invariance property of GOE($\ell$) can be restated as GOE($\ell$) = GOE($\ell) \circ (\phi_\ell \circ \iota_J)^{-1}$ for every \(J \in \mathbb{O}_\ell\). Thus, observing that \(\phi_{n_k}(X, Q) = Q^\top X Q\) on \(\Omega_k\), and applying Lemma B.6(b) to \(\phi_{n_k}\), we see that \(Q^\top X Q\) has conditional distribution GOE($n_k$) given \(\mathcal{G}\) on \(\Omega_k\), as required.

- (b) For \(k = 1, \dots, m\), let \(\psi_k : \mathcal{X}_{n_k} \to \mathcal{X}_{n_k - \ell_k}\) denote the map that extracts the lower-right \((n_k - \ell_k) \times (n_k - \ell_k)\) block of entries of an \(n_k \times n_k\) matrix. Then \(\psi_k(W) \sim \text{GOE}(n_k - \ell_k)\) whenever \(W \sim \text{GOE}(n_k)\), so \(\text{GOE}(n_k - \ell_k) = \text{GOE}(n_k) \circ \psi_k^{-1} = \text{GOE}(n_k) \circ (\phi_{n_k} \circ \iota_J)^{-1} \circ \psi_k^{-1}\) for every \(J \in \mathbb{O}_{n_k}\). We can therefore apply Lemma B.6(b) to \(\psi_k \circ \phi_{n_k}\) to conclude that \(Q_2^\top X Q_2\) has conditional distribution GOE($n_k - \ell_k$) given \(\mathcal{G}\) on \(\Omega_k\).

- (c) For \(\omega \in \Omega\), let \(P_\omega\), \(Q_\omega\) and \(R_\omega\) respectively denote the conditional distributions of \(Q^\top X Q_1\), \(Q_2^\top X Q_2\) and \((Q^\top X Q_1, Q_2^\top X Q_2)\) given \(\mathcal{G}\). For \(k = 1, \dots, m\), let \(\tilde{\psi}_k : \mathcal{X}_{n_k} \to \mathbb{R}^{n_k \times \ell_k}\) denote the map that extracts the first \(\ell_k\) columns of a \(n_k \times n_k\) matrix. Now define \(\Psi_k : \mathcal{X}_{n_k} \to \mathbb{R}^{n_k \times \ell_k} \times \mathcal{X}_{n_k - \ell_k}\) by \(\Psi_k(M) := (\tilde{\psi}_k(M), \psi_k(M))\). Then \(\tilde{\psi}_k(W)\) and \(\psi_k(W)\) are independent whenever \(W \sim \text{GOE}(n_k)\), so \(\text{GOE}(n_k) \circ \Psi_k^{-1} = (\text{GOE}(n_k) \circ \tilde{\psi}_k^{-1}) \otimes (\text{GOE}(n_k) \circ \psi_k^{-1})\). Since \((Q^\top X Q_1, Q_2^\top X Q_2) = (\Psi_k \circ \phi_k)(X, Q)\) on \(\Omega_k\), we may apply Lemma B.6(b) to \(\tilde{\psi}_k \circ \phi_{n_k}\), \(\psi_k \circ \phi_{n_k}\) and \(\Psi_k \circ \phi_{n_k}\) to deduce that \(R_\omega = P_\omega \otimes Q_\omega\) for all \(\omega \in \Omega_k\). Since \(k \in \{1, \dots, m\}\) was arbitrary, we conclude that \(R_\omega = P_\omega \otimes Q_\omega\) for all \(\omega \in \Omega = \sqcup_{k=1}^m \Omega_k\), which together with Lemma B.9(b) implies that \(Q^\top X Q_1\) and \(Q_2^\top X Q_2\) are conditionally independent given \(\mathcal{G}\). \(\square\)

### Proof of Proposition A.8.

We argue by induction on \(k \in \{0, 1, \dots, n-1\}\). The case \(k=0\) is trivial since \(W \sim \text{GOE}(n)\) and is independent of \((m^0, \gamma)\) by assumption. For a general \(1 \le k \le n-1\) (when \(n \ge 2\)), let \(\check{U}_{k-1}\) be any \(\mathcal{S}_{k-2}\)-measurable \(n \times (n - r_{k-1})\) matrix whose columns form an orthonormal basis of \(V_{k-1}\), and fix an arbitrary \(\mathcal{S}_{k-1}\)-measurable \(n \times (n - r_k)\) matrix \(\check{U}_k\) whose columns form an orthonormal basis of \(V_k\). Moreover, let \(E \equiv E_{k-1}\) be the event \(\{\check{m}^{k-1} \neq 0\} = \{r_k = r_{k-1} + 1\} \in \mathcal{S}_{k-1}\), and note that \(n - r_{k-1} \ge n - k + 1 \ge 2\).

Next, define an \(\mathcal{S}_{k-1}\)-measurable \(n \times (n - r_{k-1})\) matrix \(\check{U}\) by setting \(\check{U} := (\check{m}^{k-1} \check{U}_k)\) on \(E\) and \(\check{U} := \check{U}_k\) on \(E^c = \{\check{m}^{k-1} = 0\}\). Letting \(\check{U}\) be
