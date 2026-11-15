
We should note here that penalty functions are widely used even in the absence of multicollinearity. For example, they can be used to improve model prediction using regularization or for subset selection to reduce model complexity and improve model interpretability. Referring back to Chapter 1, consider the geometric plots of Figures 1.8 and 1.9. The contour lines around the unbiased estimate, indicated by “x”, are associated with the loss function (either LS or rank). The circles and diamonds represent the constraints of the penalty functions (ridge and LASSO, respectively). As the degree of regularization is increased through \(\lambda\), different estimates are obtained. Typically, PEs shift unbiased estimates to a series of biased estimates from which we can choose the optimal one that provides accurate prediction. This ultimate goal will drive our discussions in the sections to follow.

## 2.4 Ridge Regression

Ridge regression (Hoerl and Kennard, 1970) was developed as a way to mitigate the effects of high variance due to multicollinearity by producing a set of biased estimates with lower variance using an L2 penalty function applied to the quadratic loss function. The degree of bias is adjusted using a tuning parameter \(\lambda\) which can range from 0 to infinity, but usually an optimal value is selected as described later.

### 2.4.1 Ridge Applied to Least Squares Estimation

The penalty function of ridge applied to the quadratic loss function is given by

\(J^{\text{LS-Ridge}}(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X}\boldsymbol{\beta})^{\mathsf{T}}(\mathbf{y} - \mathbf{X}\boldsymbol{\beta}) + \lambda \boldsymbol{\beta}^{\mathsf{T}} \boldsymbol{\beta}.\)

(2.4.1)

To obtain the ridge estimates, we take the derivative of \(J^{\text{LS-Ridge}}(\boldsymbol{\beta})\) w.r.t. \(\boldsymbol{\beta}\) and set it to 0, i.e.

\(\frac{\partial J^{\text{LS-Ridge}}(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}} = -2\mathbf{X}^{\mathsf{T}}(\mathbf{y} - \mathbf{X}\boldsymbol{\beta}) + 2\lambda \boldsymbol{\beta} = 0.\)

(2.4.2)

Then, it follows that

\(-\mathbf{X}^{\mathsf{T}}\mathbf{y} + \mathbf{X}^{\mathsf{T}}\mathbf{X}\boldsymbol{\beta} + \lambda \boldsymbol{\beta} = 0,\)

(2.4.3)

and re-arranging gives the ridge regression estimator,

\(\hat{\boldsymbol{\beta}}_n^{\text{LS-ridge}} = (\mathbf{X}^{\mathsf{T}}\mathbf{X} + \lambda \boldsymbol{I}_p)^{-1}\mathbf{X}^{\mathsf{T}}\mathbf{y},\)

(2.4.4)

where \(\boldsymbol{I}_p\) is a \(p \times p\) identity matrix. This is the standard form of the ridge estimate. We can see that problems arising from multicollinearity are circumvented by adding \(\lambda\) to the diagonal elements of \(\mathbf{X}^\top \mathbf{X}\). For some \(\lambda > 0\), the matrix \((\mathbf{X}^\top \mathbf{X} + \lambda \mathbf{I}_p)\) is invertible. Furthermore, by careful selection of \(\lambda\), an accurate prediction model can be obtained in the presence (or absence) of multicollinearity.

To gain insight into the ridge mechanism, it is possible to re-write Eq. (2.4.4) in terms of \(\hat{\beta}^{\text{LS}}\) by multiplying all terms in Eq. (2.4.3) by \((\mathbf{X}^\top \mathbf{X})^{-1}\) and rearranging to obtain

```
\(-\hat{\beta}_n^{\text{LS}} + \beta + \lambda C^{-1} \beta = 0,\) (2.4.5)
```

where \(C^{-1} = (\mathbf{X}^\top \mathbf{X})^{-1}\). In doing so, we are assuming \(\mathbf{C}\) is invertible and hence, there is assumed to be no multicollinearity in \(\mathbf{X}\); in general, it may not be the case. Then

```
\(\hat{\beta}_n^{\text{LS-ridge}} = (\mathbf{I}_p + \lambda C^{-1})^{-1} \hat{\beta}_n^{\text{LS}}.\) (2.4.6)
```

In this form of ridge, we can view \(\mathbf{W}(\lambda) = (\mathbf{I}_p + \lambda C^{-1})^{-1}\) as a weight matrix that acts as a shrinkage operator on \(\hat{\beta}_n^{\text{LS}}\). The higher the value of \(\lambda\), the greater the shrinkage. As mentioned, many data sets do not have multicollinearity problems and, even in those cases, ridge is very effective in building a better model for prediction.

We have stated that ridge shrinks the unbiased estimates but have not described the manner in which this shrinkage occurs. To develop some insight, we can make a simplifying assumption that \(\mathbf{C}\) is the identity matrix, \(\mathbf{I}_p\). That is, \(\mathbf{X}\) is an orthonormal matrix. If applied to Eq. (2.3.7), we obtain \(\hat{\beta}_n^{\text{O-LS}} = \mathbf{X}^\top \mathbf{y}\), the orthonormal-LS estimator. And if applied to Eq. (2.4.6), it reduces to

```
\(\hat{\beta}_n^{\text{O-ridge}} = \frac{\hat{\beta}_n^{\text{LS}}}{1 + \lambda},\) (2.4.7)
```

where \(\hat{\beta}_n^{\text{O-ridge}}\) is the estimator for the orthonormal case. This case tells us something useful about the basic mechanism of ridge. It illustrates that ridge regression applies a factor of \(1/(1+\lambda)\) to shrink the \(\hat{\beta}_n^{\text{LS}}\) values until they reach 0 at \(\lambda = \infty\). This is called the orthogonal ridge-type estimator in this book.

However, ridge does not actually scale all parameters by the same amount as implied in the above equation. To get a better handle on the true nature of ridge, let us assume that \(C^{-1}\) is a diagonal matrix with non-zero values \(C^{jj}\), \(j=1, ..., p\). All off-diagonal terms are set to zero implying no correlation between the parameters. Therefore, we can write that for the \(j\)th parameter that

```
\(\hat{\beta}_j^{\text{D-ridge}} = \frac{\hat{\beta}_j^{\text{LS}}}{1 + \lambda C^{jj}},\) (2.4.8)
```

where \(\hat{\beta}_j^{\text{D-ridge}}\) is the estimate for the diagonal \(\mathbf{C}^{-1}\) case. This is the diagonal ridge-type estimator. We may recall that the variance of \(\hat{\beta}_n^{\text{LS}}\) is given by the covariance matrix

\(\text{Var}(\hat{\beta}_n^{\text{LS}}) = \sigma^2(\mathbf{X}^{\top}\mathbf{X})^{-1} = \sigma^2\mathbf{C}^{-1},\)

where \(\sigma^2\) is the variance of the residuals. Since \(\mathbf{C}^{-1}\) is assumed to be diagonal, we can set \(\lambda = \lambda_2\sigma^2\) in Eq. (2.4.8) and re-write the above as

\(\hat{\beta}_j^{\text{D-ridge}} = \frac{\hat{\beta}_j^{\text{LS}}}{1 + \lambda_2\sigma^2 C^{jj}} = \frac{\hat{\beta}_j^{\text{LS}}}{1 + \lambda_2 \text{Var}(\hat{\beta}_j^{\text{LS}})}.\)

As \(\lambda_2\) increases, each \(\hat{\beta}_j^{\text{LS}}\) shrinks at a rate determined by the variance of \(\hat{\beta}_j^{\text{LS}}\) to produce \(\hat{\beta}_j^{\text{D-ridge}}\). We can consider the following cases:

- (a) If \(\sigma^2 C^{jj}\) is very small, i.e. much smaller than 1, then \(\hat{\beta}_j^{\text{D-ridge}}\) will not change rapidly as \(\lambda_2\) increases.
- (b) If \(\sigma^2 C^{jj}\) is very large, i.e. much greater than 1, then \(\hat{\beta}_j^{\text{D-ridge}}\) will be quickly reduced towards zero as \(\lambda_2\) increases.
- (c) Moderate values of \(\sigma^2 C^{jj} \approx 1\) will lie between the other two cases.

This is illustrated in Figure 2.1.

The key intuition developed here is that the shrinkage rate to first-order is controlled by the variance of each estimate. That is, a higher variance forces a smaller estimate and a correspondingly smaller variance. Of course, in reality, the true ridge estimator considers the entire covariance matrix, including all \(C^{ij}\) terms where \(i, j = 1, ..., p\), to obtain the full effects of ridge shrinkage. But it is instructive to view ridge regression in this fashion to gain insight into its behavior. As we will see shortly, ridge traces capture the complex trajectories of each of \(\beta_j\) as \(\lambda_2\) increases. We will typically use \(\lambda_2\) as the ridge tuning parameter.

### 2.4.2 Ridge Applied to Rank Estimation

The rank loss function is the dispersion function for multiple linear regression as follows

\(D_n(\beta) = \sum_{i=1}^n (y_i - \mathbf{x}_i^\top \beta) a_n(R_n(\beta)).\)

Ridge regression is applied to rank-based methods in a manner similar to LS:

\(D^{\text{R-ridge}}(\beta) = D_n(\beta) + \lambda_2 \beta^\top \beta,\)
