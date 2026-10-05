# Linear Regression

We can represent the model analogously in the matrix form:

where

$y = \begin{pmatrix} y_1 \ y_2 \ \vdots \ y_n \end{pmatrix}, \quad X = \begin{pmatrix} x_{11} & x_{12} & \dots & x_{1p} \ x_{21} & x_{22} & \dots & x_{2p} \ \vdots & \vdots & \ddots & \vdots \ x_{n1} & x_{n2} & \dots & x_{np} \end{pmatrix}, \quad \beta = \begin{pmatrix} \beta_1 \ \beta_2 \ \vdots \ \beta_n \end{pmatrix}, \quad \varepsilon = \begin{pmatrix} \varepsilon_1 \ \varepsilon_2 \ \vdots \ \varepsilon_n \end{pmatrix}. \quad (13.5)$

The value of $p$ determines the notation for: $p=1$, the model is referred to as a simple linear regression model, while for $p>1$, the model is referred to as a multivariate regression model. Variables $y$ and $X$ are given, i.e. in the data set. They are arranged in vector and matrix, respectively. On the other hand, $\varepsilon$ is composed of random variables.

Let us focus on the error terms and the different nature of disturbance and residuals. Let notice that in (13.4), the term $\varepsilon$ is a random variable modelling the difference between the regressor $y$ and the deterministic function $X\beta$ involving the regressors $X$. Since $y$ depends on $X$, it is a random variable. When we are given $y$ as well as $X$ as data, then we compute the deterministic quantity

$\varepsilon = y - X\beta. \quad (13.6)$

which we call the residual. Confusing enough, use the same notation for $y$ when it is a random variable for as fixed sample when it is given. Recap, the disturbance is random while the residual is deterministic. Eq. (13.6) is all very well, but we don't find a "good enough" estimate for $\beta$, say, $\hat{\beta}$. In the given data, $y$ and $X$, we need to fit the linear regression model and Eq. (13.6) is actually wrong; it should be

$\varepsilon = y - X\hat{\beta}. \quad (13.7)$

It remains to define the notion of "good enough." We do that by minimising a suitable-function of residuals, which has a meaning of information loss between features and dependent variables. This brings us to the ordinary least squares methods.

# 13.2 ORDINARY LEAST SQUARES

In order to formulate the ordinary least squares, we have to make several assumptions:

+   - for all $i \in [1,\dots,n]$, $\varepsilon_i$ have a mean of zero, $E[\varepsilon_i] = 0$;

+   - for all $i \in [1,\dots,n]$, $\varepsilon_i$ have the same variance, $Var[\varepsilon_i] = \sigma^2 < \infty$, in other words, the random variables $\varepsilon_i$ are homoscedastic;