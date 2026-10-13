
- Due to [(11.43)](#Chp011_519-582_B9780443292385000172.xhtml#deq116), either `ξ̃[n]` or `ξ[n]` can be nonzero, but not both of them. This also applies to the corresponding Lagrange multipliers.

- Note that if `ξ̃[n] > 0` (or `ξ[n] > 0`), then from [(11.40)](#Chp011_519-582_B9780443292385000172.xhtml#deq113), [(11.46)](#Chp011_519-582_B9780443292385000172.xhtml#deq119), and [(11.47)](#Chp011_519-582_B9780443292385000172.xhtml#deq120) we obtain:

```
λ̃[n] = C  or  λ[n] = C.
```

That is, the respective Lagrange multipliers get their maximum value. In other words, they have a “big say” in the expansion in [(11.44)](#Chp011_519-582_B9780443292385000172.xhtml#deq117). When `ξ̃[n]` and/or `ξ[n]` are zero, then:

```
0 ≤ λ̃[n] ≤ C,  0 ≤ λ[n] ≤ C.
```

- Recall what we have said before concerning the estimation of `θ[0]`. Select any point corresponding to `0 < λ̃[n] < C` (`0 < λ[n] < C`) which we know is associated with `ξ̃[n] = 0 (ξ[n] = 0)`. Then `θ̂[0]` is computed from Eqs. [(11.38)](#Chp011_519-582_B9780443292385000172.xhtml#deq111) and [(11.39)](#Chp011_519-582_B9780443292385000172.xhtml#deq112). In practice, one selects all such points and computes `θ[0]` as the respective mean.

- [Fig. 11.11](#Chp011_519-582_B9780443292385000172.xhtml#f0060) illustrates `ŷ(x)` for a choice of `κ(⋅, ⋅)`. Observe that the value of `ϵ` forms a “tube” around the respective graph. Points lying outside the tube correspond to values of the slack variables larger than zero.

![Figure 11.11 The tube around the nonlinear regression curve. Points outside the tube (denoted by stars) have either ξ̃ > 0 and ξ = 0 or ξ > 0 and ξ̃ = 0. The rest of the points have ξ̃ = ξ = 0. Points that are inside the tube correspond to zero Lagrange multipliers.](images/B9780443292385000172/gr011.jpg)
