section, we explore the options available after a linear regression is performed on the data. The difference is that we now have residuals to work with. Techniques involving quantile–quantile (QQ)-plots and ordered absolute residuals can be employed to accurately detect outliers. Additionally, more effective methods can be used to surgically remove them. In particular, a new method using an iterative boxplot approach is described to enable the removal of outliers while keeping inliers intact.

# 4.6.1 LS vs. LC Residuals

As mentioned earlier, using input/output variables may not be effective in outlier detection. In this section, we show that residuals have the needed information to diagnose outliers in a dataset. Recall that the residuals are simply the difference between the true response and the predicted response for all observations. The residuals for linear regression can be computed after estimation using a general equation given by

$r_i = y_i - \hat{y}_i, \quad i = 1, \dots, n, \quad (4.6.1)$

where \(y_i\) is the true response and \(\hat{y}_i\) is the predicted value based on the regression model. Typically, outliers in the dataset have large residuals whereas inliers have small residuals. Therefore, it is possible to tell them apart by their relative positions in a residual histogram. Regardless of its size, outliers will always be positioned at one extreme or the other. The question is, should we use LS residuals or LC residuals for the task at hand?

To answer this question, consider Figure 4.12 which plots the histograms for the residuals of LS and LC of Figure 4.2(d) from the Belgian telephone dataset. For LS residuals, it is difficult to tell whether or not there are outliers since the distribution appears to be Gaussian. However, for the LC residuals, it is clear that there are six outliers. Therefore, the residuals from a robust regression contain the information needed to diagnose outliers using the histogram.

More evidence that residuals from LS should not be used to detect outliers can be found from boxplots. In Figure 4.13, we show the residuals of LS and LC from the diabetes dataset in boxplot form. The dataset

![](bbox=[0.109, 0.643, 0.838, 0.878])

Figure 4.12 Histograms of LS and LC residuals based on Figure 4.2(d).