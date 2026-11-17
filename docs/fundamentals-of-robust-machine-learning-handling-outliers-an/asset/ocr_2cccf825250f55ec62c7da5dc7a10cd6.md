![](bbox=[0.13, 0.1, 0.67, 0.4])

Figure 12.21 Time series of the average land temperature on Earth from 1750 to 2015.

assumption, a set of statistical procedures have been developed for modeling and prediction. Specifically, we will examine the ARIMA time-series modeling approach used in machine learning (see Cryer and Chan 2008). The acronym ARIMA stands for Autoregressive Integrated Moving Average. We will sequence through the different components of ARIMA and then apply it to the specific time series associated with climate change in Figure 12.21. Keep in mind that the purpose of this exercise is to illustrate how to robustify existing machine learning techniques.

# 12.5.1 Autoregressive Model

The first component of ARIMA is the autoregressive (AR) model. In such a model, the future value of the time series is constructed as a linear combination of past values of the time series. We use the notation AR(p) to refer to models that use a total of p previous values in time to predict the value at time p + 1. More concretely, assume we have a time series given by {x1, x2, ..., xn}. If we have a model with p = 6, we use the first 6 time points to predict the 7th time point. Likewise, the values from positions 2 to 7 are used to predict the value at the 8th time point, and so on. It is possible to create a matrix X with p values in each row and n - p rows, and a response vector y with the (p + 1)st values associated with each row. Then, we can apply linear regression using least squares estimation to produce an AR(p) model. Alternatively, and perhaps more in line with our objective, the log-cosh loss can be used to robustify AR(p).

More generally, for a model of order p, we consider the linear regression problem of the form,

```
$$y_t = \varphi_0 + \varphi_1 x_{t-1} + \dots + \varphi_p x_{t-p} + \varepsilon_t, \quad p+1 \le t \le n, \quad (12.5.1)$$
```

where \(\varepsilon_t\) is the noise, and \(\varphi = (\varphi_0, \varphi_1, \dots, \varphi_p)^\top \in \mathbb{R}^{p+1}\) is a vector of unknown autoregressive parameters with a response vector \(y_t = x_t\). This is called the autoregression process of order \(p (\ge 1)\). It is a form of