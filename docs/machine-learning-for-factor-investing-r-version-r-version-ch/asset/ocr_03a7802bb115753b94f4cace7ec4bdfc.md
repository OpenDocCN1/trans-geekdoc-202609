```
)
err_ens_2009 <- predict(fit_ens_2009, testing_sample) - testing_sample$R1M_Usd # Pred. errs
```

The third model is a boosted tree.

```
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

```
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

```
E_subtraining <- tibble(err_ens_2007,
                       err_ens_2009,
                       err_ens_2011,
                       err_ens_2013)
cor(E_subtraining)
```

```
##
# err_ens_2007 1.0000000 0.9610165 0.6460091 0.9990129
# err_ens_2009 0.9610165 1.0000000 0.6340258 0.9626267
# err_ens_2011 0.6460091 0.6340258 1.0000000 0.6457394
# err_ens_2013 0.9990129 0.9626267 0.6457394 1.0000000
```

The results are overall disappointing. Only one model manages to extract patterns that are somewhat different from the other ones, resulting in a 65% correlation across the board. Neural networks (on 2013 data) and penalized regressions (2007) remain highly correlated. One possible explanation could be that the models capture mainly noise and little signal.