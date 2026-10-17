names_from is the lockdown event and values_from is the date itself. Now we are back to the same form as before!

```
lockdown_wide <- pivot_wider(lockdown_long,
                                     names_from = Lockdown_Event,
                                     values_from = Date)
head(lockdown_wide)
## # A tibble: 6 x 3
##   State   Start       End
##   <chr>   <date>      <date>
## 1 Alabama 2020-04-04  2020-04-30
## 2 Alaska  2020-03-28  2020-04-24
## 3 Arizona 2020-03-31  2020-05-16
## 4 California 2020-03-19 2021-01-25
## 5 Colorado 2020-03-26  2020-04-27
## 6 Connecticut 2020-03-23 2020-05-20
```

Here's another example: suppose that I want to create a data frame where the columns correspond to the number of cases for each state in New England, and the rows correspond to the numbered months. First, I need to filter my data to New England and then summarize my data to find the number of cases per month. I use the `month()` function to be able to group by month and state. Additionally, you can see that I add an `ungroup()` at the end. When we summarize on data grouped by more than one variable, the summarized output is still grouped. In this case, the warning message states that the data is still grouped by state.

```
ne_cases <- covidcases %>%
  filter(state %in% c("Maine", "Vermont", "New Hampshire",
                      "Connecticut", "Rhode Island",
                      "Massachusetts")) %>%
  mutate(month = month(date)) %>%
  group_by(state, month) %>%
  summarize(total_cases = sum(weekly_cases)) %>%
  ungroup()
head(ne_cases)
## # A tibble: 6 x 3
##   state   month total_cases
##   <chr>   <dbl>     <int>
## 1 Connecticut   3      7489
## 2 Connecticut   4     22764
## 3 Connecticut   5     13640
## 4 Connecticut   6      2913
```