# Regression With Qualitative and Quantitative Variables 635

In summary, the ability to use categorical variables in multiple regression analyses enables us to adjust sums of squares in ways that result in tests of the hypotheses of factorial ANOVA in nonorthogonal diagonals. We can use the Method 1 approach to test hypotheses about unweighted cell means and the Method 3 approach to test about weighted means. Also, if we logically or theoretically determined orders of factors, we can perform sequential adjustments.

# 23.4 Testing Homogeneity of Regression Slopes Using Multiple Regression

In Chapters 19 and 22, we discussed tests for equality of slopes when one variable was regressed on another at different levels of a dichotomous (i.e., having only two levels) categorical variable. We selected participants in the Seasons data set aged 65 years or less with BMI scores over 40 and tested whether the rate of change of total cholesterol level (TC) with age was the same for participants identified as men and women. Although we did not use the term, sex in the data is a dummy variable that labels men by 0 and women by 1. We showed we could test the hypothesis that the rate of change was the same for men and women by regressing TC on age, sex, and an additional variable Age × Sex that was formed by multiplying age by sex. The resulting regression equation is

```
TC = 221.143 − 0.0005 age − 94.612 sex + 1.813 Age × Sex
```

Because the coefficient of the interaction term age × sex is significant, t(363) = 4.909, p = .000, we can reject the hypothesis that the slope of TC with age is equal for men and women, consistent with what we saw in Figure 22.5.

What if the categorical variable has more than two levels? If so, can we still test the homogeneity of regression slopes by demoting whether there is a significant interaction. That is, can we test whether the regression of Y on a continuous variable, X, depends on the level of A when A is a categorical variable with more than two levels. However, now more than one dummy variable is needed to code the categorical variable, the interaction term will have more than 1 df, and we will need to use a partial F test to determine whether the interaction is significant.

Consider, for example, the categorical variable education EL. We might be interested not only in its effect on TC, but also in its interaction. EL = 1 corresponds to individuals with a high school education or less (schoolry = 1, 2), EL = 2 beyond high school but not including the bachelor’s degree (schoolry = 4, 5, or 6), and EL = 3 to at least a bachelor’s degree (schoolry = 7). We treat the EL as a categorical variable. EL seems to make a difference in TC. Using the same participants as the previous analysis, mean TC is 227, 217, and 210 for EL = 1, 2, and 3, respectively, and an ANOVA with EL as the independent variable is significant, F(2, 359) = 4.908, p = .000.

Now let's consider the effects of EL on TC depend on the level of the participants. Because EL has three levels, we can code it with two dummy variables – we use effect, dummy, or any other kind of dummy coding. We can code the interaction of EL with age using two additional dummy variables obtained, by multiplying the two dummy variables to code EL by age. If we have a continuous predictor X and a categorical variable A with a levels, the proportion of the variability in Y accounted for by a regression on X and the a–1 dummy variables coding the categorical variable A is R²,Y,X.A.. If we now add the a–1 dummy variables that account for

![](bbox=[0.418, 0.843, 0.582, 0.873])