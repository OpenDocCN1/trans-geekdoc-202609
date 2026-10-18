# Listing 6.1 Loading and exploring the HouseVotes84 dataset

```
```r
data(HouseVotes84, package = "mlbench")

votesTib <- as_tibble(HouseVotes84)

votesTib

# A tibble: 435 x 17
#   Class V1   V2   V3   V4   V5   V6   V7   V8   V9   V10
#   <fct> <fct> <fct> <fct> <fct> <fct> <fct> <fct> <fct> <fct> <fct>
# 1 repu... n    y    n    y    y    y    n    n    n    y
# 2 repu... n    y    n    y    y    y    n    n    n    n
# 3 demo... NA   y    y    NA   y    y    n    n    n    n
# 4 demo... n    y    y    n    NA   y    n    n    n    n
# 5 demo... y    y    y    n    y    y    n    n    n    n
# 6 demo... n    y    y    n    y    y    n    n    n    n
# 7 demo... n    y    n    y    y    y    n    n    n    n
# 8 repu... n    y    n    y    y    y    n    n    n    n
# 9 repu... n    y    n    y    y    y    n    n    n    n
#10 demo... y    y    y    n    n    n    y    y    y    n
# ... with 425 more rows, and 6 more variables: V11 <fct>, V12 <fct>,
#   V13 <fct>, V14 <fct>, V15 <fct>, V16 <fct>
```
```

> **NOTE**  Ordinarily I would manually give names to unnamed columns to make it clearer what I’m working with. In this example, the variable names are the names of votes and are a little cumbersome, so we’ll stick with V1, V2 etc. If you want to see what issue each vote was for, run `?mlbench::HouseVotes84`.

It looks like we have a few missing values (NAs) in our tibble. Let’s summarize how many missing values we have in each variable using the `map_dbl()` function. Recall from chapter 2 that `map_dbl()` iterates a function over every element of a vector/list (or in this case, every column of a tibble), applies a function to that element, and returns a vector containing the function outputs.

The first argument to the `map_dbl()` function is the name of the data we’re going to apply the function to, the second argument is the function we want to apply. I’ve chosen to use an anonymous function (using the `~` symbol as shorthand for `function(.)`).

> **NOTE**  Recall from chapter 2 that an anonymous function is a function we define on-the-fly instead of pre-defining one and assigning it to an object.

My function takes each vector and passes it to `sum(is.na(.))` to count the number of missing values in that vector. This is applied to each column of the tibble and returns the number of missing values for each.