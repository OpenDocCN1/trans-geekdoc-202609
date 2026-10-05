# Test of Stationarity – Dickey-Fuller and Augmented Dickey-Fuller Tests

The Dickey-Fuller (DF) test tests the hypothesis that a unit root is present in an autoregressive model. The test estimates three models:

+   - The first model is an AR(1) process without constant: $y_t = ho_1 y_{t-1} + \epsilon_t$.
- The second model is an AR(1) process with constant: $y_t = eta_2 + ho_1 y_{t-1} + \epsilon_t$.
- The third model adds a trend to the AR(1) constant: $y_t = \mu_1 + eta_3 t + ho_1 y_{t-1} + \epsilon_t$.

The first model can be rewritten as $\Delta y_t = (ho_1 - 1)y_{t-1} + \epsilon_t = \Phi_1 y_{t-1} + \epsilon_t$, the second model $\Delta y_t = \mu_1 + \Phi_2 y_{t-1} + \epsilon_t$, and the third $\Delta y_t = \mu_2 + eta_3 t + \Phi_1 y_{t-1} + \epsilon_t$.
The ADF test tests the stability of AR(1) processes. The test can be augmented to detect a unit root for AR(p). It is Augmented Dickey-Fuller (ADF) test. The ADF estimates three models:

+   - The AR(p) model without constant: $\Delta y_t = \Phi_1 y_{t-1} + \sum_{j=2}^p eta_j \Delta y_{t-j} + \epsilon_t$.
- The AR(p) model with constant: $\Delta y_t = \mu_1 + \Phi_1 y_{t-1} + \sum_{j=2}^p eta_j \Delta y_{t-j} + \epsilon_t$.
- The AR(p) model with constant and trend: $\Delta y_t = \mu_2 + eta(t - p - \frac{T-p+1}{2}) + \Phi_1 y_{t-1} + \sum_{j=2}^p eta_j \Delta y_{t-j} + \epsilon_t$.

The null hypothesis of the ADF test is the non-stationarity (unit root) of the variable $y_t$, i.e. $\phi=0$. The ADF test uses statistics given by MacKinnon (1996). The null hypothesis of non-stationarity is rejected at 5% if $t_{obs}<ADF_{}$. The optimal number of lags of AR(p) is determined with linear regression and implemented with the function .quantQ.ols AIC:

To determine whether to retain the hypothesis of a unit root with or without a constant, the Student-t associated with the constant $\mu_i$ is compared with the tabulated values of the statistics. For the third model, the ADF test checks whether the coefficients associated with the constant ($\mu_2$) and trend ($eta$) are significantly different from zero with $H_0: \mu_2=0$ and $H_0: eta=0$.

The $\Delta$ of a time series is simply deltas. Data their autoregressive models can be estimated with the function .quantQ.tabulated values of the statistics given by MacKinnon can be stored in a dictionary and computed with the t-stat $t_{obs}$ as implemented in the function .quantQ.ols.fit.

The models presented so far are, limited. They only use realisations of a random variable to explain its current and future values. In addition to the use of past values of a random variable to forecast future, a model can be improved by