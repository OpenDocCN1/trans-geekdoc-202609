If you set *alpha* to 0, you conduct absolutely no error correction on that first level estimate.
You'll likely want something in between those two extremes, but you'll learn how to pick the best *alpha* value later.

So, you can roll this calculation forward through time:

```
level_current period = level_previous period + alpha * (demand_current period – level_previous period)
```

Eventually you end up with a final level estimate, level_36, where the last demand observations count for more because their error adjustments haven't been multiplied by *alpha* a zillion times:

```
level_36 = level_35 + alpha * (demand_36 – level_35)
```

This final estimate of the level is what you'll use as the forecast of future months. The demand for month 37? Well, that's just level_36. The demand for month 40? level_36. Month 45? level_36. You get the picture. The final level estimate is the best one you have for the future, so that's what you use.

Let's take a look at it in a spreadsheet.

# Setting Up the Simple Exponential Smoothing Forecast

The first thing you'll do is create a new worksheet in the workbook called SES. Paste the time-series data in columns A and B starting at row 4 to leave some room at the top of the sheet for an *alpha* value. Make sure to turn it into an Excel table. And, once that's done, rename your table to SES.SwordData.

> **CAN YOU INCLUDE A PERIOD IN YOUR TABLE NAME?
> WHAT ABOUT NAMED RANGES?**
> 
> Yes, you can. And, in fact, it's something I do regularly. I often like to name my Tables and named ranges using the following convention `[worksheet].[objectname]` to stay organized.
> 
> But I should warn you. The Microsoft product team told me point blank they don't like me using periods in my names. They say the dots can cause trouble in the new formulas like `LET` and `LAMBDA`. I've never had an issue, but I'll leave you to consider their words of caution.

You can put the number of months you have in your data (36) in cell A2 and take an initial swing at the *alpha* value in C2. I'm going with 0.5, because it's in between 0 and 1. And, you gotta start somewhere. Feel free to add labels to these inputs as shown in figure 8.3.