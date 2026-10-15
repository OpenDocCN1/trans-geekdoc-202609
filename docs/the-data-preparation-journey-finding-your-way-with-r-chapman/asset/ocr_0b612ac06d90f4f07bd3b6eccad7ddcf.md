```
## 4 E06000047 County Durham              522100
## 5 E06000005 Darlington                  107800
## 6 E06000001 Hartlepool                   92300
## # i 19 more variables: aged_4_years_and_under <dbl>,
## #   aged_5_to_9_years <dbl>,
## #   aged_10_to_14_years <dbl>,
## #   aged_15_to_19_years <dbl>,
## #   aged_20_to_24_years <dbl>,
## #   aged_25_to_29_years <dbl>,
## #   aged_30_to_34_years <dbl>, ...
```

The filter() step below does the following:

+   - selects the area code and the population categories of interest,
+   - joins the detailed geographic descriptions,
+   - filters the level 3 values, but this leaves those UA regions that are further disaggregated into the city category.

```
uk_census_pop_90 <- uk_census_pop_90 |>
  select(area_code, all_persons, aged_90_years_and_over) |>
  full_join(uk_census_geo_code, by = "area_code") |>
  # filter so that only UAs remain
  filter(geo_level == 3)
```

With this table, the proportion of persons aged 90 or older can be calculated and the table sorted in descending order:

```
uk_census_pop_90 |>
  mutate(
    pct_90_plus =
      round((aged_90_years_and_over / all_persons * 100), 1)
  ) |>
  arrange(desc(pct_90_plus)) |>
  select(area_name, aged_90_years_and_over, pct_90_plus) |>
  slice_head(n = 10)
```

```
## # A tibble: 10 x 3
##   area_name           aged_90_years_and_over pct_90_plus
##   <chr>                                   <dbl>       <dbl>
```