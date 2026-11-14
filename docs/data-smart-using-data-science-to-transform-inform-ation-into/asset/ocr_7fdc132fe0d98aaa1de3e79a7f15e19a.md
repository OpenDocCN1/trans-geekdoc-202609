# # Optimizing for One-Step Error

As you did for simple exponential smoothing, add the squared forecast error in column I.
Then use the following formula to square the errors when comparing the forecast against
the actuals:

```
=IF([@t] <= $A$2,
    [@[Forecast Error]] ^ 2,
    0
)
```

Note, we test if the values are less than the total amount of items we have in our
analysis and not against the predicted items (t >= 36). Now, in H2 and I2, you can
calculate the sum of the squared error and the standard error for the one-step forecast
exactly as we did earlier. Except, this time the model has two smoothing parameters,
so you'll divide the SSE by 36 – 2 to account for those degrees of freedom before taking
the square root.

```
=SQRT(H2 / (A2 - 2))
```

This gives you the sheet shown in Figure 8.19.

![](bbox=[0.1328, 0.4828, 0.7656, 0.618])

**Figure 8.19: Calculating the SSE and standard error**

The optimization setup is identical to simple exponential smoothing except this time
around you're optimizing both *alpha* and *gamma* together, as shown in Figure 8.20.

When you click Solve, you get an optimal *alpha* value of 0.66 and an optimal *gamma*
value of 0.05. The optimal forecast is shown in the straight-line scatter in Figure 8.21.

The trend you're using from the forecast is an additional five swords sold per month.
The reason why this trend is double the one you found using the trendline on the previous
tab is because trend-corrected smoothing favors recent points more, and in this case, the
most recent demand points have been very “trendy.” (Or is it trendish?)

Note how this forecast starts very near the SES forecast for month 37 – 290 versus
292. But pretty quickly the trend-corrected forecast begins to grow just like you'd expect
with a trend.