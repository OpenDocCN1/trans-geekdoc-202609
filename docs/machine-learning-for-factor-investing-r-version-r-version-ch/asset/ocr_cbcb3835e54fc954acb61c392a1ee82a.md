```
model %>%  # This defines the structure of the network, i.e. how layers are organized
  layer_dense(units = 16, activation = 'relu', input_shape = ncol(NN_train_features)) %>%
  layer_dense(units = 8, activation = 'tanh') %>%
  layer_dense(units = 1)  # No activation means linear activation: f(x) = x.
```

The definition of the structure is very intuitive and uses the sequential syntax in which one input is iteratively transformed by a layer until the last iteration which gives the output. Each layer depends on two parameters: the number of units and the activation function that is applied to the output of the layer. One important point is the input_shape parameter for the first layer. It is required for the first layer and is equal to the number of features. For the subsequent layers, the input_shape is dictated by the number of units of the previous layer; hence it is not required. The activations that are currently available are listed on https://keras.io/activations/. We use the hyperbolic tangent in the second-to-last layer because it yields both positive and negative outputs. Of course, the last layer can generate negative values as well, but it's preferable to satisfy this property one step ahead of the final output.

```
model %>% compile(
  loss = 'mean_squared_error',
  optimizer = optimizer_rmsprop(),
  metrics = c('mean_absolute_error')
)
summary(model)
# Model specification
# Loss function
# Optimisation method (weight updating)
# Output metric
# Model architecture
```

| Layer (type) | Output Shape | Param # |
|---|---|---|
| dense_48 (Dense) | (None, 16) | 1504 |
| dense_49 (Dense) | (None, 8) | 136 |
| dense_50 (Dense) | (None, 1) | 9 |
| Total params: 1,649 | | |
| Trainable params: 1,649 | | |
| Non-trainable params: 0 | | |

The summary of the model lists the layers in their order from input to output (forward pass). Because we are working with 93 features, the number of parameters for the first layer (16 units) is 93 plus one (for the bias) multiplied by 16, which makes 1504. For the second layer, the number of inputs is equal to the size of the output from the previous layer (16). Hence given the fact that the second layer has 8 units, the total number of parameters is (16+1)*8 = 136.

We set the loss function to the standard mean squared error. Other losses are listed on https://keras.io/losses/, some of them work only for regressions (MSE, MAE) and others only for classification (categorical cross-entropy, see Equation (7.10)). The RMS propragation optimizer is the classical mini-batch back-propagation implementation. For other weight updating algorithms, we refer to https://keras.io/optimizers/. The metric is the function used to assess the quality of the model. It can be different from the loss: for instance, using entropy for training and accuracy as the performance metric.

The final stage fits the model to the data and requires some additional training parameters: