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

where $P := TT^+$ and $P^\perp := I_n - TT^+$ represent the orthogonal projections onto $\text{Im}(T)$ and $\text{Im}(T)^\perp$ respectively. The first two terms on the right hand side of (A.9) are measurable functions of $WP = (WT)T^+$ (and hence $WT$), while the third term $P^\perp W P^\perp$ is independent of $WT$. Thus, $\mathbb{E}(W \mid WT) = WP + (WP)^\top P^\perp$. Moreover, we can write $P^\perp = \tilde{U} \tilde{U}^\top$, where the columns of $\tilde{U}$ form an orthonormal basis for