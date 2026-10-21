from the fitted line is denoted as $\hat{y}_i$, the prediction equation becomes

$$\hat{y}_i = \hat{\beta}_0 + \hat{\beta}_1 x_i,$$

where $\hat{\beta}_0$ and $\hat{\beta}_1$ represent estimates of the true $\beta_0$ and $\beta_1$, and $x_i$ is an independent variable.

Graphically, the vertical lines drawn from the prediction line to each point represent the deviations of the points from the predicted value of $y$. Thus, the deviation of the $i$th point is $y_i - \hat{y}_i$.

In order to find the best fit, it is necessary to minimize the deviations of the points. A criterion of best fit that is often employed is known as the principle of least squares. It may be stated as follows: Choose the best fitting line as the one that minimizes the sum of squares of the errors (SSE) of the observed values of $Y$ from those predicted. Expressed mathematically,

$$SSE = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2.$$

Further, the mean sum of squares of the error (MSSE) of the observed values of $Y$ could be minimized from the predicted mean. Expressed mathematically,

$$MSSE = \frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{n}.$$

Mincer and Zarnowitz (1969) suggest a decomposition of the mean squared error term into the three components representing bias, inefficiency, and random error. Mathematically, this is represented as

$$\frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{n} = (\bar{y} - \hat{y}_i)^2 + (S_y - \rho S_y)^2 + (1 - \rho^2) S_y^2,$$

where $\bar{y}$, and $S_y$ represent the mean, standard deviation, and correlation coefficient of $y$, respectively.

Using the ordinary least-squares method, Lee et al. (1986) showed that it is possible to achieve better forecasts by combining two types of betas: Using an ordinary least-squares estimate of $\beta_{OLS}$ and a Bayesian adjustment procedure of Vasicek (1973) as defined in equation (79.21):

$$\beta_V = \frac{\frac{\bar{\beta}}{V(\bar{\beta})} + \frac{\hat{\beta}_{OLS}}{V(\hat{\beta}_{OLS})}}{\frac{1}{V(\bar{\beta})} + \frac{1}{V(\hat{\beta}_{OLS})}}, \tag{79.21}$$

where $\beta_{OLS}$ is the least-squares estimate of a first-period individual beta, $V(\hat{\beta}_{OLS})$ is the variance estimate of $\beta_{OLS}$, $\bar{\beta}$ is the cross-sectional mean value