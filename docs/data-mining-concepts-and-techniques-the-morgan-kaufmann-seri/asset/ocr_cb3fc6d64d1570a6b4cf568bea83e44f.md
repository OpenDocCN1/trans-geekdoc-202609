Data in most real applications are not symmetric. They may instead be either **positively skewed**, where the mode occurs at a value that is smaller than the median (Fig. 2.1b), or **negatively skewed**, where the mode occurs at a value greater than the median (Fig. 2.1c).

# ## 2.2.2 Measuring the dispersion of data

We now look at measures to assess the dispersion or spread of numeric data. The measures include range, quantiles, quartiles, percentiles, and the interquartile range. The five-number summary, which can be displayed as a boxplot, is useful in identifying outliers. Variance and standard deviation also indicate the spread of a data distribution.

# ### Range, quartiles, and interquartile range

To start off, let's study the *range*, *quantiles*, *quartiles*, *percentiles*, and the *interquartile range* as measures of data dispersion.

Let \(x_1, x_2, \dots, x_N\) be a set of observations for some numeric attribute, \(X\). The **range** of the set is the difference between the largest (max()) and smallest (min()) values.

Suppose that the data for attribute \(X\) are sorted in ascending numeric order. Imagine that we can pick certain data points so as to split the data distribution into equal-size consecutive sets, as in Fig. 2.2. These data points are called **quantiles**. **Quantiles** are points taken at regular intervals of a data distribution, dividing it into essentially equal-size consecutive sets. (We say “essentially” because there may not be data values of \(X\) that divide the data into exactly equal-size subsets. For readability, we will refer to them as equal.) The \(k\)th \(q\)-quantile for a given data distribution is the value \(x\) such that at most \(k/q\) of the data values are less than \(x\) and at most \((q - k)/q\) of the data values are more than \(x\), where \(k\) is an integer such that \(0 < k < q\). There are \(q - 1\) \(q\)-quantiles.

The 2-quantile is the data point dividing the lower and upper halves of the data distribution. It corresponds to the median. The 4-quantiles are the three data points that split the data distribution into four equal parts; each part represents one-fourth of the data distribution. They are more commonly referred to as **quartiles**. The 100-quantiles are more commonly referred to as **percentiles**; they divide

![](bbox=[0.28, 0.65, 0.72, 0.82])

**FIGURE 2.2**
A plot of the data distribution for some attribute \(X\). The quantiles plotted are quartiles. The three quartiles divide the distribution into four equal-size consecutive subsets. The second quartile corresponds to the median.