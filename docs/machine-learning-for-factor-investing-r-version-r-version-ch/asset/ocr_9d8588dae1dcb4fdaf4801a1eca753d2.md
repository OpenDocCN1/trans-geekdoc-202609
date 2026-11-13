There are several ways to split the training data so as to build different subsets of training samples. The first dichotomy is between random versus deterministic splits. Random splits are easy and require only the target sample size to be fixed. Note that the training samples can be overlapping as long as the overlap is not too large. Hence if the original training sample has $I$ instance and the ensemble requires $M$ models, then a subsample size of $\lceil I/M ceil$ may be too conservative especially if the training sample is not very large. In this case $\lceil I/\sqrt{M} ceil$ may be a better alternative. Random forests are one example of ensembles built in random training samples.

One advantage of deterministic splits is that they are easy to reproduce and their outcome does not depend on the random seed. By the nature of factor-based training samples, the second splitting dichotomy is between time and assets. A split within assets is straightforward: each model is trained on a different set of stocks. Note that the choices of sets can be random, or dictated by some factor-based criterion: size, momentum, book-to-market ratio, etc.

A split in dates requires other decisions: is the data split in large blocks (like years) and each model gets a block, which may stand for one particular kind of market condition? Or are the training dates divided more regularly? For instance, if there are 12 models in the ensemble, each model can be trained on data from a given month (e.g., January for the first models, February for the second, etc.).

Below, we train four models on four different years to see if this helps reduce the inter-model correlations. This process is a bit lengthy because the samples and models need to be all redefined. We start by creating the four training samples. The third model works on the small subset of features, hence the sample is smaller.

```
```r
training_sample_2007 <- training_sample %>%
  filter(date > "2006-12-31", date < "2008-01-01")
training_sample_2009 <- training_sample %>%
  filter(date > "2008-12-31", date < "2010-01-01")
training_sample_2011 <- training_sample %>%
  dplyr::select(c("date", "features_short", "$R1M_Usd")) %>%
  filter(date > "2010-12-31", date < "2012-01-01")
training_sample_2013 <- training_sample %>%
  filter(date > "2012-12-31", date < "2014-01-01")
```
```

Then, we proceed to the training of the models. The syntaxes are those used in the previous chapters, nothing new here. We start with a penalized regression. In all predictions below, the original testing sample is used for all models.

```
```r
y_ens_2007 <- training_sample_2007$R1M_Usd           # Dep. var.
x_ens_2007 <- training_sample_2007 %>%               # Predictors
  dplyr::select(features) %>% as.matrix()
fit_ens_2007 <- glmnet(x_ens_2007, y_ens_2007, alpha = 0.1, lambda = 0.1)   # Model
err_ens_2007 <- predict(fit_ens_2007, x_penalized_test) - testing_sample$R1M_Usd # Pred. errs
```
```

We continue with a random forest.

```
```r
fit_ens_2009 <- randomForest(formula,
                             data = training_sample_2009,   # Same formula as for simple trees!
                             sampsize = 4000,              # Data source: 2011 training sample
                             replace = FALSE,              # Size of (random) sample for each tree
                             nodesize = 100,               # Is the sampling done with replacement?
                             ntree = 40,                   # Minimum size of terminal cluster
                             mtry = 30                     # Nb of random trees
                             # Nb of predictive variables for each tree
```
```