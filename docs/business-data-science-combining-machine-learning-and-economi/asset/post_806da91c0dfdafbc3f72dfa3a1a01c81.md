
so that our inputs are able to explain about \( 1/2 \) and \( 1/4 \) of the variation in spam occurrence and OJ sales, respectively.

These \(R^2\) formulas might look familiar. From Equation 2.21, the linear regression deviance is just the sum of squares. This means that the residual (or fit) deviance is the common sum-squared-errors statistic (SSE) and the null deviance is the sum-squared-total (SST). Thus, *for linear regression only*,

$$R^{2}=1-\frac{\mathrm{SSE}}{\mathrm{SST}}, \tag{2.26}$$

as in the familiar \(R^2\) formula from an introductory statistics class. ^10 The advantage of re-expressing this \(R^2\) in terms of deviance is that it is now a more general fit statistic that applies to *almost any machine learning model*. You can think of deviance as a useful generalization of squared-errors for more flexible modeling.

There are two additional statistics on the `summary` output for `glm` that we need to discuss. Look again at the `glm summary`:

```text
> summary(ojreg)...
(Dispersion parameter for gaussian family taken to be 0.48)
Null deviance: 30079 on 28946 degrees of freedom
Residual deviance: 13975 on 28935 degrees of freedom
AIC: 61094
```

The *dispersion parameter* is a measure of variability around the fitted conditional means. Basically, all you need to know is that for the Gaussian family (i.e., for linear regression) the dispersion parameter is an estimate for \(\sigma_2\), your error variance. Hence, in the OJ regression, R has estimated the dispersion parameter by taking the variance of your fitted residuals:

$$\hat{\sigma}^{2}=\operatorname{var}\left(\boldsymbol{\epsilon}_{i}\right)=\operatorname{var}\left(\mathbf{y}_{i}-\mathbf{x}^{\prime} \hat{\boldsymbol{\beta}}\right)=0.48 . \tag{2.27}$$

In logistic regression, there is no corresponding “error term,” so R just outputs `Dispersion parameter for binomial family taken to be 1.` If you don’t see this, then you might have forgotten to put “`type=binomial`”.

The last term in the R output that needs to be defined is the “degrees of freedom.” This is a confusing term here because what R calls degrees of freedom in this output is more properly the “residual degrees of freedom,” defined as the number of observations minus the number of parameters. Throughout the rest of the book we will use degrees of freedom (df) to refer to the “model degrees of freedom”: the number of parameters in the model. Hence, R’s residual degrees of freedom refers to \(n - df\) in the notation of this book.

## REGRESSION UNCERTAINTY

We are interested not just in the point-estimates of the regression parameters but also in the *uncertainty* around these estimates. The usual way people quantify uncertainty about regression coefficients is to simply trust the standard errors output by the software. These “standard” standard errors are OK for many purposes, so long as your model is close to representing the true data-generating process. However, the standard errors reported by R (and virtually every other software package) are sensitive to misspecification. That is, they are constructed using a theory that is reliant on the specified regression model being true. For example, in the linear regression case, the usual standard errors will be wrong if there are heteroskedastic errors—in other words, if there is not a shared \(\sigma_2\) variance for all \(\varepsilon_i\). And in both linear and logistic regression, the standard error will be incorrect if there is any dependence between observations.

To get more robust standard errors, you need to make use of *nonparametric* methods that account for the possibility that the stated model is not quite a perfect fit. As covered in Chapter 1, one useful tool for this is the bootstrap, a strategy in which you resample the data (with replacement) and use the uncertainty across samples as an estimate of actual sampling variance. You can use a bootstrap to *nonparametrically* quantify the uncertainty associated with regression coefficients. Figure 2.9, for example, compared parametric and nonparametric uncertainty estimates for the coefficient on an indicator for broadband access when predicting online spending.

In the special case of OLS regression—i.e., linear regression—there are also a number of theoretical tools you can use to obtain robust standard errors. One of the most important and useful is the class of so-called *sandwich* variance estimators. Consider a multivariate representation of our linear regression distribution:

$$y \sim N(X\beta, \Sigma). \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad (2.28)$$

Here, \(\mathbf{x}_{i}\boldsymbol{\beta}\) is matrix-vector multiplication yielding a vector with elements \(\hat{\boldsymbol{y}}_{i} = \mathbf{x}_{i}^{\prime}\hat{\boldsymbol{\beta}}\), the conditional mean in linear regression.^11 In our usual homoskedastic linear regression setup, the conditional variance matrix is \(\Sigma = \sigma^2 I\) (i.e., all zeros except for \(\sigma^2\) along the diagonal), and every observation is assumed independent with the same error variance. Leaving \(\Sigma\) unspecified in Equation 2.28 allows for generalization of our usual regression setup to scenarios with different error structures.

The sandwich variance estimators are built around the result that, for the model in Equation 2.28, the sampling variance of the regression coefficients can be written as

$$\text{var}(\hat{\boldsymbol{\beta}}) = (\mathbf{X}^{\prime}\mathbf{X})^{-1}\mathbf{X}^{\prime}\Sigma\mathbf{X}(\mathbf{X}^{\prime}\mathbf{X})^{-1}.\quad (2.29)$$

This has the error variance, \(\Sigma\), “sandwiched” by the projection \(\mathbf{X}(\mathbf{X}^{\prime}\mathbf{X})^{-1}\). To intuit where this comes from, expand the usual OLS formula for estimated coefficients:

$$\hat{\boldsymbol{\beta}} = (\mathbf{X}^{\prime}\mathbf{X})^{-1}\mathbf{X}^{\prime}\mathbf{y} = (\mathbf{X}^{\prime}\mathbf{X})^{-1}\mathbf{X}^{\prime}(\underline{\mathbb{E}}[\mathbf{y}] + \boldsymbol{\epsilon}) = \boldsymbol{\beta} + (\mathbf{X}^{\prime}\mathbf{X})^{-1}\mathbf{X}^{\prime}\boldsymbol{\epsilon}.\quad (2.30)$$

Here, \(\mathbf{x}^{\prime}\hat{\boldsymbol{\beta}}\) is the vector of true coefficients plus an error term multiplied by this \(\mathbf{X}(\mathbf{X}^{\prime}\mathbf{X})^{-1}\) projection. Standard results then have that \(\text{var}(a^{\prime}\boldsymbol{\epsilon}) = a^{\prime}\Sigma\text{var}(\boldsymbol{\epsilon})a\) for fixed vector \(a\) and random \(\boldsymbol{\epsilon}\), yielding Equation 2.29.

Consider the usual homoskedastic model, where \(\Sigma = \sigma^2 I\). In that case, Equation 2.29 becomes \(\sigma^2(\mathbf{X}^{\prime}\mathbf{X})^{-1}(\mathbf{X}^{\prime}\mathbf{X})(\mathbf{X}^{\prime}\mathbf{X})^{-1} = \sigma_2(\mathbf{X}^{\prime}\mathbf{X})^{-1}\), the standard formula for OLS sampling variance (this is the formula R uses to get its standard errors). Moving to a more general model, you can use Equation 2.29 to quantify uncertainty in the common heteroskedastic scenario where each observation has a different error variance. That is, where \(\Sigma = \text{diag}(\sigma^2) = \text{diag}([\sigma_{21}, \sigma_{22}, \ldots, \sigma_{2n}])\) with a different diagonal entry for each observation. The heteroskedastic consistent^12 (HC) standard errors are constructed by replacing \(\Sigma\) in Equation 2.29 with an estimate that allows for such heteroskedasticity:

$$\widehat{\Sigma}_{HC} = \begin{bmatrix} e_1^2 & 0 & & \\\ 0 & e_2^2 & \\ & \ddots & 0 \\ & & 0 & e_n^2 \end{bmatrix} .\quad (2.31)$$

Here, $e_i = y_i - \boldsymbol{x}_i^\prime \boldsymbol{\hat{\beta}}$ are your fitted regression residuals. The HC procedure uses these squared residuals as an estimate of observation-specific variance $\sigma_{2i}$ to get standard errors that allow for such heteroskedasticity.

The `AER` package can be used to obtain HC standard errors with little effort. Consider a little example using data on air pollution in New York. The data include daily measurements on parts-per-billion (ppb) ozone from May 1 to September 30, 1973. For this example, we'll look at the effect of the wind (measured in miles per hour, or MPH) on ozone while controlling for temperature and solar radiation (amount of sunshine). Running a simple OLS regression, we find that an extra MPH of wind leads to a drop of three ppb ozone with a standard error of 0.65.

```
> data(airquality)
> fit <- glm(Ozone ~ ., data=airquality)
> summary(fit)$coef["Wind",]
                 Estimate     Std. Error     t value     Pr(>|t|)
Wind      -3.318444e+00  6.445095e-01 -5.148789e+00 1.231276e-06
```

The `vcovHC` function in `AER` just takes the fitted `glm` (or `lm`) object as input and returns an estimate of $\text{var}(\boldsymbol{\hat{\beta}})$ that is robust to heteroskedasticity:
