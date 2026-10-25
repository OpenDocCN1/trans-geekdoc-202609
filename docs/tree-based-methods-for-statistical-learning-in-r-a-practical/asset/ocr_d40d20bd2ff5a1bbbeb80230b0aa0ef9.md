The results are displayed in Figure 6.4; the red line shows the average c-ICE value at each above grade square footage (i.e., the centered partial dependence). The heterogeneity in the c-ICE curves indicates a potential interaction effect between Gr_Liv_Area and at least one other feature. The c-ICE curves also indicate a relatively monotonic increasing relationship for the majority of houses in the training set, but you can see a few of the curves at the bottom deviate from this overall pattern.

```
ice <- partial(ames.bag, pred.var = "Gr_Liv_Area", ice = TRUE,
               center = TRUE, quantiles = TRUE, probs = 1:30 / 31)
set.seed(1123) # for reproducibility
samp <- sample.int(nrow(ames.trn), size = 500) # sample 500 homes
autoplot(ice[ice$yhat.id %in% samp, ], alpha = 0.1) +
  ylab("Conditional expectation")
```

![](bbox=[0.183, 0.345, 0.873, 0.633])

FIGURE 6.4: A random sample of 500 c-ICE curves for above grade square footage using the Ames housing bagged tree ensemble. The curves indicate a relatively monotonic increasing relationship for the majority of houses in the sample. The average of the 500 c-ICE curves is shown in red.

# 6.2.6 Example: Edgar Anderson’s iris data

For a classification example, I’ll consider Edgar Anderson’s iris data from the datasets package in R. The iris data frame contains the sepal length, sepal width, petal length, and petal width (in centimeters) for 50 flowers from each of three species of iris: setosa, versicolor, and virginica. Below, I fit a bagged tree ensemble to the data using the randomForest package: