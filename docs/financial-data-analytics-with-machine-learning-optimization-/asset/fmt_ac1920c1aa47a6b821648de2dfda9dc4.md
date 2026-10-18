
where `m(x)` is an unknown function of `x`, `ε` and `x` are uncorrelated, and `E(ε̄|x = x) = 0`. We define `σ²(x) := Var(ε̄|x = x) = Var(ȳ|x = x)`. We often assume that `m(x)` is piecewise smooth, such that it is of class `Cᵏ` for the interior points and `Cᵏ⁻¹` at the knots (boundary‐splitting points); here `Cᵏ` indicates that the derivatives up to the `k`‐th order exist and are continuous. Then for a given point `x₀ ∈ ℝ`, we expect that `m(xᵢ)` should be close to `m(x₀)` for any observed value `xᵢ` in the proximity of `x₀`. Therefore, a reasonable estimate for `m(x₀)` would be an average of the observed responses `yᵢ`'s corresponding to those `xᵢ`'s.

By Taylor expansion of `m(x)` up to order `k` at `x₀`, in the proximity of `x₀`, we have:
