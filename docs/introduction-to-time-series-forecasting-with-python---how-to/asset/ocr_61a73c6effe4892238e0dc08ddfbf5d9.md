Listing 30.12: Density plots of the Boston Robberies dataset.

Run the example and review the plots. Some observations from the plots include:

+   • The distribution is not Gaussian.

+   • The distribution is left shifted and may be exponential or a double Gaussian.

![](bbox=[0.14, 0.26, 0.81, 0.64])

Figure 30.2: Density plots of the training set for the Boston Robberies dataset.

We may see some benefit in exploring some power transforms of the data prior to modeling.

# 30.5.4 Box and Whisker Plots

We can group the monthly data by year and get an idea of the spread of observations for each year and how this may be changing. We do expect to see some trend (increasing mean or median), but it may be interesting to see how the rest of the distribution may be changing. The example below groups the observations by year and creates one box and whisker plot for each year of observations. The last year (1974) only contains 10 months and may not be a useful comparison with the other 12 months of observations in the other years. Therefore only data between 1966 and 1973 was plotted.