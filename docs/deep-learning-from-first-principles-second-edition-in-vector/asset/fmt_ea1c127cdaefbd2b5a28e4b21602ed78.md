
![Image 335](index-277_1.jpg)

## 2.1c. Stochastic Gradient Descent with Learning rate decay – Octave

```octave
source("DL7functions.m")

# Load and read MNIST
load('./mnist/mnist.txt.gz');

# Create a random permutation from 1024
permutation = randperm(1024);
disp(length(permutation));

# Use this 1024 as the batch
X = trainX(permutation, :);
Y = trainY(permutation, :);

# Set layer dimensions
# 784 – number of input features (28 x 28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions = [784, 15, 9, 10];

# Execute the L-layer Deep Learning network using SGD with learning rate decay
# hidden Activation function – relu
# output activation function – softmax
# learning rate – 0.01
# lrDecay = true
# decayRate = 0.999
# optimizer = "gd" # gradient descent
# mini_batch_size = 512
[weights, biases, costs] = L_Layer_DeepModel_SGD(X', Y', layersDimensions, ...
    hiddenActivationFunc='relu', ...
    outputActivationFunc="softmax", ...
    learningRate = 0.01, ...
    lrDecay=true, ...
    decayRate=0.999, ...
    lambd=0, ...
    keep_prob=1, ...
    optimizer="gd", ...
    beta=0.9, ...
    beta1=0.9, ...
    beta2=0.999, ...
    epsilon=10^-8, ...
    mini_batch_size = 512, ...
    num_epochs = 5000);

# Plot cost vs number of epochs
plotCostVsEpochs(5000, costs)
```

![Image 336](index-280_1.jpg)
![Image 337](index-281_1.jpg)
![Image 338](index-281_2.jpg)
![Image 339](index-281_3.jpg)
![Image 340](index-281_4.jpg)
![Image 341](index-281_5.jpg)
![Image 342](index-281_6.jpg)

## 3.1. Stochastic Gradient Descent with Momentum

Stochastic Gradient Descent with Momentum uses the exponentially weighted average method discussed above and hence moves faster into the ravine than across it. The equations are:

where `v_dW` and `v_db` are the momentum terms which are exponentially weighted with the corresponding gradients `dW` and `db` at the corresponding layer `l`.

The code snippet for Stochastic Gradient Descent with momentum in R is shown below:

```r
# Perform Gradient Descent with momentum
# Input : Weights and biases
#       : beta
#       : gradients
#       : learning rate
#       : outputActivationFunc - Activation function at hidden layer sigmoid/softmax
# output : Updated weights after 1 iteration
gradientDescentWithMomentum <- function(parameters, gradients, v, beta, learningRate, outputActivationFunc="sigmoid") {
  L = length(parameters) / 2 # number of layers in the neural network

  # Update rule for each parameter. Use a for loop.
  for (l in 1:(L-1)) {
    # Compute velocities
    # v['dWk'] = beta * v['dWk'] + (1-beta) * dWk
    v[[paste("dW", l, sep="")]] = beta * v[[paste("dW", l, sep="")]] +
      (1 - beta) * gradients[[paste('dW', l, sep="")]]
    v[[paste("db", l, sep="")]] = beta * v[[paste("db", l, sep="")]] +
      (1 - beta) * gradients[[paste('db', l, sep="")]]

    # Update parameters with velocities
    parameters[[paste("W", l, sep="")]] = parameters[[paste("W", l, sep="")]] -
      learningRate * v[[paste("dW", l, sep="")]]
    parameters[[paste("b", l, sep="")]] = parameters[[paste("b", l, sep="")]] -
      learningRate * v[[paste("db", l, sep="")]]
  }

  # Compute for the Lth layer if output activation is sigmoid
  if (outputActivationFunc == "sigmoid") {
    v[[paste("dW", L, sep="")]] = beta * v[[paste("dW", L, sep="")]] +
      (1 - beta) * gradients[[paste('dW', L, sep="")]]
    v[[paste("db", L, sep="")]] = beta * v[[paste("db", L, sep="")]] +
      (1 - beta) * gradients[[paste('db', L, sep="")]]
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] -
      learningRate * v[[paste("dW", l, sep="")]]
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] -
      learningRate * v[[paste("db", l, sep="")]]
  } else if (outputActivationFunc == "softmax") { # If output activation is Softmax
    v[[paste("dW", L, sep="")]] = beta * v[[paste("dW", L, sep="")]] +
      (1 - beta) * t(gradients[[paste('dW', L, sep="")]])
    v[[paste("db", L, sep="")]] = beta * v[[paste("db", L, sep="")]] +
      (1 - beta) * t(gradients[[paste('db', L, sep="")]])
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] -
      learningRate * t(gradients[[paste("dW", L, sep="")]])
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] -
      learningRate * t(gradients[[paste("db", L, sep="")]])
  }
  return(parameters)
}
```

### 3.1a. Stochastic Gradient Descent with Momentum – Python

```python
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
import sklearn.linear_model
import pandas as pd
import sklearn
import sklearn.datasets

# Read and load data and labels
exec(open("DLfunctions7.py").read())
exec(open("load_mnist.py").read())

training = list(read(dataset='training', path=".\\mnist"))
test = list(read(dataset='testing', path=".\\mnist"))

lbls = []
pxls = []

for i in range(60000):
    l, p = training[i]
    lbls.append(l)
    pxls.append(p)

labels = np.array(lbls)
pixels = np.array(pxls)

y = labels.reshape(-1, 1)
X = pixels.reshape(pixels.shape[0], -1)
X1 = X.T
Y1 = y.T

# Create a list of random numbers of 1024
permutation = list(np.random.permutation(2**10))

# Subset 1024 random samples from the data
X2 = X1[:, permutation]
Y2 = Y1[:, permutation].reshape((1, 2**10))

# Set layer dimensions
# 784 – number of input features (28 x 28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions = [784, 15, 9, 10]

# Execute the L-Layer Deep Learning network using SGD with momentum
# hidden Activation function – relu
# output activation function – softmax
# learning rate – 0.01
# optimizer = "momentum"
# beta = 0.9
# mini_batch_size = 512
parameters = L_Layer_DeepModel_SGD(X2, Y2, layersDimensions,
    hiddenActivationFunc='relu',
    outputActivationFunc="softmax",
    learningRate=0.01,
    optimizer="momentum",
    beta=0.9,
    mini_batch_size=512,
    num_epochs=1000,
    print_cost=True,
    figure="fig3.png")
```

![Image 343](index-285_1.jpg)

### 3.1b. Stochastic Gradient Descent with Momentum – R

```r
source("mnist.R")
source("DLfunctions7.R")
load_mnist()

x <- t(train$x)
X <- x[, 1:60000]
y <- train$y
y1 <- y[1:60000]
y2 <- as.matrix(y1)
Y <- t(y2)

# Subset 1024 random samples from MNIST
permutation <- c(sample(2^10))

# Randomly shuffle the training data
X1 <- X[, permutation]
y1 <- Y[1, permutation]
y2 <- as.matrix(y1)
Y1 <- t(y2)

# Set layer dimensions
# 784 – number of input features (28 x 28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions <- c(784, 15, 9, 10)

# Execute the L-Layer Deep Learning network using SGD with momentum
# hidden Activation function – tanh
# output activation function – softmax
# learning rate – 0.05
# optimizer = "momentum"
# beta = 0.9
# mini_batch_size = 512
retvalsSGD <- L_Layer_DeepModel_SGD(X1, Y1, layersDimensions,
    hiddenActivationFunc='tanh',
    outputActivationFunc="softmax",
    learningRate=0.05,
    optimizer="momentum",
    beta=0.9,
    mini_batch_size=512,
    num_epochs=5000,
    print_cost=True)

# Plot the cost vs number of epochs
iterations <- seq(0, 5000, 1000)
costs <- retvalsSGD$costs
df <- data.frame(iterations, costs)
ggplot(df, aes(x=iterations, y=costs)) + geom_point() + geom_line(color="blue") +
  ggtitle("Costs vs number of epochs") + xlab("No of epochs") + ylab("Cost")
```

![Image 344](index-287_1.jpg)

### 3.1c. Stochastic Gradient Descent with Momentum – Octave

```octave
source("DL7functions.m")

# Load and read MNIST
load('./mnist/mnist.txt.gz');

# Create a random permutation from 60K
permutation = randperm(1024);
disp(length(permutation));

# Use this 1024 as the batch
X = trainX(permutation, :);
Y = trainY(permutation, :);

# Set layer dimensions
# 784 – number of input features (28 x 28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions = [784, 15, 9, 10];
```
