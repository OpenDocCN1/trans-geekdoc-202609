# An Introduction to Correlation and Regression 465

# Appendix 17.1

Proof that $z_y=\pm z_x$ when $Y=b_0+b_1X$

We want to show that if X and Y have a perfect linear relationship, $z_y=z_x$ when the relationship is positive and $z_y=-z_x$, when it is negative. For any data point $(X, Y)$ that falls on a straight line, we have $Y=b_0+b_1X$. Substituting into the usual expressions for the mean and standard deviation and simplifying, we have $ar{Y}=b_0+b_1ar{X}$ and $s_y=\pm b_1s_x$, with $s_y=+b_1s_x$ when $b_1$ is positive and $s_y=-b_1s_x$ when $b_1$ is negative. Therefore, if there is a perfect linear relationship between X and Y:

```
$z_Y = \frac{Y-\bar{Y}}{s_Y} = \frac{b_0+b_1X-(b_0+b_1\bar{X})}{\pm b_1s_X} = \frac{X-\bar{X}}{\pm s_X} = \pm z_X$
```

# Exercises

17.1 [Calculating correlation, regression equations, and proportion of variance explained] Given the following data,

| X | Y |
| 1 | 11 |
| 2 | 3 |
| 3 | 7 |
| 4 | 9 |
| 5 | 9 |
| 6 | 21 |

+   a) Draw a scatterplot.
b) What is the correlation between Y and X?
c) What is the least-squares equation for the regression of Y on X?
d) What is the proportion of variance in Y accounted for by X?
e) Find the equation for the regression of X on Y.
f) What is the proportion of the variance in X accounted for by Y.

17.2 [Correlations on raw data and z	ext{} scores] Given the following data for three variables X, Y, and W:

| W | X | Y |
| 12 | 4 | 7 |
| 8 | 6 | 9 |
| 14 | 13 | 3 |
| 17 | 12 | 14 |
| 18 | 13 | 16 |