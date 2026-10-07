
## 526 Research Design and Statistical Analysis

One way of assessing the influence of the $j$th case on the regression equation is to compare the results of the analysis when the $j$th case is present with the results when it is deleted. Therefore, the difference in the fitted (i.e., predicted value, $\hat{Y}_j$) when case $j$ is included and when it is excluded from the regression equation, $DFFIT_j = \hat{Y}_j - \hat{Y}_{j(-j)}$, can be considered an index of the effect of the $j$th case.

Both $DFFIT$ and its standardized value,

```
$DFFITS_j = \frac{\hat{Y}_j - \hat{Y}_{j(-j)}}{s_{Y,X}\sqrt{h_{jj}}}$$ (19.25)
```

where $s^{(j(-j))}$ is as defined in Equation 19.22, which can be easily calculated for each data point (see Section 19.8.3). A few criteria have been suggested for a case to be considered influential.

We suggest a general cutoff of 2 and a size-adjusted cutoff of $2\sqrt{\frac{(p+1)}{N}}$ for $DFFITS$, where $p$ is the number of predictor variables.

Cook (1977) proposed a measure that takes into account the effect of deleting case $j$ on all N residuals. The measure, known as *Cook’s distance*, can be expressed as

```
$CD_j = \frac{\sum(\hat{Y}_i - \hat{Y}_{i(-j)})^2}{(p+1)s_{Y,X}^2}$ (19.26)
```

where $p$ is 1 for bivariate regression and, $p$ is the number of predictor variables in the regression equation. Cook and Weisberg (1982) suggest that Cook’s distance should be compared to an $F$ distribution with $p+1$ and $N-p-1$ $df$. A value of Cook’s distance is considered large if it equals $5$; or in $R$, $qf(5, p+1, N-p-1)$ returns the critical $F$. For regressions with more than five or six predictor variables, this leads to a criterion Cook’s distance value of about 1; however, for bivariate regression with a sample size of about 200, as in the current example, the criterion would be about 0.70 ($qf(.5, 2, 209) = .695$).

Another useful expression for Cook’s distance

```
$CD_j = \frac{t_j^2}{p+1}\frac{h_{jj}}{1-h_{jj}}}$ (19.27)
```

where $t_j$ is the internally Studentized residual of Equation 19.18. This expression makes it clearer that the influence of a data point depends on its residual – captured by $t_j^2$ – and the extent to which it is an outlier – captured by $h_{jj}$.

The final measures we consider here reflect differences in the regression coefficients $b_0$ and $b_j$ that result when case $j$ is excluded from the analysis. The change in the value of the $k$th regression coefficient when the $j$th data point is deleted is given by

```
$DFBETAS_{jk} = \frac{DFBETA_{jk}}{SE^{(j(-j))}}(b_k)$ (19.28)
```

## More About Bivariate Regression 527

where $k = 0$ for the $Y$ intercept and $k = 1$ for the slope. The standardized change is given by

```
$DFBETAS_{jk} = \frac{DFBETAS_{jk}}{SE^{(j)}(b_k)} \quad (19.29)$
```

the denominator is simply the usual standard error for $b_k$, except that $s^{(i-j)}_{YX}$ replaces $s_{XY}$. The $DFBETAS$ measure has a suggested size-related cutoff of $2/\sqrt{N}$.

Cook's distance is extremely useful for identifying influential data points that influence the fit of the regression, and the $DFBETAS$ measure is of particular interest if we are concerned with the stability of the regression coefficients. Given that statistical software can readily provide these measures of influential data points, we can consider all of them.

### 19.8.3 Integrating Analyses of Outlying Points and Influential Points

We have discussed several measures designed to help us detect data points that may have been recorded erroneously or may have a disproportionate influence on our regression statistics, or how are we to use this information? There is no single answer; rather, we must evaluate each case on our own terms. As an example, let's look back at our regression of TC for women in Table 19.5, where case 311 seems to deserve attention. It has not only an Extended Residual of $4.068$, but also a $DFITS$ of $.487$, which is greater than the criterion of $.195$. It also has $DFBETAS$ values of $.452$ and $-397$ for $b_h$ and $b_j$, respectively, which exceed the criterion of $.137$. Cook's distance for case 368 is close to the size of the largest value. When we examine case 311, we find that the data comes from a participant who is relatively young (23 years old), but who...

### 19.8.4 Using Software to Locate Outliers and Influential Points

In SPSS, we begin the regression as described in Section 17.6, then click on the Save button. Measures of influence are available by ticking the Betas and Standardized Betas, as well as Dfits and Standardized Dfits. Cook's distance is an option in the Distance section of the same window.

In R, with regression results stored in reg_out, the function influence.measures(reg_out) in the stats package will return dfbetas (standardized dbeta values, for intercept and for slope), dfits (standardized differences in fit), Cook's distance, and leverage (called hat). Each of these measures is also available as its own function (dfbetas, dfits.distance, hatvalues) and takes as input the output of regression analysis (e.g., reg_out).
