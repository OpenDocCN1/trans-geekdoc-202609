

which tells us the largest possible value for `W` is one. As a result, if `W` is much smaller than 1, we are more confident to reject the null hypothesis of the normal nature of the underlying sample. For more discussion on the statistical properties of the test, such as its `consistency`, we refer readers to [\[8](#c03.xhtml#c03-bib-0008), [13](#c03.xhtml#c03-bib-0013), [18\]](#c03.xhtml#c03-bib-0018). Meanwhile, some variants of the Shapiro–Wilk test are also available in various references including [\[14](#c03.xhtml#c03-bib-0014), [18\]](#c03.xhtml#c03-bib-0018).

### 3.A.2 Kolmogorov–Smirnov Test

Suppose that `x(1) < x(2) < ... < x(n)` are `n` real-valued observations, arranged in the ascending order, of `x1, ..., xn` drawn from an unknown distribution `F` of continuous type on `R`. For simplicity, it is assumed that all observations are distinct. The empirical distribution function is defined by:

```
F̂n(x) = { 0, x < x(1); k/n, x(k) ≤ x < x(k+1), k = 1, 2, ..., n-1; 1, x(n) ≤ x }
```

It has a jump of size `1/n` occurring at each observed value `xi`, and `Bx := F̂n(x)`, the value of the empirical distribution function at `x`, can be thought of as a random variable that can only take values of `0, 1/n, 2/n, ...`, or 1. It is clear that

```
P(nBx = k) = P(Bx = k/n) = (n choose k) (F(x))^k (1 - F(x))^(n-k), k = 0, 1, 2, ..., n,
```

