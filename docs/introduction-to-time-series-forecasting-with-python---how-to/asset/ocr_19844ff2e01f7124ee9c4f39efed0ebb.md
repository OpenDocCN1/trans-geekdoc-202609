Listing 31.18: Plot and summarize errors of an ARIMA model on the Baltimore Water Usage dataset.

Running the example first describes the distribution of the residuals. We can see that the distribution has a right shift and that the mean is non-zero at 1.081624. This is perhaps a sign that the predictions are biased.

```
count 35.000000
mean 1.081624
std 22.022566
min -52.103811
25% -16.202283
50% -0.459801
75% 12.085091
max 51.284336
```

Listing 31.19: Example output of summary statistics on the residual errors of an ARIMA model on the Baltimore Water Usage dataset.

The distribution of residual errors is also plotted. The graphs suggest a Gaussian-like distribution with a longer right tail, providing further evidence that perhaps a power transform might be worth exploring.

![](bbox=[0.12, 0.45, 0.95, 0.875])