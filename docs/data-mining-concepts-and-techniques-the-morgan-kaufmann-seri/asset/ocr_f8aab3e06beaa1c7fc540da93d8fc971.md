# 2.5.1 Normalization

The measurement unit used can affect the data analysis. For example, changing measurement units from meters to inches for *height*, or from kilograms to pounds for *weight*, may lead to very different results. In general, expressing an attribute in smaller units will lead to a larger range for that attribute and thus tend to give such an attribute greater effect or “weight.” To help avoid dependence on the choice of measurement units, the data should be **normalized** or **standardized**. This involves transforming the data to fall within a smaller or common range such as [–1.0, 1.0] or [0.0, 1.0]. (The terms *standardize* and *normalize* are used interchangeably in data preprocessing, although in statistics, the latter term also has other notations.)

Normalizing the data attempts to give all attributes an equal weight. Normalization is particularly useful for classification algorithms involving neural networks or distance measurements such as nearest-neighbor classification and clustering. If using the neural network backpropagation algorithm for classification (Chapter 10), normalizing the input values for each attribute measured in the training tuples will help speed up the learning phase. For distance-based methods, normalization helps prevent attributes with initially large ranges (e.g., *income*) from outweighing attributes with initially smaller ranges (e.g., binary attributes). It is also useful when given no prior knowledge of the data.

There are many methods for data normalization. We study *min-max normalization*, *z-score normalization*, and *normalization by decimal scaling*. For our discussion, let A be a numeric attribute with n observed values, v1, v2, ..., vn.

**Min-max normalization** performs a linear transformation on the original data. Suppose that *min<sub>A</sub>* and *max<sub>A</sub>* are the minimum and maximum values of an attribute, A. Min-max normalization maps a value, vi, of A to v'i in the range [new_min_A, new_max_A] by computing

v'i = (vi - min_A) / (max_A - min_A) * (new_max_A - new_min_A) + new_min_A. (2.32)

Min-max normalization preserves the relationships among the original data values. It will encounter an “out-of-bounds” error if a future input case for normalization falls outside of the original data range for A.

**Example 2.26. Min-max normalization.** Suppose that the minimum and maximum values for the attribute *income* are $12,000 and $98,000, respectively. We would like to map *income* to the range [0.0, 1.0]. By min-max normalization, a value of $73,600 for *income* is transformed to (73,600 - 12,000) / (98,000 - 12,000) * (1.0 - 0) + 0 = 0.716.

In **z-score normalization** (or *zero-mean normalization*), the values for an attribute, A, are normalized based on the mean (i.e., average) and standard deviation of A. A value, vi, of A is normalized to v'i by computing

v'i = (vi - A_bar) / sigma_A. (2.33)

where A_bar and sigma_A are the mean and standard deviation, respectively, of attribute A. The mean and standard deviation were discussed in Section 2.2, where A_bar = (1/n)(v1 + v2 + ... + vn), and sigma_A is computed as the square root of the variance of A (see Eq. (2.6)). This method of normalization is useful when the actual minimum and maximum of attribute A are unknown or when there are outliers that dominate the min-max normalization.