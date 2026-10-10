
# 3) Hidden layer

Having computed the gradients, we now perform gradient descent by computing a new weight, assuming a learning rate. If we do this for the output layer, we would get the updated weights.

We now compute how the total error changes for a change in weight $w_{ij}$ – (C)

Using the chain rule, we get – (D)

Considering the 1st term in (C):

Now we have – (E) and – (F), which gives the following:

Combining (D), (E) & (F) we get:

This can be represented as:

With this derivative, a new value of $w_{ij}$ is computed.

Hence there are 2 important results:
- **At the output layer we have:** $\frac{\partial E}{\partial w_{ij}} = \delta_j \cdot o_i$
- **At each hidden layer we compute:** $\frac{\partial E}{\partial w_{ij}} = \delta_j \cdot o_i$ (where $\delta$ is backpropagated)

Backpropagation was very successful in the early years, but the algorithm does have its problems, for e.g., the issue of the ‘vanishing’ and ‘exploding’ gradient. Yet it is a key development in Neural Networks, and the issues with the backprop gradients have been addressed through techniques such as the momentum method and adaptive learning rate etc.

In this post, I derive the weights at the output layer and the hidden layer. As I already mentioned above, I intend to implement a vector version of the backpropagation algorithm in Octave, R, and Python in the days to come.

---

## 2. Appendix 1 – Logistic Regression as a Neural Network

### 1.1 Python functions

```python
##############################################################################################
#
# Created by: Tinniam V Ganesh
# Date : 4 Jan 2018
# File: DLfunctions1.py
#
##############################################################################################

import numpy as np
import pandas as pd
import os
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split

# Define the sigmoid function
def sigmoid(z):
    a = 1 / (1 + np.exp(-z))
    return a

# Initialize weights and biases
def initialize(dim):
    w = np.zeros(dim).reshape(dim, 1)
    b = 0
    return w

# Compute the loss
# Inputs: numTraining, Y, A
# Outputs: loss
def computeLoss(numTraining, Y, A):
    loss = -1/numTraining * np.sum(Y * np.log(A) + (1-Y) * (np.log(1-A)))
    return loss

# Execute the forward propagation
# Inputs: w, b, X, Y
# Outputs: gradients, loss (dict)
def forwardPropagation(w, b, X, Y):
    # Compute Z
    Z = np.dot(w.T, X) + b

    # Determine the number of training samples
    numTraining = float(len(X))

    # Compute the output of the sigmoid activation function
    A = sigmoid(Z)

    # Compute the loss
    loss = computeLoss(numTraining, Y, A)

    # Compute the gradients dZ, dw and db
    dZ = A - Y
    dw = 1/numTraining * np.dot(X, dZ.T)
    db = 1/numTraining * np.sum(dZ)

    # Return the results as a dictionary
    gradients = {"dw": dw, "db": db}
    loss = np.squeeze(loss)
    return gradients, loss

# Compute Gradient Descent
# Inputs: w, b, X, Y, numIterations, learningRate
# Outputs: params, grads, losses, idx
def gradientDescent(w, b, X, Y, numIterations, learningRate):
    losses = []
    idx = []

    # Iterate
    for i in range(numIterations):
        gradients, loss = forwardPropagation(w, b, X, Y)

        # Get the derivatives
        dw = gradients["dw"]
        db = gradients["db"]

        w = w - learningRate * dw
        b = b - learningRate * db

        # Store the loss
        if i % 100 == 0:
            idx.append(i)
            losses.append(loss)

    # Set params and grads
    params = {"w": w, "b": b}
    grads = {"dw": dw, "db": db}
    return params, grads, losses, idx

# Predict the output for a training set
# Inputs: w, b, X
# Outputs: yPredicted
def predict(w, b, X):
    size = X.shape[1]
    yPredicted = np.zeros((1, size))
    Z = np.dot(w.T, X)

    # Compute the sigmoid
    A = sigmoid(Z)

    for i in range(A.shape[1]):
        # If the value is > 0.5 then set as 1
        if A[0][i] > 0.5:
            yPredicted[0][i] = 1
        else:
            # Else set as 0
            yPredicted[0][i] = 0
    return yPredicted

# Normalize the data
# Inputs: x
# Outputs: x (normalized)
def normalize(x):
    x_norm = None
    x_norm = np.linalg.norm(x, axis=1, keepdims=True)
    x = x / x_norm
    return x
```

### 1.2 R

```r
##################################################################################
#
# Created by: Tinniam V Ganesh
# Date : 4 Jan 2018
# File: DLfunctions1.R
#
##################################################################################

source("RFunctions-1.R")

# Define the sigmoid function
sigmoid <- function(z) {
  a <- 1 / (1 + exp(-z))
  a
}

# Compute the loss
# Inputs: numTraining, Y, A
# Outputs: loss
computeLoss <- function(numTraining, Y, A) {
  loss <- -1/numTraining * sum(Y * log(A) + (1-Y) * log(1-A))
  return(loss)
}

# Compute forward propagation
# Inputs: w, b, X, Y
# Outputs: fwdProp (list)
forwardPropagation <- function(w, b, X, Y) {
  # Compute Z
  Z <- t(w) %*% X + b

  # Set the number of samples
  numTraining <- ncol(X)

  # Compute the activation function
  A <- sigmoid(Z)

  # Compute the loss
  loss <- computeLoss(numTraining, Y, A)

  # Compute the gradients dZ, dw and db
  dZ <- A - Y
  dw <- 1/numTraining * X %*% t(dZ)
  db <- 1/numTraining * sum(dZ)

  fwdProp <- list("loss" = loss, "dw" = dw, "db" = db)
  return(fwdProp)
}

# Perform one cycle of Gradient descent
# Compute Gradient Descent
# Inputs: w, b, X, Y, numIterations, learningRate
# Outputs: gradDescnt (list)
gradientDescent <- function(w, b, X, Y, numIterations, learningRate) {
  losses <- NULL
  idx <- NULL

  # Loop through the number of iterations
  for(i in 1:numIterations) {
    fwdProp <- forwardPropagation(w, b, X, Y)

    # Get the derivatives
    dw <- fwdProp$dw
    db <- fwdProp$db

    # Perform gradient descent
    w <- w - learningRate * dw
    b <- b - learningRate * db

    l <- fwdProp$loss

    # Store the loss
    if(i %% 100 == 0) {
      idx <- c(idx, i)
      losses <- c(losses, l)
    }
  }

  # Return the weights and losses
  gradDescnt <- list("w" = w, "b" = b, "dw" = dw, "db" = db, "losses" = losses, "idx" = idx)
  return(gradDescnt)
}

# Compute the predicted value for input
# Predict the output for a training set
# Inputs: w, b, X
# Outputs: yPredicted
predict <- function(w, b, X) {
  m <- dim(X)[2]

  # Create a vector of 0's
  yPredicted <- matrix(rep(0, m), nrow = 1, ncol = m)

  Z <- t(w) %*% X + b

  # Compute sigmoid
  A <- sigmoid(Z)

  for(i in 1:dim(A)[2]) {
    # If A > 0.5 set value as 1
    if(A[1, i] > 0.5)
      yPredicted[1, i] <- 1
    else
      # Else set as 0
      yPredicted[1, i] <- 0
  }
  return(yPredicted)
}

# Normalize the matrix
# Inputs: x
# Outputs: normalized
normalize <- function(x) {
  # Create the norm of the matrix. Perform the Frobenius norm of the matrix
  n <- as.matrix(sqrt(rowSums(x^2)))

  # Sweep by rows by norm. Note '1' in the function which performing on every row
  normalized <- sweep(x, 1, n, FUN = "/")
  return(normalized)
}
```

### 1.3 Octave

```octave
##############################################################################################
#
# Created by: Tinniam V Ganesh
# Date : 4 Jan 2018
# File: DLfunctions.m
#
##############################################################################################

1;

# Define sigmoid function
function a = sigmoid(z)
  a = 1 ./ (1 + exp(-z));
end

# Compute the loss
# Inputs: numTraining, Y, A
# Outputs: loss
function loss = computeLoss(numtraining, Y, A)
  loss = -1/numtraining * sum((Y .* log(A)) + (1-Y) .* log(1-A));
end

# Perform forward propagation
# Inputs: w, b, X, Y
# Outputs: loss, dw, db, dZ
function [loss, dw, db, dZ] = forwardPropagation(w, b, X, Y)
  % Compute Z
  Z = w' * X + b;
end
```
