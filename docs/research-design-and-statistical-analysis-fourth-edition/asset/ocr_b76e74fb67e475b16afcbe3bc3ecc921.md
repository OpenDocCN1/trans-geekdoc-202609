# Additional Topics in Multiple Regression

![](bbox=[0.198, 0.098, 0.802, 0.493])

Figure 22.6 Scatterplot of TC versus age for men and women with regression functions, using data from participants age 65 years or less with BMI ≤ 40.

of predicted TC with age when sex = 0; that is, for the male-identifying participants. The coefficient of sex, ~94.612, is the rate of change of predicted TC with sex (i.e., the difference in predicted TC for men and women) for age = 0. We can better understand the coefficient of the product term, 1.813, by reorganizing the terms in Equation 22.10 and rewriting the equation as either

```
TC = 221.143 - 94.612 sex + (-0.0005 + 1.813 sex) age
```

or as

```
TC = 221.143 - 0.0005 age + (-94.612 + 1.813 age) sex
```

From these equations, we can see that the rate of change of predicted TC with age is a function of sex, namely, ~0.0005 + 1.813 sex. Therefore, in this data set the variable sex has only two levels, 1.813 can be interpreted as the difference between the slopes of predicted TC with age for men and women. Similarly, the change in predicted TC with sex, that is, the difference in predicted TC for men and women, is a linear function of age, ~94.612 + 1.813 age. The coefficient of the interaction component, 1.813, can also be