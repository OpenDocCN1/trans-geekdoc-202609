# Inference, Assumptions, and Power in Multiple Regression 585

entered into the equation on subsequent steps. Even though the other predictors add significantly to the predictability of Y in the absence of the first variable, they may not do so the first variable is in the equation. Forward regression procedures are more likely than backward elimination to exclude potentially useful predictors that involve suppression (see Section 20.8). Even in situations where both the suppressor variable and the variable whose variance is suppressed are useful for predicting Y, it is possible that neither variable may make it into the equation unless the other variable is already there, or if a forward selection procedure is used.

Because predictor variables are included in the regression equation if they are useful in the sample, stepwise procedures are extremely susceptible to capitalization on chance, especially when the sample is small. Recall that in the discussion of capitalization on chance in Chapter 20 we presented an example in which stepwise regression produced an equation that fits a fairly well (R = .42). Nonetheless, we demonstrated that the equation was of no use for predicting outside of that sample (cross-validated R = .10). If stepwise regression is to be used, it is essential to use cross-validation to evaluate the generality of the resulting equation.

We conclude this by reiterating that using these automated procedures is a very poor way to develop theory. Automated programs may be easy to use but are a poor substitute for thinking. Even minimal knowledge about the research situation along with careful exploration of the data should lead to better preliminary models than an automated procedure. We repeat this point because keep encountering researchers who are ignorant of, or resistant to, this advice. As Wilkinson (1998) has stated in the SYSTAT manual:

Stepwise regression is probably the most abused computerized technique ever devised. If you think you needed automated regression to solve a problem, it is almost certain that you do not. Professional statisticians rarely use automated stepwise regression because it does not necessarily find the “best” fitting model, the “real” model, or alternative “plausible” models. Furthermore, the order in which variables enter or leave a stepwise program is usually of no theoretical significance. You are always better thinking about why a model could generate your data and then testing model (p. 351).

# 21.9 Summary

+   - In Chapter 21, we discussed statistical inference in multiple regression. We also considered the models underlying the inference and introduced several statistical tests and power calculations for the regression coefficients.

+   - We discussed how to check for violations of the assumptions that under influence the inference model and how to detect outliers and influential points in multiple regression.

+   - We described confidence intervals for regression coefficients and for the multiple correlation coefficient.

+   - We described the challenges of controlling Type 1 errors in multiple regression.

+   - Finally, we considered some automated procedures available in statistical packages for finding the “best” prediction equations. Because many researchers are under the impression that these automated procedures are useful in developing theory, we emphasized the point that they should not be used to develop explanatory models.