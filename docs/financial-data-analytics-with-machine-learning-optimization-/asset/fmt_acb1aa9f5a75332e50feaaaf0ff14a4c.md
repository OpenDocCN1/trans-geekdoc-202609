
As in reality not all feature variables are necessarily comonotonic, a more appropriate and realistic approach in classification problems is to first partition the feature variables into several subgroups, and then treat the feature variables within each group as comonotonic while the totality of features in a group is independent of those in another group. However, the exhaustive searching time for the optimal partition grows rapidly with the number of features involved. We therefore have to deploy an efficient heuristic search to approximate this optimal partition without traversing all possibilities. The solution turns out to be a method of clustering. In principle, two features with a small value of some pre‐specified “distance” are regarded as comonotonic and should be clustered into the same group. Some popular distance metrics for the purpose of measuring comonotonic dependence include `Normalized Mutual Information` `U`, `Pearson's` `r`, `Kendall's` `τ_b`, and `Spearman's` `ρ`. We introduce another one based on Kendall's `τ_b`, specifically built for CIBer. It should be noted that the selection of the distance metric varies case by case, and we always aim to choose the one leading to the best performance. Let us list out these metrics in their natural empirical form, where `x_i` and `x_j` are any two distinct features with observed pairs `(x_1i, x_1j), …, (x_ni, x_nj)`:

1. **Normalized Mutual Information (NMI)** `Û` [15](#c12.xhtml#c12-bib-0015), [21](#c12.xhtml#c12-bib-0021): it quantifies the dependence between two features using entropy from information theory:

```
Û := 2 · Î(x_i; x_j) / (Ĥ(x_i) + Ĥ(x_j)).
```

Here `Î(x_i; x_j)` is the empirical mutual information between `x_i` and `x_j` defined by
