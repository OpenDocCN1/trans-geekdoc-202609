
## 10.2 Theory-based inference for simple linear regression

The histogram of the residuals shown in Figure 10.9 (left plot) does not appear exactly normal as there are some deviations, as the highest bin value appearing just to the right of the center. The histogram does not seem too far from normality. The QQ-plot (right plot) supports this conclusion. The scatterplot is not exactly on the 45-degree line but it does not deviate from it either.

We compare these results with residuals found by simulation that do not appear to follow normality as shown in Figure 10.10. In this case of model yielding the clearly non-normal residuals on the right, any results from an inference for regression would not be valid.

![](img/445742518041017e8f01f11b0c3190d9_415_0.png)

FIGURE 10.10: Non-normal residuals.

### Equality or constancy of variance for errors

The final assumption we check is the Equality or constancy of the variance for the error term across all fitted values or regressor values. Constancy of variance is also known as homoskedasticity.

Using the residuals again as rough estimates of the error terms, we want to check that the dispersion of the residuals is the same for any fitted value $\hat{y}_i$ or regressor $x_i$; In Figure 10.6, we showed the scatterplot of residuals against fitted values (right plot). We can also produce the scatterplot of residuals against the regressor duration:

```
ggplot(fitted_and_residuals, aes(x = duration, y = residual)) + 
geom_point(alpha = 0.6) + 
labs(x = "duration", y = "residual") + 
geom_hline(intercept = 0)
```

![](img/445742518041017e8f01f11b0c3190d9_415_1.png)

FIGURE 10.11: Plot of residuals against the regressor.

With the exception of the change of scale on the x-axis, it is equivalent to visualization purposes to producing a plot of residuals ($e_i$) against the fitted values ($\hat{y}_i$) or the regressor values ($x_i$). This happens because the fitted values are a linear transformation of the regressor values, $\hat{y}_i = b_0 + b_1x_i$.

Observe the vertical dispersion or spread of the residuals for different values of duration:

- For duration values between 100 and 150, the residual values are somewhere between -25 and 40, a spread of about 65 units.
- For duration values between 150 and 200 seconds, there are only a handful of observations and it is not clear what the spread is.
- For duration values between 200 and 250 seconds, the residual values are somewhere between -37 and 32, a spread of about 69 units.
- For duration values between 250 and 300 seconds, the residual values are somewhere between -42 and 27, a spread of about 69 units.

The spread is not exactly across all values of duration. It seems to be slightly higher for greater values of duration, but there seems to be a larger number of observations for higher values of duration as well. Also observe that there are two or three cluster of points and the dispersion of residuals is not completely uniform. While the residual plot is not exactly a null plot, there is no clear evidence against the assumption of homoskedasticity.

We are not surprised to see plots such as one when dealing with real data. It is possible that the residual plot is not exactly a null plot, because there may be some information we are missing that could improve our model. For example, we could include another regressor in our model. Do not forget that we are using a linear model to approximate the relationship between duration and waiting times, and we do not expect the model to perfectly describe this relationship. When you look at these plots, you are trying to find clear evidence of the data not meeting the assumptions used. This example does not appear to violate constant variance.

In Figure 10.12 we present an example using simulated data with non-constant variance.

![](img/445742518041017e8f01f11b0c3190d9_416_0.png)

FIGURE 10.12: Example of clearly non-equal variance.

Observe how the spread of the residuals increases as the regressor increases. Lack of constant variance is also known as heteroskedasticity. When heteroskedasticity is present, some of the results such as the standard error of the least-square estimators, confidence intervals, or the conclusion for a related hypothesis test would not be valid.

### What is the conclusion?

We did not find conclusive evidence against any of the assumptions of the model:

1. Linearity of relationship between variables
2. Independence of the error terms
3. Normality of the error terms
4. Equality or constancy of the variance

This does not mean that our model was perfectly adequate. For example, the residual plot was a null plot and had some clusters of points that cannot be explained by the model. But overall, there were no trends that could be considered clear violations of the assumptions and the conclusions we get from this model may be valid.

## What do we do when the assumptions are not met?

When there are clear violations of the assumptions in the model, all the results found may be suspect. In addition, there may be some remedial measures that can be taken to improve the model. None of these measures will be addressed in-depth as this material extends the scope of this book, but we briefly discuss potential solutions for future reference.

When the Linearity of the relationship between variables is not met, a simple transformation of the regressor, the response, or both variables may solve the problem.

If not, alternative methods as spline regression, generalized linear models, or non-linear models may be used to address these situations. When additional regressors are available, including other regressors as in multiple linear regression may produce better results.

If the Independence assumption is not met, but the dependency is established by a variable within the data at hand, linear mixed-effects models can also be used. These models may also be referred to as hierarchical or multilevel models.

Small departures of the Normality of the error terms are not too concerning and most of the results, including those related to confidence intervals and hypothesis tests, may still be valid. On the other hand, when the number of violations to the normality assumption is large, many of the results may no longer be valid. Using the advanced methods suggested earlier here may correct these problems too.

When the Equality or constancy of the variance is not met, adjusting the variance by adding weights to individual observations may be possible if relevant information is available that makes those weights known. This method is called linear regression or weighted least squares, and it is a direct extension of the model we have studied. If information of the weights is not available, some methods can be used to provide an estimator for the internal structure of the variance in the model. One of the most popular of these methods is called the sandwich estimator.

Checking that the assumptions of the model is satisfied is a key component of regression analysis. Constructing and interpreting confidence intervals as well as conducting hypothesis tests and providing conclusions from the results of hypothesis tests are directly affected by whether or not assumptions are satisfied. At the same time, it is often the case with regression analysis a level of subjectivity when visualizing and interpreting plots is present, and sometimes we are faced with difficult statistical decisions.

So what can be done? We suggest transparency and clarity in communicating results. It is important to highlight important elements that may suggest from relevant assumptions, and then provide pertinent conclusions. In this way, stakeholders of any analysis are aware of the model's shortcomings and can decide whether or not to agree with the conclusions presented.

## Learning check

(LC10.7) Use the un_member_states_2024 data frame included in moderndive package with variable fertility rate (fert_rate) and the regression life expectancy (life_exp).

- Use the get_regression_points() function to get the observed values, fitted values, and residuals for all UN countries.
- Perform a residual analysis and look for any systematic patterns in the residuals. Ideally, there should be little to no pattern but comment on what you find here.

(LC10.8) In the context of linear regression, a pvalue of near zero for the slope coefficient suggests which of the following?

- A. The intercept is statistically significant at a 95% confidence level.
- B. There is strong evidence against the null hypothesis that the slope coefficient is zero, suggesting there exists a linear relationship between the explanatory and response variables.
- C. The variance of the response variable is significantly greater than the variance of the explanatory variable.
- D. The residuals are normally distributed with mean zero and constant variance.

(LC10.9) Explain whether or not the residual plot helps assess each one of the following assumptions.

- Linearity of the relationship between variables
- Independence of the error terms
