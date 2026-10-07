
![](img/53d3130502f4ff3b15cbe3697d6e8c5a_55_0.png)

## 2.3.5 The Interquartile Range (IQR)

One measure of spread deserves mention here. The value of the IQR, like the closely related H-spread of the box plot, provides a measure of spread that is more resistant to extreme scores than the standard deviation. Like the H-spread measure, IQR is a resistant statistic because it ignores scores in the tails of a distribution. The value of the IQR is the difference between the 25th and 75th percentiles; it is the range of the middle 50% of the data. Calculating percentiles usually requires interpolation between points, and there are several ways to do that (Hyman & Fan, 1996). In R, we can use the quantile function in `stats` to obtain the 25% and 75% percentiles for the Royer data in Table 2.1, 80.50 and 94.25, and then use subtraction to find the IQR = 94.25 - 80.50 = 13.75. Alternatively, the `stats` function provides the IQR in one step.

## 2.4 Standardized (z) Scores

An individual's score, by itself, is not very informative. If a student earns a score of 70 on a math test, is that good or bad? If told that a score of 70 was at the 90th percentile – that it had been exceeded by only 10% of all scores – we would probably feel that the performance was quite good. On the other hand, we would be considerably less impressed if the same raw score fell at the 40th percentile. Although information about percentile values tells us where a score ranks relative to other scores, it provides no information about distances among scores. For example, a score at the 90th percentile could be many points higher than the average or only a little higher; it depends on how variable the scores are. Standardized or z scores tell us more about where the score is located within the distribution, measured in units of the variability of the data. Specifically, a z score tells us how many standard deviation units the score is above or below mean. Given a distribution of scores with mean $\bar{Y}$ and standard deviation $s$, the z score corresponding to a score $Y$ is calculated as

```
$z_Y = (Y - \bar{Y})/s \quad (2.6)$
```

For example, if the mean is 75 and the standard deviation is 15, for a score of 90, we would have $z = (90-75)/15 = 1.0$; this score is one standard deviation above the mean. In $R$, the function in the (base) package computes $z$ scores for a set of data.

Standardizing a group of scores changes the scale to one of standard deviation units, permitting comparisons with scores that were originally on a different scale. Nevertheless, there are aspects of the original distribution that remain unchanged. The following are two things that remain constant:

- 1. An individual's $z$ score has the same percentile rank as that of original score. This is because subtracting a constant, $\bar{Y}$, from every score does not change the range of orders, nor is it dividing all scores by a constant, $s$.
- 2. The shape of the distribution of $z$ is the same as that of the original data. subtraction of $z$ shifts the original distribution and division by $s$ squeezes the points closer together, but shape is preserved. If the original distribution was symmetric, the distribution of $z$ scores will also be symmetric. Likewise, if the original distribution was skewed, the distribution of $z$ scores will be, too.

As we see in Chapter 5, $z$ scores are used in drawing inferences when scores can be assumed to be normally distributed. However, the preceding point should make clear that $z$ scores are not necessarily (or even usually) normally distributed. Their distribution depends on the distribution of the scores prior to the $z$ transformation.

Two other characteristics of $z$ (and therefore the sum) of a set of $z$ scores should be noted:

- 1. The mean of a set of $z$ scores is zero. We stated earlier that when a constant is subtracted from every score, the mean is also changed by constant. In case of $z$ score, $\bar{Y}$ is subtracted from each of the $Y$ values. Therefore, the mean of the $z$ scores is $\bar{Y}$, or 0.
- 2. The variance of a group of $z$ scores is 1.0, and therefore, so is the standard deviation. Because the average of $z$ score is zero, we need only square each member of the group of $z$ scores, sum the squared values, and divide by $n-1$ to obtain the variance, $S^2$. Doing so,

```
$s_z^2 = \sum\frac{(Y-\bar{Y})^2}{s^2} / (n-1) = \sum\frac{(Y-\bar{Y})^2}{n-1} / s^2 = s^2/s^2 = 1$
```

Describing the Data 37

Standardized scores can be useful in our understanding of a data set they provide a way of comparing performances on different scales. For example, the mean and standard deviation of the subtraction accuracy scores in the Royer data set were 88.40 and 11.57, respectively; the corresponding values for multiplication were 87.43 and 13.96. Standardized scores play other roles as well. In Chapter 5, we will discuss how z scores provide percentile information when the distribution has approximate shape. Also, in Chapter 18, we will consider the correlation coefficient as an average of z.

## 2.5 Measures of the Shape of a Distribution: Skewness and Kurtosis

We have considered several measures of location (mean, median, and mode) and variability (variance, standard deviation, standard error, and $IQR$) that summarize important properties of a distribution. In addition to these measures, it is also useful to obtain measures of the shape. Measures of shape permit a more precise description of a set than location and variability alone. They also provide another way to assess the assumption of normality. This is important because a data distribution departs markedly from normality, the mean and standard deviation may lead to incorrect inferences. For symmetric population distribution the sample mean is usually considered the best estimate of the location of the population distribution. However, if the population distribution has long tails, the sample median is more likely to have a value close to that of the center of the population (Rosenberger & Gasko, 1983), and therefore would be a better estimate of the location. If the population distribution is skewed (asymmetric), a transformation, or a test based on ranks, may be helpful (see Chapter 6 for a discussion of these alternatives).

There is a third reason for our interest in measures of shape. An important stage in understanding the processes that underlie the construction of mathematical or computational models, models precise enough to predict the behavior in question. Comparing predicted and observed measures of the shape of the data distribution provides additional tests of such models.

Two aspects of shape have received the most attention from statisticians: (1) the degree of skewness, or departure from symmetry; (2) kurtosis, the proportion of data in the extreme tails and peak of the distribution. Indices of these two attributes of shape can be obtained from various computer packages, although there are frequently small differences in the details of the calculation that can result in slightly different values, especially for smaller samples.

### 2.5.1 Skewness

Skewness statistics are designed to reflect departures from symmetry. The standard definition of skewness is the average cubed deviation of scores from the mean divided by the
