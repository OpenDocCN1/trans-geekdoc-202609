
# The bias corrections for the 2nd moment

The Adam Gradient Descent is given by

The code snippet of Adam in R is included be

## Perform Gradient Descent with Adam

**Input:**
- Weights and biases
- `beta1`
- `epsilon`
- `gradients`
- `learning rate`
- `outputActivationFunc` - Activation function at hidden layer sigmoid/softmax

**Output:** Updated weights after 1 iteration

```r
gradientDescentWithAdam <- function(parameters, gradients, v, s, t, beta1=0.9, beta2=0.999, epsilon=10^-8,
                                    learningRate=0.1, outputActivationFunc="sigmoid") {

  L = length(parameters)/2 # number of layers in the neural network
  v_corrected <- list()
  s_corrected <- list()

  # Update rule for each parameter.
  for(l in 1:(L-1)) {

    # v[['dWk']] = beta * v[['dWk']] + (1-beta)*dWk
    v[[paste("dW", l, sep="")]] = beta1 * v[[paste("dW", l, sep="")]] +
      (1 - beta1) * gradients[[paste('dW', l, sep="")]]

    v[[paste("db", l, sep="")]] = beta1 * v[[paste("db", l, sep="")]] +
      (1 - beta1) * gradients[[paste('db', l, sep="")]]

    # Compute bias-corrected first moment estimate.
    v_corrected[[paste("dW", l, sep="")]] = v[[paste("dW", l, sep="")]] / (1 - beta1^t)
    v_corrected[[paste("db", l, sep="")]] = v[[paste("db", l, sep="")]] / (1 - beta1^t)

    # Element wise multiply of gradients
    s[[paste("dW", l, sep="")]] = beta2 * s[[paste("dW", l, sep="")]] +
      (1 - beta2) * gradients[[paste('dW', l, sep="")]] *
      gradients[[paste('dW', l, sep="")]]

    s[[paste("db", l, sep="")]] = beta2 * s[[paste("db", l, sep="")]] +
      (1 - beta2) * gradients[[paste('db', l, sep="")]] *
      gradients[[paste('db', l, sep="")]]

    # Compute bias-corrected second moment estimate.
    s_corrected[[paste("dW", l, sep="")]] = s[[paste("dW", l, sep="")]] / (1 - beta2^t)
    s_corrected[[paste("db", l, sep="")]] = s[[paste("db", l, sep="")]] / (1 - beta2^t)

    # Update parameters.
    d1 = sqrt(s_corrected[[paste("dW", l, sep="")]] + epsilon)
    d2 = sqrt(s_corrected[[paste("db", l, sep="")]] + epsilon)
    parameters[[paste("W", l, sep="")]] = parameters[[paste("W", l, sep="")]] -
      learningRate * v_corrected[[paste("dW", l, sep="")]] / d1
    parameters[[paste("b", l, sep="")]] = parameters[[paste("b", l, sep="")]] -
      learningRate * v_corrected[[paste("db", l, sep="")]] / d2
  }

  # Compute for the Lth layer for sigmoid activation
  if(outputActivationFunc == "sigmoid") {

    v[[paste("dW", L, sep="")]] = beta1 * v[[paste("dW", L, sep="")]] +
      (1 - beta1) * gradients[[paste('dW', L, sep="")]]

    v[[paste("db", L, sep="")]] = beta1 * v[[paste("db", L, sep="")]] +
      (1 - beta1) * gradients[[paste('db', L, sep="")]]

    # Compute bias-corrected first moment estimate.
    v_corrected[[paste("dW", L, sep="")]] = v[[paste("dW", L, sep="")]] / (1 - beta1^t)
    v_corrected[[paste("db", L, sep="")]] = v[[paste("db", L, sep="")]] / (1 - beta1^t)

    # Element wise multiply of gradients
    s[[paste("dW", L, sep="")]] = beta2 * s[[paste("dW", L, sep="")]] +
      (1 - beta2) * gradients[[paste('dW', L, sep="")]] *
      gradients[[paste('dW', L, sep="")]]

    s[[paste("db", L, sep="")]] = beta2 * s[[paste("db", L, sep="")]] +
      (1 - beta2) * gradients[[paste('db', L, sep="")]] *
      gradients[[paste('db', L, sep="")]]

    # Compute bias-corrected second moment estimate.
    s_corrected[[paste("dW", L, sep="")]] = s[[paste("dW", L, sep="")]] / (1 - beta2^t)
    s_corrected[[paste("db", L, sep="")]] = s[[paste("db", L, sep="")]] / (1 - beta2^t)

    # Update parameters.
    d1 = sqrt(s_corrected[[paste("dW", L, sep="")]] + epsilon)
    d2 = sqrt(s_corrected[[paste("db", L, sep="")]] + epsilon)
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] -
      learningRate * v_corrected[[paste("dW", L, sep="")]] / d1
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] -
      learningRate * v_corrected[[paste("db", L, sep="")]] / d2

  } else if (outputActivationFunc == "softmax") { # Compute for the Lth layer for softmax activation

    v[[paste("dW", L, sep="")]] = beta1 * v[[paste("dW", L, sep="")]] +
      (1 - beta1) * t(gradients[[paste('dW', L, sep="")]])

    v[[paste("db", L, sep="")]] = beta1 * v[[paste("db", L, sep="")]] +
      (1 - beta1) * t(gradients[[paste('db', L, sep="")]])

    # Compute bias-corrected first moment estimate.
    v_corrected[[paste("dW", L, sep="")]] = v[[paste("dW", L, sep="")]] / (1 - beta1^t)
    v_corrected[[paste("db", L, sep="")]] = v[[paste("db", L, sep="")]] / (1 - beta1^t)

    # Element wise multiply of gradients
    s[[paste("dW", L, sep="")]] = beta2 * s[[paste("dW", L, sep="")]] +
      (1 - beta2) * t(gradients[[paste('dW', L, sep="")]]) *
      t(gradients[[paste('dW', L, sep="")]])

    s[[paste("db", L, sep="")]] = beta2 * s[[paste("db", L, sep="")]] +
      (1 - beta2) * t(gradients[[paste('db', L, sep="")]]) *
      t(gradients[[paste('db', L, sep="")]])

    # Compute bias-corrected second moment estimate.
    s_corrected[[paste("dW", L, sep="")]] = s[[paste("dW", L, sep="")]] / (1 - beta2^t)
    s_corrected[[paste("db", L, sep="")]] = s[[paste("db", L, sep="")]] / (1 - beta2^t)

    # Update parameters.
    d1 = sqrt(s_corrected[[paste("dW", L, sep="")]] + epsilon)
    d2 = sqrt(s_corrected[[paste("db", L, sep="")]] + epsilon)
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] -
      learningRate * v_corrected[[paste("dW", L, sep="")]] / d1
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] -
      learningRate * v_corrected[[paste("db", L, sep="")]] / d2
  }

  return(parameters)
}
```

## 5.1a. Stochastic Gradient Descent with Adam – Python

```python
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
import sklearn.linear_model
import pandas as pd
import sklearn
import sklearn.datasets

exec(open("DLfunctions7.py").read())

# Load MNIST
exec(open("load_mnist.py").read())

training = list(read(dataset='training', path=".\\mnist"))
test = list(read(dataset='testing', path=".\\mnist"))

lbls = []
pxls = []

print(len(training))

# for i in range(len(training)):
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

# Subset 1024 from the data
![Image 365](index-306_1.jpg)

X2 = X1[:, permutation]
Y2 = Y1[:, permutation].reshape((1, 2**10))

# Set layer dimensions
# 784 – number of input features (28 x28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions = [784, 15, 9, 10]

# Execute a L-layer Deep Learning network using SGD with Adam optimization
# hidden Activation function – relu
# output activation function – softmax
# learning rate – 0.01
# optimizer="adam"
# beta1 = 0.9
# beta2 = 0.9
# epsilon = 1e-8
# mini_batch_size = 512

parameters = L_Layer_DeepModel_SGD(X2, Y2, layersDimensions,
                                   hiddenActivationFunc='relu',
                                   outputActivationFunc="softmax",
                                   learningRate=0.01,
                                   optimizer="adam",
                                   beta1=0.9,
                                   beta2=0.9,
                                   epsilon=1e-8,
                                   mini_batch_size=512,
                                   num_epochs=1000,
                                   print_cost=True,
                                   figure="fig5.png")
```

## 5.1b. Stochastic Gradient Descent with Adam – R

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
permutation = c(sample(2^10))

# Randomly shuffle the training data
X1 = X[, permutation]
y1 = Y[1, permutation]
y2 <- as.matrix(y1)
Y1 = t(y2)

# Set layer dimensions
# 784 – number of input features (28 x28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions = c(784, 15, 9, 10)

# Execute a L-layer Deep Learning network using SGD with Adam optimization
```
