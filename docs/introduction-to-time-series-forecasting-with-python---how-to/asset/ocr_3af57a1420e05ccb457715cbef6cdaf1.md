# ## 28.4  Interpreting the Confidence Interval

The `forecast()` function allows the confidence interval to be specified. The `alpha` argument on the `forecast()` function specifies the confidence level. It is set by default to `alpha=0.05`, which is a 95% confidence interval. This is a sensible and widely used confidence interval. An alpha of 0.05 means that the ARIMA model will estimate the upper and lower values around the forecast where there is only a 5% chance that the real value will not be in that range.

Put another way, the 95% confidence interval suggests that there is a high likelihood that the real observation will be within the range. In the above example, the forecast was 45.878. The 95% confidence interval suggested that the real observation was highly likely to fall within the range of values between 32.167 and 59.590. The real observation was 50.0 and was well within this range. We can tighten the range of likely values a few ways:

+   - We can ask for a range that is narrower but increases the statistical likelihood of a real observation falling outside of the range.
- We can develop a model that has more predictive power and in turn makes more accurate predictions.

Further, the confidence interval is also limited by the assumptions made by the model, such as the distribution of errors made by the model fit a Gaussian distribution with a zero mean value (e.g. white noise). Extending the example above, we can report our forecast with a few different commonly used confidence intervals of 80%, 90%, 95% and 99%. The complete example is listed below.

```
```python
# summarize multiple confidence intervals on an ARIMA forecast
from pandas import read_csv
from statsmodels.tsa.arima_model import ARIMA
# load data
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
# split data into train and test sets
X = series.values
X = X.astype('float32')
size = len(X) - 1
train, test = X[0:size], X[size:]
# fit an ARIMA model
model = ARIMA(train, order=(5,1,1))
model_fit = model.fit(disp=False)
# summarize confidence intervals
intervals = [0.2, 0.1, 0.05, 0.01]
for a in intervals:
	forecast, stderr, conf = model_fit.forecast(alpha=a)
	print('%.1f%% Confidence Interval: %.3f between %.3f and %.3f' % ((1-a)*100, forecast, conf[0][0], conf[0][1]))
```
```

Listing 28.3: Calculate multiple different confidence intervals of a forecast on the Daily Female Births dataset.

Running the example prints the forecasts and confidence intervals for each alpha value. We can see that we get the same forecast value each time and an interval that expands as our desire for a *safer* interval increases. We can see that an 80% captures our actual value just fine in this specific case.