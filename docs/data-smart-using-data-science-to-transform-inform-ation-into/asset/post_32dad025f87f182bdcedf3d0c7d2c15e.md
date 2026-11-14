
![](img/9c4b3d77873bec9e7da149a75c568d36_263_0.png)

Figure 8.2: Scatter plot of time-series data—the y-axis has been adjusted to the range 100 to 350.

## Starting Slow with Simple Exponential Smoothing

Exponential smoothing techniques base a future forecast off of past data where the most recent observations are weighted more than older observations. This weighting is done through smoothing constants. The first exponential smoothing method you're going to tackle is called simple exponential smoothing (SES), and it uses only one smoothing constant, as you'll see.

Simple exponential smoothing assumes that your time-series data consists of two components: a level (or mean) and some error around that level. There's no trend, no seasonality, just a level around which the demand hovers with little error jitters here and there. By preferring recent observations, SES can account for shifts in this level. In formula-speak then, you have this:

> *Demand at time t = level + random error around the level at time t*

The most current estimate of the level serves as a forecast for future time periods. If you're at month 36, what's a good estimate of demand at time period 38? The most recent level estimate. And time 40? The level. Simple—that's why it's called simple exponential smoothing.

So how do you get an estimate of the level?

If you assume that all your historical values are of equal importance, you just take a straight average.

This mean would give you a level, and you'd forecast the future by just saying, “Demand in the future is the average of the past demand.” And there are companies that do this. I've seen monthly forecasts at companies where future months were equal to the average of those same months over the past few years. Plus a “fudge factor” for kicks. Yes, forecasting is often done so hand-wavily that even at huge, public companies words like fudge factor are still used. This sorry state of affairs makes one consider other words that start with F.

But when the level shifts over time, you don’t want to give equal weight to each historical point in the way that an average does. If you were attempting to predict inventory based on the past, would March 2020 through December 2021 carry the same weight when forecasting in 2024? Probably not, especially when you consider that the COVID-19 global pandemic was taking place at this time. Instead, you want a level estimate that gives more weight to your recent demand observations, which will be more relevant to the current situation.

Let’s think about calculating the level, instead, by rolling over the data points in order, updating the level calculation as you go. To start, say the initial estimate of the level is the average of some of the earliest data points. In this case, pick the first year’s worth of data. Call this initial estimate of the level level₀.

level₀ = average of the first year’s demand (months 1–12)

That's 163 for the sword demand.

Now, the way exponential smoothing works is that even though you know demand for months 1 through 36, you’re going to take your most recent forecast components and use them to forecast one month ahead through the entire series.

So, you use level₀ (163) as the forecast for demand in month 1.

Now that you’ve forecasted period 1, you take a step forward in time from period 0 to period 1. The actual demand was 165, so you were off by two swords. You should update the estimate of the level then to account for this error. Simple exponential smoothing uses this equation:

level₁ = level₀ + some percentage * (demand₁ - level₀)

Note that (demand₁ - level₀) is the error you get when you forecast period one with the initial level estimate. Rolling forward:

level₂ = level₁ + some percentage * (demand₂ - level₁)

And again:

level₃ = level₂ + some percentage * (demand₃ - level₂)

Now, the percentage of the error you want to fold back into the level is the smoothing constant, and for the level, it’s historically been called alpha. It can be any value between 0 and 100 percent.

If you set alpha to 1, you’re accounting for all the error, which just means the level of the current period is the demand of the current period.

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

## Setting Up the Simple Exponential Smoothing Forecast

The first thing you'll do is create a new worksheet in the workbook called SES. Paste the time-series data in columns A and B starting at row 4 to leave some room at the top of the sheet for an *alpha* value. Make sure to turn it into an Excel table. And, once that's done, rename your table to SES.SwordData.

> **CAN YOU INCLUDE A PERIOD IN YOUR TABLE NAME?
> WHAT ABOUT NAMED RANGES?**
> 
> Yes, you can. And, in fact, it's something I do regularly. I often like to name my Tables and named ranges using the following convention `[worksheet].[objectname]` to stay organized.
> 
> But I should warn you. The Microsoft product team told me point blank they don't like me using periods in my names. They say the dots can cause trouble in the new formulas like `LET` and `LAMBDA`. I've never had an issue, but I'll leave you to consider their words of caution.

You can put the number of months you have in your data (36) in cell A2 and take an initial swing at the *alpha* value in C2. I'm going with 0.5, because it's in between 0 and 1. And, you gotta start somewhere. Feel free to add labels to these inputs as shown in figure 8.3.

Now, you'll need to insert a new line in the Excel table (at row 5 of the worksheet) at the top for the initial level estimate for time 0 (see Figure 8.3). Next create three additional columns for the table: Level Estimate column (C), a One-Step Forecast column (D) and a Forecast Error column (E). Take a look at Figure 8.3 to see my setup. Once yours looks like mine, we're ready to calculate.

| A | B | C | D | E | F |
|---|---|---|---|---|---|
| Total Months | | Level Smoothing Alpha | | | |
| 36 | | 0.50 | | | |
| t | Demand | Level Estimate | One-Step Forecast | Forecast Error | |
| 0 | | | | | |
| 1 | 165 | | | | |
| 2 | 171 | | | | |
| 3 | 147 | | | | |
| 4 | 143 | | | | |
| 5 | 164 | | | | |
| 6 | 160 | | | | |
| 7 | 152 | | | | |
| 8 | 150 | | | | |
| 9 | 159 | | | | |
| 10 | 169 | | | | |
| 11 | 173 | | | | |
| 12 | 203 | | | | |
| 13 | 169 | | | | |
| 14 | 166 | | | | |
| 15 | 162 | | | | |
| 16 | 147 | | | | |
| 17 | 188 | | | | |
| 18 | | | | | |

Figure 8.3: Initial worksheet design for simple exponential smoothing

## Adding in the One-Step Forecast and Error

To create our one-step forecast and then understand the error, we'll have to define the correct level estimate calculation. Because this calculation has multiple conditions associated with it, we're going to build it as we go. That means we'll start with a few formula stubs and then reedit them. For instance, I will tell you to update a formula you've already input into a cell. So, don't assume just because we've placed a formula in a cell, it's the last step. You'll see this as we continue through this chapter.

Second, we'll be building toward dynamic formula interaction for the most part. That means if you want to test scenarios beyond what's described here, you should easily be able to update only a few cells and perhaps stretch out an Excel table. Everything else should be set up and ready to go as we attempt to avoid hard-coded values. So feel free to play around with the examples in this chapter going beyond what we do in the text.

So far we have a few conditions that will help us build our formula: what happens when t = 0, what happens when t = 1, what happens when t > 1, and what happens when t > 36 (that's our total month count).
