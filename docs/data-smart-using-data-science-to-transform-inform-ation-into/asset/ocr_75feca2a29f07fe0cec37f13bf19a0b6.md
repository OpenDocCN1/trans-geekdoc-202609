![](bbox=[0.17, 0.11, 0.76, 0.42])

Figure 8.32: Changing the critical values into highlighted regions

# Multiplicative Holt-Winters Exponential Smoothing

Multiplicative Holt-Winters Smoothing is the logical extension of Holt's trend-corrected smoothing. It accounts for a level, a trend, and the need to adjust the demand up or down on a regular basis because of seasonal fluctuations. Note that the seasonal fluctuation needn't be every 12 months like in this example. For instance, at companies that send automated emails to customers, periodic demand could fluctuate every Thursday (people seem to think Thursday is a good day to send marketing email). Holt-Winters can account for this 7-day cycle.

Now, in most situations you can't just add or subtract a fixed amount of seasonal demand to adjust the forecast. If your business grows from selling 200 to 2,000 swords each month, you wouldn't adjust the Christmas demand in both those contexts by adding 20 swords. No, seasonal adjustments usually need to be multipliers. Instead of adding 20 swords, maybe it's multiplying the forecast by 120 percent. That's why it's called multiplicative Holt-Winters. Here's how this forecast conceives of demand:

> Demand at time t = (level + t * trend) * seasonal adjustment for time t * whatever irregular adjustments are left we can't account for

So, you still have the identical level and trend structure you had in Holt's trend-corrected smoothing, but the demand is adjusted for seasonality. And since you can't account for irregular variations in the demand, such as acts of God (or some capricious higher entity), you're not going to.