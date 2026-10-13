
In the sequel, some results tailored to the needs of our current discussion will be discussed.

### Approximation, estimation, and optimization errors

Recall that all we are given in a machine learning task is the available training set of examples. To set up the "game," the designer has to decide on the selection of (a) the loss function, `ℒ(⋅, ⋅)`, which measures the deviation (error) between predicted and target values, and (b) the set `ℱ` of (parametric) functions,

```
ℱ = {f[θ]: θ ∈ ℝ^(K)}.
```

Based on the choice of `ℒ(⋅, ⋅)`, the *benchmark* function, denoted as `f[*]`, is the one that minimizes the expected loss (see also Chapter [3](#Chp003_65-117_B9780443292385000093.xhtml)), that is,^([^(57)](#fn57))

```
f_* = argmin_f 𝔼 [ ℒ( y, f(x) ) ],
```

or equivalently

```
f_*(x) = argmin_ŷ 𝔼 [ ℒ( y, ŷ ) | x ]. (8.91)
```

Let also `f[θ[*]]` denote the optimal function that results by minimizing the expected loss constrained within the parametric family `ℱ`, that is,

![Equation](images/B9780443292385000147/fx031.jpg)(8.92)

However, instead of `f[θ[*]]`, we obtain another function, denoted as `f[N]`, by minimizing the empirical risk, `J[N](θ)`,

![Equation](images/B9780443292385000147/fx032.jpg)(8.93)

Once `f[N]` has been obtained, we are interested in evaluating its generalization performance; that is, to compute the value of the expected loss at `f[N]`, `𝔼[ℒ(y, f[N](x))]`. The excess error with respect to the optimal value can then be decomposed as [13]
