```
```r
#> #   DBP3 <dbl>, DBP4 <dbl>, SBP1 <dbl>, SBP2 <dbl>, SBP3 <dbl>,
#> #   SBP4 <dbl>, EVER_SMOKE <chr>
```
```

Grouping data is very helpful in combination with the `summarize()` function. Like with the `slice()` function, `summarize()` calculates the summary values for each group. We can now find the total number of observations as well as the mean systolic and diastolic blood pressure values for each racial group. Note that the returned summarized data is in a tibble.

```
```r
nhanes_df %>%
  group_by(RACE) %>%
  summarize(TOT = n(), MEAN_SBP = mean(SBP1, na.rm=TRUE),
            MEAN_DBP = mean(DBP1, na.rm=TRUE))
#> # A tibble: 5 x 4
#>   RACE                   TOT MEAN_SBP MEAN_DBP
#>   <fct>                <int>    <dbl>    <dbl>
#> 1 Mexican American      5277      124.     70.4
#> 2 Other Hispanic        2279      123.     70.1
#> 3 Non-Hispanic White   15473      125.     70.4
#> 4 Non-Hispanic Black    6041      129.     72.6
#> 5 Other Race            2195      122.     72.6
```
```

After summarizing, the data is no longer grouped by race. If we ever want to remove the group structure from our data, we can use the `ungroup()` function, which restores the data to a single data frame. After ungrouping by race, we can see that we get a single observation returned by the `slice()` function.

```
```r
nhanes_df %>%
  select(SEX, RACE, SBP1, DBP1) %>%
  group_by(RACE) %>%
  ungroup() %>%
  arrange(desc(SBP1)) %>%
  slice(1)
#> # A tibble: 1 x 4
#>   SEX    RACE                    SBP1  DBP1
#>   <fct>  <fct>                  <dbl> <dbl>
#> 1 Female Non-Hispanic White      270   124
```
```

# 5.4.1 Practice Question

Create a data frame summarizing the percent of patients with hypertension by smoking status. The result should look like Figure 5.2.