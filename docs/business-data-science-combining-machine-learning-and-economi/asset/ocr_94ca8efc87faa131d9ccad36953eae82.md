so that our inputs are able to explain about \( 1/2 \) and \( 1/4 \) of the variation in spam occurrence and OJ sales, respectively.

These $R_2$ formulas might look familiar. From Equation 2.21, the linear regression deviance is just the sum of squares. This means that the residual (or fit) deviance is the common sum-squared-errors statistic (SSE) and the null deviance is the sum-squared-total (SST). Thus, *for linear regression only*,

```
$R^{2}=1-\frac{\mathrm{SSE}}{\mathrm{SST}}, \tag{2.26}$
```

as in the familiar $R_{2}$ formula from an introductory statistics class. $^{10}$ The advantage of re-expressing this $R_{2}$ in terms of deviance is that it is now a more general fit statistic that applies to *almost any machine learning model*. You can think of deviance as a useful generalization of squared-errors for more flexible modeling.

There are two additional statistics on the `summary` output for `glm` that we need to discuss. Look again at the `glm summary`:

```
```text
> summary(ojreg)... 
(Dispersion parameter for gaussian family taken to be 0.48)
Null deviance: 30079 on 28946 degrees of freedom
Residual deviance: 13975 on 28935 degrees of freedom
AIC: 61094
```
```

The *dispersion parameter* is a measure of variability around the fitted conditional means. Basically, all you need to know is that for the Gaussian family (i.e., for linear regression) the dispersion parameter is an estimate for $\sigma_{2}$, your error variance. Hence, in the OJ regression, R has estimated the dispersion parameter by taking the variance of your fitted residuals:

```
$\hat{\sigma}^{2}=\operatorname{var}\left(\boldsymbol{\epsilon}_{i}\right)=\operatorname{var}\left(\mathbf{y}_{i}-\mathbf{x}^{\prime} \hat{\boldsymbol{\beta}}\right)=0.48 . \tag{2.27}$
```

In logistic regression, there is no corresponding “error term,” so R just outputs `Dispersion parameter for binomial family taken to be 1.` If you don’t see this, then you might have forgotten to put “`type=binomial`”.

The last term in the R output that needs to be defined is the “degrees of freedom.” This is a confusing term here because what R calls degrees of freedom in this output is more properly the “residual degrees of freedom,”