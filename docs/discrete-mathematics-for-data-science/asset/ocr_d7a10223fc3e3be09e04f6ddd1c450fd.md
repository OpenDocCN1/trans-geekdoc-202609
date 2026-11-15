evidence in support of the alternative hypothesis, and we conclude there is a significant relationship.

²Model testing is covered in the Resampling chapter. ⬚

For comparing one predictor variable with the y data in a regression, the appropriate test statistic is:

$t = \frac{b_1 - 0}{se_{b_1}}$

where the numerator \(b_1 - 0\) differentiates the beta coefficient \(b_1\) with a slope of zero, and \(se_{b_1}\) is the standard error of the beta coefficient.

Recall that \(b_1\) is:

$b_1 = \frac{s_{xy}}{s_x}$

The standard error of the estimate is:

$se_{b_1} = \sqrt{\frac{\sum(Y - \hat{Y})^2}{N - 2}}$

Here, the sum of squared errors is divided by \(n - 2\) instead of \(n - 1\), as we are estimating two parameters, the slope and the intercept, requiring an additional degree of freedom. This allows the standard error of the regression to be an unbiased estimate of the standard deviation of the estimate's errors.

Associated with the value of the t-statistic is the probability of obtaining a value at least as extreme as the value of the calculated t-statistic. This probability is referred to as the p-value. Note that the computations are complex and technology is normally used to calculate both the t-statistic and the p-value.