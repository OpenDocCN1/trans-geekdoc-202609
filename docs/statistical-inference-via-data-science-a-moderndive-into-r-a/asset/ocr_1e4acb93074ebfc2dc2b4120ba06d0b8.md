# 8 Estimation, Confidence Intervals, and Bootstrapping

# 8.2.2 Confidence intervals and the bootstrap: Original workflow

The process of determining bootstrap samples using them for estimation is called bootstrapping. We can estimate population parameters such as the mean, median, or standard deviation. We can also construct confidence intervals.

In this subsection, we focus on the latter and construct confidence intervals based on bootstrap samples. For this, we review the R syntax and workflow we have already used in previous sections and also introduce a new package: the infer package for tidy and transparent statistical inference.

# Original workflow

Recall how we use bootstrap samples, then calculated the sample means from these samples. Let's revisit the original workflow using dplyr verbs and the |> operator.

First, we use rep_sample_n() to resample from the original sample almonds_sample_100 of 5000 almonds. We set size = 100 to generate bootstrap samples of the same size as the original, and we resample with replacement by setting replace = TRUE. We create 1000 bootstrap samples by setting reps = 1000:

```
almonds_sample_100 |>
rep_sample_n(size = 100, replace = TRUE, reps = 1000)
```

Second, we add another pipe followed by summarize() to compute the sample mean weight for each replicate:

```
almonds_sample_100 |>
rep_sample_n(size = 100, replace = TRUE, reps = 1000) |>
summarize(mean_weight = mean(weight))
```

For this simple case, all we needed to use the rep_sample_n() function and a dplyr verb. However, using only dplyr verbs provides us with a limited set of tools that is not ideal when working with more complicated situations. This is the reason we introduce the infer package.

# 8.2.3 The infer package workflow

The infer package is an R package for statistical inference. It makes efficient use of the |> pipe operator we introduced in Section 3.1 to spell out the sequence of steps necessary to perform statistical inference in a “tidy” and transparent fashion. Just as the dplyr package provides functions with verb-like names to perform data wrangling, the infer package provides functions with intuitive verb-like names to