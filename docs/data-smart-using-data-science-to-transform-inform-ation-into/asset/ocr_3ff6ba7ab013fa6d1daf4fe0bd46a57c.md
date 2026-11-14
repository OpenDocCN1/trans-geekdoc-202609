![](bbox=[0.133, 0.106, 0.668, 0.414])

Figure 8.42: Worksheet with smoothing parameters and first one-step forecast and error

Let's update the formula in column D. It's fairly similar.

```
=IFS(
	[@t] = 0, HoltWintersInitial!$I$19,
	[@t] > 0,
	OFFSET([@Trend], -1, 0) + $F$2 * $E$2 * [@[Forecast Error]] /
	OFFSET([@[Seasonal Adjustment]], -HoltWintersInitial!$B$1, 0)
)
```

You have the previous trend plus gamma times the amount of seasonally adjusted error incorporated into the level update.

And for the January seasonal factor update, you have this:

```
=IFS(
	[@t] < 1, INDEX(
		HoltWintersInitial.SeasonalFactors[Initial Seasonal Factors],
		[@t] + HoltWintersInitial!$B$1
	),
	AND([@t] >= 1, [@t] <= $A$2),
	OFFSET([@[Seasonal Adjustment]], -HoltWintersInitial!$B$1, 0) +
	$G$2 * (1 - $E$2) * [@[Forecast Error]] /
	SUM(OFFSET(HoltWintersSeasonal.Data[@[Level]:[Trend]], -1, 0))
)
```

That's the previous factor adjusted by delta times the error ignored by the level correction scaled like the seasonal factors by dividing through by the previous level and trend. If all is correct, your screen will look like in Figure 8.43.