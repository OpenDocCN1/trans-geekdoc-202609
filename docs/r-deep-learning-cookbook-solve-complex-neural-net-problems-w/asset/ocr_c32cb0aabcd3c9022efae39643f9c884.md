+   5. Create encoder and decoder objects by passing symbolic TensorFlow variables:

```
encoder_obj = auto_encoder(x,hiddenLayerEncoder, biasEncoder)
y_pred = auto_encoder(encoder_obj, hiddenLayerDecoder, biasDecoder)
```

+   6. The y_pred is the outcome from decoder, which takes the encoder object as input with nodes and bias weights:

```
Define loss function and optimizer module.
learning_rate = 0.01
cost = tf$reduce_mean(tf$pow(x - y_pred, 2))
optimizer = tf$train$RMSPropOptimizer(learning_rate)$minimize(cost)
```

The preceding script defines mean square error as the cost function, and uses RMSPropOptimizer from TensorFlow with 0.1 learning rate for the optimization of weights. The TensorFlow graph for the preceding model is shown in the following diagram:

![](bbox=[0.143, 0.416, 0.856, 0.75])