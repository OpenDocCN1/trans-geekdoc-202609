# 526 Research Design and Statistical Analysis

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