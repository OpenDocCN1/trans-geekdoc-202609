
# Linear Regression with Regularisation

This is the fundamental reason underlying the bias-variance trade-off. In Chapter 13, we introduced cross-validation. This technique is the method for choosing the bias-variance trade-off. However, it was introduced in a way where we do not have much control over the trade-off itself. We have introduced it for the sake of understanding it. We could make binary decisions to include a feature or not. Regularisation is an approach introduced to balance the bias-variance trade-off in a smoother and more controlled way. The smoothness, in this case, means that if the model is driven by two (not entirely) correlated variables, we can reduce their mutual contribution to the regression model rather than exclude one of them.

## 20.2 REGULARISATION

The regularisation is a method for solving problems of overfitting or problems with significant variance. The method involves introducing an additional penalty in the form of shrinkage of the coefficients estimates. The shrinkage is controlled by an additional parameter, which allows for smooth (not necessarily in the mathematical sense) control of the trade-off.

Generally, an $L_p$ regularisation is used: $L_p = \sum |beta|^p$. For any regularisation, it is important to have the data normalised as we do not want to punish the coefficient just because the reasons are large in magnitude.

The solution to the OLS is by minimising the residual sum of squares:

```
$$\hat{\beta} = \arg min_{\beta} RSS = \arg min (y - X\beta)^T(y - X\beta) \quad (20.13)$$
```

The optimisation problem in eq. (20.13) is unconstrained optimisation. With regularisation, we introduce the constraint on the solution:

```
$$\hat{\beta} = \arg min_{\beta} (y - X\beta)^T(y - X\beta) \quad (20.14)$$
```

```
s.t. $L_p(\beta) \le t, \quad (20.15)$$
```

where parameter $t$ controls shrinkage and $p$ drive how we constrain the vector of parameters. Equivalently, we can rewrite eq. (20.14) into the more familiar form:

```
$$\hat{\beta} = \arg min_{\beta} (y - X\beta)^T(y - X\beta) + \lambda L_p(\beta), \quad (20.16)$$
```

where the last $\lambda L_p(\beta)$ introduces the penalty. The more weight we put on the estimated parameters, the more we are prone to increase variance out of the sample. $\lambda$ is a free parameter, which has to be chosen carefully to make the most out of the penalty. If $\lambda=0$, we recover the original OLS solution, but for $\lambda \to \infty$, the parameters are infinitely penalised and the model prefers trivial solution.

Let us make an important remark at this point. The penalty in a regularisation optimisation problem expressed in eq. (20.16) cannot be applied to the intercept.

For that purpose, it is convenient to demean the dependent variable first by calculating and subtracting the mean from every variable in the data set. When the variables are demeaned, the constrained estimation is performed and the mean added back to the equation when we predict the dependent variable.

The regularisation introduced so far is also known as shrinkage method. The objective is to shrink the estimated parameters and thus control the overfitting of the model. In the next sections, we present two of the most popular methods: the ridge regression, and the lasso regression, respectively.

## 20.3 RIDGE REGRESSION

Ridge regression is a formulation of the OLS solution where an additional penalty on the estimated parameters is imposed and has the form of an $L_2$ norm. A parameter estimated in this way is also known as a ridge estimator.

The ridge estimator is a solution to the problem:

```
$$\hat{\beta}_{\lambda}^{Ridge} = \arg min_{\beta} (y-\mathbf{X}\beta)'(y-\mathbf{X}\beta) + \lambda\beta^T\beta.\quad(20.17)$$
```

where term $\lambda\beta^T$ corresponds to $L_2$ distance. We keep the explicit dependence of the parameter $\lambda$ present in the function of an index. This reminds us that we have added a parameter which has to be properly considered.

The solution to the optimisation (20.17) can be written:

```
$$\hat{\beta}_{\lambda}^{Ridge} = (\mathbf{X}^T\mathbf{X} + \lambda\mathbf{I}_p)^{-1}\mathbf{X}^T y\quad(20.18)$$
```

where $\mathbf{I}_p$ is a unit matrix of dimension $p$.
The ridge estimator has a very convenient form. We can quickly solve it by matrix manipulations using the same sort of techniques we have used to find the OLS solution. This brings little no extra effort as we do not have to perform any optimisation when estimating the ridge estimator.
The matrix representation of the ridge estimator also reveals its original motivation. Imagine the situation where the features used in the data are linearly dependent or perfectly collinear, using the terminology of regression framework. In such a case, we can express one or more features as a linear combination of other features. These features are redundant; they do not that the matrix $XX'$ is not full rank and thus no inverse. Adding $\lambda I$, returns the full rank to the matrix and allows for a calculation of the Moore-Penrose pseudoinverse matrix. The parameters can then be solved.
The ridge regularisation can be perceived as a solution to the perfect collinearity in the data. Presence of collinearity in the data amplifies the importance of bias-variance trade-off, and thus it is tightly linked to our initial objective.

Finally, it is worth pointing out that ridge regression (not the estimator!) can be viewed as an application of the dropout technique, popular in neural networks. Without going into too much detail, we imagine a probability to an observation with certain probability p. Then, after some manipulations, we end up with the formulation of the regression, which is exactly like the one in eq. (20.17). We let the readers show the link between the dropout to drop an observation p and the regularisation parameter λ. We may then understand the usefulness of the dropout regular technique for neural networks calibration, through the lenses of our linear regression knowledge built in this chapter.

Next, let us explore the properties of the ridge estimator. First, we can show that the estimator is biased:

```
$$\hat{\beta}_{\lambda}^{Ridge}=(X^T X + \lambda I_p)^{-1}X^T Y \quad (20.19)$$
```

Wait, where $A=X^T X$ and $\lambda=0$, there is a bias in the estimator. The variance of the $\hat{\beta}_{\lambda}^{Ridge}$ estimator can be expressed using matrix manipulations:

```
$Var[\hat{\beta}_{\lambda}^{Ridge}]=Var[(I_p + \lambda A^{-1})^{-1}\hat{\beta}^{OLS}] \quad (20.25)$
$=(I_p + \lambda A^{-1})^{-1}Var[\hat{\beta}^{OLS}](I_p + \lambda A^{-1})^{-T} \quad (20.26)$
$=\sigma^2(I_p + \lambda A^{-1})^{-1}X^T X^{-1}(X^T X + \lambda I_p)^{-1} \quad (20.27)$
$=\sigma^2[X^T X + \lambda I_p]^{-1}X^T X[X^T X + \lambda I_p]^{-1}]^T. \quad (20.28)$
```

Let us recall the bias-variance formula for the MSE of estimators:

```
$MSE=E((\Theta - \hat{\Theta})^2)=E((\Theta - E[\Theta])^2 + E[\hat{\Theta} - E[\Theta]]^2) \quad (20.29)$
$=E[\Theta - E[\Theta]]^2 + E[\hat{\Theta} - E[\Theta]]^2 - 2E[\Theta - E[\Theta]][\hat{\Theta} - E[\Theta]] \quad (20.30)$
$=Var[\hat{\Theta}] + [Bias[\hat{\Theta}]]^2. \quad (20.31)$
```

It appears that there exists $\lambda^*$ such that $MSE[\hat{\beta}_{\lambda}^{Ridge}] < MSE[\hat{\beta}^{OLS}]$. This is (one of) why we use regularization.

It remains to answer the obvious question, how to identify the value of such $\lambda^*$. The performance of the model for a given $\lambda$ has to be assessed in the out-of-sample context. An intuitive tool to use is the cross-validation technique we have discussed in the previous section. It is convenient to perform the cross-validation across a grid of $\lambda$ values and optimise for $\lambda$ based on the estimated landscape in terms of measure like RMSE. We will show the details in the implementation section.
