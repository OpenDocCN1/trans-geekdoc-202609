
Binary logistic regressions can be easily extended to `Multinomial Logistic Regression` in which the response `y` is categorical, with more than two categories. For instance, let `y` take `k` categories, namely `c1, ..., ck`, and we model the corresponding probabilities by:

```
P(y_i = c1 | x_i) = 1/ξ exp(x_i^T β_1), ..., P(y_i = ck | x_i) = 1/ξ exp(x_i^T β_k),
```

where `ξ := exp(x_i^T β_1) + ... + exp(x_i^T β_k)`. These `β_j`'s cannot be uniquely estimated unless one of them is standardized to be zero. Fortunately, it does not matter which `β_j` is chosen as zero. Setting `β_1 = 0`, the model becomes:

[(10.15)](#c10.xhtml#R_c10-disp-0039)

```
P(y_i = c1 | x_i) = 1/ξ, P(y_i = c2 | x_i) = exp(x_i^T β_2)/ξ, ..., P(y_i = ck | x_i) = exp(x_i^T β_k)/ξ,
```
