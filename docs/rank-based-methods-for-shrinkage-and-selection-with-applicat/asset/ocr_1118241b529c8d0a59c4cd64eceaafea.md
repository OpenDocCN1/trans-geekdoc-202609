Hence, the ridge-type R-estimator outperforms nEnetRE uniformly.

# ## 4.10 Summary

This chapter opened with the ANOVA model and described issues of robustness and partitioning. In particular, rank and LASSO can be effectively used to partition the treatments into subgroups, if the null hypothesis is rejected using a robust ANOVA. The variance of the treatments are instrumental in separating the different parameters into subgroups. If sparsity is suspected, then the parameters can be divided into two subgroups: “zero” and “non-zero”. To identify the sparse parameters, one of the subset selection penalties can be applied. After partitioning, the estimation can be carried out using one of several shrinkage estimators.

A comparison of the different shrinkage estimators using ADL2-risk produced the following results:

+   (i) Ridge regression as a shrinkage estimator dominates all other estimators uniformly.
+   (ii) The multi-dimensional preliminary test estimator and the Stein–Saleh estimator have similar performance characteristics to the one-dimensional PTE and Stein–Saleh estimators. That is, ADL2-risk(\(\hat{\theta}_n^{SSR+}\)) \(\le\) ADL2-risk(\(\hat{\theta}_n^{SSR}\)) \(\le\) ADL2-risk(\(\hat{\theta}_n^{UR}\)) uniformly.
+   (iii) None of the other estimators dominate over each other uniformly as seen in the previous chapter.

These results are similar in nature and consistent with the results presented in Chapter 3 where the single location problem was studied. Chapter 3 also addressed the simple linear model in detail. The next step is to solve a number of simple linear problems simultaneously and this is the subject of Chapter 5.

# ## 4.11 Problems

+   4.1. Derive ADV(\(\hat{\theta}_n^{UR}\)) to complete Theorem 4.1. (Hint: see Eq. (4.4.3)).
+   4.2. Show the steps needed to derive \(\mathcal{L}_{n_j} = \kappa_j T_{n_j}^2(0)/A_{n_j}^2\).
+   4.3. Qualitatively compare and contrast the preliminary test, Stein–Saleh, positive-rule Stein–Saleh and ridge R-estimators. Quantitatively compare them by plotting graphs of the ADL2-risk as a function of \(\Delta^2\). Compare your results with those given in Section 4.9.
+   4.4. Tabulate the ADRE values in Eq. (4.7.6) against \(\Delta^2\) based on \(\lambda^2 = 2 \ln(\text{tr}(\mathcal{K}_2))\).