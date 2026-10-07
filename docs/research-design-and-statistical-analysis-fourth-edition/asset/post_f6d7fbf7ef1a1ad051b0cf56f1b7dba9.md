
# An Introduction to Correlation and Regression 465

# Appendix 17.1

### Proof that $z_y=\pm z_x$ when $Y=b_0+b_1X$

We want to show that if X and Y have a perfect linear relationship, $z_y=z_x$ when the relationship is positive and $z_y=-z_x$, when it is negative. For any data point $(X, Y)$ that falls on a straight line, we have $Y=b_0+b_1X$. Substituting into the usual expressions for the mean and standard deviation and simplifying, we have $\bar{Y}=b_0+b_1\bar{X}$ and $s_y=\pm b_1s_x$, with $s_y=+b_1s_x$ when $b_1$ is positive and $s_y=-b_1s_x$ when $b_1$ is negative. Therefore, if there is a perfect linear relationship between X and Y:

```
$z_Y = \frac{Y-\bar{Y}}{s_Y} = \frac{b_0+b_1X-(b_0+b_1\bar{X})}{\pm b_1s_X} = \frac{X-\bar{X}}{\pm s_X} = \pm z_X$
```

# Exercises

17.1 [Calculating correlation, regression equations, and proportion of variance explained] Given the following data,

| X | Y |
|---|---|
| 1 | 11 |
| 2 | 3 |
| 3 | 7 |
| 4 | 9 |
| 5 | 9 |
| 6 | 21 |

- a) Draw a scatterplot.
- b) What is the correlation between Y and X?
- c) What is the least-squares equation for the regression of Y on X?
- d) What is the proportion of variance in Y accounted for by X?
- e) Find the equation for the regression of X on Y.
- f) What is the proportion of the variance in X accounted for by Y.

17.2 [Correlations on raw data and z-scores] Given the following data for three variables X, Y, and W:

| W | X | Y |
|---|---|---|
| 12 | 4 | 7 |
| 8 | 6 | 9 |
| 14 | 13 | 3 |
| 17 | 12 | 14 |
| 18 | 13 | 16 |

# 466 Research Design and Statistical Analysis

Using software, find the correlations among W, X, and Y. Standardize the variables and recompute the correlations. They should be identical. Why?

17.3 [The effect of transformations on correlation] A Psychologist is interested in predicting Y from X in two distinct situations. She finds the following results:

| Situation 1 | Situation 2 |
|---|---|
| $b_y = 38.41$ | $b_y = .25$ |
| $s_y = 512.31$ | $s_y = 8.44$ |
| $s_y = 2.00$ | $s_y = 23.17$ |

- In which situation is the correlation between X and Y?
- Given a large number of data points (X, Y) and find that the correlation between X and Y is $r_{xy}=70$. You now add 10 to the X scores. What happens to the correlation coefficient; that is, what is the new correlation between Y and the transformed X?
- You have the same situation as in (b) - except adding 10 to each of the X scores, you multiply each of the Y by 3. Now what is the value of the correlation coefficient?
- Now perform both operations, multiply each Y by 3, and add 10 to the products. What happens to the correlation coefficient?

17.4 [Understanding influential points]

- Using the Royer data available on the book's website, find the correlation between multiplication accuracy (multac) and the time taken to solve multiplication problems (multtr) for third-graders.
- Generate the scatterplot for these variables.
- The correlation coefficient is not very resistant to the influence of data points that deviate from the best-fitting straight line. Here, 64 can be shown to be the most influential data point; that is, its removal results in more change in $r$ than the removal of any other data point. What is $r$ if case 64 is removed?

17.5 [Interpreting correlation] For each part, indicate whether the use of the correlation is reliable. If it is not, indicate why.

- The research division of the Old Southern Casket and Tobacco Corporation has just released the results of a study that is inconsistent with the health claims made against cigarette smoking. For a large sample of heavy smokers, a substantial positive correlation was found between the total number of cigarettes smoked during a lifetime and length of life, result they claim the conclusion that cigarette smoking is beneficial to health.
- It is found that for eighth-grade children there is a fairly strong negative correlation between the amount of television watched and school performance as measured by grades. It is claimed that this finding proves that watching television interferes with intellectual ability and has a negative effect on the ability to focus attention. Does this argument seem valid?

# An Introduction to Correlation and Regression 467

17.6 [The effect of transformations on correlation] A psychologist is interested in predicting Y from X in two distinct groups. She finds the following results:

| Group 1 | Group 2 |
|---|---|
| b_x = 1 | b_x = 4 |
| s_x = 20 | s_x = 10 |
| s_y = 10 | s_y = 2 |

- a) In situation is the correlation between X and Y higher?
- b) You have a large number of data points (X, Y) and find that the correlation between X and Y is $r_{xy} = 0.70$. You now transform X by multiplying each of the X scores by 10 and adding 3 to the products. You also transform Y by multiplying each of the Y scores by 2. What is the correlation coefficient between the transformed variables?

17.7 [Relating regression slope and correlation] In a large study of income (Y) as a function of years on job (X), the data for 2,000 workers with a college degree and 2,000 without a degree are the:

| College graduate | No college degree |
|---|---|---|---|
| Mean | Years (X) | Income | Years |
| 80 | 15 | 76 | 10 |
| $s^2$ | 324 | 100 | 289 |
| $r_{xy}$ | | .333 | | .235 |

> Note: Income is recorded in thousands of dollars.

- a) Find $b_{yx}$ (i.e., $\beta$, the regression coefficient for the regression of income on years of service) for each group separately.
- b) What is your best estimate of the amount by which salary increases per year for people with and without college degrees? Is this consistent with differences in the correlations in part (a)? Explain.
- c) Using separate regression equations for each group, what would you predict for people with without college degrees with 10 years of experience? 20 years of experience?

17.8 [Understanding correlations in separate and combined groups] Using the Seasons file available on the book's website, correlate height with weight, and then correlate height with weight separately for participants identified as men and women. How could you account for the discrepancies among the three?

17.9 [Interpreting correlation] For parts (a)-(c), indicate whether the use of the correlation and/or the conclusion is reasonable. If it is not, indicate why.

- a) A psychologist reads a description of a study where a correlation of -.80 was obtained between a measure of anxiety and a measure of emotional stability. To verify, he administers the same measures of anxiety and emotional stability to a random sample of patients in a Veterans Administration (VA) hospital. The observed correlation of -.20 is not significant. He concludes that he has no evidence of any relationship (at least any linear relationship) between anxiety and emotional stability.

# 468 Research Design and Statistical Analysis

- b) Martians are tall and skinny and do not weigh much. Jovians are shorter but weigh lot more. Height and weight correlate highly for each group, about r=.60. Would you expect the correlation between height and weight for a mixed group consisting of equal numbers of Martians and Jovians to be the same, bigger, or smaller than .60? Why?
- c) It is reported in the press that getting a degree from a four-year college is highly correlated with earnings; that is, several hundred thousand dollars a year in earnings.

17.10 [Correlation in separate and combined groups] Using the Seasons data set, verify that the correlation between cholesterol level (TC) and age is .506 for women only. .148 for women 50 years of age or over and .264 for women under 50 years of age. How do you explain the discrepancy? What are the corresponding results for men?

17.11 [Correlation in separate and combined groups] Using the data for patients identified as men in the Seasons set, if we consider individual men, the correlation between TC and age is .062. What is this correlation if we consider the variables of the agegrp; that is, if we find the mean value of TC and age at each level of agegrp, we use these as our data points?

17.12 [Regression to the mean]

17.13 [Regression to the mean] Assume that the correlation between the adult heights of fathers and sons is .5, and further, that the mean and standard deviations of the heights of adult males are 70.0 and 3.0 inches, respectively.

- a) Given the information that a father is 76 inches tall, what is the best linear prediction the adult height of his son?
