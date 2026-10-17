```
#> [49] "Delaware"                                      "West Virginia"
#> [51] "Rhode Island"
num_wks <- covidcases %>%
  group_by(state) %>%
  summarize(num_weeks = n_distinct(week), .groups = "drop")
summary(num_wks)
#> state        num_weeks
#> Length:51      Min.   :23.0
#> Class :character   1st Qu.:25.5
#> Mode :character  Median :26.0
#>                   Mean   :26.0
#>                   3rd Qu.:27.0
#>                   Max.   :27.0
```

Note that D.C. is written differently for each data source. We update this name in the mobility data.

```
mobility_week$state[mobility_week$state == "Washington, D.C."] <- "District of Columbia"
```

After checking the formatting of the state and week columns, we can now merge our data together. In this case, we want to add the mobility data to the case data and use a left_join().

```
# Join cases and mobility data
covid <- left_join(covidcases, mobility_week, by = c("state", "week"))
```

Next, we want to get some simple information about the continuous variables in our data. We observe two key points. First, we can see the negative values the data description warned us about, and second, there is no missing data.

```
summary(covid[, c("weekly_cases", "weekly_deaths", "m50")])
#> weekly_cases weekly_deaths m50
#> Min. : -188 Min. : -511 Min. : 0.0
#> 1st Qu.: 2 1st Qu.: 0 1st Qu.: 5.0
#> Median : 9 Median : 0 Median : 7.7
#> Mean : 87 Mean : 3 Mean : 7.7
#> 3rd Qu.: 39 3rd Qu.: 1 3rd Qu.: 9.9
#> Max. :35134 Max. :5226 Max. :49.4
```

These negative numbers are clear data discrepancies. When showing the dis-