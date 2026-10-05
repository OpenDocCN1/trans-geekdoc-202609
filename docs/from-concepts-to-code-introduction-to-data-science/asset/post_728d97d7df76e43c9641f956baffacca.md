
![](img/7f40a2246fd3d2d5353d109f489c4e33_182_0.png)

# 9 Statistics Preliminaries

To save on resources (time, money, etc.) we draw samples of data from a population of size $N$. A statistic is a quantity computed from a data sample. The hope is that the statistic is representative of the population. As data science is grounded in the collection and analysis of data samples, we have a great need to work with statistics. This section will provide a summary of descriptive statistics and inferential statistics. Descriptive statistics are useful for understanding properties of a data sample. Inferential statistics allow for drawing conclusions about a population based on a sample. A common question in inference, for example, is whether a predictor's coefficient is significantly different from zero; if so, this indicates that the predictor is important.

## 9.1 Descriptive Statistics

Our samples will be drawn from random variables which may be discrete or continuous. Each variable may take a single value at one extreme to an unbelievably large number of values at the other extreme. As the sample size grows, it becomes impossible to look at all of the data and understand its distribution. Computing statistics will help in summarizing this data, and we outline different statistics in what follows.

### Frequency Count

For data with low cardinality (say below 50 unique levels), we can count the number of times each value is taken. These occurrences can be called frequency counts or simply counts. It is also useful to calculate the percentage of times each value is taken. The values with their percentages are then equivalent to the probability mass function. For example, given observed data $S = (1, 1, 1, 2, 3, 5000)$, the values and associated counts are $F = (1 : 3, 2 : 1, 3 : 1, 5000 : 1)$. The values, counts, and percentages can be assembled in a table like this:

| value | count | percent(%) |
|---|---|---|
| 1 | 3 | 50.0 |
| 2 | 1 | 16.7 |
| 3 | 1 | 16.7 |
| 5000 | | 16.7 |
| **Total** | **6** | **100** |

For data with high cardinality, the values can be placed into bins, and then counts and percentages can be computed for each bin. This is what is done when creating a histogram. The table below summarizes counts and percentages for a large number of values measured to the thousandths place, such as 0.412 and 15.749. The bin will contain values including the left endpoint of 0 and excluding the right endpoint of 5.

| bin | count | percent(%) |
|---|---|---|
| [0,5) | 525 | 40 |
| [5,10) | 173 | 25 |
| [10,15) | 298 | 15 |
| [15,20) | 97 | 18 |
| [20,25) | 45 | 2 |
| **Total** | **1138** | **100** |

For a large number of bins, the data distribution can be better understood with a graph of the bins on the x-axis and their occurrences on the y-axis (as in a vertical bar chart).

### Central Tendency

The central tendency or center of the data is one of the most common and useful attributes. It can be measured by the variable: mode, median, or mean. The mode is the most common value taken by the variable. Frequent counts as in $F$, the mode is equal to the key with highest value (1 in this case). The mode will not be influenced by outliers, as they are rare by definition. A shortcoming of the mode is that it is purely frequency based.

The median is the value in the "middle" of the data. To be more precise, we can define the $p$th percentile of the data. The median is defined as the 50th percentile of the data; half of the values are above and below the median. For an odd number of data points, this can be found by sorting the values and taking the middle point. For an even number of data points, the median is computed as taking the midpoint of the two middle values. For the example $S$, the median will be 1.5, which is the midpoint of 1 and 2. Like the mode, the median is not influenced by outliers. The median gives a better estimate of center since it uses the ranking of values.

### Descriptive Statistics

The average or sample mean of the data applies equal weight to each observation in estimating where the data "balances." It is a statistic that estimates the population mean, denoted $\mu$. The sample mean is computed by summing the values and dividing by the number of observations $n$. For values $x_1, x_2, \dots, x_n$ drawn from random variable $X$, the formula is

$$\bar{x} = \frac{\sum_{i=1}^{n} x_i}{n}$$

Extreme outliers will have a large influence on the sample mean; for measuring the center in such a case, the median will be better. From our example $S$, the sample mean is approximately 85 due to the large outlier. While this value might give a sense of where the data balances, it does not represent most of the data. When we see the median and sample mean together for a dataset, their similarity or difference provides additional information. When the two statistics are similar, this indicates symmetry in the data distribution. When the sample mean is much larger (smaller) than the median, this indicates one or more (small) outliers.

### Spread

The dispersion or spread of the data gives how the values are distributed about a central value. For a spread of zero, all values would be the same; such variable would not be random at all. The mean is a measure of the variable's uncertainty, and several statistics are used: the range, the interquartile range (IQR), the variance, and the standard deviation.

The range is the difference between the maximum and minimum values of the data. It is simple to calculate and intuitive, but influenced by outliers, as we see with our data $R = 5000 - 1 = 4999$.

For measuring the interquartile range, we first sort the data from highest to lowest and divide the sorted values into four equal parts, quartiles. The lowest quartile of the data ranges from the minimum to Q1 (the 25th percentile), the second quartile ranges from Q1 to Q2 (the 50th percentile), the third quartile ranges from Q2 to Q3 (the 75th percentile), and the fourth quartile ranges from Q3 to the maximum.

The interquartile range is calculated as $Q3 - Q1$, which represents the range covered by the middle 50% of the data. Since it removes the highest and lowest 25% of the data, it is not sensitive to outliers. For our data sample, $IQR(S) = 2.7 - 1.0 = 1.7$. This is substantially lower than the range.

A five-number summary is very common and useful for reducing a data distribution to five statistics, namely the minimum, Q1, median, Q3 and maximum. These numbers can be depicted graphically with a boxplot in Figure 9.1. The example boxplot randomly generated data following a standard normal distribution. Notice that the median does not necessarily need to place in the middle of the boxplot.

![](img/7f40a2246fd3d2d5353d109f489c4e33_186_0.png)

Here is a list of the boxplot components:

- The leftmost vertical line (lower whisker) represents the minimum
- The left side of the box represents Q1
- The range from the minimum to Q1 represents the lowest 25% of the data, or first quartile
- The left portion of the box represents the second quartile
- The vertical line in the box represents the median
- The right portion of the box represents the third quartile
- The right side of the box represents Q3
- The box represents the middle 50% of the data
- The upper whisker represents the maximum
- The range from Q3 to the maximum represents the fourth quartile

Another variant of the boxplot draws whiskers at a distance of $1.5 \times IQR$ from Q1 and Q3. Data beyond these whiskers are outliers and plotted as points. This is done in Python, for example. The code to generate the data and boxplot are shown in the following code snippet. The parameter *whis* is set to a high level to create the boxplot with whiskers at the minimum and maximum as in the first approach.
