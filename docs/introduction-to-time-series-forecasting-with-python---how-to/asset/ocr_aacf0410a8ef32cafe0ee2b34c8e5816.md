# 23.4. Autoregression of Residual Error

```
predictions.append(pred_error)
history.append(error)
print('predicted error=%.f, expected error=%.f' % (pred_error, error))
# plot predicted error
pyplot.plot(expected_error)
pyplot.plot(predictions, color='red')
pyplot.show()
```

Listing 23.8: Forecast residual errors for the Daily Female Births dataset.

Running the example first prints the predicted and expected residual error for each time step in the test dataset.

```
...
predicted error=6.675538, expected error=3.000000
predicted error=3.419129, expected error=15.000000
predicted error=-7.160046, expected error=-4.000000
predicted error=-4.179003, expected error=7.000000
predicted error=-10.425124, expected error=-5.000000
```

Listing 23.9: Example output of forecasting residual errors on the Daily Female Births dataset.

Next, the actual residual error for the time series is plotted compared to the predicted residual error.

![](bbox=[0.15, 0.47, 0.85, 0.95])