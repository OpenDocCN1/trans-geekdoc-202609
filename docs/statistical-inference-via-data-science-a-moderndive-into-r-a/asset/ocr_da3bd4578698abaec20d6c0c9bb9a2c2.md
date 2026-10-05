# 8.1 Tying the sampling distribution estimation

# Learning check

(LC8.1) What is the expected value of the sample mean weight of almonds in a large sample according to the sampling distribution theory?

+   - A. It is always larger than the population mean.
- B. It is always smaller than the population mean.
- C. It is exactly equal to the population mean.
- D. It is equal to the population mean on average but may vary in any single sample.

(LC8.2) What is a point estimate and how does it differ from an interval estimate in the context of statistical estimation?

+   - A. A point estimate uses multiple values to estimate a parameter; an interval estimate uses a single value.
- B. A point estimate is a single value used to estimate a parameter; an interval estimate provides a range of values within which the parameter likely falls.
- C. A point estimate is the mean of multiple samples; an interval estimate is the median.
- D. A point estimate and an interval estimate are the same and can be used interchangeably.

# 8.1.1 Revisiting the almond activity for estimation

In Chapter 7, the activities was to take many random samples of size 100 from a bowl of 5,000 chocolate-covered almonds. Since we have access to the contents of the entire bowl, we can compute the population parameters:

```
almonds_bowl |>
summarize(population_mean = mean(weight),
  population_sd = pop_sd(weight))
```

```
# A tibble: 1 x 2
population_mean population_sd
  <dbl>           <dbl>
1             3.64496      0.392070
```