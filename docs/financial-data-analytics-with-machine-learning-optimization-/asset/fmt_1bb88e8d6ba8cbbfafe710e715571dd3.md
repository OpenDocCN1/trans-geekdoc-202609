
**Lemma 6.2** Suppose that `{x_n}` is an irreducible and aperiodic Markov chain with a finite state space `S = {s_1, ..., s_K}` and a transition matrix `P`. For any two states `s_i, s_j ∈ S`, let `T_{i,j} := min{n ≥ 1 : x_n = s_j | x_0 = s_i}`. Then the mean hitting time `τ_{i,j} := E(T_{i,j})` is finite. In particular, `P(T_{i,j} < ∞) = 1`.

Any irreducible Markov chains possessing all finite mean hitting times between any two states are said to be *positive recurrent*.

*Proof.* By [Corollary 6.1](#c06.xhtml#c06-fea-0008), we can find an integer `M` such that `p_{i,j}^{(m)} > 0` for every pair of `i, j` whenever `m ≥ M`. Set `α := min_{i,j} {p_{i,j}^{(M)}} > 0`. Fix any two states `s_i` and `s_j`, and suppose that the chain starts at `s_i`. Then

```
P(T_{i,j} > M) ≤ P(x_M ≠ s_j | x_0 = s_i) ≤ 1 - α.
```

Furthermore, given everything that has happened up to time `M`, we have a conditional probability at least `α` of hitting state `s_j` at the time `2M` no matter where the chain is at time `M`, so that
