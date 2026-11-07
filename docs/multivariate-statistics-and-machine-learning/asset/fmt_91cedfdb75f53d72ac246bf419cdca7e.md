
## Multivariate reduced-rank regression

Multivariate reduced-rank regression ([Izenman, 1975](#ref.xhtml#re_CIT000166)) is a very general framework for the multivariate regression model and we mention it here only for pedagogical inclusion into the general regression framework. The classic multivariate linear regression model can be stated in its most general way as

`Y` = `μ` + `C` `X` + `ε`

(5.32)

where `C` is a matrix of regression coefficients or parameters on which there exists a set of linear constraints. These linear constraints in the case of reduced rank for `C` imply that `C` = `A` `B`, where both `A` and `B` are nonunique full-rank matrices ([Izenman, 2008](#ref.xhtml#re_CIT000167), p. 177), such that we can rewrite the classical multivariate model as

$$\\begin{array}{l} {Y = \\mu + {CX} + \\varepsilon} \\\\ {\\,\\,\\,\\,\\, = \\mu + \\left( {AB} \\right)X + \\varepsilon} \\\\ \\end{array}$$

(5.33)

where in (5.33), we have simply substitued `A` `B` for `C`. That is, the reduced-rank multivariate model generalizes the classical multivariate model by, as summarized by [Izenman (2008)](#ref.xhtml#re_CIT000167), relaxing the implicit constraint on the rank of `C`, which by consequence, allows for dimension reduction. The theme is already familiar by now; a matrix of less than full rank may very well have underlying 260dimensionality “disguised” within it. By estimating `A` and `B`, we effectively “treat” the reduced-rank condition of `C`. For a proof of why `A` and `B` are nonunique, see Izenman ([2008](#ref.xhtml#re_CIT000167), p. 177).

Several statistical models, including `principal components analysis`, `exploratory factor analysis`, `canonical correlation`, `discriminant analysis`, and even `neural networks`, can be conceptualized as special cases of the reduced-rank multivariate model. What is more, the Gauss-Markov theorem for regression discussed earlier in the book generalizes to the multivariate reduced-rank counterpart. Profile analysis and time series can also be conceptualized within the reduced-rank multivariate model.

## 5.15 Canonical Correlation

The canonical correlation is the bivariate correlation between sets of variables. It is, like Pearson `r`, a linear correlation. It is the linear correlation between linear combinations of variables. That is, for linear combinations `l`[1] and `l`[2], the correlation between them is given by:

$$r\_{l\_{1},l\_{2}} = \\frac{{cov}\_{l\_{1},l\_{2}}}{\\sqrt{s\_{l\_{1}}^{2}s\_{l2}^{2}}}$$

(5.34)

where `s`[`l`[1]]² and `s`[`l`2]² are variances of the respective linear combinations ([Denis, 2021a](#ref.xhtml#re_CIT000087)) and `cov`[`l`[1], `l`[2]] is the covariance between linear combinations `l`[1] and `l`[2]. The nonzero squared population canonical correlations are the nonzero eigenvalues `λ`[`i`] of the following ([Bilodeau and Brenner, 1999](#ref.xhtml#re_CIT000030), p. 177; [Rencher and Christensen, 2012](#ref.xhtml#re_CIT000295), p. 387):

`Σ`[`y` `y`]`^(−1)` `Σ`[`y` `x`]() `Σ`[`x` `x`]`^(−1)` `Σ`[`x` `y`]() 

As a result of the eigenvalues providing the squared canonical correlations, the unsquared canonical correlations are thus equal to the square root of the eigenvalues, that is, $\\sqrt{\\lambda\_{i}}$.

How are the squared canonical correlations found? There are a few ways of obtaining them, but perhaps the easiest way is through an eigen analysis of `Σ`[`y` `y`]`^(−1)` `Σ`[`y` `x`]() `Σ`[`x` `x`]`^(−1)` `Σ`[`x` `y`]() , where such represents the matrix being analyzed in `A` in the classic form of the eigen equality:

`A` `x` = `λ` `x`

Recall that to find `λ` we set |`A`−`λ` `I`| = 0, where now instead of simply a matrix `A`,

`A` = `Σ`[`y` `y`]`^(−1)` `Σ`[`y` `x`]() `Σ`[`x` `x`]`^(−1)` `Σ`[`x` `y`]() 

and so we have

|`A`−`λ` `I`| = 0 → |`Σ`[`y` `y`]`^(−1)` `Σ`[`y` `x`]() `Σ`[`x` `x`]`^(−1)` `Σ`[`x` `y`]() − `λ` `I`| = 0

(5.35)

and hence since |`A`−`λ` `I`|`x` = 0, where `x` is an eigenvector associated with `λ`, the respective eigenvectors `a` and `b` of `Σ`[`y` `y`]`^(−1)` `Σ`[`y` `x`]() `Σ`[`x` `x`]`^(−1)` `Σ`[`x` `y`]() are found by261

(`Σ`[`y` `y`]`^(−1)` `Σ`[`y` `x`]() `Σ`[`x` `x`]`^(−1)` `Σ`[`x` `y`]() − `λ` `I`) `a` = 0

(5.36)

and

(`Σ`[`y` `y`]`^(−1)` `Σ`[`y` `x`]() `Σ`[`x` `x`]`^(−1)` `Σ`[`x` `y`]() − `λ` `I`) `b` = 0

(5.37)

That is, the first linear combination is now `l`[1] = `a`′ `x` and the second `l`[2] = `b`′ `y`. Corresponding canonical variates for each dimension are uncorrelated, and each subsequent canonical dimension extracted is uncorrelated to previous dimensions. Izenman ([2008](#ref.xhtml#re_CIT000167), p. 216) summarizes canonical correlation:

> The CVA technique ensures that every bit of correlation is wrung out of the original X and Y variables and deposited in an orderly fashion into pairs of new variables … which have a special correlation structure. If the notion of correlation is regarded as the primary determinant of information in the system of variables, then CVA is a major tool for reducing the dimensionality of the original two sets of variables.

Not surprisingly, canonical correlation can be interpreted as a special case of the aforementioned reduced-rank regression ([Izenman, 2008](#ref.xhtml#re_CIT000167)). Variations of canonical correlation include `deep variational canonical correlation` (Wang et al., [2017](#ref.xhtml#re_CIT000380)) that extends and generalizes linear canonical correlation to nonlinear models within a deep neural network parameterization. `Probabilistic canonical correlation` is discussed by [Bach and Jordan (2006)](#ref.xhtml#re_CIT000017). `Tensor canonical correlation` has also been proposed, where each observation in data consists of multidimensional arrays (tensors) (Min et al., [2020](#ref.xhtml#re_CIT000252)). Relationships between multivariate reduced rank, PCA, and CVA can be found in [Izenman (1975)](#ref.xhtml#re_CIT000166).

### 5.15.1 Canonical Correlation in R

The package `CCA` in R ([González & Déjean, 2023](#ref.xhtml#re_CIT000130)) can be used for canonical correlation as well as a version of regularized canonical correlation. The package also allows for numerous graphical visualizations of canonical correlation. Below is an example adapted from the package’s documentation on the `nutrimouse` data, where gene data is correlated to lipids on a group of mice:

```
> library(CCA)
> data(nutrimouse)
> X = as.matrix(nutrimouse$gene[,1:3])
> Y = as.matrix(nutrimouse$lipid[, 1:3])
```

Above, we designate variables X and Y, where X is gene and Y is lipid. The X variable is defined by variables 1 through 3 of the gene dataframe housed in nutrimouse. According to the package details, the gene dataframe contains a 40 × 120 matrix of numerical variables, and thus we are only selecting the first three (1:3). Likewise, we are only selecting variables 1:3 of the dataframe of the 40 rows of lipid (nrow(nutrimouse$lipid)) that are in the data. Given that we have three variables on both sides of the equation, we should get three canonical correlations in our output as the number of canonical correlations possible is equal to the lesser of the number of variables on either side of the equation:262

```
> head(X)
```

|  || X36b4 || ACAT1 || ACAT2 |
| --- | --- | --- | --- |
| 1 || \-0.42 || \-0.65 || \-0.84 |
| --- | --- | --- | --- |
| 2 || \-0.44 || \-0.68 || \-0.91 |
| 3 || \-0.48 || \-0.74 || \-1.10 |
| 4 || \-0.45 || \-0.69 || \-0.65 |
| 5 || \-0.42 || \-0.71 || \-0.54 |

```
> head(Y)
```

|  || C14.0 || C16.0 || C18.0 |
| --- | --- | --- | --- |
| 1 || 0.34 || 26.45 || 10.22 |
| --- | --- | --- | --- |
| 2 || 0.38 || 24.04 || 9.93 |
| 3 || 0.36 || 23.70 || 8.96 |
| 4 || 0.22 || 25.48 || 8.14 |
| 5 || 0.37 || 24.80 || 9.63 |

```
> res.cc = cc(X, Y)
```

The output from res.cc will provide a host of canonical correlation output (far too long to list here). It will include such output as `x` and `y` coefficients as well as `x` and `y` canonical scores. Most relevant will be the canonical correlations which we can get from
