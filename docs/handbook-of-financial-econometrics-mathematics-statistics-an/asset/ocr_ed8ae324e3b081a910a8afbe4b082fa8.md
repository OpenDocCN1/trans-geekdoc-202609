To implement the DWH test, from developments above, we need to construct 2 estimators for $\hat{\beta}_{\text{LS}}$ and $\hat{\beta}_{\text{IV}}$ such that

+   - $\hat{\beta}_{\text{LS}}$ is consistent and efficient under $H_{\text{LS}}$, but not consistent under $H_{\text{IV}}$.
+   - $\hat{\beta}_{\text{IV}}$ is consistent under both $H_{\text{LS}}$ and $H_{\text{IV}}$, but not efficient under $H_{\text{LS}}$.

In this case LS is consistent and efficient under the null hypothesis, but not consistent if **X** and **e** are not independent. IV is consistent under the null and alternative hypotheses, but not efficient under the null.

Since $y$ is the variable instrumented, our interest is with the associated parameter in comparing the LS estimates to each of the IV estimates. We can estimate the Hausman statistic for this parameter in each case as follows:

$m = \frac{\left(\hat{\beta}_{2,\text{IV}} - \hat{\beta}_{2,\text{LS}}\right)^2}{\text{var}\left(\hat{\beta}_{2,\text{IV}}\right) - \text{var}\left(\hat{\beta}_{2,\text{LS}}\right)} = \frac{\left(\hat{\beta}_{2,\text{IV}} - \hat{\beta}_{2,\text{LS}}\right)^2}{SE\left(\hat{\beta}_{2,\text{IV}}\right)^2 - SE\left(\hat{\beta}_{2,\text{LS}}\right)^2}.$

The calculated DWH statistics are provided in the Table 28.6. The $\chi^2(1)$ critical value for the 0.05 level of significance is 3.84.

Comparing the calculated statistic to the $\chi^2(1)$ critical value, the null is rejected in comparing LS to any of the IV estimates. So the LS parameter estimates are biased and inconsistent, there is contemporaneous correlation between $e_i$ and $y_i$. IV produces consistent estimates of the $\beta$ associated with $y_i$. Keep in mind, the interpretation of the DWH test is whether contemporaneous correlation has significant effects on estimates of $\hat{\beta}$ (not whether $e_i$ and $y_i$ are contemporaneously correlated).

Here are two other forms of the test, Durbin’s score and Wu–Hausman, of testing the validity of treating the explanatory variables ($y$ in this example) as exogenous.

The null is rejected in both tests, so treat $y$ as endogenous (this is consistent with the DWH test results above comparing LS to the IV estimates). From the DWH test results above, we know that we should be using an IV estimator rather than LS so that we can obtain consistent parameter estimates (LS estimates are biased). But which specification of the instruments should we use? First, we know in general that the more highly correlated the instrument is with the variable we are instrumenting, the more efficient the IV estimator. From results (compare the SE’s in the Table 28.7), $g_i$ appears to be more highly correlated with $y_i$ than is $i_i$. Second, as discussed above, all the IV estimates are very close to one another. Theoretically we know that IV3 should be the most efficient since we have more instruments than variables instrumented. Empirical results above agree, as we do see slightly smaller standard errors in IV3 than in the other IV estimates.