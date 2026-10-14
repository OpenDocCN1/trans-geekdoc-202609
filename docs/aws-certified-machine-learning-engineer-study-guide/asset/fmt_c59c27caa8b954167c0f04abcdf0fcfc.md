
# Features are constantly used by multiple teams (data scientists as well as data and ML engineers), and feature quality is critical to the accuracy of your ML model. Also, when features used to train models offline in batch are made available for real-time inference, it’s hard to keep the two feature stores synchronized. Amazon SageMaker Feature Store provides a secured and unified store to process, standardize, and use features at scale across the ML lifecycle.

In the next section, we will cover the preprocessing work that is necessary prior to feature engineering. This work starts by transforming your dataset to address inconsistency data issues, such as managing outliers, inputting missing data, and removing duplication.

## Data Cleaning and Transformation

Data cleaning is a fundamental preprocessing step that ensures your dataset is in the best possible shape for feature engineering.

With an effective data cleaning approach, you set the stage for feature engineering by transforming “dirty” data into a structured, accurate, and reliable foundation. This allows you to focus on creating and selecting the most relevant and powerful features for your ML model.

Here’s how it provides the necessary groundwork:

*   **Managing missing values.** This step addresses any gaps in your dataset, whether by imputing missing values, deleting incomplete records, or otherwise managing them. Clean data ensures that the features you engineer do not suffer from bias or inaccuracies caused by gaps in the data.

*   **Detecting and treating outliers.** By identifying and managing outliers, you can prevent them from skewing the feature distribution and impacting model performance. Clean data provides a more realistic representation of the data distribution, which is crucial for effective feature engineering.

*   **Performing deduplication.** Removing duplicate records and redundant data points helps streamline the dataset, making feature engineering more efficient and less prone to overfitting.

*   **Reformatting and standardization.** Ensuring uniform data types, units, and formats allows for more straightforward feature creation. For example, standardizing date formats and measurement units ensures consistency and comparability across features.

*   **Removing noise and errors.** Data cleaning involves identifying and correcting errors or inconsistencies within the data. This ensures that the features you create are based on accurate and reliable data, leading to more robust models.

### Managing Missing Values

It is not uncommon that your dataset has missing data. For example, some columns in your dataset may be missing values due to a data collection error, or maybe the data was simply unavailable from your data source.

Missing data can make it difficult for the selected ML algorithm to accurately interpret the relationship between the related feature and the target variable. Therefore, it is important to deal with the issue.

Unfortunately, most ML algorithms cannot deal with missing values automatically. Human knowledge is required to replace missing values with something meaningful and relevant to the problem.

The approaches to address missing data vary based on the amount of missing data. The main techniques are as follows:

*   **Collect.** If the amount of missing data is substantial and multiple features are impacted, you should try to recollect the data. However, the data ingestion process can be expensive and time-consuming. In this case, you need to determine what the trade-offs are among the cost of recollecting data, the cost of having a low-performance ML model, and alternatives such as imputation or dropping.

*   **Impute.** If you are dealing with a small number of missing values, which are randomly distributed throughout the features of your dataset, this could be due to a failure in the data ingestion process. In this case, *imputation* is likely a good option. With imputation, you populate the missing data with the mean, the median, or the most frequent value observed for your feature. If the data distribution for your feature is normal, then use the mean; otherwise, use the median or the most frequent value.

*   **Drop.** If the amount of missing data is substantial but is limited to the same feature, you may consider dropping the entire feature. You have to be careful, though, because when you drop too many features, you may not have enough data to feed the ML model.

With Amazon SageMaker, you can use Python libraries like `SimpleImputer` from `sklearn` to fill in missing values. The following snippet shows how this function works:

```
from sklearn.impute import SimpleImputer
import numpy as np

# Create a sample dataset
A = np.array([[1, 2], [None, 4], [5, None]])

# Create a SimpleImputer object
imputer = SimpleImputer(strategy='mean')

# Fit and transform the data
B = imputer.fit_transform(A)

print(B)
```

The following input array

```
[[1, 2], [None, 4], [5, None]]
```

has been transformed into this:

```
[[1, 2], [3, 4], [5, 3]]
```

AWS Glue DataBrew can also be used to fill missing values using a number of built-in transformations.

### Detecting and Treating Outliers

An *outlier* is a data point in your dataset distinct from all other data points for having a significant deviation from the mean.

What does “significantly” mean, exactly? Although the answer depends on the type of data and its probability distribution, the general consensus is that a data point is considered an outlier if it lies more than three standard deviations away from the mean. This is based on the properties of the normal distribution, where approximately 99.7% of data lies within three standard deviations from the mean.

ML algorithms are very sensitive to the distribution and the range of the values of your features. Because outliers drift from the pattern of all other data points, they have a tendency to mislead the ML algorithm during training.

For example, consider the following dataset:

```
[x,y] = [[4, 11], [3.8, 12], [4.5, 12.5], [8, 8], [9, 8.5], [9.5, 7.5], [13, 5], [14, 4.7], [13.7, 6], [25, 23]]
```

In this example, assume `x` indicates your water consumption rate per day, whereas `y` indicates the energy consumption rate per day. These numbers are just for illustration purposes.

As you can see in [Figure 3.7](#c003.xhtml#c03-fig-7), this dataset is distributed in three groups.

![FIGURE 3.7 Example of an outlier.](images/c03f007.png)

[FIGURE 3.7](#c003.xhtml#rc03-fig-7) Example of an outlier.

One data point clearly stands out and is acting as an outlier.

Although some outliers are caused by artificial errors, others just appear in your dataset as a result of natural phenomena. A natural outlier is not the result of some artificial error but instead is reflective of some truth in the data.

Your job as an ML engineer is to determine whether an outlier should stay in your dataset or needs to be changed or removed. You make this decision by leveraging statistical techniques that help you understand how relevant the outlier is with respect to the other data points in your dataset.

It is important to distinguish between noise and outliers. The former denotes a group of erroneous data points, whereas the latter refers to data points that significantly deviate from the mean of your dataset. In the rest of the chapters, you will learn how to leverage the extensive ecosystem of AWS ML services to determine what “significantly” means.

The treatment of outliers relies on three main approaches:

*   **Delete.** If outliers are due to noise or artificial errors, you can simply delete them from your dataset without impacting the quality and the accuracy of your ML model.
