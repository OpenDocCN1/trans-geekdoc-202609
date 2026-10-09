```
```python
# difference data
months_in_year = 12
diff = difference(history, months_in_year)
# predict
model = ARIMA(diff, order=(0,0,1))
model_fit = model.fit(trend='nc', disp=0)
yhat = model_fit.forecast()[0]
yhat = inverse_difference(history, yhat, months_in_year)
predictions.append(yhat)
# observation
obs = test[i]
    history.append(obs)
# errors
residuals = [test[i]-predictions[i] for i in range(len(test))]
residuals = DataFrame(residuals)
print(residuals.describe())
# plot
pyplot.figure()
pyplot.subplot(211)
    residuals.hist(ax=pyplot.gca())
pyplot.subplot(212)
    residuals.plot(kind='kde', ax=pyplot.gca())
pyplot.show()
```
```

Listing 32.20: Plot and summarize errors of an ARIMA model on the Champagne Sales dataset.

Running the example first describes the distribution of the residuals. We can see that the distribution has a right shift and that the mean is non-zero at 165.904728. This is perhaps a sign that the predictions are biased.

count 47.000000 mean 165.904728 std 934.696199 min -2164.247449 25% -289.651596 50% 191.759548 75% 732.992187 max 2367.304748

Listing 32.21: Example output of summary statistics on the residual errors of an ARIMA model on the Champagne Sales dataset.

The distribution of residual errors is also plotted. The graphs suggest a Gaussian-like distribution with a bumpy left tail, providing further evidence that perhaps a power transform might be worth exploring.