```
tail(badpenguins)
```

```
## # A tibble: 6 x 8
##   species island bill_length_mm bill_depth_mm flipper_length_mm
##   body_mass_g
##   <fct>   <fct>       <chr>          <chr>           <chr>            <chr>
## 1 Chin... Dream      50.2           18.7            198              3775
## 2 Penguin Gotham     <NA>           <NA>            <NA>             90
## 3 Pingu  Antar~     <NA>           <NA>            <NA>             <NA>
## 4 Pinga  Antar~     <NA>           <NA>            <NA>             <NA>
## 5 Opus   Bloom~     <NA>           <NA>            <NA>             <NA>
## 6 Gunter Ice K~     <NA>           <NA>            <NA>             <NA>
## # i 2 more variables: sex <fct>, year <chr>
```

```
check_penguins <- check_that(badpenguins, year >= 2007 & year <= 2009)

summary(check_penguins)
```

```
##   name items passes fails nNA error warning               expression
## 1   V1   349   344    5   0 FALSE   FALSE year >= 2007 & year <= 2009
```

```
check_penguins <- check_that(badpenguins, island %in% island_list)

summary(check_penguins)
```

```
##   name items passes fails nNA error warning               expression
## 1   V1   349   344    5   0 FALSE   FALSE island %vin% island_list
```

In both cases, we get 5 “fails”.

# 11.3.3 Investigating the fails

How can we check which records have failed?

{validate} provides two other functions, validator() and confront(), which give us a way to

+   - run multiple checks at a time, and