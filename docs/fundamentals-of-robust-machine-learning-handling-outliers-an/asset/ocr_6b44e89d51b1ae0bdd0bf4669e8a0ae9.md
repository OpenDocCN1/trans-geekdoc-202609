# ## 7.2 Understanding Quantile Regression

At a very basic level, quantile regression serves as a natural extension of robust linear regression. Unlike the usual form of robust regression, which seeks a single line dividing the data in half, quantile regression allows us to divide the data using any desired percentile, decile, or quartile. The term “quantile” encompasses all possible cases and is typically specified as a value between 0.0 and 1.0.

Consider Figure 7.1, which displays a scatter plot of a dataset along with different regression lines representing various quantiles. Notably, the data exhibits heteroscedasticity—a phenomenon where the spread of data widens like a cone as the explanatory variable increases. This implies that the variance increases proportionally. Such heteroscedasticity has implications for the quality and reliability of statistical procedures. In standard regression, we assume homoscedasticity, meaning that the standard errors remain consistent as we move along the x-axis. However, this assumption may not hold in cases like the one in Figure 7.1. Quantile regression, with its flexibility, becomes well suited for addressing such issues, as a single regression line may not adequately capture the true characteristics of the data.

Each set of estimates from a quantile regression produces a line in Figure 7.1 that divides the data based on the specified value of a quantile parameter \(\tau \in [0, 1]\).

+   - For \(\tau = 0.0\), we obtain the 0th percentile line located just below all the data points.
+   - For \(\tau = 1.0\), the 100th percentile line is located just above all the points.
+   - For \(\tau = 0.5\), the 50th percentile line divides the data in half.
+   - Other lines shown are for the 10th (\(\tau = 0.1\)), 25th (\(\tau = 0.25\)), 75th (\(\tau = 0.75\)), and 90th (\(\tau = 0.9\)) percentiles.

Note that as \(\tau\) increases from 0 to 1, the slope of the line gets steeper as more points fall below it. Essentially, the line sweeps through the points in the radial direction (indicated by the arrow) as \(\tau\) goes

![](bbox=[0.165, 0.6, 0.555, 0.86])

**Figure 7.1** Quantile regression for different percentiles, deciles, and quartiles.