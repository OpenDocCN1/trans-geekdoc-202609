At the end of training, the mean and standard deviation statistics in the layer at that time will be used to standardize inputs when the model is used to make a prediction. The default configuration estimating mean and standard deviation across all mini batches is probably sensible.

# 9.2.2 BatchNormalization in Models

Batch normalization can be used at most points in a model and with most types of deep learning neural networks.

# Input and Hidden Layer Inputs

The BatchNormalization layer can be added to your model to standardize raw input variables or the outputs of a hidden layer. Batch normalization is not recommended as an alternative to proper data preparation for your model. Nevertheless, when used to standardize the raw input variables, the layer must specify the input_shape argument; for example:

```
...
model = Sequential
model.add(BatchNormalization(input_shape=(2,)))
...
```

Listing 9.3: Example of batch normalization for input.

When used to standardize the outputs of a hidden layer, the layer can be added to the model just like any other layer.

```
...
model = Sequential
...
model.add(BatchNormalization())
...
```

Listing 9.4: Example of batch normalization between hidden layers.

# Use Before or After the Activation Function

The BatchNormalization layer layer can be used to standardize inputs before or after the activation function of the previous layer. The original paper that introduced the method suggests adding batch normalization before the activation function of the previous layer, for example:

```
...
model = Sequential
model.add(Dense(32))
model.add(BatchNormalization())
model.add(Activation('relu'))
...
```

Listing 9.5: Example of batch normalization before the activation function.

Some reported experiments suggest better performance when adding the batch normalization layer after the activation function of the previous layer; for example: