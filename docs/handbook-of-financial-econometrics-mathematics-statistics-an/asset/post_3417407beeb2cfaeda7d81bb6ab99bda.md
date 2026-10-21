
$$Z_i = d + X_i + v_i, \tag{37.35}$$

in which $Y_i$, $W_i$, and $Z_i$ are observable for $i = 1, \dots, n$, while $X_i$, $e_i$, and $v_i$ are unobservable. Equations (37.34) and (37.35) imply that

$$Y_i = \alpha + b'W_i + cZ_i + \varepsilon_i. \tag{37.36}$$

However, since both $Z_i$ and $\varepsilon_i$ depend on $v_i$, estimators of $b$ and $c$ from OLS regression are inconsistent. Lewbel (1997) shows that the consistent estimators can be obtained by using TSLS with instruments 1, $W_i$, and $q_i$, where $q_i$ is some vector of instruments that are correlated with $X_i$ but not correlated with $e_i$ and $v_i$. $q_i$ can be chosen as

- $q_{1i} = (G_i - \bar{G})$
- $q_{2i} = (G_i - \bar{G})(Z_i - \bar{Z})$
- $q_{3i} = (G_i - \bar{G})(Y_i - \bar{Y})$
- $q_{4i} = (Y_i - \bar{Y})(Z_i - \bar{Z})$
- $q_{5i} = (Z_i - \bar{Z})^2$
- $q_{6i} = (Y_i - \bar{Y})^2$

where $G_i = G(W_i)$ for any given function $G$ and $\bar{S}$ denotes the sample mean of variables $S_i$ ($S_i$ can be $Y_i$, $Z_i$, or $G_i$).

Lewbel (1997) further empirically applies the instrumental variable method to testing elasticity of patent applications with respect to research and development (R&D) expenditures. He finds, using the TSLS instrumental variable model, the estimated elasticity yields very close to one. Therefore, the TSLS instrumental variable model can mitigate the effects of measurement error and confirm the relationship between patent and R&D.

In addition, Erickson and Whited (2000, 2002) propose a two-step generalized method of moments (GMM) estimators that exploit over-identifying information contained in the high-order moments of residuals obtained from perfectly measured regressors. Basing GMM estimation on residual moments of more than second order requires that the GMM covariance matrix be explicitly adjusted to account for the fact that estimated residuals are used instead of true residuals defined by population regressions. Erickson and Whited (2000) show that estimators obtained by using moments up to seventh order perform well in Monte Carlo simulations.

Almeida et al. (2010) use Monte Carlo simulations and empirically test investment models to compare the performance of the instrumental variables approach suggested by Biorn (2000) and generalized method of moments. They find that the instrumental variable method can obtain more consistent and efficient estimators than the generalized method of moments when independent variables are subject to measurement error, resulting in weak evidence in empirical research.

However, it is difficult to obtain appropriate instrumental variables, resulting in weak evidence in empirical research. Lewbel (2012) proposes a new method to deal with measurement error problems in regression model when instrumental variables are not available. Under the assumption of heteroscedastic errors, Lewbel (2012) shows that the regression model with measurement regressors can be identified and estimated by TSLS or GMM.

## 37.3.4 Mathematical method

### 37.3.4.1 Bivariate case

Deming (1943), York (1966) and Clutton-Brock (1967) have developed a weighted-regression-method-under-iteration approach. Deming (1943) proposed that the best straight line of equation (37.1) can be obtained by minimizing the sum in the following equation:

```
S = \sum_i \{ w(X_i) (\hat{U}_i - X_i)^2 + w(Y_i) (\hat{V}_i - Y_i)^2 \}, \quad (37.37)
```

where \hat{U}_i and \hat{V}_i are the adjusted value of X_i and Y_i which make the sum in equation (37.37) a minimum. Since we require \hat{U}_i and \hat{V}_i to lie on the best straight line, we must have

```
\hat{V}_i = \alpha + \beta \hat{U}_i, \quad (i = 1, \cdots , n). \quad (37.38)
```

Both w(X_i) and w(Y_i) are the weights of various observations. They are reciprocally proportional to the variance of their measurement error respectively.

If these values of \hat{U}_i, \hat{V}_i, \alpha, and \beta make S a minimum, we have

```
\beta^3 \sum_i \frac{k_i^2}{w(X_i)} - 2\beta^2 \sum_i \frac{k_i^2 y_i}{w(X_i)} - \beta \left\{ \sum_i k_i x_i - \sum_i \frac{k_i^2 y_i}{w(X_i)} \right\} + \sum_i k_i x_i y_i = 0, \quad (37.39)
```

where x_i = X_i - \bar{X}, y_i = Y_i - \bar{Y}, \bar{X} = \sum k_i X_i / \sum k_i, \bar{Y} = \sum k_i Y_i / \sum k_i, and k_i = w(Y_i)/[\beta^2 w(X_i) + w(Y_i)].

Equation (37.39) is the least square cubic derived by York (1966). To solve equation (37.39), an initial value is assigned to \beta to estimate k_i. After obtaining the roots of equation (37.39), one of the legitimate solutions is

assigned to estimate k_i and obtain new solutions for β again. A similar procedure is employed iteratively until a convergent solution is obtained.

The mathematical approach involves the estimation of the parameters of a function conditional on the maximum likelihood function adjusted for the true values. This method is different from the classical method in three ways. First, variances of measurement errors for every observation are different. Second, a weighted regression method is applied. Third, the iteration procedure is used to obtain a consistent estimator.

It can be proved that the mathematical programming method reduces to the classical method under certain conditions.

Three special cases for the observations X_i and Y_i are discussed in the following.

(i) Only Y_i has an EIV problem.

In this case, we put more weight on X_i which has no EIV problem, then w(X_i)=∞, k_i = w(Y_i). We can solve the least square cubic

β = Σ_i w(Y_i) x_i y_i / Σ_i w(Y_i) x_i² , (37.40)

which is the estimated coefficient of weighted regression of Y_i on X_i.

(ii) Only X_i has an EIV problem.

In this case, we put more weight on Y_i which has no EIV problem, then w(Y_i)=∞, k_i = w(X_i)/β². We can solve the least square cubic as follows

β = Σ_i w(X_i) y_i² / Σ_i w(X_i) x_i y_i , (37.41)

which is the inverse-estimated coefficient of weighted regression of Y_i on X_i.

(iii) Both X_i and Y_i have EIV problem, and w(X_i)/w(Y_i)=c.

The least square cubic becomes

β² + β {c Σ_i k_i x_i² - Σ_i k_i y_i²} / Σ_i k_i x_i y_i - c = 0. (37.42)

### 37.3.4.2 Multivariate case

Lee (1973) extends the bivariate mathematical programming method, which was developed by Deming (1943), York (1966) and Clutton-Brock (1967), to a trivariate case. We define w(Z_i), w(X_i), and w(Y_i) which are the weights of the various observations of Z_i, X_i, and Y_i. It is assumed W, U, and V are

Kim (1995, 1997, 2010) further provides a maximum likelihood method to correct the EIV problem in testing the asset pricing model. Based upon two-pass capital asset pricing model, Kim (1995) shows that in a multifactor asset pricing model test the EIV leads to an underestimation of the independent variable with a measurement error and an overestimation of the independent variable without measurement error. To correct EIV biases, Kim (1995) extracts additional information about the relation between idiosyncratic error variance which can be obtained from the first step and the measurement error variance, and incorporates such additional information into the second step of the capital asset pricing model test. Assuming the homoscedasticity of the disturbance term of the market model, Kim (1995) shows that the corrected factors for the traditional least squares estimators of the cross-sectional regression coefficients can be obtained by the maximum likelihood method. The closed form estimators of the multifactor asset pricing model test can therefore be obtained. Assuming the first and second steps of the multifactor asset pricing model are

$$R_{i,t}=\alpha_i+\beta_iR_{m,t}+e_{i,t},\tag{37.45}$$

and

$$R_{i,t}=\gamma_{0,t}+\gamma_{1,t}\hat{\beta}_{i,t-1}+\gamma_{2,t}V_{i,t-1}+e_{i,t},\tag{37.46}$$

where $\beta_{i,t-1}$ is the market risk factor with measurement error, and $V_{i,t-1}$ is a risk factor with no measurement error for security $i$ at time $t-1$. The adjusted estimators in the second step can be written as follows:

$$\hat{\gamma}_{1t}=\frac{M+\left[M^2+4\delta_t m_{\hat{\beta}\hat{\beta}}^2\left(1-\left(\hat{\rho}_{RV}\hat{\rho}_{\hat{\beta}V}/\hat{\rho}_{R\hat{\beta}}\right)\right)^2\right]^{1/2}}{2m_{R\hat{\beta}}\left(1-\left(\hat{\rho}_{RV}\hat{\rho}_{\hat{\beta}V}/\hat{\rho}_{R\hat{\beta}}\right)\right)}$$

$$\hat{\gamma}_{2t}=\left(m_{RV}-\hat{\gamma}_{1t}m_{\hat{\beta}V}\right)/m_{VV},\tag{37.47}$$

$$\hat{\gamma}_{0t}=\tilde{R}_t-\hat{\gamma}_{1t}\tilde{\beta}_{t-1}-\hat{\gamma}_{2t}\tilde{V}_{t-1},$$

where

$$M=m_{RR}\left(1-\hat{\rho}_{RV}^{2}\right)-\delta_t m_{\hat{\beta}\hat{\beta}}\left(1-\hat{\rho}_{\hat{\beta}V}^{2}\right),$$

$$m_{xy}=\frac{1}{N}\sum_{i=1}^{N}\sum_{j=1}^{N}w_{ij}(x_i-\bar{x})(y_j-\bar{y})\Big/\sum_{i=1}^{N}\sum_{j=1}^{N}w_{ij},$$

$$\bar{x}=\sum_{i=1}^{N}\sum_{j=1}^{N}w_{ij}x_i\Big/\sum_{i=1}^{N}\sum_{j=1}^{N}w_{ij},$$
