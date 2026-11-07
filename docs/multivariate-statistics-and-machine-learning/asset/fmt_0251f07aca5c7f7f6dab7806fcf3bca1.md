
The simplicity of this equation [i.e., `Σ` = `Σ`(`θ`)] is only surpassed by its generality. It provides a unified way of including many of the most widely used statistical techniques in the social sciences. Regression analysis, simultaneous equation systems, confirmatory factor analysis, canonical correlations, panel data analysis, ANOVA, analysis of covariance, and multiple linear indicator models are special cases of `Σ` = `Σ`(`θ`).

The value of `Σ` is unknown, and hence we estimate `Σ` via `S`, the sample covariance matrix. We desire the distance between `S` and `S`(`θ`) to be as small as possible, that is, to be minimized, where `S`(`θ`) is the sample covariance matrix implied by the estimated model parameters. Discrepancy functions are a wide class of functions from which can be selected a specific function to minimize distance between `S` and `S`(`θ`). One such discrepancy function is that of the familiar ordinary least-squares that minimizes the distance between observed and fitted values of `y`. Other types of models feature the minimizing or maximizing of other discrepancy functions. In covariance modeling using maximum likelihood (ML), for instance, we wish to minimize the following fitting function `F[ML]` ([Bollen, 1989](#ref.xhtml#re_CIT000037), p. 107):487

`F[ML]` = log|`Σθ`| + tr(`S` `Σ`^(−1)(`θ`)) − log|`S`| − (`p`+`q`)

(13.4)

When `S` = `S`(`θ`), `F[ML]` = 0. That is, as (`S`−`S`(`θ`))→0, `F[ML]`→0, and perfect model fit is achieved, since the difference between the sample covariance matrix `S` and that implied by the model, `S`(`θ`), is equal to 0. It turns out that (`n`−1)`F[ML]` ∼ `χ²` (where `n` is sample size), which can be used for evaluating the following global null hypothesis,

`H[0]`: `Σ` = `Σ`(`θ`)

(13.5)

where the above null hypothesis `H[0]` reads that the population covariance matrix `Σ` is equal to that population covariance matrix implied by the specified parameters, that is, `Σ`(`θ`). The above null is evaluated against the alternative hypothesis `H[1]`,

`H[1]`: `Σ` ≠ `Σ`(`θ`)

(13.6)

which reads that the population covariance matrix `Σ` is unequal to that implied by the model parameters in `θ`. Equivalently, under the null hypothesis, `Σ`−`Σ`(`θ`) = 0, and hence if the model fits perfectly, the expectation for `χ²` is 0. The extent to which the model does not fit is the extent to which `Σ`−`Σ`(`θ`) ≠ 0. If you look at the null hypothesis closely, you will see that contrary to traditional null hypothesis testing in which we wish to reject the null, in SEM, we wish to actually not reject the null hypothesis. That is, a null that is supported by the data is a favorable outcome in SEM, which goes against how traditional null hypothesis testing is classically interpreted. This fact is important, since if you reject the null in SEM, it suggests your estimated model is not consistent with the covariance matrix, meaning that it does not reproduce it well, which further implies the fit between the covariance matrix based on the data is not in line with the covariance matrix implied by the model.

### 13.6.2 Evaluating Model Fit

As with most supervised learning models, we desire a measure to assess or evaluate how well the model fits the empirical data. In ordinary least-squares, that measure of model fit is typically `R²`, `R[adj]²` or some other model selection measures such as `AIC` or `BIC`. In SEM, we also require measures of model fit to assess the extent to which our designated model parameters reproduce `S`, the sample covariance matrix. As in regression and other models, there are numerous ways of assessing fit in structural equation models. Measures of model fit in SEM are typically divided into two broad categories, those assessing overall or absolute model fit, and those evaluating incremental fit, sometimes called relative fit measures. Overall measures of model fit assess the model in its entirety without reference to a competing model, whereas incremental or relative measures of fit evaluate a model relative to some reference or competing model, usually a null or baseline model, to evaluate how well the hypothesized model performs relative to the baseline model.

Why not just use `χ²` as a measure of model fit? Recall that (`n`−1)`F[ML]` ∼ `χ²` and the expectation for `χ²` under `H[0]` is equal to 0 under a perfectly fitting model. Hence, it might at first glance seem reasonable to simply use `χ²` as a measure of model fit such that the extent to which `χ²`→0 is the extent to which the model is increasingly well-fitting and the extent to which `χ²` > 0 is the extent to which the model fits poorly. That is, the extent to which `χ²` is statistically significant might be taken as a measure of increasingly poor model fit. While this approach at first glance sounds reasonable, it is very problematic, and overall, `χ²` alone makes for a poor measure of model fit in SEM. Recall that as `n` increases, achieving `p` < .05 (or some other arbitrary significance level) for `χ²` is assured other than under the restriction that `χ²` = 0. So long as `χ²` > 0 is true, and it most often will be, statistical significance of `χ²` and more importantly, lack thereof, should not be in any real way interpreted as a measure of “effect,” especially for increasing `n`.

Of course, this idea is not new and was discussed earlier in the book; p-values are not effect sizes. That is not to say a user should not utilize `χ²` as an initial assessment of fit, only that `χ²` alone will usually not tell the user what they really want to know, which is a measure of effect that is independent of the influence of sample size. In the measures that follow, both overall measures and incremental fit indices are measures of effect size (or of “fit” more generally) that are not influenced by the magnitude of `n` in the way that `χ²` is to a large extent a function of sample size.

### 13.6.3 Overall (Absolute) Measures

Some of the more common measures of overall fit include root mean square residual (`RMR`), its standardized counterpart, the standardized root mean square residual (`SRMR`), and the root mean square of approximation (`RMSEA`). We now briefly survey each of these.

The root mean square residual (`RMR`) is given by

$${RMR} = \\left\\lbrack {2{\\sum\\limits\_{i = 1}^{q}{\\sum\\limits\_{j = 1}^{i}\\frac{\\left( s\_{ij} - s\_{{}\_{ij}}^{'} \\right)^{2}}{q\\left( q + 1 \\right)}}}} \\right\\rbrack^{1/2}$$

(13.7)

where `s[i j]` is an element of the observed covariance matrix `S`, `s[i j]'` is an element of the model-implied covariance matrix `S`(`θ`), and `q` is the number of observed variables in the model. Essentially, `RMR` assesses the extent to which elements of the observed covariance matrix differ from those of the implied by taking their (squared) difference, (`s[i j]`−`s[i j]'`)². The extent to which that difference is larger than not is the extent to which `RMR` will also be large, which would be increasingly indicative of a poorly fitting model. The best-fitting model would have `s[i j]` − `s[i j]'` = 0, which would then imply an `RMR` of 0. Note that all else in the formulation are simply constants, as well as squaring and taking the square root. That is, the most meaningful part of the formula is contained in (`s[i j]`−`s[i j]'`).

One drawback of `RMR` is that `s[i j]` is computed on raw scores, and hence analogous to how the size of a covariance can be misleading due to the extent of variance in one or both variables, `RMR` can likewise be small or large, not solely due to the extent of effect present, but instead due to magnitudes of variance in the variables. Solving the scale issue with `RMR` is the standardized root mean square residual (`SRMR`) which first standardizes residuals `s[i j]` − `s[i j]'` via the product of standard deviations, `s[i]` `s[j]`,

(`s[i j]`−`s[i j]'`) / `s[i]` `s[j]`

yielding
