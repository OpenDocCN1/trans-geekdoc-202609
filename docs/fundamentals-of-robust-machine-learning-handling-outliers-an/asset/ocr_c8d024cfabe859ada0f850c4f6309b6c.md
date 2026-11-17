![](bbox=[0.11, 0.105, 0.87, 0.59])

Figure 4.5 Boxplots can be used to check for outliers in all variables for the Boston housing dataset.

# ## 4.4 Outlier Detection

After the preliminary diagnosis phase is complete, if we know that the dataset has outliers, we can move to the outliers detection phase (see Aggarwal 2017). Here, we are interested in the number of outliers in the dataset. In this section, three well-known methods are described. Note that methods for counting outliers are described in this section, whereas removing the detected outliers will be described in the next section.

# ### 4.4.1 3-Sigma Edit Rule

The 3-sigma edit rule is probably the most widely known method of outlier detection for data distributed as a Gaussian. The idea is that any data points more than 3 standard deviations away from the mean are counted as outliers. This is a sensible approach since 99.7% of the data lies within ±3σ of the mean, μ, for the normal distribution. Figure 4.8 shows a Gaussian distribution, labeled “true distribution,” along