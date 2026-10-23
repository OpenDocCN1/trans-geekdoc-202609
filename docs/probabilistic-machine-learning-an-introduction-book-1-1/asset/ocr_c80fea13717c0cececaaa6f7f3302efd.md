# 11.2.3.3 Partial regression (2d inputs)

From Eq. (11.27), we can compute the regression coefficient of Y on X as follows:

$R_{Y X} \triangleq \frac{\partial}{\partial x}\mathbb{E}[Y|X=x]=w_1 = \frac{\sigma_{XY}}{\sigma_X^2}$ (11.29)

This is the slope of the linear prediction for Y given X.

Now consider the case where we have 2 inputs, call them X and Z, so Y = w0 + wX X + wZ Z + ε, where E[ε] = 0. The least squares estimate of the coefficients are obtained when ε is uncorrelated with each of the regressors, so Cov[ε,X] = E[εX] = 0 and Cov[ε,Z] = E[εZ] = 0. Using this, one can show that the optimal coefficients for X and Y are given by

$w_X = R_{Y X·Z} = \frac{\sigma_Z^2 \sigma_{YZ} - \sigma_{YX} \sigma_{XZ}}{\sigma_Z^2 \sigma_X^2 - \sigma_{ZX}^2}$ (11.30)

$w_Z = R_{Y Z·X} = \frac{\sigma_Z^2 \sigma_{YX} - \sigma_{YZ} \sigma_{ZY}}{\sigma_Z^2 \sigma_X^2 - \sigma_{ZX}^2}$ (11.31)

The term $R_{Y X·Z}$ is called the partial regression coefficient of Y on X, keeping Z constant. This is equal to

$R_{Y X·Z} = \frac{\partial}{\partial x}\mathbb{E}[Y|X=x,Z=z]$ (11.32)

Note that this quantity is invariant to the specific value of Z we condition on. Note also that it is possible for $R_{Y X}$ to be positive and $R_{Y X·Z}$ to be negative, since conditioning on extra variables can always flip the sign of a regression coefficient, as in Simpsons paradox (see Sec. D.4.6).

# 11.2.3.4 Recursively computing the MLE

OLS is a batch method for computing the MLE. In some applications, the data arrives in a continual stream, so we want to compute the estimate online, or recursively, as we discussed in Sec. 4.6. In this section, we show how to do this for the case of simple (1d) linear regression.

Recall from Sec. 11.2.3.2 that the batch MLE for simple linear regression is given by

$\hat{w}_1 = \frac{\sum_n (x_n - \bar{x})(y_n - \bar{y})}{\sum_n (x_n - \bar{x})^2} = \frac{C_{xy}}{C_x^2}$ (11.33)

$\hat{w}_0 = \bar{y} - \hat{w}_1 \bar{x}$ (11.34)

where $C_{xy} = \text{Cov}[X,Y]$ and $C_x = \text{Cov}[X,X] = \mathbb{V}[X]$.

We now discuss how to compute these results in a recursive fashion. To do this, let us define the following sufficient statistics:

$\bar{x}^{(n)} = \frac{1}{n}\sum_{i=1}^n x_i,\quad \bar{y}^{(n)} = \frac{1}{n}\sum_{i=1}^n y_i$ (11.35)

$C_{xx}^{(n)} = \frac{1}{n}\sum_{i=1}^n (x_i - \bar{x})^2,\quad C_{xy}^{(n)} = \frac{1}{n}\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y}),\quad C_{yy}^{(n)} = \frac{1}{n}\sum_{i=1}^n (y_i - \bar{y})^2$ (11.36)