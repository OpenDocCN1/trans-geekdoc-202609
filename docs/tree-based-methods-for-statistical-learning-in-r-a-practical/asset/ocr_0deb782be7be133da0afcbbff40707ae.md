```
#> Edibility
#> odor Edible Poison
#> almond 400 0
#> anise 400 0
#> creosote 0 192
#> fishy 0 576
#> foul 0 2160
#> musty 0 36
#> none 3408 120
#> pungent 0 256
#> spicy 0 576
(Tstat <- as.vector(ctab)) # multivariate linear statistic
#> [1] 400 400 0 0 0 0 3408 0 0 0
#> [11] 0 192 576 2160 36 120 256 576
```

Typically, when \(X\) and \(Y\) are categorical, the transformation function, \(g()\), and influence function, \(h()\), map each category to a vector of dummy encoded values. For example, using the order of categories from the above contingency table (`ctab`),

\(g(X_i) = (0, 0, 0, 0, 1, 0, 0, 0, 0, 0)^\top\)

and

\(h(Y_i) = (0, 1)^\top\).

would indicate a foul smelling, poisonous mushroom. In essence, \(g(X) = \mathbf{X}\) and \(h(Y) = \mathbf{Y}\) are the associated one-hot encoded model matrices for \(X\) and \(Y\), respectively.

In the special case where \(X\) and/or \(Y\) are binary, the identity transformation will lead to the same results as long as they're encoded as 0/1. For example, if \(X\) and \(Y\) are both binary 0/1 encoded variables, then the formulas in Section 3.3.1 will lead to identical results when \(g()\) and \(h()\) are both the identity function.

The Kronecker product, denoted \(\otimes\), also appears in (3.2). The Kronecker product between two matrices can be computed in R using the `kronecker()` function or the `%x%` operator. The Moore-Penrose inverse, denoted \(\Sigma^+\) in (3.2), can be computed using the `ginv()` function from the recommended **MASS** package [Ripley, 2022].

In the next code chunk, we compute the conditional expectation and variance using (3.2). Note that the formulas simplify greatly if we work directly with the one-hot encoded matrices \(g(X) = \mathbf{X}\) and \(h(Y) = \mathbf{Y}\); in R, these can be