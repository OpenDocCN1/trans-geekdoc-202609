```
## [[2]]
## [1] "" "2" "1,669,054" "3,298,151"
## [5] "(1,629,097)" "25,150,326" "48,775,753" "(23,625,427)"
## [9] "81.8%" "87.3%" "86.2%"
```

This remains a single list, now with two elements—one for each row.

Below, the code creates an object with a list of the variable names. (Sometimes it's more effective to tackle these cleaning problems head-on with a manual solution, rather than spend time on a one-time programmatic solution.)

```
bcf_col_names <- c(
  "blank",
  "route",
  "passengers_fy2021",
  "passengers_fy2020",
  "passenger_growth",
  "passenger_tariff_revenue_fy2021",
  "passenger_tariff_revenue_fy2020",
  "passenger_tariff_growth",
  "pct_sailings_10_mins_fy2019",
  "pct_sailings_10_mins_fy2020",
  "pct_sailings_10_mins_fy2021"
)
```

```
as_tibble(test_result, .name_repair = "unique")
```

```
## New names:
## * `` -> `...1`
## * `` -> `...2`
```

```
## # A tibble: 11 x 2
##  ...1      ...2
##  <chr>     <chr>
## 1 ""      ""
## 2 "1"     "2"
## 3 "2,578,221"  "1,669,054"
## 4 "6,124,234"  "3,298,151"
## 5 "(3,546,013)"  "(1,629,097)"
## 6 "39,230,411"  "25,150,326"
## 7 "91,309,787"  "48,775,753"
```