| t | Demand | Smoothed |
|---|---|---|
| 1 | 165 | #N/A |
| 2 | 171 | #N/A |
| 3 | 147 | #N/A |
| 4 | 143 | #N/A |
| 5 | 164 | #N/A |
| 6 | 160 | #N/A |
| 7 | 152 | |
| 8 | 150 | 163.167 |
| 9 | 159 | 163.125 |
| 10 | 169 | 163.542 |
| 11 | 173 | 164.333 |
| 12 | 203 | 165.500 |
| 13 | 169 | 166.542 |
| 14 | 166 | 167.000 |
| 14 | 166 | 168.208 |

Figure 8.34: The 2x12MA smoother function accounts for the fact the moving average is an even number.

# Result of 2x12MA Smoother

![](bbox=[0.15, 0.42, 0.67, 0.77])

Figure 8.35: The smoothed demand data

You will see the formula autopopulate the table. Note how in both months 12 and 24 (December) you get spikes around 20 percent of normal, whereas you get dips in the spring. This smoothing technique has given you some point-estimates for each seasonality factor. Let's average these respective points together into a single set of values that will be the initial seasonal factors used in Holt-Winters.