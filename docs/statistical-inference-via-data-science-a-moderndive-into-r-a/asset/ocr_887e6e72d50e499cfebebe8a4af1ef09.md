We once again focus on the values in this coefficient values. Why are there now 6 entries? We break them down one by one:

+   1. intercept corresponds to the mean life expectancy of countries in Africa of 66.31 years.

+   2. continent corresponds to countries in Asia and the value +8.64 is the same difference in mean life expectancy relative to Africa we displayed in Table 5.7. In other words, the mean life expectancy of countries in Asia is 66.31 + 8.64 = 74.95.

+   3. continent corresponds to countries in Europe and the value +13.6 is the same difference in mean life expectancy relative to Africa we displayed in Table 5.7. In other words, the mean life expectancy of countries in Europe is 66.31 + 13.6 = 79.91.

+   4. continent corresponds to countries in North America and the value +9.98 is the same difference in mean life expectancy relative to Africa we displayed in Table 5.7. In other words, the mean life expectancy of countries in North America is 66.31 + 9.98 = 76.29.

+   5. continent corresponds to countries in Oceania and the value +8.11 is the same difference in mean life expectancy relative to Africa we displayed in Table 5.7. In other words, the mean life expectancy of countries in Oceania is 66.31 + 8.11 = 74.42.

+   6. continent corresponds to countries in South America and the value +8.92 is the same difference in mean life expectancy relative to Africa we displayed in Table 5.7. In other words, the mean life expectancy of countries in South America is 66.31 + 8.92 = 75.23.

To summarize, the 6 values for the regression coefficients correspond to the “baseline for comparison” continent Africa (the intercept) as well as five “offsets” from this baseline for the remaining 5 countries: Asia, Europe, North America, Oceania, and South America.

You might be asking at this why Africa was chosen as the “baseline for comparison” group. This is the case for no other reason it comes first alphabetically of the six continents; you can change this baseline group to another continent if you manipulate the variable continent factor “levels” using the forcats package. See Chapter 15 of R for Data Science (Grolemund and Wickham, 2017) for examples.

We now write the equation for our fitted values $\hat{y}$ = life exp.