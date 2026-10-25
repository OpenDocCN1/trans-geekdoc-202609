```
xnames <- setdiff(names(aq), "Ozone") # feature names
set.seed(1938) # for reproducibility
res <- sapply(xnames, FUN = function(x) { # test each feature
  gi.test(airquality[[x]], y = airquality[["Ozone"]])
})
t(res) # print transpose of results (nicer printing)
```

```
#>   chisq     pval
#> Solar.R 13.3476 2.59e-04
#> Wind    41.6137 1.11e-10
#> Temp    56.0863 6.94e-14
#> Month   3.1127  7.77e-02
#> Day     0.0201  8.87e-01
```

```
# Bonferroni adjusted p-values (same as 5 * pval in this case)
p.adjust(res["pval", ], method = "bonferroni")
```

```
#>   Solar.R   Wind    Temp   Month     Day
#> 1.29e-03 5.56e-10 3.47e-13 3.88e-01 1.00e+00
```

In this example, the predictor associated with the smallest adjusted \(p\)-value is Temp, and since \(p^*_{\text{Temp}} \approx 3.469 \times 10^{-13} < \alpha = 0.05\), Temp is the first variable that will be used to partition the data. The next step is to determine the optimal split point of Temp to use when partitioning the data (step 2) of Algorithm 3.1), which will be discussed in Section 3.4.2.

# 3.4.1.2 Example: Swiss banknotes

Let's try a binary classification problem as well. If you followed Section 3.3 and paid close attention, then you might have figured out that our `gi.test()` function should also work for 0/1 encoded binary variables.

Using the Swiss banknote data (Section 1.4.1), let's see which, if any, of the available features can be used to effectively partition the root node—recall that all the features are numeric and that the binary response (y) is already coded as 0 (for genuine banknotes) and 1 (for counterfeit banknotes):

```
bn <- treemisc::banknote # start with the root node
xnames <- setdiff(names(bn), "y") # feature names
res <- sapply(xnames, FUN = function(x) { # test each feature
  gi.test(bn[[x]], y = bn[["y"]])
})
t(res) # print transpose of results (nicer printing)
```

```
#>   chisq     pval
#> length  7.52 6.11e-03
#> left   48.89 2.71e-12
#> right  68.51 1.11e-16
#> bottom 118.61 0.00e+00
#> top    72.22 0.00e+00
```