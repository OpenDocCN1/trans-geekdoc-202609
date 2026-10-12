
## 公式与推导

(11.18)
```
x₂(n) = x₁(N + n) for n = 1, …, L − N.
```

Once the BSS algorithm has been applied to `X₁(n)` and `X₂(n)`, two windows of estimated sources `ŝ₁(n)` and `ŝ₂(n)` will be obtained respectively, where *m* is the number of sources. These two windows overlap within a time interval, but due to the inherent ambiguities of BSS `ŝ₁(n)` and `ŝ₂(n)` are not equal in this interval. Instead:

(11.19)
```
ŝ₂(n) = P · D · ŝ₁(n + N) for n = 1, ..., L − N,
```

where **P** is an *n* × *n* permutation matrix and **D** = *diag*{*d*[1], *d*[2], …, *d*[*n*]} is the scaling matrix. Therefore, `ŝ₂(t)` is just a copy of `ŝ₁(t)` in the overlap block, with the rows (sources) permuted, and each of them is scaled by a real number *d*[*i*] that accounts for the scaling ambiguity of BSS. A measure of similarity has also been used between the rows of `ŝ₁(t)` and `ŝ₂(t)` within the overlap region for this purpose.

### Cross‐correlation

The cross‐correlation between two zero‐mean wide sense stationary random signals *x*(*t*) and *y*(*t*) is defined as:

(11.20)
```
r_xy(τ) = E[x(n)y(n + τ)]
```

where *E*[·] denotes the expectation operation. This measure gives an idea of the similarity between *x*(*n*) and *y*(*n*), but its values are not bounded and depend on the amplitude of the signal. Therefore, it is preferable to use a normalization of *r*[*xy*] given by the cross‐correlation coefficient:

(11.21)
```
ρ_xy = r_xy / (σ_x σ_y)
```

where *σ*[*x*] and *σ*[*y*] are the standard deviations of *x*(*n*) and *y*(*n*) respectively, and the cross‐correlation coefficient satisfies:

(11.22)
```
−1 ≤ ρ_xy ≤ 1
```

Furthermore, if *ρ*[*xy*] = 1, then *y = ax*, with *a* > 0, and *x*(*t*) and *y*(*t*) are perfectly correlated; and if *ρ*[*xy*] = −1, then *y = −ax* and *x*(*n*) and *y*(*n*) are perfectly anti‐correlated. When the two signals have no information in common, *ρ*[*xy*] = 0, they are said to be uncorrelated.
