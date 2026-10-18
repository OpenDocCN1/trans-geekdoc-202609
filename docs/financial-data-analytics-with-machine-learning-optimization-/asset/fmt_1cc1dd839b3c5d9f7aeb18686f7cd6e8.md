
These three distribution functions are called *extreme value distributions*. We say that the random variable `x` belongs to the *Maximum Domain of Attraction* (MDA) of the extreme value distribution `H = Φ_α, Λ`, or `Ψ_α`, namely Fréchet, Gumbel, or Weibull distributions, respectively, written as `x ∈ MDA(H)`, if there exist constants `a_n > 0` and `b_n ∈ ℝ`, for `n = 1, 2, ...`, such that the condition ([8.17](#c08.xhtml#c08-disp-0078)) holds.

These three MDAs cover most of the distributions that are of interest in finance, insurance, and quantitative risk management. For instance, the distributions in `MDA(Φ_α)` include Cauchy, Pareto, Burr, Stable with index `α < 2` and log-gamma distributions; the distributions in `MDA(Λ)` include exponential-like, Weibull-like, gamma, normal, lognormal, exponential behaviour at a finite point `x_F < ∞`, *Benktander-type I* and *Benktander-type II* distributions; the distributions in `MDA(Ψ_α)` include uniform, power law behaviour at a finite point `x_F < ∞` and beta distributions. Here, `x_F` stands for the finite endpoint of the Gumbel or Weibull distributions.

A measurable function `h : ℝ₊ → ℝ₊` is said to be *regularly varying* at `∞` with an index `α ∈ ℝ \ {0}`, denoted as `h ∈ RV_α`, if for all `t > 0`,

```
lim_{x → ∞} h(tx) / h(x) = t^α.
```
