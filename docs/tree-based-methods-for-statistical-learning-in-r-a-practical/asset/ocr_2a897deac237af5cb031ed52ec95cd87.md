against the averaged predictions obtained from the for loop. The results are displayed in Figure 6.2 and show a relatively monotonic increasing relationship between above grade square footage and predicted sale price.

```
```r
x.grid <- quantile(ames.trn$Gr_Liv_Area, probs = 1:30 / 31)
pd <- numeric(length(x.grid))
for (i in seq_along(x.grid)) {
  temp <- ames.trn # temporary copy of data
  temp[["Gr_Liv_Area"]] <- x.grid[i]
  pd[i] <- mean(predict(ames.bag, newdata = temp))
}
```
```

```
```r
# PD plot for above grade square footage (Figure 6.2)
plot(x.grid, pd, type = "l", xlab = "Above ground square footage",
ylab = "Partial dependence", las = 1)
rug(x.grid) # add rug plot to x-axis
```
```

![](bbox=[0.215, 0.368, 0.875, 0.653])

# FIGURE 6.2: Partial dependence of sale price on above grade square footage for the bagged tree ensemble.

While looking at the partial dependence of the response on a single feature (i.e., main effect) is informative, it is often useful to look at the dependence on two or three predictors simultaneously^a (i.e., interaction effects). Fortunately, it is rather straightforward to modify the above for loop to accommodate multiple predictors; however, this is a good opportunity to show an alternative