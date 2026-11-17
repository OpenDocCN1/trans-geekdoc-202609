![](bbox=[0.116, 0.108, 0.877, 0.333])

Figure 12.14 F1 score as a function of p_T.

However, CELR-ridge can improve the results by adjusting the C hyperparameter, but it only provides a marginal improvement. The robust form of logistic regression achieves superior results without requiring regularization.

On the other hand, penalty functions, such as the adaptive LASSO (aLASSO), can still play an important role for LCLR in reducing variance and assessing variable importance. In particular, aLASSO traces provide useful information regarding variable ordering due to the fact that aLASSO has the oracle property. LCLR traces with aLASSO are shown in Figure 12.15. Based on the variable ordering, we find that

![](bbox=[0.156, 0.536, 0.642, 0.866])

Figure 12.15 Visualization of feature importance using LCLR-aLASSO traces for the Titanic dataset.