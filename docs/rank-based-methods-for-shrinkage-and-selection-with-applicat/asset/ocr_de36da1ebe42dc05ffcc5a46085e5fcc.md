would you determine $\hat{\beta}_n^R$ in general, given $\hat{\beta}_n^R$. Write the expression using uncentered data, $\mathbf{X}_{\text{uc}}$ and $\mathbf{y}_{\text{uc}}$. No calculations are needed here.

# 2.3. Examine Table 2.3 and Figure 2.3.

+   (a) Based on the table and the corresponding figure, which parameters would benefit most from a reduction in their variances (ignoring $\beta_0$, of course)?
+   
+   (b) Ideally, we would like to shrink only those with large variances. Which parameters would we prefer to keep the same because they already have small variances?
+   
+   (c) Next consider the ridge traces of Figure 2.5. What are the first three parameters that are reduced to almost 0 as $\lambda_2$ increases in the D-ridge plot? What are the last two parameters to be reduced to almost 0?
+   
+   (d) Why are the results from LS-ridge and rank-ridge somewhat different from those of D-ridge? (Hint: consider the effects of using the full $\mathbf{C}^{-1}$ matrix compared to a diagonal matrix to obtain the shrinkage estimates.)

# 2.4. Consider Figure 2.10 and the penalized least squares estimators for $\hat{\beta}_j^{\text{D-LASSO}}$ and $\hat{\beta}_j^{\text{D-aLASSO}}$, given below as,

$$\hat{\beta}_j^{\text{D-LASSO}} = \text{sgn}(\hat{\beta}_j^{\text{LS}})(|\hat{\beta}_j^{\text{LS}}| - \lambda_1 \text{Var}(\hat{\beta}_j^{\text{LS}}))^+$$

and

$$\hat{\beta}_j^{\text{D-aLASSO}} = \text{sgn}(\hat{\beta}_j^{\text{LS}}) \left( |\hat{\beta}_j^{\text{LS}}| - \lambda_1 \frac{\text{Var}(\hat{\beta}_j^{\text{LS}})}{|\hat{\beta}_j^{\text{LS}}|} \right)^+$$

respectively. The only difference is the use of a weighting term in aLASSO. Explain in a qualitative sense why aLASSO possesses the oracle property while LASSO does not, in general, have this feature using two different diamond shapes, one for LASSO and one for aLASSO. Show how the trajectories of the estimates may differ in the two cases. Connect your explanation to the traces shown in Figure 2.12. Why might the two traces differ?

# 2.5. Ridge and LASSO can be applied in a one-dimensional setting even though they were originally intended for multivariate regression with collinearity. For example, it can be applied to the location problem, with location parameter $\theta$, as will be discussed in detail in the next chapter.

+   (a) Devise a simple ridge-type penalty estimator that would shrink the estimate by division using $\lambda_2$ as the tuning parameter assuming you are given an unbiased rank estimate, $\hat{\theta}_n^R$. (Hint: see Eq. (2.4.7)).
+   
+   (b) Likewise, devise a simple LASSO-type penalty estimator by subtraction using $\lambda_1$ in your equation. (Hint: see Eq. (2.7.9))