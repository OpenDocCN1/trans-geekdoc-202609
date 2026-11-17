

The convexity condition is needed to find a unique minimum. We can assess the convexity of the loss function using the second derivative:

\(\psi'(r_i) = \frac{\partial^2 \rho(r_i)}{\partial^2 r_i}.\) (2.6.4)

Then, the **convexity property** is satisfied if and only if

\(\psi'(r_i) \ge 0 \text{ for all } r_i\) (2.6.5)

and it is strictly convex if \(\psi'(r_i) > 0\) for all \(r_i\).

The M-estimation approach to specifying loss functions can also be used for non-robust estimators. For \(L_2\), we have that

\(\rho_{L_2}(r_i) = \frac{r_i^2}{2}.\)

Therefore,

\(\psi_{L_2}(r_i) = r_i\)

and

\(\psi'_{L_2}(r_i) = 1.\)

So \(L_2\) has a strictly convex loss function. Now if we check \(L_1\) we find that

\(\rho_{L_1}(r_i) = |r_i|.\)

Therefore,

\(\psi_{L_1}(r_i) = \text{sgn}(r_i)\)

and

\(\psi'_{L_1}(r_i) = \begin{cases} \text{undefined} & \text{if } r_i = 0 \\ 0 & \text{if } r_i \neq 0 \end{cases}.\) (2.6.6)

The function is convex but not strictly convex and is undefined at \(r_i = 0\). So we cannot guarantee that a unique solution exists. In fact, there may be an infinite number of localized solutions using \(L_1\).

Figure 2.5 plots the \(\rho(r_i)\) and \(\psi(r_i)\) functions for \(L_1\) and \(L_2\). Note that \(L_1\) follows an absolute function, \(|r_i|\), while \(L_2\) follows a quadratic function, \(r_i^2/2\). The problem with using \(L_2\) is that the residuals are squared, which amplifies the importance of large residuals. During linear regression, outliers are considered to be, in some sense, more important than the majority of the data since outliers tend to have larger residuals. Thus, it is highly sensitive to outliers. This is the main problem with the \(L_2\) estimator.

The \(L_1\) estimator is not as sensitive to outliers because it sums the absolute value of the residuals in the loss function, but it has other problems. The \(\rho(r_i)\) function has a distinctive kink at \(r_i = 0\). When we examine its first derivative in the lower-left panel of Figure 2.5, we note that it is a discontinuous function whereas the first derivative of \(L_2\) is continuous, as seen in the lower-right panel. The discontinuity of \(L_1\) poses problems both mathematically and in numerical optimization when used for machine learning. Further, the second derivative of \(L_1\) produces an impulse function at the origin while the second derivative of \(L_2\) is flat and continuous at a value of 1. Clearly, \(L_1\) and \(L_2\) both have notable disadvantages so alternative methods are needed to handle outliers.

![](img/f26d7f591c2a080d86425985301266a4_72_0.png)

The question that immediately arises is: How do we come up with a better M-estimator? The answer is to try out different options and compare them against one another. In particular, if you want to find the median of the data and you find that the \(L_1\) loss function is not suitable, then any other \(\rho(r_i)\) function that seeks the median would be a suitable replacement. In a later section, we will consider the Huber estimator as our first M-estimator in this chapter, followed by the log-cosh estimator in the next chapter.

Notation: The general form of an M-estimator is given by:

\[
\hat{\boldsymbol{\beta}}^* = \operatorname*{argmin}_{\beta} \left[ \sum_{i=1}^n \rho(y_i - \mathbf{x}_i^T \boldsymbol{\beta}) \right].
\]

The use of **argmin** indicates the loss function should be minimized to find the associated \(\boldsymbol{\beta}\) located at the minimum. The superscript * is usually replaced by acronyms such as L1, L2, LS, LAD, LC, and H to refer to the specific type of loss function used.

## 2.7 Least Squares Estimation (LSE)

We are now ready to examine the least squares method in a more formal setting using the proper notation. Consider the multiple linear model in matrix form as follows:

\(y = \mathbf{X}\boldsymbol{\beta} + \boldsymbol{\varepsilon}.\) (2.7.1)

where \(\mathbf{y} = (y_1, \dots, y_n)^T\) is a response vector, \(\mathbf{X}\) is an \(n \times (d + 1)\) design matrix of constants with an embedded column of 1’s, and \(\boldsymbol{\varepsilon} = (\varepsilon_1, \dots, \varepsilon_n)^T\) is the error term. Here we assume \(\boldsymbol{\varepsilon} \sim N(0, \sigma^2 \mathbf{I}_n)\), the normal distribution with mean 0 and variance-covariance matrix \(\sigma^2 \mathbf{I}_n\). Regression parameters \(\boldsymbol{\beta} = (\beta_0, \dots, \beta_d)^T\) are the \(d + 1\) coefficients of interest.

The solution to a multidimensional problem is no longer a line but rather a plane or hyperplane. An example of a two-variable regression model and its solution is illustrated in Figure 2.6. In this case, the slopes are \(\beta_1\) and \(\beta_2\), while the intercept on the y-axis is \(\beta_0\). The slopes represent the angle of the plane in each dimension. Beyond two dimensions, the plane becomes a hyperplane. For obvious reasons, the hyperplanes cannot be visualized; however, the same concepts apply.

We can write the L2 loss function in two different ways. The first uses matrix notation, as follows:

\(J(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X}\boldsymbol{\beta})^T (\mathbf{y} - \mathbf{X}\boldsymbol{\beta}).\) (2.7.2)

This is just the sum of the squares of the errors written in matrix notation. To obtain the least squares estimates, \(\hat{\boldsymbol{\beta}}^{\text{LS}}\), we minimize this loss function by taking the derivative of \(J(\boldsymbol{\beta})\) w.r.t. \(\boldsymbol{\beta}\) and setting it to 0, that is

\(\frac{\partial J(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}} = -2\mathbf{X}^T (\mathbf{y} - \mathbf{X}\boldsymbol{\beta}) = 0.\) (2.7.3)

Then, it follows that

\(-\mathbf{X}^T \mathbf{y} + \mathbf{X}^T \mathbf{X} \boldsymbol{\beta} = 0.\) (2.7.4)

![](img/f26d7f591c2a080d86425985301266a4_73_0.png)

Figure 2.6 A plane with slopes \(\beta_1\) and \(\beta_2\) and intercept \(\beta_0\) representing the solution for a multiple linear regression problem with two variables.

which can then be rearranged to produce the well-known closed-form solution:

\(\hat{\boldsymbol{\beta}}^{\text{LS}} = (\mathbf{X}^{\text{T}} \mathbf{X})^{-1} \mathbf{X}^{\text{T}} \mathbf{y}.\) (2.7.5)

This is the direct matrix solution for LSE and it produces the best linear unbiased estimate (BLUE), provided \(\mathbf{X}^{\text{T}}\mathbf{X}\) is invertible. By best, we mean the one with the _lowest variance_. It is also referred to in the literature as the ordinary least squares (OLS) estimator. There are volumes of books and information available about OLS which we will not cover here.

Another way to obtain the least squares estimates is to apply an iterative method. We saw earlier that the \(L_2\) loss function is given by

\(L_2 \text{ loss} = \frac{1}{2} \sum_{i=1}^n r_i^2 = \frac{1}{2} \sum_{i=1}^n (y_i - \boldsymbol{x}_i^{\text{T}} \boldsymbol{\beta})^2.\) (2.7.6)

Then, the least squares solution is obtained as follows:

\(\hat{\boldsymbol{\beta}}^{\text{LS}} = \operatorname{argmin}_{\boldsymbol{\beta} \in \mathbb{R}^{d+1}} \left[ \frac{1}{2} \sum_{i=1}^n (y_i - \boldsymbol{x}_i^{\text{T}} \boldsymbol{\beta})^2 \right].\) (2.7.7)

Rather than try to solve this equation in closed form, it is more appropriate to use gradient descent to find the minimum. If we take the derivative of the loss function w.r.t. \(\beta_j\) and use it in the gradient descent iterative equation, we obtain:

\(\beta_j^{(t+1)} = \beta_j^{(t)} - \ell' \sum_{i=1}^n (y_i - \boldsymbol{x}_i^{\text{T}} \boldsymbol{\beta})(-x_{ij}).\) (2.7.8)

At each iteration, \(t\), we simply update each \(\beta_j^{(t)}\), \(j = 0, \dots, d\), with the gradient term to produce \(\beta_j^{(t+1)}\) until convergence. The direct matrix approach and the iterative approach produce identical results, if the matrix is well conditioned. However, the iterative approach does not require a matrix inversion and therefore avoids issues posed by a large \(\mathbf{X}\) matrix, or the possibility of an ill conditioned or singular matrix. To avoid multicollinearity problems, it is also well suited to the application of a penalty function, such as ridge or LASSO (as described in Chapter 5).

We can gain further insight into the solution if we state the loss function in terms of residuals in the form of an M-estimator as follows:

\(L_2 \text{ loss} = \frac{1}{2} \sum_{i=1}^n \rho_{L_2}(r_i) = \frac{1}{2} \sum_{i=1}^n r_i^2.\) (2.7.9)

which is just a restatement of an earlier MLE result. Then, taking the derivative w.r.t. \(r_i\) and setting it to 0, we obtain:

\(\sum_{i=1}^n r_i = 0.\) (2.7.10)

The solution of the \(L_2\) loss function is a set of estimates that forces the sum of the residuals to be identically 0. Hence, in effect, we are seeking the **mean** line through the data such that the average error is 0.

