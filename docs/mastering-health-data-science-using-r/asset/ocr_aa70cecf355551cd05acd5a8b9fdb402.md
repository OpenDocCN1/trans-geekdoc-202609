There are several variables in the data related to how long a person has experienced symptoms. In the following code, we can see that the unit of the symptoms, recorded in `length_symp_unit_fac`, determines which other column is entered. For example, if `length_symp_unit_fac == 1`, then the only column without an NA value is `length_symp_days_fac`.

```
```r
tb_df %>%
  group_by(length_symp_unit_fac) %>%
  summarize(missing_days = sum(is.na(length_symp_days_fac))/n(),
            missing_wks = sum(is.na(length_symp_wk_fac))/n(),
            missing_mnt = sum(is.na(length_symp_mnt_fac))/n(),
            missing_yr = sum(is.na(length_symp_yr_fac))/n())
#> # A tibble: 6 x 5
#>   length_symp_unit_fac missing_days missing_wks missing_mnt
#>   missing_yr
#>                 <int>       <dbl>       <dbl>       <dbl>       <dbl>
#> 1                   1           0           1           1           1
#> 2                   2           1           0           1           1
#> 3                   3           1           1           0           1
#> 4                   4           1           1           1           0
#> 5                  77           1           1           1           1
#> 6                  NA           1           1           1           1
```
```

Additionally, these measurements are positive integer values.

```
```r
min(tb_df$length_symp_days_fac, na.rm = TRUE)
#> [1] 1
is.integer(tb_df$length_symp_days_fac)
#> [1] TRUE
```
```

This allows us to create a new variable that represents whether or not someone has had symptoms for more than two weeks. In our `case_when()` function call, we first check whether the duration is missing before checking for the cases when symptoms would be less than two weeks.

```
```r
# Categorize number of weeks experiencing symptoms
tb_df <- tb_df %>%
  mutate(two_weeks = case_when((length_symp_unit_fac == 77 |
                                  is.na(length_symp_unit_fac)) ~ NA,
                               (length_symp_unit_fac == 1 &
                                  length_symp_days_fac <= 14) ~ 0,
                               (length_symp_unit_fac == 2 &
                                  length_symp_wk_fac <= 2) ~ 0,
```
```