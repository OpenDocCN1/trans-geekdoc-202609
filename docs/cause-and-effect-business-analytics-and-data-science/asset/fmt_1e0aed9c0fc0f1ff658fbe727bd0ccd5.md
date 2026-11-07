
In an article, [King and Nielsen (2019)](#chapter3.xhtml#ref3_18) argue that propensity scores should not be used for matching. They show that the more balanced the initial data are, the greater the danger that propensity score matching will “degrade inferences” (p. 2), a phenomenon they refer to as the propensity score paradox. Their other argument is that researchers are likely to report the results from versions of propensity score matching that reflect, perhaps unconsciously, their own biases, so the model chosen itself depends on the data (“model dependence”); in their words, “human choice turns model dependence into bias” (p. 5). This weakens the ability of propensity score matching to deliver unbiased judgments.
There are a number of other, increasingly popular, methods for inferring causality via matching, starting with `IPW`.

### 3.4.6 Inverse Probability Weighting (IPW)
An elegant method for measuring the treatment effect is to estimate a regression of the form
`Y[i] = α + β T[i]`
(3.11)
where `Y[i]` is the outcome of interest (e.g., GPA), and `T[i]` is the treatment, for instance, being in the honors program (see [Hernán and Robins 2006](#chapter3.xhtml#ref3_9)). However, the twist here is that this needs to be a weighted regression, where the weights are the inverse probabilities from the propensity scores. More specifically, we have:
$$w\_{i} = \\left\\{ \\begin{matrix} \\frac{1}{{\\hat{p}}\_{1}} & \\text{for~treated~case} \\\\ \\frac{1}{\\left( {1 - {\\hat{p}}\_{1}} \\right)} & {\\text{for~non} - \\text{treated~case}} \\\\ \\end{matrix}~ \\right.$$
Then the estimated coefficient `β̂` in Eqn. (3.11) gives the `ATE`.
Page 65In effect, this estimator puts higher weights on rare occurrences. This is analogous to the use of survey weights, where more weight is put on observations that are less likely to have been sampled because they are standing in for larger numbers of unsampled items. To measure the `ATT`, the weights needed are:
$$w\_{i} = \\left\\{ \\begin{matrix} {1~} & {for~treated~cases} \\\\ \\frac{{\\hat{p}}\_{i}}{\\left( 1 - {\\hat{p}}\_{i} \\right)} & {~for~non - treated~cases} \\\\ \\end{matrix}~ \\right.$$
and for the `ATC`, we have:
$$w\_{i} = \\left\\{ \\begin{matrix} \\frac{\\left( 1 - {\\hat{p}}\_{i} \\right)}{{\\hat{p}}\_{i}} & {for~treated~cases} \\\\ 1 & {~for~non - treated~cases} \\\\ \\end{matrix}~ \\right.$$
When the propensity scores are either very low or very high, the weights can become rather large, and this method becomes less robust.
One solution to the problem of extreme weights is to trim them. For instance, we may cap (“windsorize”) the weights at the 5th and 95th percentiles. There is no generally recognized standard for the cut-off percentiles ([Crump et al. 2009](#chapter3.xhtml#ref3_2); [Morgan and Winship 2015](#chapter3.xhtml#ref3_21)), so the procedure used will be decidedly ad hoc. However, [Lee et al. (2011)](#chapter3.xhtml#ref3_19), using a logistic-regression-based propensity score model, find that the trimming does lead to more robust results.
The other potential problem with the “original” weights shown here is that they are known to increase the sample size artificially, which is likely to affect the standard errors of the estimators. [Hernán and Robins (2025)](#chapter3.xhtml#ref3_10) make the case for using “stabilized” weights, which ensure the weighted sample is the same size as the original sample while leaving the coefficients unchanged (see [Chapter 9](#chapter9.xhtml), Eqn. 9.5). This is achieved by replacing `p̂[i]` with ${{\\hat{p}}\_{i}/\\overset{-}{p}},$ and (1−`p̂[i]`) with $\\left. \\left( 1 - \\hat{p} \\right.\_{i} \\right)/\\left( 1 - \\overset{-}{p} \\right)$, where $\\overset{-}{p}$ is the average propensity (or the predicted value of a logistic regression with only a constant term). So, for example, the stabilized weights for the `ATE` would be given by:
$$w\_{i} = \\left\\{ \\begin{matrix} {\\frac{\\overset{-}{p}}{{\\hat{p}}\_{i}}~} & \\text{for~treated~cases} \\\\ \\frac{\\left( 1 - \\overset{-}{p} \\right)}{\\left( 1 - {\\hat{p}}\_{i} \\right)} & {~for~non - treated~cases} \\\\ \\end{matrix}~ \\right.$$
Page 66There is a growing literature advocating for stabilized, rather than ordinary, weights.
As with propensity score matching, the inverse probability weighted regression should only be estimated using those observations that are in the region of common support.

### 3.4.7 Doubly-robust Methods
It is possible to combine the regression adjustment and the `IPW` approaches in a rather natural manner: Estimate the regression adjustment equations using the inverse probability weights.
Another possible extension is the `augmented inverse probability weighting` approach ([Glynn and Quinn 2010](#chapter3.xhtml#ref3_7)), which estimates Eqn. (3.11) but includes a number of additional variables, such as those used in the regression adjustment model.
It is also possible to combine matching and regression methods. Matching could be used first to trim (or take a “strategic subsample” from) the data, and then regression techniques could be applied to the dataset that should now look more like a dataset from a natural experiment.
All of these are examples of “doubly-robust” methods. The idea is that they hold greater promise of yielding good results, even if one of the sets of assumptions underlying (for instance) regression adjustment or `IPW` does not entirely hold. For instance, regression adjustment requires that the treatment be independent of the error in Eqn. (3.9), the causal effect does not vary with the other regressors, and the estimated equation is fully flexible ([Morgan and Winship 2015](#chapter3.xhtml#ref3_21), p. 205). The `IPW` also requires the assumption of ignorable treatment and overlap between the treated and non-treated samples.

#### 3.4.7.1 Covariate (“Nearest Neighbor”) Matching
There are also ways to match someone who is treated with someone similar who is not, but without using propensity scores. A basic form of `nearest-neighbor matching` proceeds as follows:
1. Normalize all the relevant variables (“covariates”), such as age, SAT score, and so on, so they have zero means and standard deviations of 1, using
$$u\_{i} = \\frac{X\_{i} - \\overset{-}{X}}{s\_{i}},$$
where `X[i]` is the variable, $\\overset{-}{X}$ is its mean, and `s[i]` is the standard deviation of the `X[i]`.
2. Page 67For every pair of treated and untreated (comparison) individuals, with vectors of normalized variables `U[i]^T` and `U[i]^C`, define the distance between them as
$${\\left\\| {U\_{i}^{T} - U\_{i}^{N}} \\right\\|~}\_{V} \\equiv \\sqrt{\\left( U^{T} - U^{C} \\right)'V\\left( U^{T} - U^{C} \\right)}$$
where `V` is a weight matrix. If `V` is the identity matrix, we have a standard Euclidean distance, which gives equal weights to each variable when comparing two individuals. Note that there can be a lot of pairs for which this calculation must be done.
3. Match each treated case with the closest non-treated case and find the average difference in outcome to get the Average Treatment Effect on the Treated (`ATT`); or match every treated case with the closest non-treated case, *and vice versa*, to obtain the average treatment effect (`ATE`).
In practice, the most common choice of weight matrix `V` is the inverse of the variance-covariance matrix of `U^T` and `U^C`, which gives the Mahalanobis distance. This method is non-parametric and flexible but converges relatively slowly to the true measure. In our example, this measure shows that enrollment in the honors program raised retention by 0.294 (see [Table 3.6](#chapter3.xhtml#tbl3_6)).
Table 3.5 Classification of Observations into “Coarsened” Bins [⏎](#chapter3.xhtml#b3tbl3_5)
|  || Female || Male |
| --- | --- | --- |
| SAT || 960- || 1143- || 1326- || 960- || 1143- || 1326- |
| *Observations:* ||  ||  ||  ||  ||  ||  |
