```
=INDEX(
HoltWintersInitial.SeasonalFactors[Initial Seasonal Factors],
MOD(([@t] - 1,12) + 1
)
```

| | Demand | Smoothed | Estimate | Seasonal Factor | Initial Seasonal Factors x | | | Initial Seasonal Factors | | |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 165 | #N/A | #N/A | | 0.988 | | 1 | 0.988 | -1.177% |
| 2 | 171 | #N/A | #N/A | | 1.039 | | 2 | 1.039 | 3.946% |
| 3 | 147 | #N/A | #N/A | | 0.933 | | 3 | 0.933 | -6.707% |
| 4 | 146 | #N/A | #N/A | | 0.923 | | 4 | 1.042 | 4.206% |
| 5 | 164 | #N/A | #N/A | | 1.043 | | 5 | 1.043 | 4.301% |
| 6 | 160 | #N/A | #N/A | | 0.906 | | 6 | 0.906 | -9.356% |
| 7 | 152 | 163.167 | | 0.932 | 0.921 | | 7 | 0.921 | -7.916% |
| 8 | 150 | 163.125 | | 0.920 | 0.927 | | 8 | 0.927 | -7.338% |
| 9 | 159 | 164.542 | | 0.967 | 0.968 | | 9 | 0.968 | -3.164% |
| 10 | 169 | 164.333 | | 1.028 | 1.016 | | 10 | 1.016 | 1.620% |
| 11 | 173 | 165.500 | | 1.045 | 1.048 | | 11 | 1.048 | 4.805% |
| 12 | 203 | 166.542 | | 1.219 | 1.204 | | 12 | 1.204 | 20.400% |
| 13 | 169 | 167.000 | | 1.012 | 0.988 | | | | |
| 14 | 146 | 168.208 | | 0.868 | 1.039 | | | | |
| 15 | 152 | 170.083 | | 0.894 | 0.933 | | | | |
| 16 | 165 | 171.958 | | 0.960 | 0.923 | | | | |
| 17 | 165 | 171.958 | | 0.960 | 1.043 | | | | |
| 18 | 17 | 178.875 | | 0.095 | 1.043 | | | | |
| 19 | 18 | 176.083 | | 0.914 | 0.906 | | | | |

Figure 8.38: Repeating the initial seasons factors so that we can deseasonalize each month in the dataset

Insert another column to the right of E. Name this column Deseasonalized Data. Now, divide the original series in column B by the seasonal factors in E to remove the estimated seasonality present in the data.

As you've done on previous tabs, insert a scatter plot of column F and toss a trendline through it. Displaying the trendline equation on the graph, you get an initial trend estimate of 2.29 additional sword sales per month and an initial level estimate of 144.42 (see Figure 8.39). For good measure, I would also add these calculations to the sheet as I've done in H19:I20. Instead of LINEST, I used the SLOPE and INTERCEPT functions because I don't feel like dealing with all the arguments in LINEST.

# Getting Rolling on the Forecast

Now that you have the initial values for all the parameters, create a new tab called HoltWintersSeasonal, where you'll start by pasting the time-series data on row 4 just as you did for the previous two forecasting techniques. Name this Excel table HoltWintersSeasonal.Data.

In columns C, D, and E next to the time series, you're going to put the Level, Trend, and Seasonal Adjustment, respectively. To start, unlike on previous tabs where you needed to insert only one new blank row 5, this time around you need to insert blank rows 5 through 16 and label them as time slots -11 through 0 in column A. In cells A1 and A2 place the label Total Months and the count of months in our data. When you're ready, compare your work to Figure 8.40.