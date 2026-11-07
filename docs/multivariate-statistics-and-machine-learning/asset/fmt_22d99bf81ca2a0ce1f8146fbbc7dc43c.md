
A single `MANOVA` on the three response variables conducted simultaneously keeps the type I error rate fixed at whatever `α` is set to for the `MANOVA` (e.g., 0.05). This is a statistical benefit to performing a `MANOVA` over several `ANOVAs`; however, if substantively the `MANOVA` does not make sense, as discussed, a `MANOVA` model makes no sense to conduct for statistical reasons alone. The scientific or substantive rationale should dominate over the statistical here.

### 4.6.2 Extending the Univariate Model: Hotelling’s T²
The easiest and most direct way of extending the univariate model to the multivariate one is via the simple between-subjects `t`-test and generalization to Hotelling’s `T²`, which is the multivariate counterpart where we model more than a single continuous response variable. This essentially will generalize to more complex models, but we focus on the `t`-test because it emphasizes the core principles in going from a univariate to multivariate landscape.

Recall the univariate `t`-test discussed earlier in our review of essential statistics:212

$$\\begin{array}{l} {t = \\frac{E\\left( {\\overline{y}}\_{1} \\right) - E\\left( {\\overline{y}}\_{2} \\right) - \\delta\_{0}}{\\sqrt{\\frac{\\left( n\_{1} - 1 \\right)s\_{1}^{2} + \\left( n\_{2} - 1 \\right)s\_{2}^{2}}{n\_{1} - n\_{2} - 2}\\left( {\\frac{1}{n\_{1}} + \\frac{1}{n\_{2}}} \\right)}}} \\\\ {\\,\\,\\, = \\frac{\\mu\_{1} - \\mu\_{2} - \\delta\_{0}}{\\sqrt{\\frac{\\left( n\_{1} - 1 \\right)s\_{1}^{2} + \\left( n\_{2} - 1 \\right)s\_{2}^{2}}{n\_{1} - n\_{2} - 2}\\left( {\\frac{1}{n\_{1}} + \\frac{1}{n\_{2}}} \\right)}}} \\\\ \\end{array}$$

Consider now what happens when we square `t`,

$$t^{2} = \\frac{\\left( {\\overline{y}}\_{1} - {\\overline{y}}\_{2} \\right)^{2}}{\\frac{\\left( n\_{1} - 1 \\right)s\_{1}^{2} + \\left( n\_{2} - 1 \\right)s\_{2}^{2}}{n\_{1} - n\_{2} - 2}\\left( {\\frac{1}{n\_{1}} + \\frac{1}{n\_{2}}} \\right)}$$

Next, we express the denominator as an inverse so that there is no denominator:

$$t^{2} = \\left( {\\overline{y}}\_{1} - {\\overline{y}}\_{2} \\right)\\left\\lbrack {\\frac{\\left( n\_{1} - 1 \\right)s\_{1}^{2} + \\left( n\_{2} - 1 \\right)s\_{2}^{2}}{n\_{1} - n\_{2} - 2}\\left\\lbrack {\\frac{1}{n\_{1}} + \\frac{1}{n\_{2}}} \\right\\rbrack} \\right\\rbrack^{- 1}\\left( {\\overline{y}}\_{1} - {\\overline{y}}\_{2} \\right)$$

Finally, we end up with

$$T^{2} = \\frac{n\_{1}n\_{2}}{n\_{1} + n\_{2}}\\left( {\\overline{y}}\_{1} - {\\overline{y}}\_{2} \\right)'\\left( S^{- 1} \\right)\\left( {\\overline{y}}\_{1} - {\\overline{y}}\_{2} \\right)$$

(4.24)

For the one-sample mean vector, the corresponding `T²` is the following:

$$\\begin{array}{l} {T^{2} = \\left( \\overline{y} - \\mu\_{0} \\right)'\\left( {\\frac{1}{n}S} \\right)^{- 1}\\left( \\overline{y} - \\mu\_{0} \\right)} \\\\ {\\,\\,\\,\\,\\,\\,\\, = n\\left( \\overline{y} - \\mu\_{0} \\right)'S^{- 1}\\left( \\overline{y} - \\mu\_{0} \\right)} \\\\ \\end{array}$$

(4.25)

`T²` is distributed as $\\frac{\\left( n - 1 \\right)p}{\\left( n - p \\right)}F\_{p,n - p}$, where `p` and `n - p` are degrees of freedom, where `p` is the number of variables and `n` is sample size. For details on likelihood ratio tests in relation to `T²`, see Johnson and Wichern ([2007](#ref.xhtml#re_CIT000173), pp. 217–218). Confidence regions can also be computed for `T²` and multivariate populations (see Johnson & Wicher, [2007](#ref.xhtml#re_CIT000173), pp. 220–221).

### 4.6.3 Multivariate Test Statistics
In the univariate `ANOVA` setting, there is only a single `F`-test to perform. In the multivariate setting, because of the alternative way covariances of response variables may be structured within groups on the independent variable(s), multiple multivariate tests have been developed and are available in virtually all software. These include `Wilk’s lambda`, `Pillai’s trace`, `Roy’s largest root`, and the `Lawley-Hotelling’s trace`. We provide only a cursory “glimpse” into the variety of multivariate tests. For a full development of how these tests come about, see [Johnson and Wichern (2007)](#ref.xhtml#re_CIT000173).213

Wilk’s lambda, `Λ`, is given by

$$\\Lambda = \\frac{\\left| E \\right|}{\\left| H + E \\right|} = \\frac{\\left| E \\right|}{\\left| T \\right|}$$

(4.26)

where under the null hypothesis,

$$\\Lambda = \\frac{\\left| E \\right|}{\\left| 0 + E \\right|} = \\frac{\\left| E \\right|}{\\left| E \\right|} = 1.0$$

and where `H` is the “hypothesis” matrix and `E` the “error” matrix. Note that Wilk’s is an inverse criterion, meaning that if there is no effect, we would expect `Λ` to equal 1.0. This is unlike the `F`-ratio in univariate `ANOVA`, where larger F’s are preferred over smaller.

On the opposite extreme, if `H` accounts for all of the variation, then,

$$\\Lambda = \\frac{\\left| 0 \\right|}{\\left| H + 0 \\right|} = \\frac{\\left| 0 \\right|}{\\left| H \\right|} = 0$$

Wilk’s lambda can also be expressed in terms of eigenvalues of `E^(-1)H`:

$$\\Lambda = {\\prod\\limits\_{i = 1}^{s}\\frac{1}{1 + \\lambda\_{i}}}$$

(4.27)

where `λ[i]` are the eigenvalues extracted from the analysis.

Pillai’s trace is defined as

$$V^{(s)} = {tr}\\left\\lbrack {\\left( E + H \\right)^{- 1}H} \\right\\rbrack = {\\sum\\limits\_{i = 1}^{s}\\frac{\\lambda\_{i}}{1 + \\lambda\_{i}}}$$

(4.28)

Note that Pillai’s uses all eigenvalues (often called “roots”), `λ[i]`. If we use only the largest of these roots, this gives rise to `Roy’s largest root`. That is, Roy’s largest root is simply the largest eigenvalue extracted and hence represents only the largest dimension underlying the data. Roy’s largest root is especially useful if one dimension dominates all others, which translates into one eigenvalue being much larger than the others. When the distribution of eigenvalues is more spread out, Pillai’s is more appropriate since presumably more than a single dimension is of interest.

Lastly, Lawley-Hotelling’s trace is simply a sum of eigenvalues and is thus given by

$$U^{(s)} = \\text{tr}\\left( E^{- 1}H \\right) = {\\sum\\limits\_{i = 1}^{s}\\lambda\_{i}}$$

(4.29)

### 4.6.4 Evaluating Equality of Covariance Matrices: The Box-M Test
Recall that in univariate `ANOVA`, we were required to evaluate the assumption that all variances were equal. In the multivariate counterpart, we not only have variances to deal with; we also have covariances. Hence, the assumption now includes that all covariances across levels (or cells) of the independent variable are equal, that is,214

`H[0]`: `Σ[1]` = `Σ[2]` = `Σ[3]`... = `Σ[p]`

(4.30)

where `Σ[p]` are the `p` covariance matrices for each population under levels of the independent variable.

There are different approaches to evaluating this assumption. One is simply a crude (yet still useful) visual approach to learn whether the covariance matrices are relatively similar to one another to deem their population counterparts at least approximately equal and proceed with the `MANOVA`. The `Box-M test` is another approach that evaluates this assumption and is available in R in the `biotools` package ([da Silva, 2021](#ref.xhtml#re_CIT000075)) under the `boxM` test, which can be easily demonstrated directly from the package on the iris data:

```
> library(biotools)
> data(iris)
> boxM(iris[, -5], iris[, 5])
Box M-test for Homogeneity of Covariance Matrices
data: iris[, -5]
Chi-Sq (approx.) = 140.94, df = 20, p-value < 2.2e-16
```
