```
# extract the character strings in the 8th & 9th position
str_sub(bls_employment_naics21$`Series ID`, start = 8, end = 9)
```

## [1] "00" "10" "20" "21" "22" "23" "30"

Starting on the inside of the parentheses, we have the str_sub() function to create those two-character strings. Next is the str_detect() with a regex that identifies those that have a digit other than zero in the first position, and a zero in the second. The table is then filtered for those rows where that was detected.

```
# NAICS 212
bls_employment_naics21_3digit <- bls_employment_naics21 |>
  # filter those that match the regex in the 8th & 9th position
  filter(str_detect(
    str_sub(`Series ID`, start = 8, end = 9),
  "[^0][0]"))

bls_employment_naics21_3digit
```

## # A tibble: 3 x 3
##   `Series ID`   `Annual 2019` `Annual 2020`
##   <chr>                 <dbl>         <dbl>
## 1 CEU1021100001          144.          130.
## 2 CEU1021200001          190.          176.
## 3 CEU1021300001          344           247.

The final step in cleaning this table would be to put it into a tidy structure. Currently it violates the second principle of tidy data, that each observation forms a row. (Wickham, 2014, p.4) In this case, each year should have its own row, rather than a separate column for each.

We can use the {tidyr} (Wickham, 2021b) package's pivot_longer() function for this:

```
bls_employment_naics21_3digit |>
  pivot_longer(
    cols = contains("Annual"),
    names_to = "year",
    values_to = "employment")
```