
![](img/f26d7f591c2a080d86425985301266a4_196_0.png)

Figure 6.9 Traces of LC-ridge estimates as a function of \(\lambda\).

result based on five trials. We could continue to do more runs but roughly the same result would be obtained.

The last step is to perform estimation using LC-ridge and \(\lambda = 8 \times 10^{-6}\) to obtain the model. Consider the LC-ridge traces of Figure 6.9 with a vertical line representing the resulting model. Note that it has similar characteristics to the LS-ridge traces in Figure 6.3 and the vertical line is roughly in the same place. One line was produced using the quadratic risk and the other using the test RMSE. In this case, with only three outliers the results are expected to be similar. However, in other datasets, with a larger percentage of outliers, the LS-ridge results may not be acceptable since the estimates will not be accurate and the variances will be large. Therefore, datasets with outliers will require robust regularization to build an accurate and general model.

## 6.7 Model Complexity

The complexity of a model generally refers to the number of parameters used by the model. A model with only a few parameters is a low-complexity model, and one with a large number of parameters is a high-complexity model. It is a goal in data science to produce a model that uses the fewest variables while still retaining high predictive power. There are many reasons for this. One is that fewer variables produce a more compact model which is highly desirable to avoid overfitting. It is also easier to assess their relative importance if there are fewer of them. The second issue is that there are variables that add noise to the model, and it is preferable to remove these variables. Third, and perhaps more subtly, the variance of the residuals (which ideally should be small) can be large if there are too many variables in the model. To understand this point, consider the unbiased estimator of residual variance which is given by

\(\hat{\sigma}^2 = \frac{1}{n - (d + 1)} \sum_{i=1}^n (r_i - \bar{r})^2.\) (6.7.1)

As \((d + 1)\) approaches \(n\), the residual variance goes to infinity. Hence, keeping \(d\) small will reduce the variance of all parameters because they all depend on \(\hat{\sigma}^2\).

In effect, we have another bias-variance trade-off involving the number of variables in our model. If we have too many variables, we risk overfitting the dataset and that leads to a high variance. If we have too few variables, we risk underfitting which creates a high bias situation. Our next objective will be to seek the optimal number of variables using some form of feature selection.

### 6.7.1 Variable Selection Using LS-LASSO

One useful application of penalty functions involves using the LASSO penalty to select the optimal number of parameters. The diabetes dataset will be used to demonstrate the procedures. It has 10 variables, namely, s1, s2, s3, s4, s5, s6, age, bmi, bp, and sex. With domain knowledge, the relative importance of each variable may already be known. However, the approach to be described can be used with or without domain knowledge. The first step is to generate the LS-LASSO traces as shown in Figure 6.10. In contrast to the LS-ridge traces, the LS-LASSO traces all terminate abruptly on the \(\lambda\)-axis. The zero points are indicated with a "\(\bullet\)" for each parameter. By selecting a suitable \(\lambda\), a subset of the variables can be removed. This is how it is able to perform variable selection by setting some variables to 0.

To clarify the procedure, if a vertical line is drawn at \(\lambda = 0.25\) on the LS-LASSO traces, then any variable to the left of the line can be removed, while those on the right are kept. In this case, s1, age, s2, s4, and s6 are all set to 0, meaning that they are removed from the model. By doing so, a compact model is produced for the diabetes dataset involving only s3, s5, bp, bmi, and sex. The LS-ridge traces do not provide this ability since all variables tend to reach 0 gradually rather than abruptly (cf. see Figure 6.3).

### 6.7.2 Variable Ordering Using LC-aLASSO

There are many different ways to assess variable importance but most of them rely on an outlier-free dataset. For example, the adjusted-R\(^2\), BIC, AIC, and \(C_p\) metrics used for subset selection (see James et al. 2023)\(^5\) require either the mean or the standard deviation, which are not robust. Therefore, we suggest removing outliers (see Chapter 4) before using these techniques. Another approach is to use the absolute value of the t-statistic (see Chapter 5) obtained from an LC linear regression. In this section, we describe an alternative method using an oracle penalty function, specifically aLASSO. This method provides a visualization of variable ordering using penalty traces (see Saleh et al. 2022).

![](img/f26d7f591c2a080d86425985301266a4_198_0.png)

Figure 6.10 Traces of LS-LASSO estimates as a function of \(\lambda\).

Before proceeding further, we note that LS-LASSO is extremely valuable in high-dimensional applications where there are a large number of variables, say d = 10,000, because it will remove most of the unimportant variables. But here we are concerned with a proper ordering of a smaller number of variables. In this situation, there are two notable problems with LS-LASSO. The first is obviously the lack of robustness of LS. The second is the lack of the oracle property in LASSO (see Chapter 5). We can remedy both by utilizing LC-aLASSO.

The first step is to generate the LC-aLASSO traces as shown in Figure 6.11. The figure provides the LC-aLASSO variable ordering labeled from 1 to 10. According to LC-aLASSO, the most important variable is s5, then bmi and then bp. If we compare it against Figure 6.10, it is clear that the variables reach 0 in a different order compared to LS-LASSO. In the case of LS-LASSO, bmi is the most important, slightly more than s5 and then a distant third is bp. The complete orderings of all 10 variables are provided in Table 6.2 along with another ordering based on the t-statistic of the unpenalized LC estimates. Recall from Chapter 5 that, by ranking the |t-statistic|, we obtain an approximate ordering of the variables. The t-statistic itself is the ratio of the estimate to the standard error. Note that all three methods (t-statistic, LC-aLASSO, and LS-LASSO) produce different orderings (see columns 5, 6, and 7). Which is correct? The t-statistic method and LC-aLASSO are the same for the last five variables. However, the only one with the oracle property is LC-aLASSO and we know that asymptotically, it will produce the correct order. According to the theory, this is a good ordering of the variables based on the given data.

![](img/f26d7f591c2a080d86425985301266a4_199_0.png)

Figure 6.11 Traces of LC-aLASSO estimates as a function of \(\lambda\), with variable ordering labeled from most important (1) to least important (10).

But how can this be verified? There are many ways to do this but one way is to simply create a training set and test set and then run 10 different LC regressions without a penalty function. The first run will have only one variable; the second with two variables, and so on. The starting variable is the most important one, followed by the addition of the next most important and so on until all 10 variables are included. The variable order is provided in the LC-aLASSO column of the table. For each case, we obtain the estimates on the training set and monitor the prediction error on the test set. The resulting plot should have a convex shape according to an inherent bias–variance trade-off. If there are any spikes in the plot, there may be a problem with the ordering, perhaps due to the limits of a finite amount of data.

To proceed, we first define a training set and a test set, but this time we choose an even split between the two. If we do not use a 50-50 split on the diabetes dataset, the estimates may not be accurate or the test MSE may not be reliable. In general, there needs to be sufficient data in both the training and test sets to obtain acceptable results. At each step, the number of regression variables will be different. The training and testing loops can be performed using k-random validations and the test MSE is averaged over all the trials. Note that the effect of outliers is not significant in the diabetes dataset so the use of the MSE is acceptable.

We start with only variable s5 in the model to be built using the training set and then compute the test MSE. As we incrementally add bmi and then bp to the regression model, we expect the test MSE to decrease because the model accuracy is improving. However, at some point, noise variables will be added
