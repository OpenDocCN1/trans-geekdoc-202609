# 18.9 Chapter 16

We recycle the AE model trained in Chapter 15. Strangely, building smaller models (encoder) from larger ones (AE) requires to save and then reload the weights. This creates an external file, which we call “ae_weights”. We can check that the output does have 4 columns (compressed) instead of 7 (original data).

```
save_model_weights_hdf5(object = ae_model,filepath ="ae_weights.hdf5", overwrite = TRUE)
encoder_model <- keras_model(inputs = input_layer, outputs = encoder)
encoder_model %>%
load_model_weights_hdf5(filepath = "ae_weights.hdf5",skip_mismatch = TRUE,by_name = TRUE)
encoder_model %>% compile(
loss = 'mean_squared_error',
optimizer = 'adam',
metrics = c('mean_absolute_error')
)
encoder_model %>%
keras::predict_on_batch(x = training_sample %>%
dplyr::select(features_short) %>%
as.matrix()) %>%
head(5)
```

## [,1] [,2] [,3] [,4]
## [1,] 1.038496 -0.2121131 0.5755218 0.7277557
## [2,] 1.037245 -0.1829648 0.5782604 0.6981937
## [3,] 1.035456 -0.1848094 0.5722961 0.7637734
## [4,] 1.030122 -0.1830992 0.5703658 0.7688833
## [5,] 1.015239 -0.1816818 0.5698297 0.7628086

# 18.10 Chapter 17

All we need to do is change the rho coefficient in the code of Chapter 16.

```
set.seed(42)
n_sample <- 10^-5
rho <- (-0.8)
sd <- 0.4
a <- 0.06 * rho
data_RL3 <- tibble(returns = a/rho + arima.sim(n = n_sample,
list(ar = rho),
sd = sd),
action = round(runif(n_sample)*4)/4) %>%
mutate(new_state = if_else(returns < 0, "neg", "pos"),
reward = returns * action,
state = lag(new_state),
action = as.character(action)) %>%
na.omit()
```

The learning can then proceed.