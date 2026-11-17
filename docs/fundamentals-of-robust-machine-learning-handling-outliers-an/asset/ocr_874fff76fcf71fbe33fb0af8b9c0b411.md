Another problem with the MSE metric is that the units are not the same as the response variable. This can be fixed by using the RMSE which produces the same units of measure as the response variable. The RMSE is given by

\( RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^n (y_i - \hat{y}_i)^2} = \sqrt{\frac{1}{n} \sum_{i=1}^n r_i^2} \). \(\text{(4.8.2)}\)

For the two cases of Figure 4.19, RMSE = 5.4 for LS and RMSE = 6.5 for LC. Of course, there is no change in the outcome of which method is better according to the RMSE metric. Again, LS is better than LC based on the RMSE, which is misleading. The reason is that the line fitted by LC is further away from the outliers and this gives rise to a higher RMSE. This will always be the case since the outliers will be far from the regression line or hyperplane in robust regression. On the other hand, LS will try to balance the residuals of the outliers and inliers to reduce the RMSE. Therefore, the MSE or RSME statistic should only be selected when working with outlier-free datasets.

# 4.8.2 Median Absolute Error (MAE)

We need to find a better evaluation statistic with outliers in mind. A robust metric is the residual MAE given by

\( MAE = \text{median}(|y_1 - \hat{y}_1|, |y_2 - \hat{y}_2|, \dots, |y_n - \hat{y}_n|). \) \(\text{(4.8.3)}\)

Here, the median is used so it is a robust error measure. If the MAE is computed on the same dataset as in Figure 4.19, then for LS, we have MAE = 3.45 and for LC, we have MAE = 0.49. Hence, the results favor LC by a substantial margin. This robust metric is much more suitable for datasets with outliers as it takes into account that the robust method would necessarily have larger residuals due to outliers. This was seen earlier in the residual histograms of Figure 4.19.

Another metric often used is the mean absolute error (MnAE) given by

\( MnAE = \frac{1}{n} \sum_{i=1}^n |y_i - \hat{y}_i| = \frac{1}{n} \sum_{i=1}^n |r_i|. \) \(\text{(4.8.4)}\)

Typically, this metric uses the same acronym as the MAE. Both are referred to in the literature as MAE. To avoid confusion between the two, we use MnAE.$^3$ Beware that this metric is not robust because it uses the mean. It is somewhat better than MSE since it is not squaring the errors so the difference is not exaggerated. In the case of Figure 4.19, the MnAE = 4.24 for LS and MnAE = 3.98 for LC. In this case, it slightly favors LC even though this metric is not robust. However, it can favor LS in other cases even when LC is better. Therefore, it is not as reliable a metric as MAE when comparing LS to LC. The MAE is the only truly robust metric.

Now consider Figure 4.20 in which there are no outliers. For this case, the MSE = 0.169 and MAE = 0.055 for LS, whereas MSE = 0.170 and MAE = 0.054 for LC. They are almost identical which