"permutation" to employ the OOB-based permutation variable importance procedure discussed in Section 7.5.2.

```
library(ranger)
```

```
# Obtain a list of probability forests, one for each imputed data set
set.seed(2147) # for reproducibility
rfos <- lapply(t3.mice, FUN = function(x) {
  ranger(as.factor(survived) ~ ., data = x, probability = TRUE,
         importance = "permutation")
})
```

```
# Check OOB errors (Brier-score, in this case)
sapply(rfos, FUN = function(forest) forest$prediction.error)
#>  1  2  3  4  5  6  7  8  9
#> 0.134 0.133 0.135 0.134 0.134 0.134 0.135 0.134 0.132
#>  10 11 12 13 14 15 16 17 18
#> 0.133 0.132 0.133 0.133 0.135 0.135 0.135 0.133 0.134
#>  19 20 21
#> 0.134 0.134 0.133
```

The OOB errors from each model are comparable; that's a good start! The average OOB Brier score is 0.134, with a standard deviation of 0.001.

Next, I'll look at variable importance. With multiple imputation I think the most sensible thing to do is to just plot the variable importance scores from each run together, so that you can see the variability in the results:

```
# Compute list of VI scores, one for each model. Note: can use
# FUN = ranger::importance` to be safe
vis <- lapply(rfos, FUN = importance)
```

```
# Stack into a data frame
head(vis <- as.data.frame(do.call(rbind, args = vis)))
```

| | pclass | age | sex | sibsp | parch |
|---|---|---|---|---|---|
| 1 | 0.0531 | 0.0370 | 0.122 | 0.0130 | 0.0149 |
| 2 | 0.0529 | 0.0404 | 0.125 | 0.0143 | 0.0145 |
| 3 | 0.0504 | 0.0323 | 0.124 | 0.0126 | 0.0139 |
| 4 | 0.0498 | 0.0336 | 0.125 | 0.0149 | 0.0131 |
| 5 | 0.0540 | 0.0393 | 0.122 | 0.0135 | 0.0161 |
| 6 | 0.0533 | 0.0407 | 0.123 | 0.0137 | 0.0142 |

```
# Display boxplots of results
boxplot(vis, las = 1)
```

Figure 7.23 shows a boxplot of the m = 21 variable importance scores for each feature; these are the OOB-based permutation scores discussed in Section 7.5.2. The results do not vary too much, so we can be somewhat confident in the overall ranking of the features. Clearly sex is the most important