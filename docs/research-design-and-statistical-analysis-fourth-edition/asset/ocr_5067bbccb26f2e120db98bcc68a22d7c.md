$r = -0.49$. Both values suggest strongly linear relationships, although we will see later that some nonlinear relationships can yield similar $r$ values. Because the correlation coefficient is inherently a $z$ score measure, it should be interpreted with caution. We discuss interpretation of correlation in great detail in Chapter 18.

# 2.7.3 Linear Regression

Although the correlation coefficient is an index of how well a bivariate distribution is fit by a straight line, it does not describe the line. In Chapter 18, we show that the straight line that predicts Y from X has its slope and intercept given by

```
$b_1 = r \frac{s_Y}{s_X}$$
```

```
$and \ b_0 = \bar{Y} - b_1\bar{X}$$
```

For example, the regression equation that predicts multiplication accuracy from subtraction accuracy for third-graders in the Royer data set is

predicted multiplication accuracy = $1.631 + 0.883 \times$ subtraction accuracy

Therefore, we would predict that a student with subtraction accuracy of 90 would have a multiplication accuracy of 81, rounding to the nearest integer. Every 10 point increase in subtraction accuracy is associated with, on average, an 8.8 point increase in accuracy. The regression equation is useful for prediction and it provides a description of the relationship between multiplication and subtraction accuracy.

There is much more to be said about correlation and regression, and more generally about measures relating two or more variables. Chapters 18–20 expand upon this very introduction to bivariate relationships, and Chapters 21–25 continue our discussion by considering more than two variables and nonlinear relationships.

# 2.8 Summary

In this chapter, we presented various ways of looking at data. The process of understanding our results begins with exploration of the data. Exploration should go beyond computing means and standard deviations and correlation coefficients. Therefore, we considered ways of graphing the distribution of observations (e.g., histograms, box plots, scatterplots), of calculating measures of location (e.g., median, mean) and variability (e.g., standard deviation, $IQR$), and of calculating measures of shape (skewness, kurtosis). Data description and exploration serves several important purposes:

+   - A thorough description is essential to understand the data.
- Exploration provides a check on assumptions underlaying subsequent statistical tests, such as the assumption of a normal distribution of scores.
- Data exploration can be a source of hypotheses. A thorough description of a data set often leads to discovery: Unexpected differences between conditions may be noticed and pursued. Details of a distribution of scores may provide a deeper understanding of the nature of the effect of a manipulation.