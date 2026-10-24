![](bbox=[0.285, 0.115, 0.735, 0.49])

# FIGURE 2.3
Boxplot for the unit price data for items sold at four branches of an online store during a given time period.

**Example 2.11. Boxplot.** Fig. 2.3 shows boxplots for unit price data for items sold at four branches of an online store during a given time period. For branch 1, we see that the median price of items sold is $80, Q1 is $60, and Q3 is $100. Notice that two outlying observations for this branch were plotted individually, as their values of 175 and 202 are more than 1.5 times the IQR here of 40.

# *Variance and standard deviation*

Variance and standard deviation are measures of data dispersion. They indicate how spread out a data distribution is. A low standard deviation means that the data observations tend to be very close to the mean, whereas a high standard deviation indicates that the data are spread out over a large range of values.

The variance of N observations, x1, x2, ..., xN (when N is large), for a numeric attribute X is

```
\sigma^2 = \frac{1}{N} \sum_{i=1}^N (x_i - \bar{x})^2 = \left( \frac{1}{N} \sum_{i=1}^N x_i^2 \right) - \bar{x}^2, \quad (2.6)
```

where \bar{x} is the mean value of the observations, as defined in Eq. (2.1). The standard deviation, \sigma, of the observations is the square root of the variance, \sigma^2.