

# Box Plots

Box plots help divide observations into defined intervals called **quartiles** and compare them with the entire observation. It represents the data as the 25th, 50th, and 75th quartiles. It consists of a body (the interquartile range, IQR) where most observations are concentrated. The whiskers or lines represent the maximum and minimum values. Points outside the whiskers are considered **outliers**.

[Figure 2.1](#c02.xhtml#c02-fig-0001) shows a box plot.

![Figure 2.1 Box plot showing quartiles](images/c02f001.png)

[**Figure 2.1**](#c02.xhtml#R_c02-fig-0001) Box plot showing quartiles

## Line Plots

Line plots plot the relationship between two variables to analyze trends in data over time.

[Figure 2.2](#c02.xhtml#c02-fig-0002) shows a line plot.

![Figure 2.2 Line plot](images/c02f002.png)

[**Figure 2.2**](#c02.xhtml#R_c02-fig-0002) Line plot

## Bar Plots

Bar plots are used to analyze data trends and compare categorical data, such as weekly sales figures, website visitor counts, or monthly product revenue.

[Figure 2.3](#c02.xhtml#c02-fig-0003) shows a bar plot.

![Figure 2.3 Bar plot](images/c02f003.png)

[**Figure 2.3**](#c02.xhtml#R_c02-tbl-0003) Bar plot

## Scatter Plots

Scatter plots are the most commonly used plots in data science, primarily used to visualize clusters in datasets and show the relationship between two variables.

# Statistics Basics

In statistics, we have three measures of central tendency: mean, median, and mode. They help us describe data and can be used to clean data from a statistical perspective.

## Mean

The mean is an accurate measure to describe data when there are no outliers present in the data.

## Median

The median is used when there are outliers in the dataset. You can find the median by arranging the data values from low to high.

If the number of data points is even, the median is the average of the two middle numbers; if odd, the median is the middle value. For example, in the dataset 1, 1, 2, 4, 6, 6, 9, the median is 4. For the dataset 1, 1, 4, 6, 6, 9, the median is 5. Take the average of 4 and 6, which is `(4+6) / 2 = 5`.

## Mode

The mode is used when there are outliers and most of the data is the same. The mode is the value or values that appear most frequently in a dataset.

For example, for the dataset 1, 1, 2, 5, 5, 5, 9, the mode is 5.

## Outlier Detection

The mean is a measure of central tendency affected by outliers, which in turn affects the standard deviation.

For example, consider the following small dataset:

*   `[15, 18, 7, 13, 16, 11, 21, 5, 15, 10, 9, 210]`

It is visible to the naked eye that 210 is an outlier far greater than the other values.

As shown in [Table 2.1](#c02.xhtml#c02-tbl-0001), adding the outlier caused a significant change in the mean compared to the median and mode. **Variance** is the average of the squared differences from the mean.

[**Table 2.1**](#c02.xhtml#R_c02-tbl-0001) Mean, Median, and Mode for Outlier Detection

| With Outlier | Without Outlier |
| --- | --- |
| Mean: 12.72 | Mean: 29.16 |
| Median: 13 | Median: 14 |
| Mode: 15 | Mode: 15 |

## Standard Deviation

Standard deviation is the square root of variance. Standard deviation is an excellent method for identifying outliers. Data points that are more than one standard deviation away from the mean can be considered outliers.

## Correlation

Correlation is simply a standardized form of covariance. The value of the correlation coefficient ranges from -1 to +1. The correlation coefficient is also known as the Pearson correlation coefficient.

*   **Positive Correlation** When the value of one variable increases, the value of the other variable increases correspondingly; this is called **positive correlation**.
*   **Negative Correlation** When the value of one variable increases, the value of the other variable decreases correspondingly; this is called **negative correlation**.
*   **Zero Correlation** When the change in the value of one variable has no substantial effect on the other variable, it is called **zero correlation**.

# Data Quality and Reliability

The quality of a model depends on the quality and reliability (or feasibility) of the data. Model quality also depends on the scale of the training data.

**Reliability** is the degree to which you can trust the data. If data is unreliable, it means it contains missing values, duplicate values, and bad features; you can think of it as dirty data. If you train a model on dirty data, you are unlikely to get useful predictions. To ensure data reliability, you can do the following:

*   Check for label errors, as they are sometimes manually annotated and prone to errors.
*   Check for noise in features, such as GPS measurements.
*   Check for outliers and data skew.

When collecting data, it is important to have a concrete definition of quality. We will discuss several parameters of data quality in the following sections.

## Data Skew

**Data skew** occurs when the normal distribution curve is asymmetrical, causing the data to be skewed. This means there are outliers in the data or the data distribution is uneven.

A normal distribution has a skewness of 0.

Data can be right-skewed or left-skewed (see [Figure 2.4](#c02.xhtml#c02-fig-0004)). You can analyze skewness by understanding statistical measures of the dataset, such as mean, median, and standard deviation.

![Figure 2.4 Data skew](images/c02f004.png)

[**Figure 2.4**](#c02.xhtml#R_c02-fig-0004) Data skew

For right-skewed data, a real-world example could be income data, because most people have average incomes, while only 0.01% of people earn more than the rest of the population (such as billionaires like Jeff Bezos), resulting in outliers or right skew.

Skewed data is not good for model performance because extreme outliers affect the model's predictive ability. Through various transformations such as log transformation and normalization, you can convert a skewed distribution into a normal distribution by removing outliers. If the target variable has skew, you can use Synthetic Minority Over-sampling Technique (SMOTE), undersampling, or oversampling.

## Data Cleaning

The goal of normalization is to transform features to a similar scale. This improves model performance and training stability. (See `https://developers.google.com/machine-learning/data-prep/transform/normalization`.)

## Scaling

Scaling refers to converting floating-point feature values from their natural range into a standard range—for example, from 1,000–5,000 to 0 to 1 or -1 to +1. Scaling is very useful when the feature set contains multiple features. It has the following advantages:

*   In deep neural network training, scaled features allow gradient descent to converge better than unscaled features.
*   Scaling eliminates the possibility of "NaN traps" because every value is scaled into a numerical range.
*   Without scaling, the model pays undue attention to features with wider numerical ranges.

## Log Scaling

Log scaling is used when some data samples follow a power-law distribution or have extremely large values. For example, when some samples are 10,000 while others are in the 0–100 range, you would use log scaling.

Taking the log brings them to the same range. For example, `log(100,000) = 100` while `log(100) = 10`. Thus, your data will be adjusted to the 0 to 100 range through log scaling.

## Z-Score

This is another scaling method where values are calculated as the number of standard deviations away from the mean. When you have a few outliers, calculate the Z-Score as follows:

*   `Scaled value = (value − mean) / stddev`

For example, given

*   `Mean = 100`
*   `Standard deviation = 20`
*   `Original value = 130`

The scaled value is 1.5. Z-Scores lie between -3 and +3, so any value outside this range will be an outlier.

