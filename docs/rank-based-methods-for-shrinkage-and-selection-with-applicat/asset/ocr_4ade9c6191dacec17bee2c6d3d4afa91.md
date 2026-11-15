An estimator performs better than another if it has a lower ADL2-risk. We will also be comparing the ADL2-risk efficiency (ADRE) of the various estimators. The relative efficiency of an estimator of interest, \(\hat{\theta}_n\), compared to a reference estimator, \(\hat{\theta}_n^*\), is defined as

```
\(\text{ADRE}(\hat{\theta}_n : \hat{\theta}_n^*) = \frac{\text{ADL}_2\text{-risk}(\hat{\theta}_n^*)}{\text{ADL}_2\text{-risk}(\hat{\theta}_n)}.\)
```

For R-estimation, we will need the services of a scoring function. We define the score function in the following manner:

```
\(\psi(u, f) = -\frac{f'(F^{-1}(u))}{f(F^{-1}(u))}, \quad 0 < u < 1,\)
```

and

```
\(\psi^+(u, f) = -\frac{f'(F^{-1}(\frac{1+u}{2}))}{f(F^{-1}(\frac{1+u}{2}))}.\)
```

For instance, consider the logistic distribution,

```
\(F(x) = \frac{1}{1 + \exp(-x)},\)
```

which satisfies the required continuity and symmetry conditions. Then

```
\(f(x) = \frac{\text{d}F(x)}{\text{d}x} = \frac{\exp(-x)}{(1 + \exp(-x))^2}.\)
```

It follows that

```
\(f'(x) = \frac{\text{d}f(x)}{\text{d}x} = -\frac{\exp(-x)(1 - \exp(-x))}{(1 + \exp(-x))^3},\)
```

and also

```
\(F^{-1}(u) = -\ln \left(\frac{1}{u} - 1\right),\)
```

such that

```
\(F^{-1}\left(\frac{1+u}{2}\right) = -\ln \left(\frac{2}{1+u} - 1\right) = -\ln \left(\frac{1-u}{1+u}\right).\)
```

Therefore, the score function is

```
\(\psi(u, f) = -\frac{f'(F^{-1}(u))}{f(F^{-1}(u))} = -\frac{-u(1-u)(2u-1)}{u(1-u)} = 2u - 1\)
```