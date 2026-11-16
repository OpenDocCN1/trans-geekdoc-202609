![](bbox=[0.255, 0.075, 0.725, 0.245])

# Figure 1. Example of distribution of infection events in simulated experiment.

The numerical results of the model take the number of people diagnosed with the real epidemic as the observed value and use the MCMC method to conduct large-scale sampling and iteration to obtain a stable distribution of simulated values (Ullah et al. 2023). Bayesian fitting explores suitable parameter value ranges that go through. After 1000 MCMC iterations, a linear regression equation is established between the sampling results and the actual values, and the unknown parameter pInfect in the program is determined by measuring the coefficients in the equation:

$y = \alpha\hat{y} + \beta$ (1)

In the formula, y is the actual value of the model, and \(\hat{y}\) is the fitted value of the model. When the output result \(\alpha\) is close to 1 and \(\beta\) is close to 0, the simulated value of the model is most comparable to the actual value, and the model parameters are the optimal parameters (Yao et al. 2021).

At the same time, to verify the rationality of the parameter calibration results, this paper compares the results of the three methods of MCMC sampling, the least-squares method and manual coarse parameter adjustment. It uses the goodness of fit (\(R^2\)) and the coefficient of equation (1) to compare; the formula for calculating \(R^2\) is as follows:

$R^2 = \frac{\sum_{i=1}^n (\hat{y}_i - \bar{y})^2}{\sum_{i=1}^n (y_i - \bar{y})^2}$ (2)

In the formula, \(\bar{y}\) is the mean value of the observed value. The best estimates of unknown parameters are shown in Table 2.

# Table 2. Comparison of parameter settings.

| Parameter | Parameter Description | MCMC | Least two multiplications | Artificial rough parameter tuning |
| :--- | :--- | :--- | :--- | :--- |
| pInfect1 | Phase 1 infection rate | 0.236 | 0.252 | 0.241 |
| pInfect2 | Stage 2 infection rate | 0.097 | 0.101 | 0.101 |
| pInfect3 | Stage 3 infection rate | 0.008 | 0.011 | 0.012 |
| alpha | Linear equation coefficients after fitting | 1.125 | 1.042 | 0.67 |
| beta | Linear equation coefficients after fitting | 1.015 | 2.123 | 93.93 |
| R<sup>2</sup> | The goodness of fit of the model | 0.995 | 0.99 | 0.851 |

The optimal infection rate MCMC fitting values of the three stages are respectively: the first stage is 0.239, the second stage is 0.099, and the third stage is 0.009. The fitted coefficients \(\alpha = 1.126, \beta = 1.011\) (Bhatt and Sharma 2023). Since the MCMC sampling results are