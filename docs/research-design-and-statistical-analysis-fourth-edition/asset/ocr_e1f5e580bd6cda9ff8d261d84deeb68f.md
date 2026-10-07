# Appendix 19.1

The Standard Errors of $b_0$ and $b_1$

We start by showing that $b_i$ can be expressed as a linear combination of the Ys. From Equation 17.11,

```
$b_1 = r\frac{s_Y}{s_X}$
```

Substituting expressions for $r$ (Equation 17.3), $s_Y$ and $s_X$, and simplifying,

```
$b_1 = \frac{1}{N-1} \sum \frac{(X_i - \bar{X})}{s_X} \frac{(Y_i - \bar{Y})}{s_Y} s_X = \frac{1}{(N-1)s_X^2} \sum(X_i - \bar{X})(Y_i - \bar{Y})$$\n= \frac{\sum(X_i - \bar{X})Y_i}{s_X} - \frac{\sum(X_i - \bar{X})\bar{Y}}{s_X^2}$\n= \frac{\sum(X_i - \bar{X})\bar{Y}}{SS_X} = 0$
```

Therefore, $b_i$ can be expressed as a linear combination of the Ys; that is,

```
$b_1 = \sum f_i Y_i$ where $f_i = \frac{X_i - \bar{X}}{SS_X}$
```

The variance of $b_i$,

```
$var(b_1) = var(\sum f_i Y_i) = var(f_1 Y_1 + f_2 Y_2 + ... + f_N Y_N)$$\n= var(f_1 Y_1) + var(f_2 Y_2) + ... + var(f_N Y_N)$, assuming independence$\n= f_1^2\sigma_1^2 + f_2^2\sigma_2^2 + ... + f_N^2\sigma_N^2$\n= \sigma_{\epsilon}^2(f_1^2 + f_2^2 + ... + f_N^2)$, assuming homoscedasticity$\n= \sigma_{\epsilon}^2 \sum f_i^2$
```

Now, because

```
$f_i = \frac{X_i - \bar{X}}{SS_X}$
```