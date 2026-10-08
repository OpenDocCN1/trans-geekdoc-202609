# 11.13 The Proportional Hazard Assumption

```
stroke_zph <- cox.zph(stroke_mv, transform = 'km')
stroke_zph
```

```
## chisq df p
## stroke_type 1.38336 1 0.24
## gcs 0.00764 1 0.93
## referral_from 1.39355 1 0.24
## GLOBAL 1.63410 3 0.65
```

The test is not significant (p value = 0.65), and the p-value for each of the covariate is larger than 0.05. These evidences support that the there risks are proportional over time.

```
stroke_zph_rank <- cox.zph(stroke_mv, transform = 'rank')
stroke_zph_rank
```

```
## chisq df p
## stroke_type 1.29 1 0.26
## gcs 1.62 1 0.20
## referral_from 1.86 1 0.17
## GLOBAL 3.05 3 0.38
```



We can plot these residuals

+   - deviance
- Schoenfeld
- scaled Schoenfeld

For example, let's start with plotting the residuals

```
ggcoxdiagnostics(stroke_mv, type = "deviance")
```

```
## Warning: `gather_()` was deprecated in tidyr 1.2.0.
## i Please use `gather()` instead.
## i The deprecated feature was likely used in the survminer package.
## i Please report the issue at `https://github.com/kassambara/survminer/issues`.
## This warning is displayed once every 8 hours.
## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was generated.

## `geom_smooth()` using formula = 'y ~ x' `
```