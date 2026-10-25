Here we would reject the null hypothesis at the \(\alpha = 0.05\) level (\(p < 0.001\)) and conclude that there is some degree of association between Temp and Ozone.

For comparison, we can use the `independence_test()` function from package **coin**, which provides a flexible implementation of the conditional inference procedures described in Hothorn et al. [2006b]; see `?coin::independence_test` for details. This is demonstrated in the code snippet below:

```
library(coin)
independence_test(Ozone ~ Temp, data = aq, teststat = "quadratic")
#>
#> Asymptotic General Independence Test
#>
#> data:  Ozone by Temp
#> chi-squared = 56, df = 1, p-value = 7e-14
```

Happily, we obtain the exact same results. Note that \(c_m\) and \(c_q\) will only differ when the linear statistic (3.1) is multivariate.

# 3.3.2 Example: X and Y are both nominal categorical

When \(X\) and \(Y\) are both categorical, \(T\) is essentially the vectorized (i.e., flattened) contingency table between \(X\) and \(Y\); in this section, I'll continue to drop the bold notation. Assume \(X\) and \(Y\) have \(q\) and \(p\) unique categories, respectively. A contingency table between \(X\) and \(Y\) is nothing more than a \(q \times p\) table containing the observed frequencies of each \(qp\) pair of categories from \(X\) and \(Y\).\(^\text{b}\) Recall the appearance of the matrix vectorization operator, \(\text{vec}()\), in formulas (3.1)-(3.2). The \(\text{vec}()\) operator turns an \(m \times n\) matrix into an \(mn \times 1\) column vector. So a vectorized \(q \times p\) contingency table is just a \(qp \times 1\) column vector containing the individual frequencies, where the vectorization happens columnwise. For example, if \(A = \left( \begin{array}{cc} a & b \\ c & d \end{array} \right)\) is a \(2 \times 2\) matrix (or contingency table), then \(\text{vec}(A) = (a, c, b, d)^\top\), where \(\top\) represents the transpose operator.

Let's return to the mushroom edibility example (Section 1.4.4). Let \(X = \text{odor}\) and \(Y = \text{Edibility}\); both are nominal categorical with nine and two categories, respectively. A contingency table cross-classifying each variable is given below using the `xtabs()` function (see `?stats::xtabs` for details). The vectorized contingency table is also constructed by calling `as.vector()`:

```
mushroom <- treemisc::mushroom
(ctab <- xtabs(~ odor + Edibility, data = mushroom))
```

b Here we assume that the q categories of X define the rows of the contingency table, but in general, it does not matter.