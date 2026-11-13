

There are several ways to split the training data so as to build different subsets of training samples. The first dichotomy is between random versus deterministic splits. Random splits are easy and require only the target sample size to be fixed. Note that the training samples can be overlapping as long as the overlap is not too large. Hence if the original training sample has $I$ instance and the ensemble requires $M$ models, then a subsample size of $\lceil I/M \rceil$ may be too conservative especially if the training sample is not very large. In this case $\lceil I/\sqrt{M} \rceil$ may be a better alternative. Random forests are one example of ensembles built in random training samples.

One advantage of deterministic splits is that they are easy to reproduce and their outcome does not depend on the random seed. By the nature of factor-based training samples, the second splitting dichotomy is between time and assets. A split within assets is straightforward: each model is trained on a different set of stocks. Note that the choices of sets can be random, or dictated by some factor-based criterion: size, momentum, book-to-market ratio, etc.

A split in dates requires other decisions: is the data split in large blocks (like years) and each model gets a block, which may stand for one particular kind of market condition? Or are the training dates divided more regularly? For instance, if there are 12 models in the ensemble, each model can be trained on data from a given month (e.g., January for the first models, February for the second, etc.).

Below, we train four models on four different years to see if this helps reduce the inter-model correlations. This process is a bit lengthy because the samples and models need to be all redefined. We start by creating the four training samples. The third model works on the small subset of features, hence the sample is smaller.

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

Then, we proceed to the training of the models. The syntaxes are those used in the previous chapters, nothing new here. We start with a penalized regression. In all predictions below, the original testing sample is used for all models.

```r
y_ens_2007 <- training_sample_2007$R1M_Usd           # Dep. var.
x_ens_2007 <- training_sample_2007 %>%               # Predictors
  dplyr::select(features) %>% as.matrix()
fit_ens_2007 <- glmnet(x_ens_2007, y_ens_2007, alpha = 0.1, lambda = 0.1)   # Model
err_ens_2007 <- predict(fit_ens_2007, x_penalized_test) - testing_sample$R1M_Usd # Pred. errs
```

We continue with a random forest.

```r
fit_ens_2009 <- randomForest(formula,
                             data = training_sample_2009,   # Same formula as for simple trees!
                             sampsize = 4000,              # Data source: 2011 training sample
                             replace = FALSE,              # Size of (random) sample for each tree
                             nodesize = 100,               # Is the sampling done with replacement?
                             ntree = 40,                   # Minimum size of terminal cluster
                             mtry = 30                     # Nb of random trees
                             # Nb of predictive variables for each tree
)
err_ens_2009 <- predict(fit_ens_2009, testing_sample) - testing_sample$R1M_Usd # Pred. errs
```

The third model is a boosted tree.

```r
train_features_2011 <- training_sample_2011 %>%
  dplyr::select(features_short) %>% as.matrix()       # Independent variable
train_label_2011 <- training_sample_2011 %>%
  dplyr::select(R1M_Usd) %>% as.matrix()             # Dependent variable
train_matrix_2011 <- xgb.DMatrix(data = train_features_2011,
                                 label = train_label_2011)    # XGB format!
fit_ens_2011 <- xgb.train(data = train_matrix_2011,       # Data source
                          eta = 0.4,                    # Learning rate
                          objective = "reg:linear",     # Objective function
                          max_depth = 4,                # Maximum depth of trees
                          nrounds = 18                  # Number of trees used
                         )
err_ens_2011 <- predict(fit_ens_2011, xgb_test) - testing_sample$R1M_Usd # Prediction errors
```

Finally, the last model is a simple neural network.

```r
NN_features_2013 <- dplyr::select(training_sample_2013, features) %>%   # Matrix format is important
                    as.matrix()
NN_labels_2013 <- training_sample_2013$R1M_Usd
model_ens_2013 <- keras_model_sequential()
model_ens_2013 %>%   # This defines the structure of the network, i.e. how layers are organized
  layer_dense(units = 16, activation = 'relu', input_shape = ncol(NN_features_2013)) %>%   #
  layer_dense(units = 8, activation = 'tanh') %>%   #
  layer_dense(units = 1)
model_ens_2013 %>% compile(   # Model specification
  loss = 'mean_squared_error',   # Loss function
  optimizer = optimizer_rmsprop(),   # Optimisation method (weight updating)
  metrics = c('mean_absolute_error')   # Output metric
)
model_ens_2013 %>% fit(NN_features_2013,   # Training features
                       NN_labels_2013,      # Training labels
                       epochs = 9, batch_size = 128   # Training parameters
                      )
err_ens_2013 <- predict(model_ens_2013, NN_test_features) - testing_sample$R1M_Usd
```

Endowed with the errors of the four models, we can compute their correlation matrix.

```r
E_subtraining <- tibble(err_ens_2007,
                       err_ens_2009,
                       err_ens_2011,
                       err_ens_2013)
cor(E_subtraining)
```

| | err_ens_2007 | err_ens_2009 | err_ens_2011 | err_ens_2013 |
|---|---|---|---|---|
| err_ens_2007 | 1.0000000 | 0.9610165 | 0.6460091 | 0.9990129 |
| err_ens_2009 | 0.9610165 | 1.0000000 | 0.6340258 | 0.9626267 |
| err_ens_2011 | 0.6460091 | 0.6340258 | 1.0000000 | 0.6457394 |
| err_ens_2013 | 0.9990129 | 0.9626267 | 0.6457394 | 1.0000000 |

The results are overall disappointing. Only one model manages to extract patterns that are somewhat different from the other ones, resulting in a 65% correlation across the board. Neural networks (on 2013 data) and penalized regressions (2007) remain highly correlated. One possible explanation could be that the models capture mainly noise and little signal.

## 11.4 Exercise

Build an integrated ensemble on top of 3 neural networks trained entirely with Keras. Each network obtains one third of predictors as input. The three networks yield a classification (yes/no or buy/sell). The overarching network aggregates the three outputs into a final decision. Evaluate its performance on the testing sample. Use the functional API.

## Portfolio backtesting

In this section, we introduce the notations and framework that will be used when analyzing and comparing investment strategies. Portfolio backtesting is often conceived and perceived as a quest to find the best strategy - or at least a solidly profitable one. When carried out thoroughly, this possibly long endeavor may entice the layman to confuse a fluke for a robust policy. Two papers published back-to-back warn against the **perils of data snooping**, which is related to _p_-hacking. In both cases, the researcher will torture the data until the sought result is found.

Fabozzi and de Prado (2018) acknowledge that only strategies that work make it to the public, while thousands (at least) have been tested. Picking the pleasing outlier (the only strategy that seemed to work) is likely to generate disappointment when switching to real trading. In a similar vein, Arnott et al. (2019b) provide a list of principles and safeguards that any analyst should follow to avoid any type of error when backtesting strategies. The worst type is arguably **false positives** whereby strategies are found (often by cherrypicking) to outperform in one very particular setting, but will likely fail in live implementation.

In addition to these recommendations on portfolio constructions, Arnott et al. (2019a) also warn against the hazards of blindly investing in smart beta products related to academic factors. Plainly, expectations should not be set too high or face the risk of being disappointed. Another takeaway from their article is that **economic cycles** have a strong impact on factor returns: correlations change quickly and drawdowns can be magnified in times of major downturns.

Backtesting is more complicated than it seems and it is easy to make small mistakes that lead to _apparently_ good portfolio policies. This chapter lays out a rigorous approach to this exercise, discusses a few caveats, and proposes a lengthy example.

### 12.1 Setting the protocol

We consider a dataset with three dimensions: time \(t = 1, ..., T\), assets \(n = 1, ..., N\) and characteristics \(k = 1, ..., K\). One of these attributes must be the price of asset \(n\) at time \(t\), which we will denote \(p_{t,n}\). From that, the computation of the arithmetic return is straightforward (\(r_{t,n} = p_{t,n}/p_{t-1,n} - 1\)) and so is any heuristic measure of profitability. For simplicity, we assume that time points are equidistant or uniform, i.e., that \(t\) is the index of a trading day or of a month for example. If each point in time \(t\) has data available for all assets, then this makes a dataset with \(I = T \times N\) rows.

The dataset is first split in two: the out-of-sample period and the **initial buffer** period. The buffer period is required to train the models for the first portfolio composition. This period
