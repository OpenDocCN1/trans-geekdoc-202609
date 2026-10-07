# 472 Research Design and Statistical Analysis

Some characteristics of a bivariate distribution in X and Y are as follows:

+   - The marginal distributions (i.e., the distribution of one variable, collapsing over values of the other variable) of X and Y are normal with variances $\sigma_X^2$ and $\sigma_Y^2$, respectively.
- If X and Y have a correlation of zero, they are independent. That is, given normality, the only systematic relationship between X and Y is a linear one. The conditional means of Y (i.e., the means of the Y scores at particular values of X) fall on the straight line with the equation $\mu_{Y|X} = \mu_Y + eta_{YX}(X-\mu_X)$ where $eta_{YX} = ho\sigma_Y/\sigma_X$ is the slope of the population regression that predicts Y from X. The conditional distributions of Y are normal with variance $\sigma_{Y|X}^2 = \sigma_Y^2(1-ho^2)$. The conditional means of X fall on the straight line with the equation $\mu_{X|Y} = \mu_X + eta_{XY}(Y-\mu_Y)$ where $eta_{XY} = ho\sigma_X/\sigma_Y$ is the slope for the regression of X on Y, and the conditional distributions of X are normal with variance $\sigma_{X|Y}^2 = \sigma_X^2(1-ho^2)$.

The inferential procedures to which we now turn bivariate normal population distributions. If an assumption is violated, results may be biased.

# 18.2.2 Using the t Distribution to Test the Null Hypothesis $H_0: \rho = 0$

We can test whether there is a linear component to the relationship between X and Y in the population by considering the null hypothesis $H_0: \rho = 0$. When $ho = 0$, the statistic

```
t = \frac{r}{\sqrt{(1-r^2)/(N-2)}} \quad (18.1)
```

has a t distribution with N-2 degrees of freedom. We can use this expression as the test statistic to test the null hypothesis $H_0: \rho = 0.1$. For example, the correlation between subtraction and multiplication for the 28 third graders in the Royer data set is .594. The value of the t statistic with 26 df is $(.594)\sqrt{(1-.594)^2/26} = 3.77$. We can use Appendix Table C.3, or command 1-pt(3.77, 26) in R, to find the p-value is less .001. Therefore, we reject the null hypothesis that $H_0: \rho = 0$.

Power calculations for the null hypothesis $H_0: \rho = 0$ are readily performed with available software. G*Power 3.1 can calculate the sample size to obtain any desired level of power. Suppose we need the sample size to have power .80 for rejecting the null hypothesis $H_0=0$, using a two-tailed t test with $\alpha = .05$. Further suppose that we expect the population correlation to be "medium," $ho = .30$. Use G*Power 3.1 to calculate the desired sample size, select t tests as the Test family, and then select Correlation from the Tests menu to choose the Point biserial model.$^2$ For the type of power analysis, select a priori: Compute required sample size $p=.30, \alpha=.05$, power $=80$, and request a two-tailed test in the Input Parameters box. Now click on Calculate. G*Power 3.1 indicates to have power equal to .80, it is necessary to have sample size of N=82 (see Figure 18.3).

It is important to estimate this N so that we can decide whether it is worth the resources necessary to achieve a reasonable level of power. If we simply ahead