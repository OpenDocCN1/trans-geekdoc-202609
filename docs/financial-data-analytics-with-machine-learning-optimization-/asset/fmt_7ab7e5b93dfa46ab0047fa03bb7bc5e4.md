
From the definition, it is always clear that `H(x) ≥ 0`. If `x` is degenerate, then `H(x) = 0`, and there is no ambiguity in `x`. If `x` is Bernoulli taking values 0 or 1, we have `H(x) ∈ [0, 1]`, and `H(x) = 1` if and only if it is equally likely for `x` to take 0 and 1. In general, if `x` is a discrete random variable taking `n` different values, with the corresponding probabilities `p_i` for `i = 1, 2, ..., n`, the Shannon entropy is maximized when `p_i ≡ 1/n` for all `i`, and the corresponding entropy `H(x)` is `log₂ n`. This claim follows by an application of Jensen's inequality

Next, if `x ∈ X` is a continuous random variable with a continuous density function `f(x)`, the corresponding Shannon entropy is refined as the so-called *differential entropy*

[(13.4)](#c13.xhtml#R_c13-disp-0006)

```
h(x) := -∫(ln f(x)) = -∫_X f(x) ln f(x) dx.
```

However, differential entropy lacks a number of properties that Shannon entropy possesses, such as non-negativity and scale invariance, hence differential entropy is not a direct generalization of Shannon entropy. For instance, consider `x ~ N(μ, σ²)`, then
