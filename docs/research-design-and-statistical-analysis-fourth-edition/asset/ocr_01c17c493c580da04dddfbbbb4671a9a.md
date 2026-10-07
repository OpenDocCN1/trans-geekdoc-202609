# Additional Topics in Multiple Regression 609

predictor of TC for older participants, and age is a less useful predictor of TC for participants with large BMI values.

How do we interpret the other regression coefficients in Equation 22.14 and their tests of significance in Figure 22.8? The coefficient of age, 5.209, is the slope of predicted TC for BMI = 0. The standard error, 1.383, and the corresponding t value of 3.765 are also conditional on the value of BMI = 0. Similarly, the coefficient of BMI, 7.844, is the slope of predicted TC vs BMI for age = 0, and the standard error and t also hold only for age = 0.

We are not likely to be interested in what happens at age = 0 and BMI = 0, but we may be interested in testing whether a coefficient is significant at a value of the other predictor. For example, we may wish to test whether the slope of predicted TC vs BMI is significant at age = 20. There are several ways to conduct this. We can find the value by substituting age = 20 into Equation 22.15. We can also develop expressions for the standard error of the slope at age = 20 and conduct the appropriate t test. However, the easiest way to perform this test of a simple effect is to transform the variable and regress

Suppose we create the variable age20 = age - 20. Then we can regress TC on age20, BMI and age20xBMI, a variable obtained by multiplying age20 and BMI. The resulting equation is

```
TC = 33.931 + 5.209 age 20 + 5.135 BMI – 0.135 age 20 × BMI
```

The interpretation of the coefficients is comparable to that of Equation 22.14. Here we are most interested in the coefficient of BMI, 5.135, which is the slope of predicted TC with BMI at age=0, that is, at age=20. The coefficient is significantly different from 0, t(177) = 3.765, p = .000. So we can say that the slope for BMI is significant at age = 20. Note that the coefficient of the product term is not affected by transforming age to age20 = age - 20. The same approach can be used to test the coefficient of any other age. Similarly, we can test the coefficients of age at different levels of BMI by transforming BMI and reordering the regressions.

# 22.8.4 Using Centering to Reduce Multicollinearity

When we add a product term to a regression equation that already contains the terms making up it, we are likely to have multicollinearity. This is because a product term will generally be highly correlated with its constituents. For example, in our continuing example using ages 20-65 with BMI scores no greater than 40, age and BMI have correlations of .801 and .675 with the product term age × BMI. For the regression of TC on the variance inflation factors (see Section 22.5.1) are 35.53, 23.44, and 64.42, respectively, which suggests a serious problem with multicollinearity. The square root of the VIFs shows that the standard errors of the regression coefficients are at least 4 times larger when the age × BMI is included than it is not. Because of this, it is often suggested that regression product terms should be conducted with centered variables (see, for example, Jacquard, Turissi, & Wan, 1990).

Suppose we take the suggestion and center all the variables by replacing them by their deviation scores, resulting in the centered variables age (equal to age minus the mean of the age scores), BMIcent, TCcent, and the product term Age × BMIcent (note that we obtain the product term by multiplying the centered variables, not by multiplying