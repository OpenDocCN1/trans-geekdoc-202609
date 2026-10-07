
(b); on average, the squared errors are smaller in Panel (a) than Panel (c), reflecting the fact that X contains information about the likely value of Y. The detailed interpretation is as follows:

- 1. If we do not use any information about X when predicting the corresponding value of Y, the best least-squares prediction for each Y can be shown to be $\bar{Y}$, the mean of the Y scores. If we use $\hat{Y}$ for the prediction of each of the N predictions is the total variability in the Y scores, the sum of squares $SS_Y = \Sigma(Y - \bar{Y})^2$. That is, $SS_Y$, is literally the sum of all the squared errors in Figure 17.8 (c).
- 2. If we use the information about X and predict using the regression equation, as in Figure 17.8 (a), the sum of the squared errors for the set of predictions is $SS_{residual} = \Sigma(Y - \hat{Y})^2$. Substituting the expression for $\hat{Y}$ from Equation 17.10 and simplifying, the sum of the squared residuals can be shown to be

$$SS_{residual} = (1 - r^2)SS_Y$$ (17.15)

- 3. The amount by which prediction error is reduced when the regression equation is used instead of the mean is, therefore,

$$SS_{regression} = SS_Y - SS_{residual} = SS_Y - (1 - r^2)SS_Y = r^2SS_Y$$ (17.16)

- 4. Therefore, the *proportion* by which prediction error is reduced (or the proportion of the variability in Y accounted for by the regression on X) is

$$\frac{SS_{regression}}{SS_Y} = \frac{r^2 SS_Y}{SS_Y} = r^2$$

The coefficient of determination, $r^2$, is therefore a measure of how well the linear regression fits the data. According to the Cohen (1977, 1988) guidelines, $r^2$ values of .01, .09, and .25 are small to medium, and large linear relationships, respectively. For the arithmetic data (Figure 17.1), the correlation between the subtraction and multiplication accuracy is .594, so the coefficient of determination is $(594)^2 = .353$. This tells us that the variability of Y scores by the regression line $(1 - .353) = .647$ of the variability of $\hat{Y}$. Therefore, if we use the regression to predict $\hat{Y}$ instead of $Y$ we will reduce the prediction error by one-third.

We should note that $r^2$ has been frequently misinterpreted, and that some of these interpretations have resulted in inappropriate claims made in the literature. For example, the statement has been made in a number of psychology textbooks that children achieve about 50% of their adult intelligence by age 4. There is no valid basis for this statement; it is based on a misunderstanding of $r^2$. Specifically, it is based on the results of several longitudinal studies that found IQ scores at age 17 to have a correlation of .7 with IQ scores at age 4 (see Bloom, 1964). The resulting $r^2$ of .5 (or 50%) provides an indication of how predictable adult IQ is from IQ at age 4, using linear regression. However, this result says nothing about the relative amounts of intelligence at age 4 and 17, and therefore provides no evidence for the statement.

## 17.6.5 Partitioning of Variability in Regression and the Standard Error of the Estimate

Equation 17.16 indicates how the variability in the Y scores can be partitioned into two components – the variability of the predicted scores about the mean and the variability of the actual Y scores about the regression line. Rewriting Equation 17.16, we have

$$SS_{Y} = SS_{regression} + SS_{residual} = r^2SS_{Y} + (1-r^2)SS_{Y} = \Sigma(Y-\bar{Y})^2 = \Sigma(\hat{Y}-\bar{Y})^2 + \Sigma(Y_i-\hat{Y}_i)^2$$

Among other things, this helps us understand an important measure of error of prediction in regression called the standard error of the estimate. Although $r^2$ is a commonly used measure of strength of relationship, such as the variance of the estimate (basically, the mean of the squared raw-score prediction errors) or its square root, the standard error of the estimate, provides more useful information than either $r$ or $r^2$ about the accuracy of predictions based on the raw-score regression equation. The standard error of the estimate is the most commonly used measure of variability of the data points around the regression line and is typically provided as part of the regression output by software packages. For the regression of Y on X, the standard error of the estimate is defined as

$$s_{Y.X} = \sqrt{\frac{\Sigma(Y_i-\hat{Y}_i)^2}{N-2}} = \sqrt{\frac{SS_{residual}}{N-2}} = \sqrt{\frac{(1-r^2)SS_{Y}}{N-2}}$$

In Equation 17.18, there are $N-2$ df associated with $SS_{residual}$ because there are N data points and two restrictions; that is, $df$ are due by estimating the intercept and slope of the regression equation. We will encounter the standard error of estimate when we develop hypothesis testing and confidence intervals for regression statistics.

## 17.6.6 Using Software for Least-Squares Linear Regression

Least-squares linear regression is commonly available in software packages. In SPSS, select Regression from Analyze menu, and choose Linear. Move Y to the dependent variable box and X to the independent variable, and click OK. The unstandardized coefficients in the output correspond to the $b_0$ and $b_1$ of Equations 17.11 and 17.12, and the standardized coefficient is the slope (i.e., correlation) from Equation 17.9. Note that $r$, $r^2$, and the standard error of the estimate are also presented in the "model summary" section of the output.

In R, we can use the $lm$ function in the {stats} package to fit a linear model. For example, if Y and X are two variables in a data frame called dat, we can regress Y on X using the command lm(Y~X, data=dat). The output reports the values of $b_0$ and $b_1$. We can request

## An Introduction to Correlation and Regression

Now we have introduced linear regression and coefficients such as the standard error of the estimate, we are in a position to describe the correlation in more detail. Moreover, they often serve as raw material for more complex procedures such as factor analysis.

## 17.7 More About Interpreting the Pearson Coefficient

Now we have introduced linear regression and coefficients such as the standard error of the estimate, we are in a position to describe the correlation in more detail.

## 17.7.1 Ten Things to Remember About Correlation

- 1. The Pearson correlation coefficient depends on variabilities of X and Y. Because the correlation coefficient is a measure of the similarity of X and Y (see Figure 17.6), $s_x$ and $s_y$ affect $r$. From Equation 17.13, we have

$$r = b_1 \frac{s_X}{s_Y}$$

This means that for a given slope, different correlations will result from different deviations of X and Y. Even if for both slope and standard error of estimate, $s_{y,x}$ and $s_{x,y}$ are constant, Equations 17.13, 17.17, and 17.18 can be used to show that different values of $r$ will result for different values of $s_x$ and $s_y$, for example,

  - For a given $b_1$ and $s_{y,x}$, $r$ increases with $s_x$.
  - For a given $s_{x,y}$, $r$ increases with $b_1$, $s_x$ and $s_y$.
  - For a given $s_x$ and $s_{x,y}$, $r$ increases with $b_1$.

Therefore, if we are concerned with Y changes with X, we should generally look at $b_1$, not $r$.

- 2. Because the correlation coefficient depends on $s_x$ and $s_y$, it is a sample-specific measure. Given a population in which X and Y are linearly related with a population correlation of $\rho$, the value of $r$ obtained in a sample depends on how the sample is selected. If the sample is largely selected from only part of the distribution of X (say, the regions A, B, or C in Figure 17.9), $r$ will tend to be smaller than $\rho$ because $s$ will tend to be smaller than $\sigma$, in the population. Note that this dependence on the variability of X in the sample does not hold for the unstandardized estimate of slope, $\beta_1$.

This type of bias is frequently referred to as the restriction of range problem; all things being equal, the sample correlation will be smaller if there is less variability in X.
