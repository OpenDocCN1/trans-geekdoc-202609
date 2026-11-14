![](bbox=[0.137, 0.098, 0.814, 0.41])

Figure 3.4 Categorization of wind forecasting techniques based on methods.

outcome at the next time step. On the other hand, rather than using past values of the forecast variable in a regression, a moving average (MA) model uses past forecast errors in a regression-like model.

Autoregressive exogenous moving average (ARMAX) is a nonlinear model that captures all the uncertainties related to the stochastic nature of the wind. Let us look at the two other models, ARMA and ARIMA, in more detail.

# 3.3.1 ARMA model

Among various statistical models, ARMA model is a popular forecasting- method. In ARMA, AR stands for autoregressive, and MA stands for moving average. Thus a combined autoregressive (of order p) and moving average (of order q) forms an ARMA(p, q) model. The order of ARMA models, p for AR and q for MA, denotes the lag between present and past values of the variable under test. Thus a generic ARMA model can be mathematically expressed as

```
$(y_t - \mu_x) = \phi_1(y_{t-1} - \mu_x) + \phi_2(y_{t-2} - \mu_x) + \cdots + \phi_p(y_{t-p} - \mu_x)
+ \xi_t - \theta_1\xi_{t-1} - \theta_2\xi_{t-2} - \cdots - \theta_q\xi_{t-q},\quad (3.3)$
```