Although, in real scenarios, you usually need to treat missing data via exclusion or imputation, never forget that you can always try to look at the source process and check if you can retrieve (or, at least, better understand) the missing data. You may face this option in the exam.

If you don’t have an opportunity to recover your missing data from anywhere, then you should move on to other approaches, such as **listwise deletion** and **imputation**.

Listwise deletion refers to the process of discarding some data, which is the downside of this choice. This may happen at the row level or the column level. For example, suppose you have a DataFrame containing four columns and one of them has 90% of its data missing. In such cases, what usually makes more sense is dropping the entire feature (column), since you don’t have that information for the majority of your observations (rows).

From a row perspective, you may have a DataFrame with a small number of observations (rows) containing missing data in one of its features (columns). In such scenarios, instead of removing the entire feature, what makes more sense is removing only those few observations.

The benefit of using this method is the simplicity of dropping a row or a column. Again, the downside is losing information. If you don’t want to lose information while handling your missing data, then you should go for an imputation strategy.

Imputation is also known as replacement, where you will replace missing values by substituting a value. The most common approach to imputation is replacing the missing value with the mean of the feature. Please take note of this approach because it is likely to appear in your exam:

| Age |
|---|
| 35 |
| 30 |
| |
| 25 |
| 80 |
| 75 |

Table 4.10 – Replacing missing values with the mean or median

Table 4.10 shows a very simple dataset with one single feature and five observations, where the third observation has a missing value. If you decide to replace that missing data with the mean value of the