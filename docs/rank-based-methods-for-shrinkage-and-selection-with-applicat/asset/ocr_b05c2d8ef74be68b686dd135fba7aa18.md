roughly equal size. One subset is left aside, \(\{(\mathbf{x}^{\text{test}}, \mathbf{y}^{\text{test}})\}\), termed the test set, while the remaining \(K - 1\) subsets, called the training set, are used to fit the model. The result estimator is called \(\hat{\boldsymbol{\beta}}^{\text{train}}\). The fitted model is then used to predict the responses of the test data set. Finally, prediction errors are obtained by taking the squared deviation of the observed and predicted values in the test set, i.e.

```
\(\text{PE}_k^k = \|\mathbf{y}_k^{\text{test}} - \hat{\mathbf{y}}_k^{\text{test}}\|^2; \quad k = 1, 2, ..., K,\)
```

where \(\hat{\mathbf{y}}_k^{\text{test}} = \mathbf{X}_k^{\text{test}} \hat{\boldsymbol{\beta}}_k^{\text{train}}\). The process is repeated for all \(K\) subsets and the prediction errors are combined. To account for the random variation of the cross validation, the process is reiterated \(N\) times and the median prediction error (MPE) is estimated using

```
\(\text{MPE} = \text{median} \left\{ \frac{1}{K} \sum_{k=1}^K \text{PE}_1^k, ..., \frac{1}{K} \sum_{k=1}^K \text{PE}_N^k \right\},\)
```

where \(\text{PE}_i^k\) is the prediction error considering the \(k\)th test set in the \(i\)th iteration. The performance of the arbitrary estimator, \(\hat{\boldsymbol{\beta}}_n^{\star}\), with respect to the full model estimator, \(\hat{\boldsymbol{\beta}}_n^{\text{ULiR}}(d)\), is obtained by the efficiency (Eff) formula defined as

```
\(\text{RMPE}(\hat{\boldsymbol{\beta}}^*; \hat{\boldsymbol{\beta}}_n^{\text{ULiR}}(d)) = \frac{\text{MPE}(\hat{\boldsymbol{\beta}}_n^{\text{ULiR}}(d))}{\text{MPE}(\hat{\boldsymbol{\beta}}^*)}.\)
```

If the value of RMPE is greater than 1, then \(\hat{\boldsymbol{\beta}}^*\) performs better than \(\hat{\boldsymbol{\beta}}_n^{\text{ULiR}}(d)\). Our results are based on \(N = 500\) resampled bootstrap samples. In Table 8.2, we report the estimations for the 10 parameters, and the MPE and RMPE of each method. Note, PTLRE1, PTLRE2, PTLRE3, and PTLRE4 stand for PTLRE with \(\alpha = 0.01\), \(\alpha = 0.05\), \(\alpha = 0.15\), and \(\alpha = 0.25\), respectively. From this table, the restricted Liu-type R-estimator (RLRE) performs better than other estimators, based on an MPE of 17.92 and an RMPE of 1.54. When comparing the other penalized estimators, the positive-rule Stein-type shrinkage Liu-type R-estimator (PRSLRE) has a lower median prediction error of only 19.66 while the rest are above 20.0. Among the remaining penalized estimators, aLASSO is the best at 20.11, while MNET stands in the second position with 21.94.

The results are somewhat counter to conventional wisdom whereby a sparse regression model should benefit greatly from the use of penalty estimators such as LASSO and aLASSO. But the results in the table indicate that PRSLRE (with RMPE of 1.40) is superior to LASSO (with RMPE of 1.17) and competitive with or slightly better than aLASSO (with RMPE of 1.37) on this data set. As seen earlier in Chapter 2, there is sparsity in this data set and PRSLRE was able to