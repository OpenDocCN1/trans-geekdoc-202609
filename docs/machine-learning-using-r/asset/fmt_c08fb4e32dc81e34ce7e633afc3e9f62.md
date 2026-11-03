
The above features may have led to the issue of reporting near-zero variance features (will be discussed later) and would have resulted in dropping the complete feature.

Thus we create a copy of the `raw_dt` which includes active employees as well as employees who left the organization in 2015 and 2016 ([Table 6.4](#14_Chapter06.xhtml#tab6.4)). The `filter_dt` is created as a copy so that, raw data remains intact for further manipulation if needed.

![](images/page182-04.png)![](images/page182-05.png)![](images/page183-01.png)

Binning of numeric features, log transformations of numeric features, scaling numeric features, merging of labels occurring in low frequency in categorical feature are some other ways to **reduce variation in the data** before certain machine learning models are applied.

If we write `filter_dt = raw_dt`, then due to R’s copy-on-modify, `filter_dt` will still point to the same location in memory as `raw_dt`. Therefore, modifying `filter_dt`, say, by adding a new column or setting a new key will also modify `raw_dt`. To avoid this, we have to explicitly write: `filter_dt = copy(raw_dt)`

## Create Feature Set (X) and Outcome Variable (Y)

We will use the similar approach as in [Chapter 5](#13_Chapter05.xhtml) to create the feature list

![](images/page183-02.png)![](images/page184-01.png)

We can also get numeric and categorical predictors separately using the following code:

![](images/page184-02.png)![](images/page185-01.png)

Compare and note the difference on how the numeric and categorical feature lists were created in [Chapter 4](#09_Chapter01.xhtml).

## Analysing the Feature Set (X)

The features in the model may lead to several issues while building it. We need to identify the issues in features before proceeding with model building. We will discuss some of the basic issues and ways to identify and remove the issues.

Identification and removal of features which shows near zero variance, linear dependency, and correlation with other features are important considerations in **data pre-processing stage.**

### Zero and Near-Zero Variance (NZV) Features[²](#14_Chapter06.xhtml#ch6-r-fn2)

**1.** The data generating mechanism can create predictors that can only have a single unique value (i.e., a ‘zero-variance predictor’).

**2.** Predictors might have only a handful of unique values that occur with very low frequencies. These may create a problem when data is split using cross validation (`CV`)/bootstrap.

To identify these types of predictors, the following two metrics can be calculated (Khun, 2007):

**1.** **Frequency ratio:** The frequency of the most prevalent value over the second most frequent value. The frequency ratio will be near one for well-behaved predictors and very large for highly-imbalanced data.

**2.** **Percentage of unique values:** The number of unique values divided by the total number of samples (times 100). This value will approach zero as the granularity of the data increases.

`nearZeroVar()` from the `caret` package can be used to identify features which show NZV. We may consider a predictor to be near-zero variance:

**1.** If the frequency ratio is greater than a pre-specified threshold (default 95/5 = 19).

**2.** And the unique value percentage is less than a threshold (default 10 per cent).

![](images/page185-02.png)

As can be seen from [Table 6.5](#14_Chapter06.xhtml#tab6.5), the features showing near-zero value issues are as follows:

**1.** `PATERNITY_MATERNITY_LEAVE_LAST_QUARTER` and `JOINING_BONUS`.

**2.** `LAST_WORKING_DATE` also shows the NZV issue. We will anyways drop the date column before model building.

Let us compute the frequency ratio and per cent of unique values for `PATERNITY_MATERNITY_LEAVE_LAST_QUARTER`.

**1.** For `PATERNITY_MATERNITY_LEAVE_LAST_QUARTER`, the most prevalent value is *N* and it occurred 7,444 times. The second most prevalent value is *Y* and it occurred 101 times. So, the frequency ratio will be 7,444/101 = 73.70. Also, out of a total of 7,545 observations, the unique values in `PATERNITY_MATERNITY_LEAVE_LAST_QUARTER` is 2. Thus, the per cent unique (2/7,545)*100 = 0.02650762. Since the frequency ratio is greater than 19 (default) and per cent unique is less than 10 per cent, `PATERNITY_MATERNITY_LEAVE_LAST_QUARTER` is flagged as an NZV feature.

![](images/page186-01.png)

Had we not created `filter_dt` ([Table 6.4](#14_Chapter06.xhtml#tab6.4)) by including records for employees with `LAST_WORKING_DATE`, for the years 2014, 2016, and 2015; variable `SL2015` would also have shown as an NZV feature as:

**2.** In `raw_dt`, the most prevalent value for `SL2015` is 0 days’ leave and it occurred 11,793 times. The second most prevalent value is 60 days’ leave and it occurred 604 times. So, the frequency ratio will be 19.52. Also, out of a total of 16,501 observations, the unique value in `SL2015` is 66. Thus, the per cent unique (66/16,501) = 0.0039. Since the frequency ratio is greater than 19 (default), and per cent unique is less than 10 per cent, `SL2015` would have been flagged as an NZV feature.

We will drop all the features showing NZV, before model building.

### Linear Dependency

One of the common issues is linear dependency between features. A set of features is said to be linearly dependent if there is a set of scalars, not all zero, such that the linear combination is a zero vector. In the attrition data, we have three features, that is, `RM_REPORTEES_COUNT`, `RM_REPORTEE_MALE`, `RM_REPORTEE_FEMALE` which are linearly dependent.

**1.** `RM_REPORTEES_COUNT` - (`RM_REPORTEE_MALE` + `RM_REPORTEE_FEMALE`) = 0

While trying to estimate the beta coefficients in regression modelling, linearly dependent features result in a singular matrix and thus the beta coefficients of one of the linearly dependent features may not get estimated.

Note that a matrix is called a singular matrix if the determinant of a matrix is zero and thus the inverse of a matrix cannot be computed. Matrix inverse gets used in estimating beta coefficients. The other issue which may arise from the linearly dependent feature is of multi-collinearity. Multi-collinearity is discussed in the next section.

The function `findLinearCombos()` from the `caret` package uses the QR decomposition of a matrix to enumerate sets of linear combinations.

![](images/page187-01.png)

There are two feature lists which are linearly dependent.

**1.** Feature number 16, 17, and 18 are `RM_REPORTEES_COUNT`, `RM_REPORTEE_MALE` and `RM_REPORTEE_FEMALE`.

**2.** Feature number 2, 15, and 20 are `EMPLOYEE_AGE_DURING_DOJ`, `RM_AGE` and `AGE_DIFFERENCE`:

**3.** Feature number 23 (`LEAVE_PREVIOUS_YEAR`) is sum of `CL2014`, `PL2014`, and `SL2014`.

**4.** Feature number 24 (`LEAVE_CURRENT_YEAR`) is sum of `CL2015`, `PL2015`, and `SL2015`.

We will have to drop one or more of these features before proceeding with model building.

### Multi-Collinearity

Let us analyze the correlation between variables and drop features which are highly correlated variables. We will build a correlation matrix ([Table 6.6](#14_Chapter06.xhtml#tab6.6)) amongst the numeric variables by using the `cor()` function. We will plot the correlation matrix for visual inspection and use `findCorrelation()` function to report feature names which are highly correlated at cut-off of 0.70.

![](images/page188-01.png)

The correlation heatmap is shown in [Figure 6.3](#14_Chapter06.xhtml#fig6.3). The diagonal line represents correlation of the feature with itself and can be ignored. For other features, the darker shades reflect features which are highly correlated (positive as well as negative). From [Figure 6.3](#14_Chapter06.xhtml#fig6.3), we can see there are features which are highly correlated.

**1.** `AGE_DIFFERENCE` is highly correlated with `EMPLOYEE_CURRENT_AGE`, `EMPLOYEE_AGE_DURING_DOJ`, and `RM_AGE`
