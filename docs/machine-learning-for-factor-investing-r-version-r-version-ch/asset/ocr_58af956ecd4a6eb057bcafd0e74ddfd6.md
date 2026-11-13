```
```r
ntree = n_trees[j],      # Nb of random trees
  mtry = 5)              # Nb of predictors for each tree
mse_RF[j] <- mean((predict(fit_temp, testing_sample) - testing_sample$R1M_Usd)^2)
}
mse_RF
```
```

# [1] 0.03967754 0.03885924 0.03766900 0.03696370 0.03699772

Trees are by definition random so results can vary from test to test. Overall, large numbers of trees are preferable and the reason is that each new tree tells a new story and diversifies the risk of the whole forest. Some more technical details of why that may be the case are outlined in the original paper by Breiman (2001).

For the last exercises, we recycle the formula used in Chapter 6.

```
```r
tree_2008 <- rpart(formula,
  data = data_ml %>% filter(year(date) == 2008), # Data source: 2008
  cp = 0.001,
  maxdepth = 2)
rpart.plot(tree_2008)
```
```

The first splitting criterion in Figure 18.10 is enterprise value (EV). EV is an indicator that adjusts market capitalization by substracting debt and adding cash. It is a more faithful account of the true value of a company. In 2008, the companies that fared the least poorly were those with the highest EV (i.e., large, robust firms).

```
```r
tree_2009 <- rpart(formula,
  data = data_ml %>% filter(year(date) == 2009), # Data source: 2009
  cp = 0.001,
  maxdepth = 2)
rpart.plot(tree_2009)
```
```

In 2009 (Figure 18.11), the firms that recovered the fastest were those that experienced high volatility in the past (likely, downwards volatility). Momentum is also very important: the firms with the lowest past returns are those that rebound the fastest. This is a typical example of the momentum crash phenomenon studied in Barroso and Santa-Clara (2015) and Daniel and Moskowitz (2016). The rationale is the following: after a market downturn, the stocks with the most potential for growth are those that have suffered the largest losses. Consequently, the negative (short) leg of the momentum factor performs very well, often

![](bbox=[0.25, 0.69, 0.75, 0.89])

# FIGURE 18.10: Tree for 2008.