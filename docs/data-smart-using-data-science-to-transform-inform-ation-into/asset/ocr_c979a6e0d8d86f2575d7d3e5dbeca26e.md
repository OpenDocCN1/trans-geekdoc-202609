| A | B | C | D | E | F | G |
|---|---|---|---|---|---|---|
| Total Months | | | Level smoothing parameter (alpha) | Trend smoothing parameter (gamma) | Seasonal smoothing parameter (delta) |
| 36 | | | 0.5 | 0.5 | 0.5 |
| t | Demand | Level | Trend | Seasonal Adjustment | One-Step Forecast | Error |
| -11 | #N/A | #N/A | 0.988 | #N/A | #N/A |
| -10 | #N/A | #N/A | 1.039 | #N/A | #N/A |
| -9 | #N/A | #N/A | 0.933 | #N/A | #N/A |
| -8 | #N/A | #N/A | 0.913 | #N/A | #N/A |
| -7 | #N/A | #N/A | 1.043 | #N/A | #N/A |
| -6 | #N/A | #N/A | 0.906 | #N/A | #N/A |
| -5 | #N/A | #N/A | 0.921 | #N/A | #N/A |
| -4 | #N/A | #N/A | 0.927 | #N/A | #N/A |
| -3 | #N/A | #N/A | 0.988 | #N/A | #N/A |
| -2 | #N/A | #N/A | 1.016 | #N/A | #N/A |
| -1 | #N/A | #N/A | 1.048 | #N/A | #N/A |
| 0 | 144.424 | 2.290 | 1.204 | #N/A | #N/A |
| 1 | 165 | 156.839 | 7.353 | 1.022 | 144.988 | 20.012 |
| 2 | 171 | 164.350 | 7.432 | 1.040 | 170.671 | 0.329 |
| 3 | 147 | 164.675 | 3.878 | 0.914 | 160.262 | -13.262 |
| 4 | 143 | 162.624 | 0.914 | 0.897 | 153.822 | -10.822 |
| 5 | 164 | 160.388 | -0.661 | 1.033 | 170.572 | -6.572 |
| 6 | 160 | 168.120 | 3.536 | 0.930 | 144.783 | 15.217 |
| 7 | 152 | 168.361 | 1.888 | 0.912 | 158.067 | -6.067 |
| 8 | 150 | 166.064 | -0.204 | 0.915 | 157.757 | -7.757 |
| 9 | 159 | 163.355 | -1.457 | 0.981 | 163.951 | -4.951 |
| 10 | 169 | 164.102 | -0.355 | 1.023 | 164.522 | 4.478 |
| 11 | 173 | 164.408 | -0.025 | 1.050 | 171.616 | 1.384 |
| 12 | 203 | 166.493 | 1.031 | 1.212 | 197.918 | 5.082 |
| 13 | 169 | 166.416 | 0.477 | 1.019 | 171.266 | -2.266 |

# Figure 8.43: Taking the update equations through month 36

Note that in all three of these formulas *alpha*, *gamma*, and *delta* are referenced via absolute references, so they don’t move. But you should really consider using named ranges. (I avoid them here because there’s so much sheet copying, and I think it would make things a bit worse for instruction—but in real life, this is the perfect place for named ranges.)

Now that you have your final level, trend, and seasonal estimates, it’s time to forecast. First, extend the size of the table to 48 records. Next, let’s add our Actual and Forecast columns as we did previously. In the Actuals column, use the following formula:

```
=IF(AND([@t] > 0, [@t] <= $A$2, [@Demand], NA())
```

Next, let’s add our forecasting function, which would officially begin after t >= 37.

```
=IF([@t] > $A$2,
    (XLOOKUP($A$2, [t], [Level]) + ([@t] - $A$2) * XLOOKUP($A$2, [t], [Trend])) *
    OFFSET([@[Seasonal Adjustment]], -HoltWintersInitial!$B$1, 0),
    NA()
)
```