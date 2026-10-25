![](bbox=[0.19, 0.09, 0.88, 0.35])

FIGURE 7.22: Imputed values for the 263 missing age values. The yellow line corresponds to the proximity-based imputation. The light gray lines correspond to the 15 different imputation runs using MICE, and the black line corresponds to their average.

for this passenger as 17.522 years, whereas MICE gives an average of 4.571 years and a plausible range of 0.75–8.00 years. Similarly, the proximity method imputed the age for case 959—a third-class female with three children—as 23.52 whereas MICE gave an average of 40.238. Which imputations do you think are more plausible?

```
t3[c(956, 959), ]
```

```
#>   survived pclass age   sex sibsp parch
#> 956      0     3  NA female     3     1
#> 959      0     3  NA female     0     4
```

# 7.9.3.2 Analyzing the imputed data sets

With the m = 21 completed data sets in hand, I can proceed with the RF analysis. The idea here is to fit an RF separately to each completed data set. I’ll then look at the variance of the results (e.g., OOB error, variable importance scores, etc.) to judge its sensitivity to the different plausible imputations. Below, I use the ranger package to fit a (default) RF/probability machine to each of the m = 21 completed data sets. In anticipation of looking at the sensitivity of the variable importance scores, I set importance =