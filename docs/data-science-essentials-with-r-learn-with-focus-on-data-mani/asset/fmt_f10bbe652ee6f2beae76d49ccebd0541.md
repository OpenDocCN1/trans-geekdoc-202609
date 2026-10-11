
# Deleting missing values

Deleting missing values is generally not recommended because it can result in a loss of valuable information from the dataset. In most cases, it is best to avoid deletion unless the proportion of missing values is very small. In such cases, removing the missing values can be a reasonable option without significantly affecting the integrity of the dataset. Different deletion approaches for missing values are shown in [Figure 3.6](#ch03.xhtml#fig3-6):

![](images/Figure3.8.jpg)

**Figure 3.6: Deletion approaches of missing values**

## The listwise deletion (Dropping entire rows)

This approach removes entire rows of data containing missing values, which is also called complete case deletion. However, listwise deletions are only appropriate for missing completely at Random `MCAR` values. The below code shows listwise deletion using `drop_na()`:

```
# check the dimensions of gapminder
dim(gapminder)
## 10545 9

# drop rows: missing values in any column
drop_rows_any <- gapminder %>% drop_na()

# check the dimensions of the new dataframe
dim(drop_rows_any)
## 7139 9

# drop rows: missing values in any specific column (for example, fertility)
drop_rows_fertility <- gapminder %>% drop_na(fertility)

# check the dimensions of the new dataframe
dim(drop_rows_fertility)
## 10358 9
# The above command removed 187 rows from gapminder that has missing values in the column "fertility"
```

## Dropping entire columns

Sometimes, a column in a dataset may contain a high percentage of missing values, such as 80% or more. If this feature is not significant for the analysis, it may be tempting to delete from the dataset. However, it is essential to remember that deleting data is unreliable for handling missing values. While removing a feature with high missingness can make the dataset manageable, it may also result in a loss of valuable information that could be useful for other analysis. Therefore, exploring different approaches for handling missing values is generally recommended before resorting to deletion. In the following example, we are focusing on removing a specific column, `country_gdp`, from the Gapminder dataset:

```
# drop the column country_gdp (using base R)
gapminder$country_gdp <- NULL

# drop the column country_gdp (using dplyr)
gapminder <- select(gapminder, -country_gdp)
```

The above code uses both Base R and the `dplyr` package to remove the `country_gdp` column from the Gapminder DataFrame.

# Imputations

Imputation is another approach to replace missing values in a dataset with estimated values. The method used for imputation can vary depending on the nature of the problem and the data being analyzed. There are numerous approaches to imputation, each with its own advantages and disadvantages, and the choice of method should be carefully considered, based on the specific needs of the analysis. [Figure 3.7](#ch03.xhtml#fig3-7) displays various techniques to impute missing values in a dataset:

![](images/Figure3.9.jpg)

**Figure 3.7: Imputation techniques of missing values**

## Typical imputation techniques for non-time series problems

*   **Imputation with a constant value**: One approach to handle missing data is imputing it with a constant value. This involves replacing all missing values in a dataset with a single value (for example, replace with `0`). While this approach is straightforward and easy to implement, it may not be suitable for all data types.
*   **Imputation using column statistics**: Another common approach for imputing missing values is using the respective column's statistics, such as `mean`, `median`, or `mode`. This approach involves calculating the column-wise statistics for the non-missing values and replacing the missing values with the calculated value. This method can be effective, especially when the missing data is not significantly affecting the overall distribution of the data.

## Imputations techniques for time series problems

*   **Replace missing values with the last observed value (forward fill)**: This approach involves replacing missing values with the most recent previous value observed in the data. This method assumes that the missing values are likely similar to the most recent previous value.
*   **Replace missing values with the next observed value (backward fill)**: This method replaces missing values with the most recent next value observed in the data. This method assumes that the missing values are similar to the next observed value.
*   **Linear and spline interpolation method**: Interpolation estimates missing values based on the surrounding data points. Linear interpolation involves connecting two adjacent data points with a straight line and using this line to estimate the missing value. Spline interpolation is a complex method that involves fitting a curve to the data points and using this curve to estimate missing values. Both methods can effectively impute missing data, but spline interpolation tends to be more accurate and flexible than linear interpolation. However, it is essential to note that interpolation assumes a certain level of continuity in the data and may not be appropriate if the missing values are not well-represented by the surrounding data.

[Table 3.2](#ch03.xhtml#tab3-2) lists essential R functions typically used for imputing missing values:

| Function | Package | Description |
| --- | --- | --- |
| `replace_na` | `tidyr` | Replaces missing values with a specified value. |
| `fill` | `tidyr` | Imputes missing values using the last observed value (forward fill) or the next observed value (backward fill). |
| `na.spline` | `zoo` | Imputes missing values using a spline interpolation. |
| `na.approx` | `zoo` | Imputes missing values using linear interpolation. |
| `mice` | `mice` | Impute missing values in a DataFrame using multiple imputations with chained equations. |
| `missForest` | `missForest` | Imputes missing values using a random forest algorithm. |

**Table 3.2: Description of essential R functions for imputing missing values**

# Conclusion

In this chapter, we have covered various data exploration techniques using the Gapminder dataset. We defined the dataset and then focused on selecting relevant columns and filtering rows based on certain conditions. We also learned to identify and remove duplicate rows in a dataset and sort data by one or more columns. Additionally, we explored how to work with factors in R. One of the most common challenges in real-world datasets is missing data. We covered different approaches for handling it, including detecting missing data visually using the `naniar` library and understanding the reasons for missing data. We also explored various methods for treating missing data, such as imputation with constant values, column statistics, and interpolation methods. These techniques ensure that our data analysis is based on complete and accurate data and can lead to more meaningful insights and predictions.

In the next chapter, you will learn essential data manipulation techniques to become more proficient at wrangling and preparing your data for downstream analysis.

## Join our book's Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![](images/fm1.png)

# CHAPTER 4: Wrangling Data

## Introduction
