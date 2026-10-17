# Histogram of pain$PAIN_CHANGE

![](bbox=[0.12, 0.16, 0.82, 0.39])

```
pain$PERC_PAIN_CHANGE <- pain$PAIN_CHANGE /
pain$PAIN_INTENSITY_AVERAGE
summary(pain$PERC_PAIN_CHANGE)
#> Min. 1st Qu. Median Mean 3rd Qu. Max. NA's
#> -1 0 0 Inf 0 Inf 14520
```

In the summary of the percent change, we can see that the maximum value is Inf. This is R’s representation of infinity. This occurred because some patients have an initial pain score of 0, which creates infinite values when we divide through by this value to find the percent change. We can test whether something is infinite using the is.infinite() or is.finite() functions. This shows that there were three patients with infinite values. The value -Inf is used to represent negative infinity.

```
sum(is.infinite(pain$PERC_PAIN_CHANGE))
#> [1] 3
```

Another special value in R is NaN, which stands for “Not a Number”. For example, 0/0 results in a NaN value. We can test for NaN values using the is.nan() function.

```
0/0
#> [1] NaN
```