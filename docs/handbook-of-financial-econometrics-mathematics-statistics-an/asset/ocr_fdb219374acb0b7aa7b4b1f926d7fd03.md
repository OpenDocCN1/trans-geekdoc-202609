the relationship linear. For example, let $x_0$ and $x_t$ be the sales of a firm in the base year and in year $t$, respectively. Then the underlying relationship is

$$x_t = x_0 e^{g t}$$

where $x_0$ is the base-year sales figure, $g$ is the growth rate, and $t$ is the length of time in terms of number of periods. Then, via the natural logarithm transformation, we obtain

$$\log_e x_t = \log_e (x_0 e^{g t})$$
$$= \log_e x_0 + g t, \qquad (26.12)$$

where $\log_e$ is the natural logarithm operator. Equation (26.12) can be defined as a log-linear regression model,$^5$

$$\log_e x_t = \alpha' + \beta' t + \varepsilon'_t, \qquad (26.13)$$

where
$\alpha' = \log_e x_0$
$\beta' = g = \text{growth rate of a firm's sales}$

JNJ's annual sales data (1980–2010), presented in Table 26.7, are used to show how equation (26.12) can be employed to forecast JNJ's future sales, and equation (26.13) to estimate the growth rate of JNJ's historical sales.

# Example 26.3: Forecasting Sales and Estimating Growth Rate.

Suppose Johnson & Johnson Company is interested in forecasting its sales revenues for each of the next 6 years. The sales manager of the company would also like to estimate the historical growth rate of sales revenue.

To make forecasts and assess their reliability, we must construct a time-series model for the sales revenue data listed in Table 26.7. A plot of the data (Figure 26.9) reveals a linearly increasing trend. Therefore, the linear time trend regression defined in equation (26.11) can be used to do forecasting. By the method of least squares, we obtain the least-squares model in terms of sales ($x_t$) and time intervals ($t$) as

$$\hat{x}_t = \hat{\alpha} + \hat{\beta} t = -7965.026 + 2089.257 t,$$
with $R^2 = .903$.