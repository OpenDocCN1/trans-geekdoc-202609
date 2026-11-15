ADL_2\text{-risk}(\hat{\theta}_n^{*\text{ridge}}(\lambda)) = \eta^2 \left( 1 + \frac{\tilde{\varkappa}_n^2}{Q} \frac{1}{(1+\lambda)^2} (1 + \lambda^2 \Delta^2) \right).

+   3.6. Derive the ADL$_2$-risk for the intercept parameter $\hat{\theta}_{n,\text{SR}}^{\text{PTR}}.$
+   3.7. Derive the ADL$_2$-risk for the intercept parameter $\hat{\theta}_{n,\text{SR}}^{*\text{ridge}}.$
+   3.8. Consider the results shown in Table 3.5 and Figure 3.5. Noting the similarity of the results of the location and intercept parameters, compare the different estimators in Problems 3.4, 3.5, 3.6 and 3.7. Which is the best and which is the worst of the three?

+   3.9. (PROJECT) The dispersion function for the location parameter, $\theta$, was given as
+   
+   $D_n(\Theta) = \sum_{i=1}^n |y_i - \theta| \alpha_n^+(R_{n_i}^+(\Theta)).$
+   
+   The estimator is given by
+   
+   \(\hat{\theta}_n^{\text{UR}} = \underset{\theta \in \mathbb{R}}{\text{argmin}}\{D_n(\Theta)\}.\)

+   (a) Use the following R code to generate a data set with $n = 64$:
+   
+   ```
+   set.seed(123)
+   #Pick 64 random points
+   n <- 64
+   y <- rnorm(n)+0.97194 #adjust to make median = 1
+   ```

+   (b) Use the following unrestricted rank estimator to find the estimate. It uses the dispersion function for the location parameter. What is $\hat{\theta}_n^{\text{UR}}$ based on the results of the code?
+   
+   ```
+   minimize.Dn <- function(theta, y) {
+   n <- length(y)
+   abs_diff <- abs(y-theta)
+   rank_abs_diff <- rank(abs_diff,
+   ties.method = "first")
+   an_plus <- sqrt(3.0)*(rank_abs_diff)/(n+1.)
+   Dnsum <- sum(abs_diff*an_plus)/n
+   return(Dnsum)
+   }
+   
+   op.result <- optim(2.0,
+   fn = minimize.Dn,
+   method = "BFGS",
+   y = y)
+   ```