
Indeed, beyond regularization methods, the decision of whether or not to standardize must be made in many other methods as well (e.g., principal components analysis). Offering a “cookbook” recommendation to “always standardize” is not good statistical teaching, especially without carefully considering whether or not it is desirable that the original variances of the measurement units play a role in the ensuing statistical analyses. Once more with the Bayesian prior concept, sometimes we want those variances to impact the solution, whereas other times we do not. The key point is that neither solution is definitively right or wrong, and the decision to keep measurements in their original units or transform them to standardized units needs to be made on a case-by-case basis.

### 6.2.6 Ridge Regression in R

Ridge regression in R can be performed using the `lmridge` package ([Imdad & Aslam, 2018](#ref.xhtml#re_CIT000165)). For an excellent summary of this package, see Ullah et al. ([2018](#ref.xhtml#re_CIT000366)). The package is *outstanding* in its coverage of all things “ridge.” In the following, we fit a ridge regression to the `Hald` data. The data relate to an engineering application that was concerned with the effect of the composition of cement on heat evolved during hardening. What is most relevant about this data for our purposes is that the features are relatively highly correlated and hence well-suited for ridge regression. Consult the package for further details on this specific example.

Let’s first briefly survey the `Hald` data:
```
> library(lmridge)
> data(Hald)
> head(Hald)
```

|  || Y || X1 || X2 || X3 || X4 |
| --- | --- | --- | --- | --- | --- |
| \[1,\] || 78.5 || 7 || 26 || 6 || 60 |
| --- | --- | --- | --- | --- | --- |
| \[2,\] || 74.3 || 1 || 29 || 15 || 52 |
| \[3,\] || 104.3 || 11 || 56 || 8 || 20 |
| \[4,\] || 87.6 || 11 || 31 || 8 || 47 |
| \[5,\] || 95.9 || 7 || 52 || 6 || 33 |
| \[6,\] || 109.2 || 11 || 55 || 9 || 22 |

274 
We will fit a model where `y` is hypothesized as a function of predictors `X1` through `X4`:
```
> mod <- lmridge(y ~ X1 + X2 + X3 + X4, data = as.data.frame(Hald),
+ scaling = “sc”, K = seq(0, 1, 0.001))
```
The “sc” for `scaling` scales the predictors to correlation form. The option `scaling = "centered"` would have simply centered all predictors. The option `K` designates the ridge biasing *tuning* parameter, where in the above we chose options 0, 1, 0.001, which means R will compute coefficients starting at 0 up to 1, at steps or increments of 0.001.

We now call the fitted model which shows parameter estimates for values of `K` 0–0.004. These are the *raw* or “de-scaled” weights fitted by the ridge regression:
```
> mod
Call:
lmridge.default(formula = y ~ X1 + X2 + X3 + X4, data = as.data.frame(Hald),
K = seq(0, 1, 0.001), scaling = “sc”)
```

|  || Intercept || X1 || X2 || X3 || X4 |
| --- | --- | --- | --- | --- | --- |
| K=0 || 62.40537 || 1.55110 || 0.51017 || 0.10191 || \-0.14406 |
| --- | --- | --- | --- | --- | --- |
| K=0.001 || 71.32028 || 1.45679 || 0.41874 || 0.00650 || \-0.23358 |
| K=0.002 || 75.32580 || 1.41283 || 0.37795 || \-0.03741 || \-0.27346 |
| K=0.003 || 77.60713 || 1.38657 || 0.35493 || \-0.06322 || \-0.29591 |
| K=0.004 || 79.08396 || 1.36858 || 0.34021 || \-0.08058 || \-0.31023 |

The following will yield *scaled* coefficients:275
```
> mod$coef
```

|  || K=0 || K=0.001 || K=0.002 || K=0.003 || K=0.004 || K=0.005 |
| --- | --- | --- | --- | --- | --- | --- |
| X1 || 31.607147 || 29.6853546 || 28.7895380 || 28.254405 || 27.887857 || 27.613799 |
| --- | --- | --- | --- | --- | --- | --- |
| X2 || 27.500315 || 22.5718760 || 20.3730129 || 19.132537 || 18.339056 || 17.790004 |
| X3 || 2.261167 || 0.1442803 || \-0.8300639 || \-1.402819 || \-1.787926 || \-2.070135 |
| X4 || \-8.353056 || \-13.5438292 || \-15.8561502 || \-17.157745 || \-17.987880 || \-18.560165 |

We can obtain predicted values as follows:
```
> predict(mod)
```

|  || K=0 || K=0.01 || K=0.02 || K=0.03 || K=0.04 || K=0.05 || K=0.06 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 78.49535 || 78.49063 || 78.65269 || 78.81280 || 78.96609 || 79.11210 || 79.25112 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2 || 72.78893 || 73.10007 || 73.26551 || 73.41722 || 73.56132 || 73.69948 || 73.83256 |
| 3 || 105.97107 || 106.39463 || 106.38297 || 106.34900 || 106.30959 || 106.26726 || 106.22416 |
| 4 || 89.32720 || 89.48225 || 89.48739 || 89.48752 || 89.48842 || 89.49055 || 89.49423 |
| 5 || 95.64939 || 95.70913 || 95.84146 || 95.96400 || 96.07594 || 96.17731 || 96.26972 |
| 6 || 105.27469 || 105.27361 || 105.21815 || 105.16162 || 105.10662 || 105.05234 || 104.99962 |
| 7 || 104.14885 || 104.10473 || 104.09527 || 104.08482 || 104.07302 || 104.05858 || 104.04282 |

Many other statistics are available in the ridge package for the fitted model. For instance, we can obtain a plot, the so-called *ridge trace plot* of the fitted model as given in [Figure 6.3](#c6.xhtml#f6.3).

![Figure 6.3 Ridge trace plot featuring ridge coefficients as a function of the biasing parameter K.Return to text.⏎](images/fig6.3.jpg)

*Figure 6.3* Ridge trace plot featuring ridge coefficients as a function of the biasing parameter K.[Return to text.⏎](#c6.xhtml#re_f6.3)
```
> plot(mod)
```
The plot in [Figure 6.3](#c6.xhtml#f6.3) shows the value of ridge coefficients for various values of `K`. We can see that the minimum MSE occurs at `K = 0.012`. We can also generate a summary of the model via `summary(mod)`, which will produce parameter estimates, standard errors, and other model information.

Cross-validation plots can also be obtained using `cv.plot()`, and AIC and BIC values can be obtained as in [Figure 6.4](#c6.xhtml#f6.4), showing where AIC and BIC values are at their minimums as a function of degrees of freedom (DF):

![Figure 6.4 AIC and BIC as a function of degrees of freedom.Return to text.⏎](images/fig6.4.jpg)

*Figure 6.4* AIC and BIC as a function of degrees of freedom.[Return to text.⏎](#c6.xhtml#re_f6.4)
```
> info.plot(mod)
```
276 
We can also get vectors of AIC and BIC values by `K` values via the following (output not shown): `infocr(mod)[, 1]`, `infocr(mod)[, 2]`. Our survey of the capabilities of `lmridge` only scratches the surface of what the package is capable of generating. See the package’s details for a wealth of further options.

## 6.3 Lasso Regression

The ridge regression just featured is only one way that we may shrink parameter estimates. A second popular and modern way is through lasso regression. In lasso regression, the idea of minimizing *E*(*y*[0]−*f̂*(*x*[0]))² over and above what OLS regression would accomplish remains through imposing a penalty term, but this time, instead of the penalty $\\lambda{\\sum\\limits\_{j = 1}^{p}\\beta\_{j}^{2}}$ as in ridge, the penalty term is $\\left. \\lambda\\left. \\sum\\limits\_{j = 1}^{p} \\right|\\,\\beta\_{j} \\right|$so that we are now minimizing the following:

$$\\left. RSS = {\\sum\\limits\_{i = 1}^{n}\\left( {y\_{i} - \\beta\_{0} - {\\sum\\limits\_{j = 1}^{p}{\\beta\_{j}x\_{ij}}}} \\right)^{2}} + \\lambda{\\sum\\limits\_{j = 1}^{p}\\left| \\beta\_{j} \\right.} \\right|$$  
(6.9)
