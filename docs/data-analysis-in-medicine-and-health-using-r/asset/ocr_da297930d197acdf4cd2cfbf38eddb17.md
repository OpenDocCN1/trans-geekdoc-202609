# 11.11 Estimation from Cox Proportional Hazards Regression

+   - the standard error
- the p-value
- the confidence intervals for the log hazard

```
tidy(stroke_type,
  conf.int = TRUE)
```

```
## A tibble: 1 x 7
## term estimate std.error statistic p.value conf.low conf.high
## <chr> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
## 1 stroke_typeIS -0.0662 0.317 -2.09 0.0368 -1.28 -0.0406
```

The simple PH model with covariate stroke type shows that the patients with HS -0.0662 times the crude hazard for death as compared to patients with HS (p-value = 0.0368).

The 95% confidence intervals for the crude hazard are calculated by:

> $\hat{\beta} \pm 1.96 \times \widehat{SE}(\hat{\beta})$

> $-0.062 \pm 1.96 \times 0.317 = -1.284, -0.041$

```
tidy(stroke_type,
  exponentiate = TRUE,
  conf.int = TRUE)
```

```
## A tibble: 1 x 7
## term estimate std.error statistic p.value conf.low conf.high
## <chr> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
## 1 stroke_typeIS 0.516 0.317 -2.09 0.0368 0.277 0.960
```

We can get the crude hazard ratio (HR) by exponentiating the log HR. In this example, the simple PH model with covariate stroke type shows that the patients with IS have 49% lower risk for stroke death as compared to patients with HS (p-value = 0.0368 and 95%CI[0.277, 0.960]).

The 95% confidence intervals for crude HR are calculated by

> $exp[\hat{\beta} \pm 1.96 \times \widehat{SE}(\hat{\beta})]$

Hence, the lower bound for crude HR is $exp(-1.284) = 0.277$ and the upper bound for crude HR is $exp(-0.0041) = 0.996$ at 95% confidence.

Let's model the risk for stroke death for covariate gcs: