# 28 Research Design and Statistical Analysis

![](bbox=[0.118, 0.096, 0.881, 0.289])

Figure 2.3 Normal probability (Q–Q) plots of multiplication response times and speeds.

We might ask whether the departures from the straight line that we observe are large enough to affect subsequent inferential analyses. We will have more to say about this and its implications for data analysis in Chapter 6, which we discuss the t test and its assumptions.

# 2.3 Numerical Summaries of the Data

A graph provides an immediate picture of the overall shape of a distribution, the variability in the observations, and whether there are outliers in the data. Additionally, box plots provide specific information about the location of the distribution (i.e., the median); box plots provide a specific measure of variability, too (i.e., the H-spread). Numerical estimates of specific characteristics of the data are very useful in helping us understand a data set. Further, some measures are more prominent in inferential procedures, most notably the mean and standard deviation. Thus, in this section, we focus on the mean and measures of variability that complement the mean; the standard deviation, variance, and standard error of the mean.

Most statistical packages provide several useful descriptive statistics for a data set. For example, the data of Table 2.1 were submitted to the Explore module in SPSS to generate the statistics. Similarly, the R function been in [stats] package provides five five number: minimum, lower hinge, median, upper hinge, and maximum. R has many functions for summarizing data, such as mean and median, that can be applied to vectors of data individually or to several simultaneously. For example, the summary function in the [base] package provides descriptive statistics on each variable in a data frame. We will also make use of the summarise function in [dplyr] to calculate specific summary statistics.

# 2.3.1 Measures of Location: Mean, Median, and Mode

When we talk about the location of the data, we are referring to its central tendency: what values are typical, or near the middle of the data set? We have already met one measure of location, the median, which is the value above which, and below which, half of the data fall. The median value may not be represented in the data. For example, the median of Y = [1, 3, 9, 10, 11] is 6, the average of the two middle scores, 3 and 9. The mode describes