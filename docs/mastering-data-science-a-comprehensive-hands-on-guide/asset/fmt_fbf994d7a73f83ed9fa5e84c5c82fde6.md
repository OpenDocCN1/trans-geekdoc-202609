
Statistics is the branch of mathematics that deals with the collection, organization, analysis, interpretation, and presentation of data. It provides tools and methods to make sense of data, identify patterns, and draw meaningful conclusions. In essence, statistics is the science of learning from data and making decisions under uncertainty.

## Types of Statistics
Statistics is broadly divided into Descriptive Statistics and Inferential Statistics. Each serves a different purpose in data analysis.

### 8.1.1 Descriptive Statistics
Descriptive statistics summarizes and organizes data in such a way as to describe its major characteristics. These techniques give a broad overview of the data, which helps to understand better its characteristics.

Key Concepts in Descriptive Statistics:
The key concepts included in descriptive statistics are measures of central tendency, measures of dispersion, and visualization tools since descriptive statistics is often used in summarizing and organizing data to highlight their main features.

Measures of central tendency describe the center of a data set. The mean is just the average value: it's the sum of all the data points divided by the number of points. For example, for the data set \[2, 4, 6\], the mean is (2+4+6)/3 = 4. The median represents the middle value when the data are sorted. For example, the median of \[1, 3, 5\] is 3. The mode is the most common value, for example, 2 in \[1, 2, 2, 3\].

Measures of dispersion give information about the spread or variability of data. The range refers to the difference between the maximum and minimum values. For example, in the list \[3, 7, 10\], the range is 10 - 3 = 7. Variance is a measure of how far the data points are spread out from the mean; the standard deviation, on the other hand, is simply the square root of the variance and indicates, on average, how far apart data points are from the mean.

Lastly, such visualization tools as histograms, bar charts, and scatter plots are typical for descriptive statistics—making it much easier to perceive patterns and distributions. These present a compact overview of leading features in the data.

Example of Descriptive Statistics:
If a class of students scores \[70, 85, 90, 75, 80\] in a test:
Mean: (70 + 85 + 90 + 75 + 80)/5 = 80
Median: 80 (middle value when sorted)
Range: 90 - 70 = 20

### 8.1.2 Inferential Statistics
Inferential statistics involve making predictions, decisions, or inferences about a population based on a sample of data. It uses probability theory to generalize findings and assess the likelihood of certain outcomes.

Key Concepts in Inferential Statistics:
Key concepts in inferential statistics include population versus sample, hypothesis testing, confidence intervals, p-values, and regression analysis. The population refers to the entire group being studied, such as all residents of a city. In contrast, a sample is a subset of the population used for analysis. For example, surveying 500 residents out of the entire city population provides a sample.

Hypothesis testing determines whether there is enough evidence to accept or reject a hypothesis. For instance, researchers may test if a new drug is more effective than an existing one. Confidence intervals offer a range of values to estimate the true population parameter. For example, "the average height of students is between 5.5 and 6.0 feet with 95% confidence."

The p-value measures the probability of observing results as extreme as the current data, assuming the null hypothesis is true. Regression analysis studies the relationships between variables and can be used for predictions, such as estimating house prices based on factors like area and location. These concepts form the foundation of inferential statistics, enabling researchers to draw meaningful conclusions from data.

Example of Inferential Statistics:
A company surveys 1,000 customers out of a population of 10,000 to determine customer satisfaction. Based on the sample, they infer that 80% of the customers are satisfied.

### 8.1.3 Comparison of Descriptive and Inferential Statistics

| Aspect || Descriptive Statistics || Inferential Statistics |
| --- | --- | --- |
| Purpose || Summarizes data. || Draws conclusions about a population based on a sample. |
| Focus || Entire dataset (e.g., mean, median). || Predictions and hypotheses. |
| Methods || Mean, median, mode, range, standard deviation. || Confidence intervals, p-values, regression analysis. |
| Example || Average height of students in a class. || Predicting the average height of all students in a school. |

### Why Study Statistics?
Statistics is essential in various fields, including:
• Business: Analyzing sales data to improve strategies.
• Medicine: Testing the effectiveness of new treatments.
• Social Sciences: Conducting surveys and polls.
• Sports: Evaluating player performance and team strategies.

In conclusion, statistics bridges the gap in data and decision-making. While descriptive statistics summarizes and helps to understand data, inferential statistics allows making predictions and inferences about a population at large. Mastering these two types of statistics is fundamental to an efficient analysis and interpretation of data.

# 8.2 Mean, Median, Mode
Mean, median, and mode are statistical measures that represent the central tendency or "average" of a dataset. They summarize a dataset by identifying a central point around which the data is distributed.

## 8.2.1 Mean
The mean, often referred to as the average, is calculated by dividing the sum of all values in a dataset by the total number of values.

Formula: Mean = Sum of all values / Total number of values

Example: Consider the dataset: \[2,4,6,8,10\]
• Sum of values: 2+4+6+8+10=30
• Number of values: 5
• Mean: 30 / 5 =6

When to Use: The mean is useful when the data is evenly distributed without extreme outliers, as it is sensitive to such outliers.

Example with Outlier: Dataset: \[2,4,6,8,100\]
Mean: (2+4+6+8+100) / 5 = 24 Here, the outlier (100) significantly skews the mean, making it less representative of the central tendency.

## 8.2.2 Median
The median is the middle value in a sorted dataset. If the dataset has an odd number of values, the median is the exact middle value. If it has an even number of values, the median is the average of the two middle values.

Steps to Calculate:
• Sort the dataset in ascending order.
• Identify the middle value(s).

Example:
Dataset (odd number of values): \[1,3,5,7,9\]
• Sorted: \[1,3,5,7,9\]
• Median: 5 (middle value)

Dataset (even number of values): \[1,3,5,7\]
• Sorted: \[1,3,5,7\]
• Median: (3 + 5)/2 = 4

When to Use: The median is preferred when the dataset contains outliers, as it is less affected by extreme values.

Example with Outlier: Dataset: \[2,4,6,8,100\]
Median: 6 (remains representative despite the outlier).

## 8.2.3 Mode
The mode is the value that occurs most frequently in a dataset. A dataset can have:
• One mode (unimodal).
• Two modes (bimodal).
• More than two modes (multimodal).
• No mode if all values occur with equal frequency.

Example:
Dataset: \[2,3,4,4,5,6\]
Mode: 4 (appears twice).

Dataset (bimodal): \[1,2,2,3,3,4\]
Modes: 2 and 3 (both appear twice).

Dataset (no mode): \[1,2,3,4\]
No value repeats, so there is no mode.

When to Use: The mode is useful for categorical data where you want to identify the most common category.

Example with Categories:
Dataset: \["Red","Blue","Red","Green"\]
Mode: "Red" (appears most frequently).

## 8.2.4 Comparison of Mean, Median, and Mode

| Measure || Definition || Sensitivity to Outliers || Best Use Case |
| --- | --- | --- | --- |
| Mean || Average of all values || Highly sensitive || When data is evenly distributed |
