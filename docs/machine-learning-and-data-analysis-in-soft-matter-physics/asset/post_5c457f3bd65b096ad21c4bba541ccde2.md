
## Types of Feature Selection:

- Filter Method: Based on the statistical measure of the relationship between the feature and the target variable. Features with a high correlation are selected.

- Wrapper Method: Based on the evaluation of the feature subset using a specific machine learning algorithm. The feature subset that results in the best performance is selected.

- Embedded Method: Based on the feature selection as part of the training process of the machine learning algorithm.

### Benefits of Feature Selection:

- Reduces Overfitting: By using only the most relevant features, the model can generalize better to new data.

- Improves Model Performance: Selecting the right features can improve the accuracy, precision, and recall of the model.

- Decreases Computational Costs: A smaller number of features requires less computation and storage resources.

- Improves Interpretability: By reducing the number of features, it is easier to understand and interpret the results of the model.

## 5. Feature Scaling

Feature Scaling is the process of transforming the features so that they have a similar scale. This is important in machine learning because the scale of the features can affect the performance of the model.

### Types of Feature Scaling:

- Min-Max Scaling: Rescaling the features to a specific range, such as between 0 and 1, by subtracting the minimum value and dividing by the range.

- Standard Scaling: Rescaling the features to have a mean of 0 and a standard deviation of 1 by subtracting the mean and dividing by the standard deviation.

- Robust Scaling: Rescaling the features to be robust to outliers by dividing them by the interquartile range.

### Benefits of Feature Scaling:

- Improves Model Performance: By transforming the features to have a similar scale, the model can learn from all features equally and avoid being dominated by a few large features.

- Increases Model Robustness: By transforming the features to be robust to outliers, the model can become more robust to anomalies.

- Improves Computational Efficiency: Many machine learning algorithms, such as k-nearest neighbors, are sensitive to the scale of the features and perform better with scaled features.

- Improves Model Interpretability: By transforming the features to have a similar scale, it can be easier to understand the model's predictions.

## 2.5.4 Feature Engineering Methods

![](img/c4a53cbbd40023d194b7887dddf3293b_75_0.png)

### Imputation

Imputation is the process of managing missing values, which is one of the most common problems when it comes to preparing data for machine learning. By missing values, we mean places where information is missing in some cells of a respective row.

There may be different causes for missing values, including human error, data flow interruptions, cross-datasets errors, etc. Since data completeness impacts how well machine learning models perform, imputation is quite important.

Here are some ways how you can solve the issue of missing values:

- If a row is less than 20-30% complete, it's recommended to dismiss such a record.

- A standard approach to assigning values to the missing cells is to calculate a mode, mean, or median for a column and replace the missing values with it.

- In other cases, there are possibilities to reconstruct the value based on other entries. For example, we can find out the name of a country if we have the name of a city and an administrative unit. Conversely, we can often determine the country/city by a postal code.

You can find more sophisticated approaches to imputation in this post.

### Outlier Handling

Outlier handling is another way to increase the accuracy of data representation. Outliers are data points that are significantly different from other observations.

This graph shows how outliers can influence the ML model. By dismissing the outliers, we can achieve more accurate results.

![](img/c4a53cbbd40023d194b7887dddf3293b_76_0.png)

It can be done by removing or replacing outliers. Check out this post for an overview of the five most popular approaches to handling outliers.

### One-Hot Encoding

Categorical values (often referred to as nominal) such as gender, seasons, pets, brand names, or age groups often require transformation, depending on the ML algorithm used. For example, decision trees can work with categorical data. However, many others need the introduction of additional artificial categories with a binary representation. Binary representation means you assign a value of 1 if the feature is valid and 0 if it is not.

| ID | Male | Female |
|---|---|---|
| User 1 | 1 | 0 |
| User 2 | 0 | 1 |

One-hot encoding is a technique of preprocessing categorical features for machine learning models. For each category, it designs a new binary feature, often called a "dummy variable."

### Log Transformation

This method can approximate a skewed distribution to a normal one. Logarithm transformation (or log transformation) replaces each variable x with a log(x).

![](img/c4a53cbbd40023d194b7887dddf3293b_77_0.png)

### The Benefits of Log Transform:

- Data magnitude within a range often varies. For example, magnitude between ages 10 and 20 is not the same as that between ages 60 and 70. Differences in this type of data are normalized by log transformation.

- Normalizing magnitude differences and increasing the robustness of the model also reduces the negative effect of outliers.

If we compare graphs on top and bottom, we'll see that mode, mean, and median are slightly different for normal and skewed distribution.

![](img/c4a53cbbd40023d194b7887dddf3293b_78_0.png)

### Scaling

Scaling is a data calibration technique that facilitates the comparison of different types of data. It is useful for measurements to correct the way the model handles small and large numbers.

For example, despite its small value, the floor number in a building is as important as the square footage.

As another example, it is easier to perform a comparative analysis of the planets if we normalize values using their proportions against each other instead of actual diameters.

![](img/c4a53cbbd40023d194b7887dddf3293b_78_1.png)

The most popular scaling techniques include:

- min-max scaling

- absolute maximum

- standardization

- normalization

Min-max scaling is represented by the following formula:

The absolute maximum scaling technique consists in dividing all figures in the data set by its max value.

Standardization is done by calculating the difference between the individual numbers and their mean, divided by the range of variation, called the standard deviation (sigma).

Normalization is quite similar, except that we work with the difference of each value from the mean, divided by the difference between maximum and minimum values in the dataset.

## 2.5.5 Feature Engineering Tools

There are several tools available for feature engineering. Here are some popular ones:

### 1. Featuretools

Featuretools is a Python library that enables automatic feature engineering for structured data. It can extract features from multiple tables, including relational databases and CSV files, and generate new features based on user-defined primitives. Some of its features include:

- Automated feature engineering using machine learning algorithms.

- Support for handling time-dependent data.

- Integration with popular Python libraries, such as pandas and scikit-learn.

- Visualization tools for exploring and analyzing the generated features.

- Extensive documentation and tutorials for getting started.

### 2. TPOT

TPOT (Tree-based Pipeline Optimization Tool) is an automated machine learning tool that includes feature engineering as one of its components. It uses genetic programming to search for the best combination of features and machine learning algorithms for a given dataset. Some of its features include:
