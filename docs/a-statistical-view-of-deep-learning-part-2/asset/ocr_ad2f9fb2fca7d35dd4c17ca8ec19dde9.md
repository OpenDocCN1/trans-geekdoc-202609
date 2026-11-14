# Defining the network model in the R interface to Keras

```
model <- keras_model_sequential()
model %>%
  layer_dense(units = 256, activation = 'relu') %>%
  layer_dense(units = 128, activation = 'relu') %>%
  layer_dense(units = 10, activation = 'softmax')
```

keras.rstudio.com