
finds that the best-fitting regression model is $\widetilde{TC}=124.00+1.873age$ $R^2=.321$. The backward elimination procedure dropped $BMI$ as a predictor doing so did not result in a significant reduction in $R^2$ given the other predictors in the model at that step in the process. In contrast, the forward selection procedure included $BMI$ doing so improved the fit significantly. If this variability in the final equation surprises you, you may wish to review the discussion of the meaning of regression coefficients and suppression effects in Chapter 20.

## 21.8.3 Stepwise Regression

Stepwise regression, the most popular of these automated selection procedures, are a combination of forward selection and backward elimination. The procedure is essentially the same as forward select except after each new predictor has been added to the regression equation, all the predictors are re-examined to determine whether they should be removed. A partial F test is performed on the predictor in the equation that produces the smallest increment in $R^2$. If the predictor no longer satisfies the criteria for inclusion, it is removed from the equation. Statistical software allows the user to set the significance levels (or critical $F$ values) for entering or removing a variable. With the five-predictor $TC$ example, stepwise regression finds that the best-fitting model $TC=103.423+1.874age+.860BMI$ with $R^2=.333$, the same model identified using forward selection.

It is not difficult to see why it is desirable to remove a predictor that had entered early in the analysis. For example, suppose $X_i$ is highly predictable from $X_4$ and $X_5$, but is highly correlated with $Y$ than either of them. Even though $X_i$ may enter the equation because of its high correlation with $Y$, it will become superfluous after $X_4$ and $X_5$ are entered. Even if $X_i$ contributes significantly to the predictability of $Y$ by itself, it may not make a significant contribution over and that provided by the other variables.

It is important to emphasize that when predictors entered into the equation are selected from a larger pool, the significance levels put out by stepwise processes are not "real" p-values. Because many researchers seem to be unaware of this fact, stepwise regression outputs are frequently misinterpreted. As Wilkinson states, stepwise regression routines are probably the most notorious source of "pseudo p-values" in the field of automated analysis. With forward selection, we recommend Wilkinson's (1979) tables be used to test $R^2$ for significance.

We again emphasize that the motive for the automated procedures described in this section is to develop useful equations that contain subsets of the available predictors. There is no reason to think that the equations they produce are explanatory models. Variables that are useful predictors need not be important components of a good theory or causal explanation of the situation. The automated procedures may include unintentionally variables in the regression equations and may fail to include the important variables. Consider, for example, a stepwise regression with several predictors that are highly correlated with both the criterion and with each other. The correlation between the criterion and the predictor included in the first step may be only marginally greater than the correlation between the criterion and the other predictors. Nonetheless, including the first predictor may prevent any of the others from being entered into the equation on subsequent steps. Even though the other predictors add significantly to the predictability of Y in the absence of the first variable, they may not do so the first variable is in the equation. Forward regression procedures are more likely than backward elimination to exclude potentially useful predictors that involve suppression (see Section 20.8). Even in situations where both the suppressor variable and the variable whose variance is suppressed are useful for predicting Y, it is possible that neither variable may make it into the equation unless the other variable is already there, or if a forward selection procedure is used.

Because predictor variables are included in the regression equation if they are useful in the sample, stepwise procedures are extremely susceptible to capitalization on chance, especially when the sample is small. Recall that in the discussion of capitalization on chance in Chapter 20 we presented an example in which stepwise regression produced an equation that fits a fairly well (R = .42). Nonetheless, we demonstrated that the equation was of no use for predicting outside of that sample (cross-validated R = .10). If stepwise regression is to be used, it is essential to use cross-validation to evaluate the generality of the resulting equation.

We conclude this by reiterating that using these automated procedures is a very poor way to develop theory. Automated programs may be easy to use but are a poor substitute for thinking. Even minimal knowledge about the research situation along with careful exploration of the data should lead to better preliminary models than an automated procedure. We repeat this point because keep encountering researchers who are ignorant of, or resistant to, this advice. As Wilkinson (1998) has stated in the SYSTAT manual:

Stepwise regression is probably the most abused computerized technique ever devised. If you think you needed automated regression to solve a problem, it is almost certain that you do not. Professional statisticians rarely use automated stepwise regression because it does not necessarily find the “best” fitting model, the “real” model, or alternative “plausible” models. Furthermore, the order in which variables enter or leave a stepwise program is usually of no theoretical significance. You are always better thinking about why a model could generate your data and then testing model (p. 351).

## 21.9 Summary

- In Chapter 21, we discussed statistical inference in multiple regression. We also considered the models underlying the inference and introduced several statistical tests and power calculations for the regression coefficients.
- We discussed how to check for violations of the assumptions that influence the inference and how to detect outliers and influential points.
- We described confidence intervals for regression coefficients and for the multiple coefficient.
- We described the challenges of controlling Type 1 errors in multiple regression.
- Finally, we considered some automated procedures available in statistical packages for finding the “best” equations. Because many researchers are under the impression that these automated procedures are useful in developing theory, we emphasized the point that they should not be used to develop explanatory models.

# Research Design and Statistical Analysis

## Exercises

21.1 Bivariate and multiple regression In an experiment designed to determine the effects of dosage on performance, the following data (available as data set EX21_1) are obtained:

| Dosage in milligrams | 10 | 20 | 30 | 40 |
| :--- | :--- | :--- | :--- | :--- |
| 6.8 | 10.4 | 10.7 | 8.9 |
| 2.8 | 6.4 | 14.4 | 12.5 |
| 5.2 | 13.1 | 15.9 | 12.7 |
| 4.8 | 8.7 | 10.6 | 7.4 |
| | 12.4 | | |
| | 7.2 | | |

- a) Perform an ANOVA to test the effect of dosage.
- b) Regress performance on dosage to determine whether there is a significant linear relationship between performance and dosage.
- c) Determine whether there is a significant nonlinear relationship between performance and dosage.
- d) Determine whether there is a significant quadratic component to the relationship by creating a new variable, dosageq, formed by squaring dosage (you will need to compute a new variable), and then regress performance on dosage and dosagesq. Find the best-fitting quadratic equation.

21.2 Stepwise regression Data set EX21_2 contains hypothetical data for verbal achievement of students in elementary school; potential predictor variables are quality and quality, measures of school and teacher characteristics, and schback and pbackground, measures of student and parent background.

- a) The school and teacher measures contribute to the predictability of verbal ability? Do the student and parent measures? Consider regression equations containing different combinations of predictors in arriving at your answer.
- b) Perform a stepwise regression using one of the standard packages. Do you think that the regression equation identified by the stepwise regression is a reasonable explanatory model?

21.3 Planning sample size Using data from an observational study, we plan to perform a multiple regression analysis with six predictor variables. If we want to test the hypothesis that all population regression coefficients are equal to 0 at α = .05, how many cases do we need to have a power of .80:

- a) if we expect an R^2 of .30?
- b) if R^2 = .20?
- c) if R^2 = .10?

21.4 Testing all regression coefficients We perform a multiple regression with six predictors and find that R^2 = .20. Can we reject the null hypothesis that all the regression coefficients = 0 in the population if N = 50?
