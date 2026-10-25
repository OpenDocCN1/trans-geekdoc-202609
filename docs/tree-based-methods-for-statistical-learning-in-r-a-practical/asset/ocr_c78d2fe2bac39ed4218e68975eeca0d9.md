influence function h() converts the right-censored survival times to log-rank scores.

To illustrate, let's test the null hypothesis of general independence between the predictor bili (serum bilirubin (mg/dl)) and the log-rank scores of the response:

```
library(coin)
```

```
independence_test(Surv(time, status) ~ bili, data = pbc2,
  teststat = "quadratic")
```

```
#>
#> Asymptotic General Independence Test
#>
#> data: Surv(time, status) by bili
#> chi-squared = 77, df = 1, p-value < 2e-16
```

```
# Our 'gi.test()' function from earlier should also work
```

```
lr.scores <- coin::logrank_trafo(Surv(pbc2$time, pbc2$status))
```

```
gi.test(pbc2$bili, y = lr.scores)
```

```
#>
#> chisq pval
#> 77.5 0.0
```

Using alpha = 0.05, we would reject the null hypothesis (p < 0.001) and conclude that the level of serum bilirubin is associated with survival rate. But this doesn't tell us much beyond that. Do subjects with higher levels of serum bilirubin tend to survive longer? To answer questions like this, we can use CTree to recursively partition the data using conditional inference-based tests of independence between each feature and the log-rank scores:

```
(pbc2.ct <- partykit::ctree(Surv(time, status) ~ ., data = pbc2))
```

```
#>
#> Model formula:
#> Surv(time, status) ~ trt + age + sex + ascites + hepato + spiders +
#> edema + bili + chol + albumin + copper + alk.phos + ast +
#> trig + platelet + protime + stage
#>
#> Fitted party:
#> [1] root
#> |   [2] bili <= 1.9
#> |   |   [3] edema in 0
#> |   |   |   [4] stage <= 2: Inf (n = 61)
#> |   |   |   [5] stage > 2: 4191 (n = 104)
#> |   |   [6] edema in 0.5, 1: Inf (n = 16)
#> |   |   [7] bili > 1.9
#> |   |   [8] protime <= 11.2
#> |   |   |   [9] age <= 44.5
#> |   |   |   |   [10] bili <= 5.6: 3839 (n = 29)
#> |   |   |   |   [11] bili > 5.6: 1080 (n = 7)
```