
### (a) Convergence rates

A convergence rate characterizes the progress of the optimality measure (e.g., the objective residual `F(ŵ^(t)) − F^⋆`, the squared distance to solution `∥ŵ^(t) − w^⋆∥²`, or the squared norm of gradient `∥∇F(ŵ^(t))∥²`) with respect to the iteration `t`, where `ŵ^(t)` is an approximate solution. For example, in the gradient method for smooth and convex problems, we have `F(w^(t + 1)) - F^⋆ ≤ (L∥w^0 - w^⋆∥²) / (2(t + 1))`, showing that the objective residual `F(w^(t)) − F^⋆` decreases with a speed of at least `1/t`, which is written as `F(w^(t)) − F^⋆ = 𝒪(1/t)`. We can also write `F(w^(t + 1)) - F^⋆ = 𝒪(R₀²L / (t + 1))` for `R₀ := ∥w⁰ − w^⋆∥` to show the dependence of the rate on `L` and `R₀`.

Note that we generally attempt to establish an upper bound rate, but can also show that this upper bound matches the lower bound rate (up to a constant factor) for certain classes of algorithms under a given set of assumptions on (1.1), see, e.g., [45]. For gradient-type methods, the optimal convergence rates under only convexity and `L`-smoothness is `𝒪(1/t²)`, which is guaranteed by Nesterov's optimal methods. For nonconvex problems, gradient-type methods only achieve an `𝒪(1/t)` rate on `∥∇F(ŵ^(t))∥²` under the `L`-smoothness. Linear convergence rates can be achieved with additional assumptions such as strong convexity, error bound, quadratic growth, or PL condition. However, we do not further discuss these variants in this chapter.

### (b) Complexity

The concept of complexity comes from theoretical computer science, but is widely used in computational mathematics, particularly in optimization. Formal definitions of complexity can be found, e.g., in [43, 45]. We distinguish two types of complexity for our gradient-type methods: iteration-complexity (or analytical complexity), and computational complexity (or sometimes called arithmetic complexity, or work complexity) [45]. In gradient-type methods, the overall computational complexity is generally dominated by the oracle complexity, which characterizes the total number of function and/or gradient evaluations required for finding an approximate solution. We notice that we overload the concept `oracle`, which is formally defined, e.g., in [45]. Mathematically, the oracle complexity of `T` iterations of an algorithm (in our context) is defined as follows:

```
Oracle complexity := ∑_{t=0}^{T} Per-iteration complexity at iteration t.
```
(1.19)

The **per-iteration complexity** characterizes the workload (e.g., the number of gradient evaluations) at each iteration. At each iteration, we often count the most dominated computational steps such as gradient evaluations, function evaluations, proximal operations, projections, matrix–vector multiplications, or Hessian–vector multiplications. If this per-iteration complexity is fixed, then

```
Oracle complexity = Number of iterations × Per-iteration complexity.
```

For example, for the standard gradient descent method for smooth and convex problems, the per-iteration complexity is `𝒪(1)`, i.e., requires one gradient evaluation, leading to oracle complexity `𝒪(1/ϵ)` in order to obtain `w^(t)` such that `F(w^(t)) − F^⋆ ≤ ϵ`. Indeed, from the convergence bound `F(w^t) - F^⋆ ≤ (L∥w^0 - w^⋆∥²) / (2t)`, we infer that `F(w^(t)) − F^⋆ ≤ ϵ` is implied by `(L∥w^0 - w^⋆∥²) / (2t) ≤ ϵ`, leading to `t ≥ ⌈(L∥w^0 - w^⋆∥²) / (2ϵ)⌉`. Hence, we need at most `t_max := ⌈(L∥w^0 - w^⋆∥²) / (2ϵ)⌉ = 𝒪(1/ϵ)` iterations, and therefore `𝒪(1/ϵ)` gradient evaluations.

### 1.2.10 Initial point, warm-start, and restart

For convex algorithms, which can converge to a global minimizer `w^⋆` starting from any initial point `w⁰`, the choice of `w⁰` will affect the number of iterations as the term `∥w⁰ − w^⋆∥²` for any solution `w^⋆` appears in the bound of the convergence guarantee, e.g., `F(w^T) - F^⋆ ≤ 𝒪(L∥w^0 - w^⋆∥² / T^ν)` for `ν = 1` or `ν = 2`. Clearly, if `w⁰` is close to `w^⋆`, then the number of iterations `T` is small.

For nonconvex algorithms, initialization plays a crucial role since different initial points `w⁰` may make the algorithm converge to different approximate stationary points `w^⋆`, and their quality is different. Stationary points are candidates for local minimizers, but some may give us maximizers or saddle points. If we do get a local minimizer, then it may still be a bad one, which is far from any global minimizer or which gives us a bad prediction error in machine learning.

A warm-start strategy uses the output of the previous run or the previous iteration to initialize the algorithm at the current stage or iteration. It is based on the idea that the previous run already gives us a good approximation of the desired solution. Initializing from this point may give hope for a quick convergence to the target optimal solution. Warm-start is widely used in sequential iterative (e.g., sequential quadratic programming) or online learning methods.
