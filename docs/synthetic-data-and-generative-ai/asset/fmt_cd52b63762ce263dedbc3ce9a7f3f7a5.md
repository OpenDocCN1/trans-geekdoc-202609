
Figure 8.3 Scatterplots: median vs weighted method, on validation (left) vs training set (right).

[Fig. 8.2](#Chp008_131-145_B9780443218576000126.xhtml#f0015) is an original visualization, rarely seen. It allows you to look at individual residual errors and prediction intervals, regardless of the dimension of the problem.

### 8.4.3 Amplitude restoration

As mentioned a few times earlier, the fuzzy regression, especially the methodology based on the median, acts as a low-pass filter in signal processing. This is not surprising: after all it removes the noise. Indeed, it can be used as a data compression technique. As a result, predicted values have a lower variance than the observed ones, and the slope `β` in [Table 8.1](#Chp008_131-145_B9780443218576000126.xhtml#t0010) or [Fig. 8.3](#Chp008_131-145_B9780443218576000126.xhtml#f0020) is well below one. To correct this “issue”, one has to standardize the predicted values, so that the mean and variance match that of the observed response in the training set. In short, the predicted values must be recalibrated. Because of this, the mean squared error is not a good metric to assess performance. Also, here the R-squared is the square of the correlation, but it is not equal to `1 - S_S[res]/S_S[tot]`![Image](images/B9780443218576000126/si58.png), unlike in traditional regression where both agree.

The same phenomenon takes place when smoothing time series. A moving average can be used to predict or interpolate values. It also removes some noise, and reduces the amplitude of the signal. A scatterplot of exact values versus moving average will exhibit the same sharp drop in the slope. And it can be corrected using the same strategy, with no impact on the R-squared measured as the square of the correlation between observed and predicted (smoothed) values.

## 8.5 Exercises

The first exercise consists of proving a fundamental result: the fact that, under certain circumstances, the fuzzy regression technique described in this chapter is an exact interpolation technique. The proof does not involve math beyond elementary arithmetic, but rather out-of-the-box thinking. The second exercise is about another simple, numerically stable interpolation technique, this time based on partial fractions. The prerequisite is a first course in calculus, to understand and solve this problem. The third exercise explores an alternative to validation sets. The fourth exercise is a generalization to higher dimensions.

### Exercise 8.1

**Fuzzy regression for interpolation**. Let (`x[1]`, `y[1]`, `z[1]`), …, (`x[n]`, `y[n]`, `z[n]`)![Image](images/B9780443218576000126/si59.png) be the training set points. We use a spline system with `M = n`![Image](images/B9780443218576000126/si40.png) splines. Each spline is uniquely defined by `r` training set points. The `k`th spline (`k = 1, …, n`![Image](images/B9780443218576000126/si60.png)) always contains (`x[k]`, `y[k]`, `z[k]`)![Image](images/B9780443218576000126/si61.png). In other words, `L[k](x[k], y[k]) = z[k]`![Image](images/B9780443218576000126/si62.png). Prove that as `s → ∞`![Image](images/B9780443218576000126/si39.png), the weight-based predicted value `z[w]`![Image](images/B9780443218576000126/si44.png) evaluated at any training set location (`x`, `y`)![Image](images/B9780443218576000126/si26.png), is equal to the observed value `z` at that location.

#### Solution

When `s = ∞`![Image](images/B9780443218576000126/si63.png), `w[k](x, y) = 1`![Image](images/B9780443218576000126/si64.png) if (`x`, `y`) = (`x[k]`, `y[k]`)![Image](images/B9780443218576000126/si65.png) is the location of a training set point, and 0 otherwise. If multiple training set points have the same (`x`, `y`)![Image](images/B9780443218576000126/si26.png) but different `z`'s, then the predicted `z[w]`![Image](images/B9780443218576000126/si44.png) at (`x`, `y`)![Image](images/B9780443218576000126/si26.png) will be the average of those `z`'s. This is because at least one factor in the product formula [(8.2)](#Chp008_131-145_B9780443218576000126.xhtml#deq5) is equal to zero, and thus the product is zero.

To complete the proof, one has to carefully look at formula [(8.1)](#Chp008_131-145_B9780443218576000126.xhtml#deq4). Assume that (`x`, `y`) = (`x[k]`, `y[k]`)![Image](images/B9780443218576000126/si65.png). If `i ≠ k`![Image](images/B9780443218576000126/si66.png), the `i`th term in formula [(8.1)](#Chp008_131-145_B9780443218576000126.xhtml#deq4) is zero, because at least one factor in each inner product if zero. But if `i = k`![Image](images/B9780443218576000126/si67.png), both products are equal to one, and thus `L[k](x, y) = z[k]`![Image](images/B9780443218576000126/si68.png).

### Exercise 8.2

**Partial fractions for interpolation**. This may be particularly useful for time series interpolation. Assume `f` is a smooth, slow growing even function, and `f(t)`![Image](images/B9780443218576000126/si69.png) is known if `t` is a positive integer. Then `f(t)`![Image](images/B9780443218576000126/si69.png) is uniquely determined everywhere on the real axis. In short, there is an exact interpolation formula for the whole function, if we know `f(t)`![Image](images/B9780443218576000126/si69.png) for `t = 0, 1, 2`![Image](images/B9780443218576000126/si70.png) and so on. The formula is

```
f(t) = \frac{\sin\pi t}{\pi} \cdot \left\lbrack \frac{f(0)}{t} + \phi^{\prime}(t)\sum\limits_{k = 1}^{\infty}{( - 1)}^{k}\frac{f(k)}{\phi(t) - \phi(k)} \right\rbrack,
```

![Image](images/B9780443218576000126/si71.png)(8.5)

and it works in particular if `ϕ(t) = t²`![Image](images/B9780443218576000126/si72.png), `ϕ'(t) = 2t`![Image](images/B9780443218576000126/si73.png) is the derivative with respect to `t`, and

```
f(t) = \sum\limits_{k = 0}^{\infty}\alpha_{k}\cos\beta_{k}t,\text{~with~}|\beta_{k}| < \pi.
```

![Image](images/B9780443218576000126/si74.png)(8.6)

The purpose of this exercise is to prove the validity of formula [(8.5)](#Chp008_131-145_B9780443218576000126.xhtml#deq8) under the right conditions, and to apply it to the real part of the Dirichlet eta function `η(σ + i t)`![Image](images/B9780443218576000126/si75.png) [[Wiki](https://en.wikipedia.org/wiki/Dirichlet_eta_function)], for (say) `σ = 0.8`![Image](images/B9780443218576000126/si76.png) and `0 < t < 30`![Image](images/B9780443218576000126/si77.png). Unlike the interpolation technique in [Exercise 8.1](#Chp008_131-145_B9780443218576000126.xhtml#enun0010), formula [(8.5)](#Chp008_131-145_B9780443218576000126.xhtml#deq8) provides only an approximation, albeit an excellent one. The approximation is exact if you include all the infinitely many terms. It can be used for **time series disaggregation** [[2]](#Chp008_131-145_B9780443218576000126.xhtml#br0010). A potential application is to break down hourly temperature predictions into 5 minute increments.

#### Solution

A detailed discussion about this interpolation formula and its generalization, can be found [here](https://mathoverflow.net/questions/376081/infinite-partial-fraction-expansions-to-compute-fractional-iterations-and-recurr). Note that the real part of the Dirichlet eta function (closely linked to the **Riemann Hypothesis**) is

```
\Re\lbrack\zeta(\sigma + it)\rbrack = \sum\limits_{k = 1}^{\infty}{( - 1)}^{k + 1}\frac{\cos(t\log k)}{k^{\sigma}},\quad\sigma > 0.
```

![Image](images/B9780443218576000126/si78.png)
