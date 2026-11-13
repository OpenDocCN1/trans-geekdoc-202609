```
## 3 2014-03-31 -0.01574262 2 2014-03-01 236.028 0.002042055 2.32
## 4 2014-04-30 -0.07923669 2014-04-01 236.468 0.001864186 2.29
## 5 2014-05-31 -0.08927884 2014-05-01 236.918 0.001903006 2.17
## 6 2014-06-30 0.04113976 2014-06-01 237.231 0.001321132 2.15
```

We can now build a tree that tries to explain the accuracy of models as a function of macro-variables.

```
library(rpart.plot) # Load package for tree plotting
fit_ens <- rpart(abs(err_NN_test) ~ inflation + termspread, # Tree model
                 data = ens_data,
                 cp = 0.001) # Complexity param (size of tree)
rpart.plot(fit_ens) # Plot tree
```

![](bbox=[0.244, 0.273, 0.752, 0.537])

# FIGURE 11.3: Conditional performance of a ML engine.

The tree creates clusters which have homogeneous values of absolute errors. One big cluster gathers 92% of predictions (the left one) and is the one with the smallest average. It corresponds to the periods when the term spread is above 0.29 (in percentage points). The other two groups (when the term spread is below 0.29%) are determined according to the level of inflation. If the latter is positive, then the average absolute error is 7%, if not, it is 12%. This last number, the highest of the three clusters, indicates that when the term spread is low and the inflation negative, the model's predictions are not trustworthy because their errors have a magnitude twice as large as in other periods. Under these circumstances (which seem to be linked to a dire economic environment), it may be wiser not to use ML-based forecasts.

# 11.3.2 Shrinking inter-model correlations

As shown earlier in this chapter, one major problem with ensembles arises when the first layer of predictions is highly correlated. In this case, ensembles are pretty much useless. There are several tricks that can help reduce this correlation, but the simplest and best is probably to alter training samples. If algorithms do not see the same data, they will probably infer different patterns.