changes in moving average calculation. It measures how much the moving average trails behind the actual data.

+   • Cause: This is because moving averages are based on the window of previous values, which makes changes in the average reflect changes that have already taken place. So, selecting the appropriate window size is crucial for balancing lag and responsiveness. For example, a 5 day moving average for daily stock prices responds quickly to price changes but may be noisy, whereas a 50 day moving average is smoother but slower to react.
+   • Impact: The moving averages are computed on data collected over different time periods, depending on specified number n, the moving averages in fact smooth out short-term fluctuations that are usually associated with higher fluctuations and unsystematic risks.
+   • Considerations: This delay can be described further by various attributes, such as the the windows size and the data refresh rate. This means that smaller windows and more often updates will cause less lag, and large windows and less often updates will cause more lag.

Lag in the moving average is defined as the time gap between fluctuations in the given data and fluctuations in the moving average. This is a property of moving averages that defines its ability to be affected by the changes in the data.

# Question 5: Discuss the use of feature engineering in time series analysis. What features might be relevant for modeling?