
![](img/f3b106d7e76ae3afcec8895afa28732c_93_0.png)

Figure 2.2 Two outliers found in the Q–Q plot for the Swiss data set. This is a plot of the percentiles of the residuals (dots) against the standard normal distribution (line).

(James et al., 2013). There are 47 observations in this data set. We randomly pick observations (with replacement) to create a new data set containing 47 observations, which implies that we may have repeated observations in our synthesized data set. We then compute the estimates and repeat this procedure multiple times to generate parameter distributions. Figure 2.3 shows the LS estimate distributions after sampling the data set in this manner. The mean values of each distribution are the unbiased estimates. The spread of the estimates around the mean captures the variance. We note that β2, β3 and β5 have large variances, as confirmed by Table 2.3. In addition, β0 has a large variance but we will not be applying the ridge penalty to it; only β1 ... β5 will be penalized because they are directly associated with the response. In fact, we will center the data so that the intercept is not even calculated when applying ridge.

## 2.5.3 Reducing Variance using Ridge

In order to reduce the variance, we can apply ridge regression. It is useful to visually examine the shrinkage in action of one parameter and its variance, as shown in Figure 2.4, with embedded boxplots. This figure was produced by

![](img/f3b106d7e76ae3afcec8895afa28732c_94_0.png)

Figure 2.3 Sampling distributions of rank estimates.

taking the ridge weight matrix of Eq. (2.4.6) and progressively increasing the tuning parameter \(\lambda_2\) by an order of magnitude. The values chosen were 1, 10, 100 and 1000. As we can observe, the effect of the LS-ridge on \(\beta_5\) is that the sample mean value is reduced towards the null while the bootstrapped sample variance is likewise reduced. This occurs for all other parameters at different rates, and for both LS and rank methods.

## 2.5.4 Ridge Traces

It is instructive to know what happens to each parameter as we vary \(\lambda_2\). As we increase \(\lambda_2\), the estimates tend to decrease but exactly how they decrease is not as easy to predict. In this section, we examine the so-called ridge traces whereby the estimates are plotted as a function of \(\log(\lambda_2)\). Typically, plotting the estimates as a function of \(\lambda_2\) is not as informative as \(\log(\lambda_2)\) because of the large scale over which shrinkage occurs. In this and other chapters, we will be using traces to illustrate many of the characteristics and properties of penalty estimators. We use ridge to introduce the traces and their meaning.

![](img/f3b106d7e76ae3afcec8895afa28732c_95_0.png)

**Figure 2.4** Shrinkage of \(\beta_5\) due to increase in ridge tuning parameter, \(\lambda_2\).

For a given trace, we have to build \(m\) models, one for each selected \(\lambda_2\). Earlier, we considered three different equations with \(\mathbf{C}^{-1}\) being an orthonormal matrix in Eq. (2.4.7), a diagonal matrix in Eq. (2.4.10) and a full matrix in Eq. (2.4.6). These cases are shown in Figure 2.5 for O-ridge, D-ridge and LS-ridge, respectively. Additionally, the R-ridge trace using Eq. (2.4.12) is also provided. They are all different in their shrinkage behavior which gives us some insight into their inherent properties. Two important points are worth mentioning here. First, if we pick any vertical line associated with a specific \(\lambda_2\) value, the intersection of that line and the curves would give us the penalized estimates. We should note that there is nothing magical about a particular \(\lambda_2\) value. It depends on the scale of values associated with the corresponding estimator. A low or high value of \(\lambda_2\) does not have any specific meaning. Second, the traces for ridge do not theoretically reach 0 unless \(\lambda = \infty\), although many may appear to reach 0 at a much earlier value. This point will become more meaningful when we discuss the LASSO traces.

It is interesting to observe that the orthonormal case exhibits the basic shrinkage operation of ridge. We see all five variables of the top-left of Figure 2.5 converging towards zero at the same rate because their decay is controlled only by \(1/(1 + \lambda_2)\). The diagonal case is much more interesting since the trajectories

![](img/f3b106d7e76ae3afcec8895afa28732c_96_0.png)

Figure 2.5 Ridge traces for orthonormal, diagonal, LS, and rank estimators (m = 40).

are controlled by $1/(1+\lambda_2 C^{JJ})$. Note that the top-right of Figure 2.5 more closely resembles the accurate plots of LS-ridge and R-ridge shown in the two bottom panels, respectively. This validates the equations showing that $C^{JJ}$ controls most of the trace characteristics. The diagonal traces only capture the *uncorrelated trajectory* of each parameter so the traces monotonically converge to zero without ever crossing zero. The full ridges traces may not be monotonic in their behavior and may cross zero and change signs. Still, the diagonal case gives us insight into the nature of the traces. In fact, the orthogonal and diagonal cases serve as simple but effective penalty estimators in their own right (cf. Saleh et al., 2019).

The traces for LS-ridge and R-ridge illustrate the differences between these two cases. In the R-ridge case, variable $Ex$ is clearly non-monotonic but this is not as noticeable in the LS-ridge case. The main difference between the two traces lies along the \(\log(\lambda_2)\)-axis due the difference in the unpenalized loss functions for each method. A simple forward or backward translation of one or the other would align them. In general, the shape of LS and rank traces for ridge may differ slightly with no outliers, but more noticeably when outliers are present.

## 2.6 Selection of Ridge Parameter \(\lambda_2\)

Naturally, questions arise as to how to set the proper value of \(\lambda_2\) and the nature of the trade-off as we shrink the estimates and their variances. In short, we are trading off bias against variance (i.e. under-fitting vs. over-fitting), and the proper value of \(\lambda_2\) is based on a desired prediction performance of our model. We now delve deeper into each question in the context of LS, which will be similar to rank. Note that an optimal \(\lambda_2\) value is unique to an estimator and generally cannot be compared or transferred between estimators. Additionally, the optimal \(\lambda_2\) usually lies in a range of values in practice, as opposed to being one unique value.

### 2.6.1 Quadratic Risk

We start by describing the infamous *bias-variance trade-off* which is at the heart of selecting the optimal \(\lambda_2\). We know the meaning of variance – the degree of uncertainty associated with an estimate. A working definition of the bias is the difference between the expected value of a given estimator, \(\mathbb{E}(\hat{\boldsymbol{\beta}}_n)\), and the true value, \(\boldsymbol{\beta}\). An estimator is said to be unbiased if \(\mathbb{E}(\hat{\boldsymbol{\beta}}_n) = \boldsymbol{\beta}\). When we decrease the variance, we tend to increase the bias. We seek to balance the two by choosing the appropriate \(\lambda_2\).

It is well known that LSE provides the minimum variance of a set of linear unbiased estimates so it would appear that we cannot improve it. However, the variance may still be rather large if there is strong correlation between variables, i.e. a certain amount of collinearity exists among the columns of the design matrix. By applying a penalty function, we increase the bias and decrease the variance until the estimates minimize a given statistic.

Consider the use of the mean-square error (MSE) (Montgomery et al., 2012), also referred to as quadratic risk (and ADL\(_2\)-risk in Chapter 3), for the purposes of finding the optimal \(\lambda_2\) to balance the bias and variance. The MSE of the estimates given by

```
MSE(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}}) = \text{tr}(\text{Var}(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}})) + \text{bias}^2(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}})
```

where tr(\(\boldsymbol{M}\)) is the trace of some matrix, \(\boldsymbol{M}\), which involves adding up the diagonal terms of \(\boldsymbol{M}\), and let bias\(^2(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}}) = \text{bias}^\top(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}})\text{bias}(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}})\). The formulas for bias and variance for LS-ridge are given by

```
bias^2(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}}) = \lambda_2^2 \boldsymbol{\beta}^\top (\mathbf{X}^\top \mathbf{X} + \lambda_2 \mathbf{I}_p)^{-2} \boldsymbol{\beta},
```
