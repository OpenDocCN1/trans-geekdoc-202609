# Appendix 519

We further split our training set to get a validation set of 5,000 samples. We also proceed to scale down the pixel intensities from 0–255 down to the 0–1 range and convert them to floats by dividing by 255:

```
X_valid, X_train=X_train_full[:5000] / 255,
X_train_full[5000:] / 255,
y_valid, y_train=y_train_full[:5000],
y_train_full[5000]:
X_test=X_test / 255.
```

Let us build MLP model. Our MLP consists of an input layer, taking in the 784 flattened vector of the 28×28 image. The network will also consist of two hidden layers and the output layer, which will use a softmax activation to convert the output numbers to probabilities. The first hidden layer of our network has 300 neurons. The second hidden layer has 100 neurons. Both layers used the rectified linear unit (ReLU) activation function. The output layer consists of ten neurons mapping to the tens in the MNIST fashion dataset. We will use some handy functions from keras to easily build our network:

```
model=keras.models.Sequential(
keras.layers.Flatten(input_shape=[28
```

The total number of trainable parameters for this network can be computed as:

+   - A fully connected hidden layer with 235,500 parameters (784 input × 300 neurons + 300 bias terms)
- A fully connected second hidden layer with 30,100 parameters (300 neurons from the first hidden layer × 100 neurons for the second layer + 100 bias terms)
- A fully connected output layer with 1,010 parameters (100 inputs from the second layer × 10 neurons + 10 bias terms)

In total, our network has 266,610 total trainable parameters.

Our network is initialized with a set of random weights and biases set to 0. Before we begin the process of training our model, we must compile the model, defining our function and performance metric. Here, we use accuracy as our performance metric, as