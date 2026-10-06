where $H(\hat{\Theta})$ is the corresponding Hessian,

```
$H(\hat{\Theta}) = \left( \begin{array}{ccc} \frac{\partial^2 L(\Theta)}{\partial\theta_1^2} & \frac{\partial^2 L(\Theta)}{\partial\theta_1\partial\theta_k} & \frac{\partial^2 L(\Theta)}{\partial\theta_1\partial\theta_K} \ \frac{\partial^2 L(\Theta)}{\partial\theta_k\partial\theta_1} & \frac{\partial^2 L(\Theta)}{\partial\theta_k^2} & \frac{\partial^2 L(\Theta)}{\partial\theta_k\partial\theta_K} \ \ \frac{\partial^2 L(\Theta)}{\partial\theta_K\partial\theta_1} & \frac{\partial^2 L(\Theta)}{\partial\theta_K\partial\theta_k} & \frac{\partial^2 L(\Theta)}{\partial\theta_K^2} \end{array} \right) - \hat{\Theta}$ (10.17)
```

To account for the difference in the number of parameters in our choice of fitting candidates, we use several complementary criteria to pick the winner:

+   (1) The Akaike information criterion (AIC), as Akaike (1974):
$AIC = 2K - 2\ln L(\hat{\Theta})$ (10.18)

The Akaike information criterion estimates the out-of-sample prediction error of different statistical models for a given set. One can increase the likelihood by adding additional parameters. For instance, the normal distribution has two parameters, $\mu, \sigma$, while the generalized hyperbolic distribution has five, $\alpha, \beta, \delta, \lambda$. However, introducing extra parameters increases the risk of overfitting the data. By penalizing with more parameters, AIC becomes a useful tool for model selection based on the relative quality of each model. The model with the lowest AIC wins.

+   (2) The Hannan–Quinn information criterion (HQIC), as Hannan and Quinn (1979):
$HQIC = 2K\ln(N) - 2\ln L(\hat{\Theta})$ (10.19)

HQIC and AIC are broadly similar; however, the penalty term is larger in HQIC than in AIC.

+   (3) The Schwarz information criterion (SIC), also known as the Bayesian information criterion (BIC), as Schwarz (1978):
$SIC = K\ln N - 2\ln L(\hat{\Theta})$ (10.20)

BIC and AIC are strictly close, however, the penalty term is larger in BIC than in both AIC and HQIC.

For each of the above, the objective is to choose the fitting distribution producing the lowest value.

In addition, we consider the following commonly used to evaluate the goodness of fit:

+   (1) The Anderson–Darling test, as Anderson and Darling (1954):
$ADT = -N - \frac{1}{N} \sum_{n=1}^{N} (2n-1)\ln(\hat{F}(y_n)) + \ln(1-\hat{F}(y_{N+1-n}))$ (10.21)