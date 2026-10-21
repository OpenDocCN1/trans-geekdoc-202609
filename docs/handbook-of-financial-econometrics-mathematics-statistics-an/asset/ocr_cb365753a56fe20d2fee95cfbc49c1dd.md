to account for error committed by (ARIMA)$_t$, the larger will be the weight given to (Econometric)$_t$.

Composite predictions may be viewed as portfolios of predictions. If the econometric models and ARIMA's errors are denoted by $u_{1t}$, and $u_{2t}$, respectively, then from (87A.2) the composite prediction error is seen to be $\epsilon_t = B(u_{1t}) + (1 - B)(u_{2t})$. (87A.4)

The composite error is the weighted average of individual errors. The objective is to minimize the variance of the weighted average, given its expected value. In the case of prediction portfolios the weighted average always has expectation zero if individual predictions are unbiased; or it may be given expectation zero by addition of an appropriate constant.

Minimizing composite error variance over a finite sample of observations leads to the estimate of $B$ given by $\hat{B} = \frac{s_2^2 - s_{12}}{s_1^2 + s_2^2 - 2s_{12}}$. (87A.5)

where $s_1^2$, $s_2^2$, and $s_{12}$ are the sample variance of $u_{1t}$, the sample variance of $u_{2t}$, and the sample covariance of $u_{1t}$ and $u_{2t}$, respectively. For large samples, or in the case that the variances Var($u_{1t}$) and Var($u_{2t}$) and the covariance Cov($u_{1t} u_{2t}$) are known, equation (87A.5) becomes $B = \frac{\text{Var}(u_{2t}) - \text{Cov}(u_{1t}, u_{2t})}{\text{Var}(u_{1t}) + \text{Var}(u_{2t}) - 2\text{Cov}(u_{1t}, u_{2t})}$. (87A.6)

The minimum variance weight is seen to depend on the covariance between individual errors as well as on their respective variance. Holding the covariance constant, the larger the variance of the ARIMA error relative to that of the econometric error, the larger the weight given to the econometric prediction.