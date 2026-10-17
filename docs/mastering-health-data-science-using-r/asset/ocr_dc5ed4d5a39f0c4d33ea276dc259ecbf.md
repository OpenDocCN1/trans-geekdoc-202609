![](bbox=[0.166, 0.093, 0.838, 0.348])

# Figure 7.1: Pivoting Longer.

```
lockdown_long <- lockdowndates %>%
  pivot_longer(cols = c("Lockdown_Start", "Lockdown_End"),
   names_to = "Lockdown_Event", values_to = "Date") %>%
  mutate(Date = as.Date(Date, formula = "%Y-%M-%D"),
         Lockdown_Event = ifelse(Lockdown_Event=="Lockdown_Start",
                                 "Start", "End")) %>%
  na.omit()
head(lockdown_long)
#> # A tibble: 6 x 3
#>   State   Lockdown_Event Date
#>   <chr>   <chr>          <date>
#> 1 Alabama Start            2020-04-04
#> 2 Alabama End            2020-04-30
#> 3 Alaska  Start          2020-03-28
#> 4 Alaska  End            2020-04-24
#> 5 Arizona Start          2020-03-31
#> 6 Arizona End            2020-05-16
```

In R, we can also transform our data in the opposite direction (from long form to wide form instead of from wide form to long form) using the function pivot_wider(). This function again first takes in a data table, but now we specify the arguments names_from and values_from. The former indicates the column that R should get the new column names from, and the latter indicates where the row values should be taken from. For example, in order to pivot our lockdown data back to wide form in the following code, we specify that