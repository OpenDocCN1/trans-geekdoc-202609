

![](img/f26d7f591c2a080d86425985301266a4_363_0.png)

Figure 12.4 Using RMSE and MAE to find iteration count for regularization.

median-absolute error (MAE), as described in Chapter 4. The RMSE criteria is effective when outliers are **not** present in the test set whereas MAE is more suitable for test sets with outliers. When splitting the data into random CV training and test sets, there may be an unknown number of outliers in the test set. Therefore, it is better to use the sum of the RMSE and MAE to find the optimal number of iterations.

In Figure 12.4, each gray trajectory represents a different combination of CV training and test sets, as described above. The dark trajectory is the average of the 10 trajectories and it indicates that an iteration count in the neighborhood of 300 is suitable for this dataset. This value is now fixed for all further comparisons using the neural network.

## 12.2.3 Comparison of LSNN and LCNN

The next step is to use the above methodology to compare least squares NN (LSNN) and log-cosh NN (LCNN). For the purposes of the comparison, we consider four different cases involving outlier inclusion and removal. First, we remove all outliers that were found during EDA (see Table 12.1) and run a comparison between the robust and non-robust regressions. Second, we remove only the $50K data that look suspicious (see Figure 12.1) and rerun the regressions. These two cases will allow us to gain some insight into the inherent problems of the removal of outliers detected during EDA using only boxplots, histograms and quantiles of explanatory and response variables. Third, we keep all the outliers in the dataset and re-run the regressions. Finally, we remove all outliers using the iterative boxplot method (see Chapter 4), which is a very effective method, and rerun the regressions.

A comparison of the four cases, with the number of outliers removed in parentheses, is shown in Table 12.2. The comparison metrics are the RMSE and the MAE. There are several things to note in Table 12.2. First, the RMSE and MAE metrics are higher for LSNN compared to LCNN in all cases on the training set. However, the true measure of the quality of a model is the prediction accuracy on the test set. We see that the first column has the highest errors of the four cases. This is the problem with using EDA as the guide to outlier detection. It removes some inliers along with some outliers, but not necessarily all outliers.

Table 12.2 RMSE and MAE for the Boston Housing Dataset.

| Removal Method (outliers) | Remove All Potential Outliers (158) | Remove Only $50K Data (16) | Keep All Outliers (0) | Remove All True Outliers (52) |
|---|---|---|---|---|
| LSNN | | | | |
| CV train RMSE | 2.66 | 2.13 | 2.42 | 1.72 |
| CV train MAE | 1.27 | 1.22 | 1.37 | 1.02 |
| CV test RMSE | 1.98 | 1.46 | 2.42 | →1.29 |
| CV test MAE | 2.08 | 1.50 | 1.56 | 1.44 |
| LCNN | | | | |
| CV train RMSE | 1.95 | 1.72 | 2.04 | 1.38 |
| CV train MAE | 0.40 | 0.51 | 0.53 | 0.38 |
| CV test RMSE | 1.66 | 1.46 | 2.78 | →1.29 |
| CV test MAE | 1.94 | 1.44 | 1.28← | 1.26← |

The second column produces a noticeable improvement for LSNN just by removing the $50K data. In the case of LCNN, the training error is higher using MAE, but the test scores are lower. In the third column, we find that LCNN is much better than LSNN since LCNN is robust and no outliers have been removed. However, in the fourth column, only the true outliers (52 in total) have been removed so the dataset is outlier-free. Note the left-pointing arrows indicate where LCNN is producing almost identical results for MAE regardless of whether outliers are present or not. Similarly, the right-pointing arrows in the fourth column show that the RMSE values are the same for LCNN and LSNN when true outliers are removed. All the values are roughly the same at about 1.3, which is considered to be about the lowest value obtainable for this dataset.

It is an interesting exercise to take the 52 outliers extracted by the iterative boxplot method to see where they actually land in the original dataset. This is shown in Figure 12.5 for MEDV against the same two variables mentioned earlier (RM and LSTAT). The gray regions are the inlier data and the dark dots are the outliers.

![](img/f26d7f591c2a080d86425985301266a4_364_0.png)

Figure 12.5 Actual outliers (black dots) based on residuals using the iterative boxplot method (see Chapter 4).

Clearly, some of the true outliers would not be detectable prior to regression because they are only detectable in a 14-dimensional space, not a 2-dimensional space. This is the danger of trying to sift out the outliers during EDA. If we removed all 158 potential outliers, there would be 106 inliers that would be inadvertently removed. If we removed only the $50K winsorized data, it would reduce the errors but we would still not catch all the outliers. The only viable options are to run robust regression without removing outliers, or use the iterative boxplot method to remove true outliers and use LSNN or LCNN. As noted earlier, outliers are having a noticeable effect on the overall accuracy of the LSNN model, which should not be used for this dataset unless outliers are removed.

## 12.2.4 Predicting Housing Prices

We now have a model based on the 546 parameters generated using the neural network. This model can be used to predict the price of any new house that is up for sale in the same region. For our purposes, we can predict the prices for the original dataset and compare the predictions against the original prices. The predictions are based on the model from the third column of Table 12.2. This is shown in Figure 12.6. Notice that the histogram is essentially the same but the suspicious $50K homes are gone and the distribution is well-behaved. The error in the prediction, according to the MAE value in Table 12.2, is about $1.3K. This is what we would expect of a very accurate model generated by a neural network using robust methods.

## 12.2.5 RMSE vs. MAE

The results presented in Table 12.2 were obtained for one specific split of the training set into its CV components. To solidify the understanding of how to interpret RMSE and MAE metrics when used with robust methods, we examine the effects of 10 different splits of the training set, one for the original data with outliers and one for outlier-free data (i.e. as done in the last two columns of Table 12.2). Before proceeding, we should remove the INDUS variable since it was found to be a nuisance variable in Chapter 6. Next, we run LCNN for 300 epochs using 12 inputs and 39 units in the hidden layer of the neural network.

![](img/f26d7f591c2a080d86425985301266a4_365_0.png)

**Figure 12.6** Original and predicted housing prices.

![](img/f26d7f591c2a080d86425985301266a4_366_0.png)

Figure 12.7 LCNN CV test set errors on 10 trials comparing RMSE and MAE on datasets with and without outliers.

The CV test results of the 10 trials on the two datasets, each using an 80–20 split, are given in Figure 12.7. On the left, we can clearly see that the RMSE is large in the dataset with outliers compared to the outlier-free data. This is why RMSE is not advisable for use on datasets with outliers. It causes an inflation of residuals which leads to large RMSE values. The outlier-free data produces a relatively constant low value across all 10 trials. On the right panel, we note that MAE is roughly the same whether or not outliers exist in the dataset. We know that the robust MAE metric will be roughly constant (at around 1.5 in this case) across many different configurations of the training and test sets if LCNN is used, regardless of the presence or absence of outliers. The recommendation is to observe both RMSE and MAE when using robust methods.

## 12.2.6 Correlation Coefficients

Finally, we return to the issue of computing the correlation coefficients. In statistics, a correlation coefficient is a numerical measure that quantifies the strength and direction of the linear relationship between two variables. The value of a correlation coefficient ranges from –1 (strong negative correlation) to 1 (strong positive correlation). We noted earlier in Table 12.1 that the correlation coefficients relative to the response variable MEDV could not be trusted due to the presence of outliers. But how do we obtain values that are trustworthy? We must use the outlier-free data. There is no choice here.

Figure 12.8 plots two sets of correlation coefficients for the explanatory variables relative to MEDV. One set is directly taken from Table 12.1. The other set is obtained in the same manner using outlier-free data. Note that most of the values change noticeably when the outliers are removed. Some are higher, while others are lower. For example, the original value of the correlation coefficient is 0.25 for the DIS variable. After removing the outliers, the value jumps to 0.50. This is a significant change in the value. For AGE, the value drops from –0.4 down to –0.6. If accurate values of the correlation coefficients are important for a particular data science application, then outliers must be removed before applying the necessary computations. Again, the iterative boxplot method (see Chapter 4) is the most reliable way to find and remove outliers.

