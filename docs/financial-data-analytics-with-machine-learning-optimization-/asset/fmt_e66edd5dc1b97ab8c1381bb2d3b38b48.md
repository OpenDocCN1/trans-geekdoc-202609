
In particular, when `Σ_P = Σ_Q`, the relative entropy from `Q` to `P` becomes larger when `μ_P` and `μ_Q` are farther apart. On the other hand, when `μ_P = μ_Q`, the direction of change whenever `Σ_P ≠ Σ_Q` is not as straightforward. Consider the one‐dimensional case with variances `σ_P^2` and `σ_Q^2`, and an arbitrary correlation coefficient `ρ`. The relative entropy from `Q` to `P` is then reduced to:

```
D(P‖Q) = 1/2 (σ_P^2 / σ_Q^2 - ln(σ_P^2 / σ_Q^2) - 1)
```

which becomes larger if the ratio `σ_P^2 / σ_Q^2` is farther away from 1.

### ii) Cross Entropy:

The *cross entropy* between two discrete distributions `P` and `Q` is defined as

[(13.8)](#c13.xhtml#R_c13-disp-0029)
```
H(P, Q) := H(P) + D(P‖Q)
```

where `H(P) := -∑_{x ∈ 𝒳} P(x) ln P(x)` denotes the rescaled entropy of `P`. By simplifying ([13.8](#c13.xhtml#c13-disp-0029)), an equivalent definition is:

```
H(P, Q) = -∑_{x ∈ 𝒳} P(x) ln Q(x).
```

As long as `P` is fixed, `H(P)` is a constant independent of `Q`, so there is an equivalence between relative entropy and cross entropy. A similar notion of entropy can be defined for continuous distributions by replacing summation by integration. In real applications, cross entropy is often served as an objective function in deep learning to measure the similarities between the sample distribution of labels and the predicted distribution.

## 13.3 INFORMATION GAIN
