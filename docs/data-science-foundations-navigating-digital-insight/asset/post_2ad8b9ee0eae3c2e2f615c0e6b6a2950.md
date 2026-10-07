
- MAE: This is the average absolute difference between predicted and actual values.
- MSE: This is the average squared difference, highlighting larger errors.
- R-squared: This is the proportion of variance in the target variable explained by the model.

![](img/7ae4e3b756b64cea6e0099c9c3867e53_204_0.png)

# KYD yourself

Linear regression is quite a straightforward technique to apply. The key warnings when using it with your data are related to the ‘linear’ approach. A lot of real-life data does not follow a nice, simple straight-line approach. Imagine the battery capacity prediction: do we really think that it will take 20 years for the battery to be 0 per cent capacity? Or do we think that after 10 years things are going to be behaving quite differently?

Business examples

- Weather forecasting: Meteorologists use linear regression to predict tomorrow’s temperature based on today’s weather patterns.
- Business decisions: Companies use it to forecast sales, plan inventory and set prices.
- Medical research: Doctors use it to understand the relationship between risk factors and diseases.

# PREDICTING VALUE OVER TIME: TIME SERIES ANALYSIS

Time series analysis involves forecasting future values based on historical data collected over time, used in various domains to predict trends and patterns. When we look at data across time, things might be more complicated than a straight line (as we saw in linear regression). Often, we can see movements across different times of year – think about sales around Christmas. Many time series analysis methods take account of this ‘seasonality’ and use mathematical techniques to model them. The equations used in these methods are more complex and beyond the scope of this book, but the modern data scientist would use tools to run the models, so the important priority is understanding what the model shows rather than the calculations themselves.

Imagine you’re tracking your weight over a year. Time series analysis is like looking at how your weight changes by month, spotting any patterns (like gaining weight during the holidays) and predicting what your weight might be next month. It deals with data that happens over time, like stock prices, weather patterns or website traffic.

When to use time series analysis:

- **Forecasting**: Use for predicting future values, for example predicting next year’s sales for a business.
- **Trend spotting**: Use for identifying long-term patterns, for example seeing if the number of tourists visiting a city is increasing or decreasing over time.
- **Seasonality detection**: Use for finding repeating patterns within a certain time period, for example noticing that ice cream sales are always higher in the summer.
- **Anomaly detection**: Use for finding unusual or unexpected events, for example spotting a sudden drop in website traffic.

Components of time series:

- **Trend**: The long-term movement in the data.
- **Seasonality**: Regular, repeating patterns or cycles.
- **Noise**: Random variability not attributed to trend or seasonality.

Techniques for time series forecasting:

- **Exponential smoothing**: This applies exponentially decreasing weights to past observations for forecasting, which means it gives less weight to older values.
- Autoregressive integrated moving average (ARIMA): This is a model capturing trend and seasonality in time series data. It uses elements of regression and moving averages.

# STATISTICAL MODEL – AUTOREGRESSIVE INTEGRATED MOVING AVERAGE

Understanding time series analysis – ARIMA

ARIMA breaks down into three main components:

- **AR (auto regressive)**: This means the model uses past values to predict future ones. You may remember that we used the word ‘regression’ in our linear regression model – it is a similar principle here.
- **I (integrated)**: This means the model looks at changes between values instead of the raw data. This helps to deal with trends or data that changes over time.
- **MA (moving average)**: This uses a mean average of the data, but, instead of looking at all of the data items, it will use a certain number of past and future values. This forces the model to keep re-evaluating the ‘average’ based on nearby values.

When you want to understand how data moves with time, you have to take account of changes in the trend. The ARIMA model is adept at using relevant values to predict the next changes by focusing on a moving picture of the data.

# The output

The ARIMA model will predict future values, and these tend to be plotted on a graph.

# The formula

The simplest ARIMA method is known as the Box–Jenkins model. It is a combination of the linear trend and the moving average.

$Y_t = \delta + \phi_1 Y_{t-1} + \phi_2 Y_{t-2} + ... + \phi_p Y_{t-p} + \epsilon_t + \theta_1 \epsilon_{t-1} + \theta_2 \epsilon_{t-2} + ... + \theta_q \epsilon_{t-q}$

![](img/7ae4e3b756b64cea6e0099c9c3867e53_208_0.png)

# What does it look like?

Applying ARIMA takes a number of steps, and it will certainly be necessary to use tools to calculate results on any reasonable-size data set. Let's work through the steps that are taken as an example of what happens during the process.

Using some basic mobile phone sales data, let's try and predict what will happen in the future:

| Week | Mobile sold |
| :--- | :--- |
| 1 | 500 |
| 2 | 520 |
| 3 | 530 |
| 4 | 570 |
| 5 | 580 |
| 6 | 600 |
| 7 | 630 |

# Step 1: Check if the data is stationary

ARIMA works best when data does not have any clear trend. To make data stationary, we calculate the difference between values.

| Week | Difference |
| :--- | :--- |
| 2 | 20 |
| 3 | 10 |
| 4 | 40 |
| 5 | 10 |
| 6 | 20 |
| 7 | 30 |

# Step 2: Identify the ARIMA parameters (p, d, q)

ARIMA has three parameters:

1. **p (auto regressive)**: This is the number of past values used.
2. **d (differencing)**: This is the number of times the data is differenced.
3. **q (moving average)**: This is the number of past errors used.

In our example, we use ARIMA(1, 1, 1).

# Step 3: Create the ARIMA model

The ARIMA model combines the components (AR, I, MA) to forecast future values:

- **AR**: Looks at the previous value.
- **I**: Works with differenced data.
- **MA**: Adjusts for past errors.

# Step 4: Fit the model to the data

Let's fit the ARIMA(1, 1, 1) model to our data.

# Step 5: Forecast for Week 8

1. Start with the differenced data: From Week 7, the difference was +30 (change from Week 6 to 7).
2. Use AR: Look at the previous difference (+30) to predict the next difference. If $p = 1$, the model assumes the next difference might be similar (close to +30).
3. Add MA: Adjust for past errors. Let's say the model underestimated Week 7's sales by 10 phones. The MA component corrects this by taking 10 from the prediction.
4. Combine everything: The model predicts the next difference as Next Difference = (Previous Difference) + (Error Adjustment).

For our example: Next Difference = 30 + (-10) = 20

**Undo the differencing**: To get the actual forecasted sales for Week 8, we add the predicted difference (+20) to the sales from Week 7 (630):

Week 8 Sales = 630 + 20 = 650

# Step 6: Forecast for future weeks

You can repeat this process for additional weeks.
