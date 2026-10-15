```
island_list <- c("Biscoe", "Dream", "Torgersen")

check_penguins <-
  check_that(penguins,
    if (species == "Adelie") island %in% island_list)

summary(check_penguins)
```

```
##  name items passes fails nNA error warning
## 1  V1  344  344  0  0 FALSE  FALSE
##                       expression
## 1 species != "Adelie" | (island %in% island_list)
```

_What happens if we fail to include Dream Island in our list of islands where Adélie penguins are found?_

The {validator} also allows us to check variable types within our check_that() function. Because R stores a dataframe column as a single type, this returns only one pass/fail evaluation.

```
summary(check_that(penguins, is.integer(year)))
```

![](bbox=[0.1, 0.68, 0.85, 0.78])

**FIGURE 11.2** _summary(check_that(penguins))_.

# 11.3.2  badpenguins

The “badpenguins.rds” file adds five fictional penguins to the original “penguins” table, including measurement data. Let’s load the data file “badpenguins.rds” (an R data file) and run a couple of the tests we used earlier:

```
badpenguins <- read_rds(dpjr_data("badpenguins.rds"))
```