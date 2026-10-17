at this limit. To create a new line, you can hit enter either after an operator (e.g., %>%, +, |) or within a set of unfinished brackets or parentheses. Either of these breaks lets R know that your code is not finished yet.

Lastly, we can subset the data using the `slice()` function to select a slice of rows by their index. The function takes in the dataset and a vector of indices. In the following example, we find the first and last rows of the data.

```
slice(nhanes_df, c(1, nrow(nhanes_df)))
#>    AGE  SEX             RACE  EDUCATION INCOME       SMOKE YEAR LEAD
#> 1  77 Male Non-Hispanic White MoreThanHS   5.00 NeverSmoke 1999  5.0
#> 2  38 Male Non-Hispanic White MoreThanHS   1.56 StillSmoke 2017  0.9
#>
#>    BMI_CAT HYP ALC DBP1 DBP2 DBP3 DBP4 SBP1 SBP2 SBP3 SBP4
#> 1  BMI<=25   0 Yes   58   56   56   NA  106   98   98   NA
#> 2  BMI>=30   1 Yes   98   92   98   NA  150  146  148   NA
```

A few other useful slice functions are `slice_sample()`, `slice_max()`, and `slice_min()`. The first takes in an argument `n` which specifies the number of *random* rows to sample from the data. For example, we could randomly sample 100 rows from our data. The latter two allow us to specify a column through the argument `order_by` and return the n rows with either the highest or lowest values in that column. For example, we can find the three male observations from 2007 with the highest and lowest blood lead levels and select a subset of columns to display.

```
# three male observations with highest blood lead level in 2007
nhanes_df %>%
  filter(YEAR == 2007, SEX == “Male”) %>%
  select(c(RACE, EDUCATION, SMOKE, LEAD, SBP1, DBP1)) %>%
  slice_max(order_by = LEAD, n = 3)
#>             RACE       EDUCATION      SMOKE LEAD SBP1 DBP1
#> 1  Non-Hispanic Black LessThanHS NeverSmoke 33.1  106   66
#> 2      Other Hispanic LessThanHS StillSmoke 26.8  106   72
#> 3      Other Hispanic LessThanHS StillSmoke 25.7  112   60

# three male observations with lowest blood lead level in 2007
nhanes_df %>%
  filter(YEAR == 2007, SEX == “Male”) %>%
  select(c(RACE, EDUCATION, SMOKE, LEAD, SBP1, DBP1)) %>%
  slice_min(order_by = LEAD, n = 3)
#>             RACE       EDUCATION      SMOKE LEAD SBP1 DBP1
#> 1  Non-Hispanic White LessThanHS NeverSmoke 0.177  114   80
#> 2      Other Hispanic LessThanHS QuitSmoke  0.280  122   62
#> 3    Mexican American MoreThanHS QuitSmoke  0.320  112   66
```