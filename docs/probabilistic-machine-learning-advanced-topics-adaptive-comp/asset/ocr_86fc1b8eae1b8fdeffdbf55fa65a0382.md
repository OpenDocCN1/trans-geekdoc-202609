In practice, we can estimate the quantity by fitting a new regression model \(\hat{Q}_Z\) that predicts \(Y\) from \(A\) and \(X \backslash Z\). Then we compute

\(\begin{aligned} R^2_{Y \cdot Z | T, X \backslash Z} = 1 - \frac{\frac{1}{n} \sum_i (y_i - \hat{Q}(t_i, x_i))^2}{\frac{1}{n} \sum_i (y_i - \hat{Q}_Z(t_i, x_i \backslash z_i))^2}. \end{aligned}\)

Using Theorem 8, we can measure influence of observed covariate \(Z\) on treatment assignment given \(X \backslash Z\) in an analogous fashion to the outcome. We define \(g_{X \backslash Z}(X \backslash Z) = P(A=1|X \backslash Z)\), then fit a model for \(g_{X \backslash Z}\) by predicting \(A\) from \(X \backslash Z\), and estimate

\(\begin{aligned} \hat{\alpha}_{Z|X \backslash Z} = 1 - \frac{\frac{1}{n} \sum_i \hat{g}(x_i)(1 - \hat{g}(x_i))}{\frac{1}{n} \sum_i \hat{g}_{X \backslash Z}(x_i \backslash z_i)(1 - \hat{g}_{X \backslash Z}(x_i \backslash z_i))}. \end{aligned}\)

**Grouping covariates** The estimated values \(\hat{\alpha}_{X \backslash Z}\) and \(\hat{R}^2_{Y,X \backslash Z}\) measure the influence of \(Z\) conditioned on all the other confounders. In some cases, this can be misleading. For example, if some piece of information is important but there are multiple covariates providing redundant measurements, then the estimated influence of each covariate will be small. To avoid this, group together related or strongly dependent covariates and compute the influence of the entire group in aggregate. For example, grouping income, location, and race as ‘socioeconomic variables’.

# ## 36.7.2.2 Practical use

We now have sufficient results to produce Austen plots such as Figure 36.7. At a high level, the procedure is:

+   1. Produce an estimate \(\hat{\tau}\) using any modeling tools. As a component of this, estimate the propensity score \(\hat{g}\) and conditional outcome model \(\hat{Q}\).
+   
+   2. Pick a level of bias that would suffice to change the qualitative interpretation of the estimate (e.g., the lower bound of a 95% confidence interval).
+   
+   3. Plot the values of \(\alpha\) and \(R^2_{Y, \text{par}}\) that would suffice to induce that much bias. This is the black curve on the plot. To calculate these values, use Theorems 6 and 7 together with the estimated \(\hat{g}\) and \(\hat{Q}\).
+   
+   4. Finally, compute reference influence level for (groups of) observed covariates. In particular, this requires fitting reduced models for the conditional expected outcome and propensity that do not use the reference covariate as a feature.

In practice, an analyst only needs to do the model fitting parts themselves. The bias calculations, reference value calculations, and plotting can be done automatically with standard libraries.\(^{12}\). Austen plots are predicated on Equation (36.105). This assumption replaces the purely parametric Equation (36.98) with a version that eliminates any parametric requirements on the observed data. However, we emphasize that Equation (36.105) does, implicitly, impose some parametric assumption on the structural causal relationship between \(U\) and \(A, Y\). Ultimately, any conclusion drawn from