+   - Autoregressive integrated moving average (ARIMA): This is a model capturing trend and seasonality in time series data. It uses elements of regression and moving averages.

# STATISTICAL MODEL – AUTOREGRESSIVE INTEGRATED MOVING AVERAGE

Understanding time series analysis – ARIMA

ARIMA breaks down into three main components:

+   - AR (auto regressive): This means the model uses past values to predict future ones. You may remember that we used the word ‘regression’ in our linear regression model – it is a similar principle here.

+   - I (integrated): This means the model looks at changes between values instead of the raw data. This helps to deal with trends or data that changes over time.

+   - MA (moving average): This uses a mean average of the data, but, instead of looking at all of the data items, it will use a certain number of past and future values. This forces the model to keep re-evaluating the ‘average’ based on nearby values.

When you want to understand how data moves with time, you have to take account of changes in the trend. The ARIMA model