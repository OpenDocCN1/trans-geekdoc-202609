
### Uniform convexity and star-convexity

Function `F` is said to be `μ`-Hölder uniformly convex of order `ν ≥ 1` if $F(w^{\prime}) \geqslant F(w) + \langle\nabla F(w),w^{\prime} - w\rangle + \frac{\mu}{\nu}{\| w^{\prime} - w\|}^{\nu}$ for all `w`, `w'` ∈ `ℝ^(p)`, see, e.g., [68]. Clearly, if `ν = 2`, then we obtain the strong convexity. If `ν = 2` and `w = w^⋆`, a minimizer of `F`, then `F` is said to be `μ`-star strongly convex. These conditions are often used in gradient-type methods to establish linear convergence rates [42].

### Sharpness, quadratic growth, and error bound conditions

Assume that there exist `γ > 0` and `ν ≥ 1` such that $F(w) - F(w^{\star}) \geqslant \frac{\gamma}{\nu}{\| w - w^{\star}\|}^{\nu}$ for all `w` ∈ `ℝ^(p)` and a minimizer `w^⋆` of `F`. If `ν = 1`, then we say that `F` is sharped at `w^⋆`. If `ν = 2`, then we say that `F` has a quadratic growth property. Clearly, if `F` is strongly convex, then it has a quadratic growth property. However, nonconvex functions may still have a quadratic growth property. This property can be extended to an `ω`-convexity as in [14]. Another related concept is error bound [39], which is defined as `γ`∥∇`F`(`w`)∥ ≥ ∥`w` − `w^⋆`∥ for some `γ > 0` and all `w` ∈ `ℝ^(p)`. Both quadratic growth and error bound conditions can be used to establish [local] linear convergence of gradient-type methods, see, e.g., [16].

Other properties can be used to analyze convergence of gradient methods such as essential strong convexity, weak strong convexity, restricted secant inequality [30, 42], Kurdyka–Łojasiewicz (KL) condition [4], and Aubin's property [56].

### 1.2.7 Optimality certification

Finding an exact solution of [(1.1)] is impractical. Our goal is to approximate a solution of this problem in some sense. Let us discuss what we can approximate for [(1.1)] in both convex and nonconvex problems.

Assume that `w^⋆` is a global optimal solution of [(1.1)] with the optimal value `F^⋆ = F(w^⋆)` and `ŵ` is an approximate solution produced by an algorithm. One obvious condition to certify the optimality is to compute the objective residual `F(ŵ) − F(w^⋆)`. We often expect to find `ŵ` such that `F(ŵ) − F(w^⋆) ≤ ϵ` for a given tolerance `ϵ > 0`. This condition is usually used for convex optimization or special classes of nonconvex problems, e.g., under a gradient dominance condition. The construction of `ŵ` usually relies on two possible ways. The first is to simply take the last iterate `w[T]` as `ŵ := w^(T)`, where `w^(T)` is the final iterate of the algorithm. The second option is to form an averaging or a weighted averaging vector as

```
ŵ := (1 / (T + 1)) * Σ_{t=0}^{T} w^t,  or  ŵ := (1 / S_T) * Σ_{t=0}^{T} γ_t w^t,
```

(1.12)

where `γ[t] > 0` are given weights (usually related to the step-size `η[t]`, but could be different), and `S_T := Σ_{t=0}^{T} γ_t`. In general, averaging vectors have better theoretical convergence rate guarantees, but they may break desired properties of solutions such as sparsity or low-rankness, etc., compared to the last-iterate `w^(T)`. In convex optimization, we often use Jensen's inequality to obtain $F(ŵ) - F(w^⋆) \leqslant (1 / S_T) * Σ_{t=0}^{T} γ_t [F(w^t) - F(w^⋆)]$ for our convergence rate bounds since we obtain a convergence rate bound for the right-hand side.
