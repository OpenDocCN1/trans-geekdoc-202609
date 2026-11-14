If you’ve never used LINEST before, Excel’s help documentation on the function is very good. You provide LINEST with the dependent variable data (demand in column B) and the independent variable data (you have only one independent variable, and it’s the periodic time data in column A).

You also have to provide a flag of TRUE to let the function know to fit an intercept as part of the regression line, and you have to provide a second flag of TRUE to get back detailed stats like standard error and R squared. For the Time-series tab data then, a linear regression can be run as follows:

```
=INDEX(LINEST(SwordData[Demand],SwordData[t],TRUE,TRUE),1,1)
```

Go ahead and place this slope in cell B39 (and in A39 create a label that says Slope). You see, LINEST returns all the regression stats in an array, so either you can run LINEST as an array formula to dump everything out into a selected range in a sheet or you can run LINEST through the INDEX function and pull off just the values you care about one by one like we’re doing here. I prefer the latter method as it’s easier to work with.

So, to get the Standard Error, use the following formula in cell B40 on the Time-series tab by feeding LINEST through INDEX.

```
=INDEX(LINEST(SwordData[Demand],SwordData[t],TRUE,TRUE),2,1)
```

And, in B41, you can pull the Degrees of Freedom as follows:

```
=INDEX(LINEST(SwordData[Demand],SwordData[t],TRUE,TRUE),4,2)
```

You should get 34 for the degrees of freedom (this is calculated as 36 data points minus 2 coefficients used for the linear regression).

You now have the three values you need to perform a t-test on the statistical significance of your fitted trend. You can calculate the test statistic as the absolute value of the slope divided by the standard error for the slope. You can pull the p value for this statistic from the t distribution with 34 degrees of freedom using the T.DIST.2T function in B42.

```
=T.DIST.2T(ABS(B39/B40),B41)
```

This returns a p value near 0 implying that if the trend were nonexistent in reality (slope of 0), there’s no chance we would have gotten a slope so extreme from our regression. This is shown in Figure 8.13.

So you have a trend! Now you just need to incorporate it into your forecast.

# Holt's Trend-Corrected Exponential Smoothing

Holt’s trend-corrected exponential smoothing expands simple exponential smoothing to create a forecast from data that has a linear trend. It’s often called double exponential smooth-