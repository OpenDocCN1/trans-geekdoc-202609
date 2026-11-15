To obtain the LSE, we first center the data, both the design matrix (comprised of columns A, Ex, Ed, C and I) and the response (column F). Then we use Eq. (2.3.7) to obtain the estimates. For the standard errors of LSE, we can first compute the value of \(\hat{\sigma}^2 = \text{SSE}/(n-p) = 50.1\), noting that SSE is from Eq. (2.3.11). Then we apply Eqs. (2.3.8) and (2.3.10) to obtain the s.e. We can obtain the LS intercept, called \(\beta_0\) or \(\theta_n\), using *uncentered data* of \(\mathbf{y}\) and \(\mathbf{X}\) from

\(\hat{\theta}_n^{LS} = \frac{1}{n} \sum_{i=1}^n (y_i - \mathbf{x}_i^{T} \hat{\beta}_n^{LS}).\) (2.5.1)

For R-estimates, we do not need to center the data prior to estimation. We simply minimize (2.3.12) to obtain the parameters, and use (2.3.13) to obtain the s.e. with \(\hat{\eta}^2 = 49.0\). The rank intercept can be obtained using the median of the residuals from the original uncentered data of \(\mathbf{y}\) and \(\mathbf{X}\)

\(\hat{\theta}_n^R = \text{median}_{1 \le i \le n} (y_i - \mathbf{x}_i^{T} \hat{\beta}_n^R).\) (2.5.2)

The parameter values from LSE and rank methods are shown in Table 2.3. We find that the LSE and rank results5 are similar, both for estimates and standard error (s.e.), implying that there are no outliers. However, a check of the Q-Q plot for the residuals indicates two outliers, one in each tail, as shown in Figure 2.2.

Although both LS and rank produce roughly similar results, this does not imply the absence of outliers in the data, as seen around ($-2.5, -2.5$) and ($2.5, 2.5$) of the Q-Q plot. So one cannot simply assume no outliers when LS and rank estimates are similar. We should keep this in mind when interpreting the results of the two estimators. What we do know is that both estimators are equivalent in this balanced scenario. Of course, any imbalance in the number outliers in either tail may lead to different LS and rank estimates. In any case, we will first study this balanced outlier situation, where we expect similar performance, and then later examine the unbalanced case using a different data set.

# 2.5.2 Parameter Variance using Bootstrap

We draw the reader's attention to the standard error columns in Table 2.3. It is well known that these values quantify the uncertainty in the estimates. If we square the standard error, we obtain the estimated variance for each parameter. We can illustrate this more concretely by sampling the given data set multiple times and then computing estimates for each sample. That is, we can create sampling distributions of the estimates using the bootstrap method

5 These results are obtained from R using lm() for LSE and rfit() for R-estimates.