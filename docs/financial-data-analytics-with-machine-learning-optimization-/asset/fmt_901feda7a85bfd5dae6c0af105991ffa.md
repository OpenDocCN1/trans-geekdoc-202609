
A `regression tree` is similar to a classification tree, except that while the label variable `y` must be categorical for a classification tree, for a regression tree it takes a continuum of values. Recall that the main inspiration behind classification trees is segmenting the space of feature vectors `D` into `M` simpler regions, namely `D1, ..., DM`. The predictor function `f̂` (to predict the label in this case) is written as:

[(13.18)](#c13.xhtml#R_c13-disp-0050)
```
f̂(x) = Σ(k=1 to M) c_k * 1{x ∈ D_k}
```

Building a classification tree `T` is essentially finding a set of terminal leaf nodes `{T1, ..., TT}` that minimizes the misclassification error `R(T)` in ([13.14](#c13.xhtml#c13-disp-0046)) (or ([13.16](#c13.xhtml#c13-disp-0048)) if cost complexity pruning is adopted). For building a regression tree, we shall replace the 0‐1 loss of `1{y_i ≠ ŷ_T_l}` by the squared loss function:

[(13.19)](#c13.xhtml#R_c13-disp-0051)
```
R(T) := (1/n) Σ(l=1 to T) Σ((x_i, y_i) ∈ T_l) (y_i - ŷ_T_l)^2
```

and the resulting tree built from minimizing ([13.19](#c13.xhtml#c13-disp-0051)) is commonly called a regression tree with `M = T` being the total number of partitions. Certainly, we can simply assign a single but continuous label value for each `T_l`, for example the mean for the subsample at each terminal node:

(13.20)
```
ŷ_T_l = (1/|T_l|) Σ((x_i, y_i) ∈ T_l) y_i, for l = 1, ..., T
```

On the other hand, we can also rewrite ([13.19](#c13.xhtml#c13-disp-0051)) as:
