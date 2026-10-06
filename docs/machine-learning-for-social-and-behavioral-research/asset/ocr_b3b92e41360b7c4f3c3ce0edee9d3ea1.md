# Machine Learning for Social and Behavioral Research

model. While it is clear how the prediction is modeled (i.e., averaged predictions from the ensemble of decision trees), it is less clear how each variable is associated with the outcome. To reduce the effect of this limitation by bagging, researchers have developed variable importance metrics. As noted, one of the largest drawbacks to ensemble methods, such as bagging, is uncertainty as to the relationship between the predictors and the outcome. Simply put, there is no single tree structure or set of coefficients to interpret. To overcome this limitation of ensemble methods, relative importance metrics have been proposed to determine how much each variable contributes to the prediction of the outcome. Following Breiman et al. (1984), variable importance for a decision tree is calculated as

```
$I_i(T) = \sum_{t=1}^{M} \Delta(\delta_i, t)$
```

for each predictor $x_i$, where there are $J-1$ internal nodes, node $t$, $\delta_i$ is the surrogate split for $x_i$, and $\Delta_i$ is a measure of error improvement for node $t$ (e.g., decrease in purity or other measure of misfit). This variable importance metric is referred to as the *increase in purity purity*. By using surrogate splits, it also allows variables that were not included in the derived tree to selected, have importance values greater than zero. This is particularly important in the presence of correlated predictors. It becomes relatively straightforward to extend this variable importance metric to an aggregation across trees. That is, variable importance for an ensemble of decision trees is

```
$I_i = \frac{1}{M} \sum_{m=1}^{M} l_i(T_m)$
```

where $M$ is the number of trees. These values for each predictor are rarely interpreted in this manner, but typically transformed so that the sum equals 100 or the most important predictor takes a value of 100. An alternative method for calculating variable importance is the use of permutation tests. From Strobl, Bouleix, Kneib, Augustin, and Zeiles (2008): “that a random permutation of the values of the predictor variable is supposed to mimic the absence of the variable from the model.” This form of variable importance was proposed in Breiman (2001a) using the out-of-bag (OOB) samples. Specifically, for the Mth tree grown, prediction performance (e.g., RMSE) is recorded for the OOB sample. Next, for the lth

> Note that we subsequently drop the term *relative* and just refer to *variable importance*.