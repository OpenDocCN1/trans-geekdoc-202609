# 26 Golbraikh and Tropsha's - [18] criterion

At least one slope of regression lines (k or k') between the regressions of actual (Ay) against predicted output (Pj) or Pj against Ay through the origin, i.e., Ay = k x Pj and Pj = k' Ay, respectively.

```
$k = \frac{\sum_{i=1}^n (A_i \times P_i)}{A_i^2}$

$k' = \frac{\sum_{i=1}^n (A_i \times P_i)}{P_i^2}$

\(m = \frac{R^2 - R_0^2}{R^2}\)

\(n = \frac{R^2 - R_{0^\prime}^2}{R^2}\)
```

+   - k and k' need to be close to 1.0 or at least within the range of 0.85 and 1.15.
+   - m and n are performance indexes and their absolute value should be lower than 0.1.

# 27 Q.S.A.R. model by Roy and Roy [19] -

```
$R_m = R^2 \times \left(1 - \sqrt{|R^2 - R_0^2|}\right)$
```

where

```
\(\frac{\sum_{i=1}^n (P_i - A_i^o)^2}{\sum_{i=1}^n (P_i - P_{mean})^2}, A_i^o = k \times P_i^o\)

\(= 1 - \frac{\sum_{i=1}^n (A_i - P_i^o)^2}{\sum_{i=1}^n (A_i - A_{mean})^2}, P_i^o = k' \times A_i\)
```

+   - \(R_m\) is an external predictability indicator. \(R_m > 0.5\) implies a good fit.

# 28 Frank and Todeschini - [20] -

Recommend maintaining a ratio of 3-5 between the number of observations and input parameters.