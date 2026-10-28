+   - Frame analysis is one more way of getting information concerning events and not time frames; this hails from the knowledge that change may happen irregularly.

In conclusion, the issues related to handling non-constant spacing include composing the right model, proper sampling methodologies, and constructing the methods that take into account the irregularity in the observation time.

# Question 5: How would you handle missing values in a time series dataset?

**Answer**: Handling missing values in a time series dataset involves strategies like deletion, imputation, or model-based approaches similar to supervised and unsupervised data preprocessing:

+   - **Deletion**: Exclude cases with missing values (complete case or available case analysis).
+   - **Imputation**: Impute values by mean/median subtraction, use linear regression, by averaging values of different time periods, or use parametric model for missing values.
+   - **Model-based methods**: If there are missing values, then it should be imputed using time series models or ML algorithms.
+   - **Domain-specific knowledge**: When data is missing, fill the gaps using prior knowledge of the domain.

Select the method in regard with data characteristics, and it is suggested to compare results between different strategies.

# Question 6: How do you identify and handle outliers or anomalies in a time series dataset?