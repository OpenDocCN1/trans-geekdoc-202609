# More About Bivariate Regression 521

be strictly independent because they are all based on the same estimates of $b_0$ and $b_1$. Nonetheless, if $N$ is reasonably large, this unavoidable dependency will be very small so that residuals can meaningfully examined for evidence of lack of independence. This is typically done by examining the pattern of residuals as a function of time of observation. The rationale for this is that data is collected and recorded sequentially. If the error components are independent, the residuals should not vary systematically. Systematic variation may reflect changes in participants, measuring devices, or surroundings. When the residuals are plotted against time or case, the result should again look like the top panel of Figure 19.5.

It is possible for error components to exhibit different kinds of serial correlations. For example, the residual correlation to case $i$ may tend to be similar (or dissimilar) to those residuals to case $i-1$ or $i-2$. Several package values of the Durbin-Watson statistic forms the basis for a test of serial correlation in adjacent residuals. The D statistic

```
$D = \frac{\sum(e_i - e_{i-1})^2}{\sum e_i^2} \quad (19.16)$
```

will be small when sequentially adjacent residuals are positively correlated and large when they are negatively correlated. $D$ is approximately equal to $2(1 - r_{i,i-1})$, where $r_{i,i-1}$ is the correlation between sequentially adjacent residuals. Therefore $D$ can range from 0 to 4, with large deviations in each direction from a value of 2 providing stronger evidence of serial correlation. A more detailed description of the test, and appropriate tables for assessing significance, may be found in Draper and Smith (1998). Under some conditions, weighted least-squares can be used to perform the regression analysis when the data are serially correlated (e.g., see Draper & Smith, 1998). In the current example, as we see from the model summary table in the SPSS regression output in Figure 19.6, the Durbin-Watson statistic is close to 2, indicating that the serial correlation for adjacent residuals is close to zero.

To obtain the Durbin-Watson statistic in SPSS, begin the regression as described in Section 17.6, then in the Statistics bar and tick the box for Durbin-Watson in the Residuals section. In R, we can use the function in the [lmtest] package; dwest(datWSc~$datW) returns 2.084, $p=0.073$, the same value as in SPSS.

# 19.8 Locating Outliers and Influential Data Points

In Chapter 2, we introduced outliers and extreme outliers that were more than 1.5, or 3, times the H-spread of the data. In bivariate regression, a point can be an outlier in the Y dimension if its value does not follow the general pattern established by the other data points. In other words, if its Y value, conditional on X, is unusual or extreme, then it is an outlier that has a relatively large residual. It may also be an influential point if its removal would substantially change the ordinary least-squares regression outcome. If a point is an outlier in the X dimension, we say it has high leverage, much like an individual sitting at the extreme end of a playground teeter teeter.

As we will see, outliers are not necessarily influential points, but it is always important to check for the presence of both outliers and influential data points. Once located,