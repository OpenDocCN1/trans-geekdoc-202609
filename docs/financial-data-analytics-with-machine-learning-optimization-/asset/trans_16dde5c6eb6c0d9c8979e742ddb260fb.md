

which holds by noting the very definition of the density `f`, namely `∫_Xf f(x) dx = 1` and `f(x) = 0` whenever `x ∈ Xg − Xf`. In other words, the aforementioned sample average converges to the theoretical quantity of `E(h(x))`, and hence the algorithm is indeed valid. As an illustration, for instance, readers may refer to [Subsection 6.4.2](#c06.xhtml#c06-sec-0035) for an application of this sampling method in the context of `stochastic volatility` models.

## 5.2 VARIANCE REDUCTION TECHNIQUE

Most often, after knowing how to simulate a sequence of random variables, the next immediate application is to estimate various quantities of interest, or simply some statistics, of a more complicated probability distribution. For instance, we are often interested in estimating the underlying unknown theoretical mean `μ_x := x`, and one may think of using the `Monte Carlo` method. As pointed out in [Section 1.4](#c01.xhtml#head-2-8), one direct approach is to use the sample mean

```
μ̂_x = (1/n) Σ_{i=1}^{n} x_i,
```

as the estimator, where `x_1, ..., x_n` is a random sample simulated from the distribution of `x`. The accuracy of this estimator can be assessed by examining its variance. As discussed in [Subsection 1.4.2](#c01.xhtml#head-3-3), it is given by:

```
Var(μ̂_x) = Var((1/n) Σ_{i=1}^{n} x_i) = (1/n²) Σ_{i=1}^{n} Var(x_i) = (1/n) Var(x).
```

