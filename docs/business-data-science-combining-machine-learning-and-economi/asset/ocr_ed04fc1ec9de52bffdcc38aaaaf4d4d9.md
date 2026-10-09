```
> n <- nrow(SC) # the number of observations  
> K <- 10 # the number of ‘folds’  
> # create a vector of fold memberships (random order)  
> foldid <- rep(1:K, each=ceiling(n/K))[sample(1:n)]  
> # create an empty dataframe of results  
> OOS <- data.frame(full=rep(NA, K), cut=rep(NA, K))
```

Finally, we run the OOS experiment as a for loop.

```
> for(k in 1:K){
+   train <- which(foldid!=k) # train on all but fold ‘k’
+
+   ## fit the two regressions
+   rfull <- glm(FAIL~., data=SC, subset=train, family=binomial)
+   rcut <- glm(FAIL~., data=SC[, cutvar], subset=train, family=binomial)
+
+   ## get predictions: type=response so we have probabilities
+   predfull <- predict(rfull, newdata=SC[-train,], type="response")
+   predcut <- predict(rcut, newdata=SC[-train,], type="response")
+
+   ## calculate and log R2
+   OOS$full[k] <- R2(y=SC$FAIL[- train], pred=predfull, family="binomial")
+   OOS$cut[k] <- R2(y=SC$FAIL[- train], pred=predcut, family="binomial")
+
+   ## print progress
+   cat(k, " ")
+ }
1  2  3  4  5  6  7  8  9 10
```

When we plot the resulting OOS $R_2$ samples, the results are striking. Figure 3.3 shows that the full model actually yields negative $R_2$! How can this happen? Look at the $R_2$ formula: $1 - \mathrm{dev}(\widehat{\boldsymbol{\beta}}) / \mathrm{dev}(\boldsymbol{\beta} = 0)$. The $R_2$ will be negative if your fitted model performs worse than the null model. That is, if your $\hat{y}$ estimates are further from the truth than the overall average, $\bar{y}$. In this