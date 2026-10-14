
`selected_features_mask = sel2.get_support()`

# Get the column labels of selected features

`X_train.columns[selected_features_mask]`

In return we obtain the list of features selected:

`['Adj Close_ret', 'Low_ret' , 'Relative_Change_Open_Close_ret' , 'BBB_20_2.0_ret', 'High_1', … ]`

### Recursive feature elimination

Given an external estimator (`clf`) that assigns importance[25](#chap06.xhtml#footnote-096) (weights) to features, the goal of recursive feature elimination (RFE) is to select features by recursively considering smaller and smaller sets of features. First, the estimator is trained on the initial set of features and the importance of each feature is obtained. Then, the least important features are pruned from the current set of features. That procedure is recursively repeated on the pruned set until the desired number of features to select is reached.

```
from sklearn.feature_selection import RFE

sel3 = RFE(clf, n_features_to_select = k_best , step = 0.3)

sel3.fit(X_train, y_train)

sel3.get_feature_names_out()[:100]
```

The following is a small extract of the features selected:

```
['Gap_Previous_Close', 'CCI', 'GOOG_Adj Close_ret', 'AMZN_Open_ret',
'TSLA_Low_ret', 'NVDA_Low_ret', 'IBM_Low_ret', 'IBM_Adj Close_ret',
'Close_diff_frac_0.2_ret', 'Price_Momentum_ret', 'BBB_20_2.0_ret',
'MSFT_Volume_5', 'IBM_Open_4', 'IBM_Low_3', 'IBM_Volume_3',
'IBM_Volume_5', 'Price_Momentum_3', 'Intraday_Price_Range_1',
'Intraday_Price_Range_4', 'Intraday_Price_Range_5','Closing_Position_1', 'Gap_Previous_Close_5','Relative_Change_Open_Close_3' 'Normalized_Volume_Weighted_Close_1', 'MACD_Histogram_3',
'Open_ret_5', 'Adj Close_ret_3', …]
```

`RFE` iteratively removes the least important features until only the most relevant ones remain. The code above demonstrates how `RFE` is applied using a classifier (`clf`) to rank feature importance and select the top `k_best` features.

After fitting the model, the `get_feature_names_out()` function retrieves the most informative features that contribute to predictions. Below is a sample of the selected features, which include technical indicators (e.g., `CCI`, `MACD_Histogram`), price-based transformations (e.g., `Gap_Previous_Close`, `Intraday_Price_Range`), and fractional differentiations (`Close_diff_frac_0.2_ret`). These selected features enhance the model's predictive power by reducing noise and focusing on the most impactful variables.

With `RFE` identifying the most relevant features, we now explore feature selection using dimensionality reduction techniques like `PCA` and `UMAP`.

### Feature selection with PCA and UMAP

Previously, we discussed `PCA` and `UMAP` as methods for feature engineering. These techniques are often used in the feature selection phase. In such scenarios, the original features are substituted with the new features derived from `PCA` or `UMAP`.

Rather than simply selecting the right features for input into the model, the focus shifts to using all the features and merging them using `PCA` or `UMAP` techniques. This approach creates a new set of features with reduced dimensions. For the implementation, we have already exposed the code in the previous section dedicated to `UMAP`.

Now that we know how to select significant features let us look at how to proceed when you want to benefit from the virtues of each of these propositions.

### Combine best features with set operators

The set operators are an appropriate answer for combining all these feature proposals. In this example, we combine the proposals of the three competing feature selection methods (`sel1`, `sel2`, and `sel3`) exposed in the previous sections:

```
sel1 = SelectPercentile(mutual_info_classif, percentile = pct , n_neighbors = 10)

# Initialize SelectKBest with mutual information
sel2 = SelectKBest(mutual_info_classif, k = k_best) 
sel3 = RFE(clf, n_features_to_select = k_best , step = 0.3)
```

The set methods encapsulate the selected features in sets:

```
set1 = set(sel1.get_feature_names_out())
set2 = set(sel2.get_feature_names_out())
set3 = set(sel3.get_feature_names_out())
```

Sets are combined using the set operators `union`[26](#chap06.xhtml#footnote-095) and `intersection`[27](#chap06.xhtml#footnote-094):

```
set1or2 = set1.intersection(set2)
print(len(set1or2))
set1or2or3 = set1or2.union(set3)
```

Choosing between the `union` and `intersection` of feature sets from competitive feature selection methods depends on the context:

- For datasets with a limited number of observations (compared to the number of features), the `intersection` is the safer choice to avoid overfitting.
- If the feature selection methods are fundamentally different and complementary (e.g., one is statistically based, as `mutual_info_classif`, and the other is model-based, as `RFE`), their `union` could result in a more comprehensive feature set. `union` is beneficial when the methods are complementary, and there is sufficient data to support a larger feature set. Otherwise, `union` could result in a larger feature set, which could increase the complexity of the model and possibly lead to overfitting.

## Conclusion

By the end of this chapter, we understood how to master the feature engineering and feature selection techniques that are essential for optimizing the performance of machine learning models.

This applies not only to predictive performance but also, and equally importantly, to the aspects of post-production, deployment, and maintenance of machine learning models. These facets are collectively referred to as Machine Learning Operations (`ML-Ops`). We should also mention that feature selection has practical benefits in a production environment. Models with fewer features are generally faster to run, easier to interpret, and more cost-effective, particularly when handling large datasets.

Now that we have a solid foundation in machine learning, we are ready to explore advanced algorithms.

In the next chapter, we will focus on sophisticated machine learning methods, ranging from ensemble techniques to continuous online learning approaches.

---

- `H` is the entropy of the random variable `X`
- `p(x_i)` is the probability of occurrence of the `i`-th outcome
- The summation runs over all `n` possible outcomes of `X`

**Join our book’s Discord space**

Join the book’s Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![Discord](images/Discord.png)

# Chapter 7  

## Advanced Machine Learning Models for Trading

### Introduction

This chapter explores advanced machine learning techniques for algorithmic trading, examining methods that go beyond traditional supervised learning. We will look at state-of-the-art ensemble methods and online learning approaches to improve trading strategies.

The chapter begins with an in-depth look at ensemble methods, which combine multiple models to improve predictive accuracy and reduce overfitting. We then discuss boosting, bagging, and specific algorithms such as `XGBoost` and `LightGBM`, highlighting their applications in algorithmic trading.

The chapter also explores advanced regression methods, including Least Absolute Shrinkage and Selection Operator (`LASSO`) and ridge regression, and provides insight into their effectiveness in financial forecasting. In addition, we will explore online learning, examining tools such as `Scikit-multi flow` to show their role in real-time financial signal tracking. The goal of this chapter is to provide a comprehensive understanding of these advanced methods so that readers can apply them effectively.

### Structure

In this chapter, we will cover the following topics:

- [Understanding advanced machine learning](#chap07.xhtml#h32)
- [Introduction to ensembling methods](#chap07.xhtml#h33)
- [Advanced ensembling method for classification](#chap07.xhtml#h34)
