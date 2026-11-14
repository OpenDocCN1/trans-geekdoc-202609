| Total Months | Level smoothing parameter (Alpha) | Trend smoothing parameter (Alpha) | Slope | Intercept |
| :--- | :--- | :--- | :--- | :--- |
| 36 | 0.50 | 0.50 | 0.8369 | 155.88 |

| t | Demand | Level | Trend | One-Step Forecast | Forecast Error |
| :--- | :--- | :--- | :--- | :--- | :--- |
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
| 18 | 161 | | | | |
| 19 | 162 | | | | |
| 20 | 169 | | | | |
| 21 | 185 | | | | |
| 22 | 188 | | | | |
| 23 | 200 | | | | |

# Figure 8.15: The initial level and trend values

```
=IF ( [@t]=0,
    $G$2,
    SUM (OFFSET ( [@[Level]] : [@[Trend]] , -1 , 0 ) ) + C$2* [@[Forecast Error]]
)
```

The trend in D6 is updated as the previous trend plus gamma times alpha times the error.

```
=IF ( [@t]=2,
    $F$2,
    OFFSET ( [@Trend] , -1 , 0 ) +D$2*C$2* [@[Forecast Error]]
)
```

The Excel table will automatically populate these formulas. This is shown in Figure 8.16.

# Forecasting Future Periods

Just as we did before, we'll add two additional columns to the table: Actuals and Forecast. Once added, extend the time value column in column A down to 48 months. Next, in our Actuals and Forecast columns, add the following formulas, respectively.