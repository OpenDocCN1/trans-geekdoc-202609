# Processing features

for linear models. This transformer handles just low categorical features by performing one-hot encoding, leaving high cardinality categorical ones apart.

# 6.1.1 Multivariate missing data imputation

Having missing data in your tabular dataset is a blocking problem because, apart from GBDs solutions such as XGBoost, LightGBM, and Scikit-learn's HistGradientBoosting, classical learning algorithms do not have any support for missing values. In addition, even if your GBDTs choice of choice can handle missing, as explained in the next section, you may still find imputing the missing values more effective because you can check beforehand how each feature or specific case is handled.

In chapter 2, we discussed simple imputation methods, such as using the mean or the median, and value of building indicators, enabling algorithms to spot patterns that are present more easily. This section will provide more details about these techniques and multivariate imputation.

First, missing cases depend on unobserved variables as features that you don't access to, missing data can be categorized as

+   - Missing completely at random (MCAR)—In this scenario, data missing is unrelated to observed and unobserved variables. The missingness occurs randomly across the dataset. 

+   - Missing at random (MAR)—MAR assumes that unobserved variables, the unobserved ones, can explain the missingness. In other words, the probability of missingness depends solely on the observed data.

When the missing cases depend on the unobserved values of the missing data itself, you fall into the case of missing not at random (MNAR), which requires quite a specialized treatment that is not a topic of this book. However, suppose you understand the mechanism behind missing not at random missing data, such as when you don't get information in the census about people who are too rich (because of privacy) or too poor. In that case, you can try to gather features that hint their wealth to add to your dataset and fall back to the MAR case.

Generally, you have cases where missing data is MCAR or MAR. In both cases, apart from simple imputation with an expected value works perfectly with MAR, you can reconstruct your missing data through multivariate imputation. Multivariate imputation is a method that uses the correlations among predictors to imput missing values. It involves building a series of models to estimate the missing values based on the relationships between variables. In this approach, each model treats a feature with missing values and the remaining features as predictors. The resulting model is then used to determine what values to replace the missing values in the target. You may set the algorithm cycles through the features to imput. You usually use the default setting, starting from the features with less missing data and progressing to those with more missing values, which is preferred and most effective.