in 2021 and drastically reduced the number of eligible abortions. We could test whether there were significantly fewer abortions in 2021 compared to 2020 using a one-sided t-test. Our null hypothesis is that \(\mu \ge 6.23\), the mean abortion rate in 2020. To run this hypothesis test, we use the `t.test()` function. For a one-sample t-test, we need to specify our sample x, the alternative hypothesis `alternative` (default is a two-sided test), the true value of the mean `mu` (default 0), and a confidence level `conf.level` (default 0.95). In the following code, we run this t-test, and we can see from the result that we reject the null hypothesis at the 0.05 level and observe a statistically significant decline in the abortion rate in 2021.

```
t.test(county_rates_2021, alternative = "less", mu = 6.23,
       conf.level=0.95)
#>
#> One Sample t-test
#>
#> data:  county_rates_2021
#> t = -2, df = 253, p-value = 0.02
#> alternative hypothesis: true mean is less than 6.23
#> 95 percent confidence interval:
#>  -Inf 5.98
#> sample estimates:
#> mean of x
#>   5.17
```

The output for this test is printed. If we want to reference these values, we need to save the result. The object `t_test_res` is a list that contains information about the statistic, p-value, confidence interval, etc. The list of outputs is similar to other test objects, so it is useful to look at what is contained in each by reading the test documentation (`?t.test`). We find the p-value from `t_test_res`.

```
t_test_res <- t.test(county_rates_2021, alternative = "less",
                     mu = 6.23, conf.level = 0.95)
names(t_test_res)
#> [1] "statistic"   "parameter"   "p.value"     "conf.int"
#> [5] "estimate"    "null.value"  "stderr"      "alternative"
#> [9] "method"      "data.name"

t_test_res$p.value
#> [1] 0.0161
```