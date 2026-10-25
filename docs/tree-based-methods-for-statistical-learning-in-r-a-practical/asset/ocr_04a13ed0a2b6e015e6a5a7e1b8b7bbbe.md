![](bbox=[0.226, 0.126, 0.831, 0.353])

FIGURE 7.21: Nonparametric density estimate of age for the complete cases (blue line) and 15 imputed data sets.

Nonparametric densities for passenger age are given in Figure 7.21. There is one density for each of the imputed data sets (red curves) and one density for the original complete case (blue curve). The overall distributions are comparable, but there is certainly some variance across the m = 21 imputation runs. Our goal is to run an RF analysis for each of the m = 21 completed data sets and inspect the variability of the results. For instance, I might graphically show the m = 21 variable importance scores for each feature, along with the mean or median.

Next, I call complete() (from package mice) to produce a list of the m = 21 completed data sets which I can use to carry on with the analysis. The only difference is that I'll perform the same analysis on each for the completed data sets.9

```
t3.mice <- complete(
  data = imp,    # "mids" object (multiply imputed data set)
  action = "all", # return list of all imputed data sets
  include = FALSE # don't include original data (i.e., data with NAs)
)
length(t3.mice) # returns a list of completed data sets
#> [1] 21
```

QThis approach is probably not ideal in situations where the analysis is expensive (e.g., because the data are “big” and the model is expensive to tune). In such cases, you may have to settle for a smaller, less optimal value for m.