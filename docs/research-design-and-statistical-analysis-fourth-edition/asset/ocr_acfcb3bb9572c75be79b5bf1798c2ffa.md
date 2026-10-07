# 514 Research Design and Statistical Analysis

For example, in the statistics class example discussed in Chapter 17, the raw-score regression equation for predicting final score ($\hat{Y}$) from the pretest score (X) is $\hat{Y}=-36.083 + 3.546\hat{X}$ and the corresponding standardized regression equation is $\hat{z}_i=.725z_i$. The standardized coefficient $b_i$ is the change in $\hat{z}$ (in units of Y) to a one-unit increase in X. In the statistics class example, each increase of one point on the pretest corresponds to a predicted increase of 3.546 points on the final exam. The standardized coefficient is the change in $\hat{z}$, corresponding to an one-unit increase in $z_i$ — or, $b'_i$, is the change in $s_i$ corresponding to an increase of one $s_i$ in X. For the statistics class example, this means that one standard deviation in X corresponds to an increase of .725 in $\hat{z}_i$ (or, an increase of .725 $s_i$ in $\hat{Y}$).

For any given sample, the standardized and unstandardized coefficients will have the same sign, and their significance will yield identical results. Does one of these coefficients better characterize the nature of the relationship? Sources such as the publication of the American Psychological Association state that both the standardized and unstandardized coefficients should be reported in results. We have no problem however, unless we are specifically interested in changes stated in terms of standard deviations or in terms of relative standing, we will usually be better off with the unstandardized coefficients for the following reasons:

+   1. If the scales are meaningful, one-unit changes are more understandable than changes of one standard deviation.

+   2. If the scales are not meaningful or if there is a great deal of measurement error, the use of unit-free measures such as $R^2$ and standardized coefficients is more likely to obscure this fact. Standardizing poor will not help. As Achen (1977, p. 806) puts it, "To replace the unacceptable by making it unacceptable."

+   3. The standard deviations of X and Y in two separate samples will be different, so that standardized regression coefficients are sample specific in the same way as correlation coefficients. In fact, bivariate regression, the standardized regression coefficients are the correlation coefficients and therefore should not be used to compare across groups.

+   4. The standardized regression coefficient is equal to the unstandardized coefficient multiplied by $s_y/s_x$. Therefore, with two separate samples, A and B, we may find that the unstandardized coefficient is larger in A than in B because of differences in the standard deviations (see Exercise 19.5).

+   5. Finally, the standardized coefficient depends on the variance of all the variables that contribute to the error term and therefore to $s_{yy}$, whether they are not in the model, is less stable than the unstandardized coefficient when variances vary across samples.

# 19.7 Checking for Violations of Assumptions

Because our conclusions can be in error if there are severe violations of the assumptions, next discuss how to check for violations. First, we emphasize that if we try to understand our data, we should not rely on summary statistics like the correlation coefficient or the slope of the regression line. It is also important to plot the data and to use the diagnostics that are usually provided by statistical software. In Figure 17.10, we presented scatterplots for four very different data sets that have identical values of N,