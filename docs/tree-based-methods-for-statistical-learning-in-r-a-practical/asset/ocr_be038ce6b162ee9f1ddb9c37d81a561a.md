```
#> $ pay_4  : num -1 0 0 0 0 0 0 0 -2 ...
#> $ pay_5  : num -2 0 0 0 0 0 0 0 -1 ...
#> $ pay_6  : num -2 0 0 0 0 0 0 0 -1 ...
#> $ bill_amt1 : num 3913 2682 29239 46990 8617 ...
#> $ bill_amt2: num 3102 1725 14027 48233 5670 ...
#> $ bill_amt3: num 689 2682 13559 49291 35835 ...
#> $ bill_amt4: num 0 3272 14331 28314 20940 ...
#> $ bill_amt5: num 0 3455 14948 28959 19146 ...
#> $ bill_amt6: num 0 3261 15549 29547 19131 ...
#> $ pay_amt1 : num 0 0 1518 2000 2000 ...
#> $ pay_amt2 : num 689 1000 1500 2019 36681 ...
#> $ pay_amt3 : num 0 1000 1000 1200 10000 657 38000 0..
#> $ pay_amt4 : num 0 1000 1000 1100 9000 ...
#> $ pay_amt5 : num 0 0 1000 1069 689 ...
#> $ pay_amt6 : num 0 2000 5000 1000 679 ...
#> $ default : num 1 1 0 0 0 0 0 0 0 ...
```

Note that the categorical variables have been numerically re-encoded. The next code chunk removes the column ID and cleans up some of the categorical features by re-encoding them from numeric back to the actual categories based on the provided column descriptions:

```
# Remove ID column
credit$id <- NULL

# Clean up categorical features
credit$sex <- ifelse(credit$sex == 1, yes = "male", no = "female")
credit$education <- ifelse(
  test = credit$education == 1,
  yes = "graduate school",
  no = ifelse(
    test = credit$education == 2,
    yes = "university",
    no = ifelse(
      test = credit$education == 3,
      yes = "high school",
      no = "other"
    )
  )
)

credit$marriage <- ifelse(
  test = credit$marriage == 1,
  yes = "married",
  no = ifelse (
    test = credit$marriage == 2,
    yes = "single",
    no = "other"
  )
)
```