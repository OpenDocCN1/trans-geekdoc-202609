# 7.5.4 Time series bootstrapping

Time series bootstrapping is a method of resampling that uses the past data points of a time series to simulate new data points. This method is used by data scientists to explore the variance and predict future trends in the data. Bootstrap samples are generated from the series of past data points by selecting random data points with replacement and are then used in various statistical tests [27]. This method is especially useful when the data set is too small to provide accurate or reliable results. By generating a bootstrap sample from the original data, the variance and potential trends can be explored, and realistic predictions can be made.

# 7.5.4.1 Extending bootstrapping to time series data

A method known as extending bootstrapping to time series data makes use of resampling to reveal patterns in the behavior of a time series while taking into consideration its complexity. By selecting replacement samples at random from a data set, the resampling approach known as “bootstrapping” can estimate the distribution of a statistic. It is frequently used to replicate the uncertainty surrounding a statistic, allowing us to draw conclusions about the population’s unknowable values.

When applied to time series data, it creates simulated time series that reflect the underlying distribution of the actual time series to be tested [28]. It can be used to assess the reliability of an estimate, identify potential outliers, provide insights into the structure of the time series, and allow comparison between multiple time series. By simulating future values of a time series, it can also be used to predict future values and analyze their stability.

# 7.5.4.2 Block bootstrap and stationary bootstrap methods

Block bootstrap and the stationary bootstrap are two methods of sampling data that can be used to create a larger set of data for analysis and prediction. Block bootstrap is a method of sampling data that breaks the original dataset into smaller blocks called bootstrap replicates. This allows for the creation of a larger sample from the original dataset. The advantage of this methodology is that the original dataset tends to be preserved in the blocks, since each block will contain some of the original \$mu\$ variability.

The stationary bootstrap is a sampling technique that preserves the structure of the original data. This is done by sampling random points in the data, and assigning them to a new sample set. When the underlying generation method of the data is sufficiently varied and applicable to a wide range of data, it is valuable. It permits the generation of numerous distinct samples from a single initial dataset while maintaining the original \$mu\$ variability.