# 3.2.2 Techniques based on methods of forecasting

Based on the methods of forecasting, several techniques are implemented for accurate wind speed forecasts. Traditionally, the persistence method is used to predict the future values of the variables under the assumption that the conditions remains unchanged between “present” time t and forecast time t + h. Mathematically, for a variable v, the persistence algorithm is given as

```
\hat{v}_{t+h} = v_t \tag{3.2}
```

and is best suited for variables with stationary time series as they possess identical statistical properties.

Moving forward, statistical models like ARMA, ARIMA, and f-ARIMA are also used to forecast wind speed for very-short-term and short-term-based forecasting. These models predict future values based on the past data. Machine learning-based methods are gaining popularity owing to their ability to handle large historical data. Methods like the support vector regression, artificial neural network, extreme learning machine, and Gaussian process regression are some of the commonly used machine learning techniques for wind forecasting. Since the wind speed is a stochastic time series, various signal decomposition techniques like the wavelet transform, empirical mode decomposition, ensemble empirical mode decomposition, and complementary ensemble empirical mode decomposition are used in tandem with machine learning methods to forecast the short-term wind speed.

Fig. 3.4 illustrates different forecasting techniques based on forecasting methods.

# 3.3 Statistical methods

In benign terms, statistical forecasting methods indicate the use of statistics based on the available historical quantitative data to ascertain what could happen in the future.

Short-term wind forecasting is the most commonly used forecasting category, which many day-ahead markets need to clear the market scenarios by the end of the day. Among these, the most used forecasting methods are a combination of two or more machine learning methods combined with time-series models like AR, MA, ARMA, ARIMA, and ARMAX. Auto regression (AR) is a time-series model that uses observations taken from previous time steps as input to a regression equation to forecast the