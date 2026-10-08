# 8.10 Simple Binary Logistic Regression

## AIC: 174.92

## Number of Fisher Scoring iterations: 5

To get the model using in a data frame, so we can edit value of more easily, we can use the tidy() function from the broom package. The package also contains functions to provide other parameters useful for us later.

The function conf_int() will provide the confidence intervals (CI). The default is at the 95 level:

```
tidy(fatal_glm_1, conf_int = TRUE)
```

```
## tibble: 2 x 7
## term estimate std.error statistic p.value conf.low conf.high
## <chr> <dbl> <dbl> <dbl> <dbl> <dbl>
## 1 (Intercept) 3.29 0.604 5.45 e-14 -8 2.17 4.55
## 2 gcs -0.388 0.0521 -7.96 e-04 -0.497 -0.292
```

The estimates are the odds for death for a given value of gs. In this example, each unit increase in gs, the crude or unadjusted odds for death for stroke change by a factor -0.388 with 95 CI ranges from -0.497and-0.292.

Now, let's use another covariate, stroke_type. Stroke type has 2 levels or categories; Hemorrhagic Stroke (HS) and Ischemic Stroke (IS). HS is known to cause a higher risk for deaths in stroke. We will model stroke type (stroke_type), name the model as fatal_glm_2 and show the result using tidy()

```
fatal_glm_2 <-
glm(status ~ stroke_type,
  family = binomial(link = 'logit'))
tidy(fatal_glm_2, conf_int = TRUE)
```

```
## tibble: 2 x 7
## term estimate std.error statistic p.value conf.low conf.high
## <chr> <dbl> <dbl> <dbl> <dbl> <dbl>
## 1 (Intercept) -2.05 0.258 -7.95 e-01 -2.59 -1.57
## 2 stroke_typeHaemorrh- 2.02 0.344 5.88 4.05e-09 1.36 2.72
```

The simple logistic regression model show that patients with Hemorrhagic Stroke (HS) had a higher odds for death during admission (by a factor 2.02) compared to patients with Ischemic Stroke (IS).