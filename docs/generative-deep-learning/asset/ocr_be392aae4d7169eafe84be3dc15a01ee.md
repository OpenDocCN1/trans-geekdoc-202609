that sum to 1, which can be interpreted as the likelihood that the image belongs to each class.

In Keras, activation functions can be defined within a layer (Example 2-5) or as a separate layer (Example 2-6).

# Example 2-5. A ReLU activation function defined as part of a Dense layer

```
x = layers.Dense(units=200, activation = 'relu')(x)
```

# Example 2-6. A ReLU activation function defined as its own layer

```
x = layers.Dense(units=200)(x)
x = layers.Activation('relu')(x)
```

In our example, we pass the input through two Dense layers, the first with 200 units and the second with 150, both with ReLU activation functions.

# Inspecting the model

We can use the model.summary() method to inspect the shape of the network at each layer, as shown in Table 2-1.

Table 2-1. Output from the model.summary() method

| Layer (type) | Output shape | Param # |
|---|---|---|
| InputLayer | (None, 32, 32, 3) | 0 |
| Flatten | (None, 3072) | 0 |
| Dense | (None, 200) | 614,600 |
| Dense | (None, 150) | 30,150 |
| Dense | (None, 10) | 1,510 |
| Total params | 646,260 |  |
| Trainable params | 646,260 |  |
| Non-trainable params | 0 |  |

Notice how the shape of our Input layer matches the shape of x_train and the shape of our Dense output layer matches the shape of y_train. Keras uses None as a marker for the first dimension to show that it doesn't yet know the number of observations that will be passed into the network. In fact, it doesn't need to; we could just as easily pass 1 observation through the network at a time as 1,000. That's because tensor operations are conducted across all observations simultaneously using linear algebra—this is the part handled by TensorFlow. It is also the reason why you get a performance increase when training deep neural networks on GPUs instead of CPUs: GPUs are