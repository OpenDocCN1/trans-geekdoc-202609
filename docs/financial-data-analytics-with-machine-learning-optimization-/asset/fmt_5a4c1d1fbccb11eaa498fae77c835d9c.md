
*Proof.* By [Theorem 6.1](#c06.xhtml#c06-fea-0004), there exists an integer `N` such that `p_{i,i}^{(n)} > 0` for all `i` and for all `n ≥ N`. Consider any two states `s_i, s_j ∈ S`. As the chain is irreducible, we can find some integer `n_{i,j} ≥ 0` such that `p_{i,j}^{(n_{i,j})} > 0`. Let `M_{i,j} = N + n_{i,j}`. For any `m ≥ M_{i,j}`, we have

```
P(x_m = s_j | x_0 = s_i) ≥ P(x_{m-n_{i,j}} = s_i, x_m = s_j | x_0 = s_i)
= P(x_m = s_j | x_{m-n_{i,j}} = s_i) P(x_{m-n_{i,j}} = s_i | x_0 = s_i) > 0.
```

Therefore, `p_{i,j}^{(m)} > 0` for all `m ≥ M_{i,j}`. The corollary is proven by taking

```
M := max{M_{1,1}, M_{1,2}, ..., M_{1,K}, M_{2,1}, ..., M_{K,K}}.
```
