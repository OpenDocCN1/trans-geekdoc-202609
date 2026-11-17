using the three methods. In all cases, LC regression was used to obtain the residuals. All three methods show that there are no outliers in the Swiss dataset. For the diabetes dataset, only the 1.5-IQR method produced the correct result. The other two methods could not determine the number of outliers accurately. For the Boston Housing data, the 3-sigma edit rule performed badly compared to the other methods. The 4.5-MAD and 1.5-IQR methods produced similar results, although we will find later that there are more outliers than these numbers indicate. The main conclusion here is that the 1.5-IQR approach is the most effective one when combined with LC residuals.

# 4.6.3 Ordered Absolute Residuals (OARs)

Aside from histograms and boxplots, there are a number of other ways to visually diagnose a dataset for outliers. One useful approach is to plot the absolute values of the residuals in sorted order from smallest to largest. A large residual is indicative of an outlier whether it be positive or negative. The notation used when ordering a set of values from smallest to largest is to place parentheses around the subscript of the variable. If we have a set of values in random order, such as x_1, ..., x_n, then x_{(1)}, ..., x_{(n)} are referred to as the order statistics. When we take the absolute value of the quantities and then order them, we use the notation, |x|_{(1)}, ..., |x|_{(n)} for the absolute order statistics.

Exercise: Given x_1 = 0.4, x_2 = -0.6 and x_3 = 1.7, find the order statistics and then the absolute order statistics.

Ans.: The order statistics are given by x_{(1)} = -0.6, x_{(2)} = 0.4, and x_{(3)} = 1.7. The absolute order statistics are given by |x|_{(1)} = 0.4, |x|_{(2)} = 0.6, and |x|_{(3)} = 1.7.

Consider Figure 4.14 showing the ordered absolute residuals from the Belgian telephone dataset based on Figure 4.2(d) for both LS and LC cases. There are a total of 24 residuals in each case. We plot the absolute order statistics of the residuals from |r|_{(1)} to |r|_{(24)}, using an index from 1 to 24 along the x-axis. The LS residuals produce a plot that makes it difficult to separate outliers from the rest of the data points. This is because LS forces the residuals to have a Gaussian distribution which tends to blur the distinction

![](bbox=[0.1, 0.67, 0.9, 0.845])

Figure 4.14 Ordered absolute residual plots of LS and LC estimators.