Table 2 presents a detailed summary of the attributes of the dataset through descriptive statistics. The dataset's minimum value, 9.530611, represents the lowest observed value. 25% of the data is below the value of 9.860006 at the 25th percentile. The average, which denotes the dataset's average value, is determined to be 9.929916. At 0.106237, the standard deviation, which quantifies the range of values around the mean, is rather low. The midway value of the dataset is represented by the median, or 50th percentile, which is found at 9.935374. Turning now to the 75th percentile, 75% of the data is below the 10.007803 threshold. At 33065.91, the dataset's maximum value is noticeably high. Last but not least, the distribution's skewness, or asymmetry, is somewhat positively skewed at 0.36336, implying a tail that extends to higher values. When taken as a whole, these statistics offer insightful information about the distributional features and attributes of the dataset, facilitating comprehension of its shape, central tendency, and dispersion.

# Trend Analysis Results

The trend that was extracted from the hourly thermal production data using classical decomposition, a statistical method for finding fundamental recurring trends in a time series data set is depicted in Figure 3. This finding confirms that the trend that was seen over the chosen sample period is waning. This pattern of decline suggests a gradual decrease or reduction in the amount of heat generated over time. Decisions on thermal scheduling, allocation of resources, and infrastructure development can be influenced by these insights, which are crucial for grasping the long-term patterns and efficacy of thermal energy-producing systems (Smith and Johnson, 2020).

The Mann-Kendall test findings for the variable of electricity demand are displayed in Table 3. The power demand for the observed time appears to have had a substantial decrease trend, as indicated by the Mann-Kendall test statistic of -114.7675. Kendall's Tau coefficient of -0.3750, which shows a high negative connection between time and electricity usage, lends more evidence to this. The observed trend is statistically significant, as indicated by the Mann-Kendall test p-value of 0.001, which is less than the 0.05 traditional level of significance. Sen's slope estimator, which has a value of -0.0882, also offers an estimate of the rate at which electricity consumption changes over time. The results of the Mann-Kendall test are supported by this negative figure, which points to a declining trend in power demand. All things considered, these findings point to a notable decline in the demand for energy within the studied time frame.

We extract a nonlinear trend by fitting the cubic smoothing spline function with cubic smoothing spline constraints represented by the equation;

```
min_g p * \sum_{i=1}^{n} (y_i - g(x_i))^2 + (1 - p) * \int (g^{..}(x_i))^2 dx, p \in [0, 1]. (1.7)
```

# Table 2. Descriptive statistics

| Min | 25% | Mean | sd | 50% | 75% | Max | Kurtosis | Skewness |
|---|---|---|---|---|---|---|---|---|
| 9.530611 | 9.860006 | 9.929916 | 0.106237 | 9.935374 | 10.007803 | 33065.91 | -0.02405 | 0.36336 |