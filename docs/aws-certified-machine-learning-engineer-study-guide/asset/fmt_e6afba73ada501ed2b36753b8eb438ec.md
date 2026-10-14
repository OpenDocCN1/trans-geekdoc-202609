
## Logarithmic transform

By replacing the outlier with its logarithm in a given base (e.g., base `e`, base 2, base 10, and so on), you are compressing the range of values for a feature, resulting in a reduction of the extreme variation between the values. As a result, the outlier won’t be too far off from the other values for that feature. For example, the logarithm base 10 (`log10`) of 1000 is 3. That’s because `10^3 = 1000`, which brings it closer to other smaller values without losing its significance.

## Impute

Just as for missing values, you could use the mean of the feature, for instance, and impute that value to replace the outlier value. This would be an excellent approach if the outlier was caused by artificial errors.

Outliers often create a skewed distribution, as shown in [Figure 3.7](#c003.xhtml#c03-fig-7). Log transformation can help normalize this distribution, making it more symmetrical and improving the performance of your ML model.

[Figure 3.8](#c003.xhtml#c03-fig-8) illustrates the same dataset after representing the ordinate axis `y` using a logarithmic scale. The outlier data point `[25, 23]` has `x = 25` and `y = 23`. Because `log10(23) = 1.37172724`, you can see how this data point no longer deviates significantly from the mean.

![FIGURE 3.8 Outlier treatment with logarithmic transformation.](images/c03f008.png)

[FIGURE 3.8](#c003.xhtml#rc03-fig-8) Outlier treatment with logarithmic transformation.

For the exam, you need to know the AWS services that help you detect and treat outliers, which are Amazon SageMaker Data Wrangler and AWS Glue DataBrew.

You can use Amazon SageMaker Jupyter notebooks to load your dataset using Python libraries like `pandas`.

To determine which outlier detection algorithm to use, you need to analyze the histogram for each feature. [Figure 3.9](#c003.xhtml#c03-fig-9) illustrates the histograms for our dataset generated using the following Python snippet:

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
data = np.array([[4, 11], [3.8, 12], [4.5, 12.5], [8, 8], [9, 8.5], [9.5, 7.5], [13, 5], [14, 4.7], [13.7, 6], [25, 23]])
df = pd.DataFrame(data, columns=['Feature1', 'Feature2'])

# Plot histograms
plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
sns.histplot(df['Feature1'], kde=True)
plt.title('Water Usage Distribution (m³/day)')

plt.subplot(1, 2, 2)
sns.histplot(df['Feature2'], kde=True)
plt.title('Energy Usage Distribution (kWh/day)')

plt.show()
```

![FIGURE 3.9 Histograms for water and energy usage.](images/c03f009.png)

[FIGURE 3.9](#c003.xhtml#rc03-fig-9) Histograms for water and energy usage.

In [Figure 3.9](#c003.xhtml#c03-fig-9), the histograms show a right-skewed data distribution for both features. A right-skewed data distribution means that the majority of our data points are clustered toward the lower end of the range, with a long tail extending to the right. This tail represents a small number of data points that have much higher values than the rest of the dataset. Essentially, most values are low, and only a few are exceptionally high, which is exactly our scenario with the data point `[25, 23]` representing the highest value pair.

For skewed data, the interquartile range (IQR) method is often considered one of the best approaches for detecting outliers. The IQR is less affected by skewness and provides a robust measure to identify extreme values.

Assuming `Q1` and `Q3` denote the first and the third quartiles of our dataset, here’s a quick overview of how it works:

*   Compute `Q1` and `Q3`.
*   Compute `IQR = Q3 - Q1`.

Any data point whose value is smaller than `Q1 - 1.5 * IQR` or greater than `Q3 + 1.5 * IQR` is considered an outlier.

In our example, we can leverage the built-in `quantile` method, available from the `DataFrame` class in both the `numpy` and `pandas` libraries, to detect outliers from the dataset, as illustrated in the following snippet:

```
import numpy as np
import pandas as pd

# Load dataset
data = np.array([[4, 11], [3.8, 12], [4.5, 12.5], [8, 8], [9, 8.5], [9.5, 7.5], [13, 5], [14, 4.7], [13.7, 6], [25, 23]])
df = pd.DataFrame(data, columns=['Feature1', 'Feature2'])

# Calculate IQR
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1

# Define outlier conditions
outliers = ((df < (Q1 - 1.5 * IQR)) | (df > (Q3 + 1.5 * IQR))).any(axis=1)
df['Outlier'] = outliers

print("Original Data with Outlier Flags:")
print(df)

# Treat outliers by removing them
df_cleaned = df[~df['Outlier']].drop(columns='Outlier')

print("\nCleaned Data without Outliers:")
print(df_cleaned)
```

This program produces the output shown in [Figure 3.10](#c003.xhtml#c03-fig-10), where you can see how the script detected the data point `[25, 23]` as an outlier and subsequently removed it.

![FIGURE 3.10 Detecting and treating outliers.](images/c03f010.png)

[FIGURE 3.10](#c003.xhtml#rc03-fig-10) Detecting and treating outliers.

For normally distributed data, the Z-score method is highly effective for detecting outliers. Here’s a quick rundown:

*   Compute the mean `μ` of your dataset.
*   Compute the standard deviation `σ` of your dataset.
