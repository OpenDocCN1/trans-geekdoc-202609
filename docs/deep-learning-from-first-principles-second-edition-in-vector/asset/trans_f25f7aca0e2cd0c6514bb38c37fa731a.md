

# Python 实现

```python
y_min, y_max = X[1, :].min() - 1, X[1, :].max() + 1

colors = ['black', 'gold']

cmap = matplotlib.colors.ListedColormap(colors)

h = 0.01

# Generate a grid of points with distance h between them
xx, yy = np.meshgrid(np.arange(x_min, x_max, h), np.arange(y_min, y_max, h))

# Predict the function value for the whole grid
Z = model(np.c_[xx.ravel(), yy.ravel()])

Z = Z.reshape(xx.shape)

# Plot the contour and training examples
plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral)

plt.ylabel('x2')

plt.xlabel('x1')

plt.scatter(X[0, :], X[1, :], c=y, cmap=cmap)

plt.title("Decision Boundary for logistic regression")
plt.savefig(fig, bbox_inches='tight')
```

## `plot_decision_boundary` 函数

```python
# Plot a decision boundary
# Input : Input Model,
# X
# Y
# sz - Num of hidden units
# lr - Learning rate
# Fig to be saved as
# Returns Null
def plot_decision_boundary(model, X, y, sz, lr, fig):

    # Set min and max values and give it some padding
    x_min, x_max = X[0, :].min() - 1, X[0, :].max() + 1
    y_min, y_max = X[1, :].min() - 1, X[1, :].max() + 1

    colors = ['black', 'gold']

    cmap = matplotlib.colors.ListedColormap(colors)

    h = 0.01

    # Generate a grid of points with distance h between them
    xx, yy = np.meshgrid(np.arange(x_min, x_max, h), np.arange(y_min, y_max, h))

    # Predict the function value for the whole grid
    Z = model(np.c_[xx.ravel(), yy.ravel()])

    Z = Z.reshape(xx.shape)

    # Plot the contour and training examples
    plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral)

    plt.ylabel('x2')

    plt.xlabel('x1')

    plt.scatter(X[0, :], X[1, :], c=y, cmap=cmap)

    plt.title("Decision Boundary for hidden layer size:" + sz + " and learning rate:" + lr)

    plt.savefig(fig, bbox_inches='tight')
```

# 2.2 R 实现

```r
##############################################################################################
#
# Created by: Tinniam V Ganesh
# Date : 11 Jan 2018
# File: DLfunctions2_1.R
#
##############################################################################################

library(ggplot2)

# Sigmoid function
sigmoid <- function(z) {
  a <- 1 / (1 + exp(-z))
  a
}

# Compute the model shape given the dataset
# Input : X - features
# Y - output
#
# Returns: no of training samples, no features, no hidden, no output
getModelShape <- function(X, Y) {
  numTraining <- dim(X)[2] # No of training examples
  numFeats <- dim(X)[1]    # No of input features
  numHidden <- 4           # No of units in hidden layer

  # If Y is a row vector set numOutput as 1
  if (is.null(dim(Y)))
    numOutput <- 1 # No of output units
  else
    numOutput <- dim(Y)[1]

  # Create a list of values
  modelParams <- list("numTraining" = numTraining, "numFeats" = numFeats,
                      "numHidden" = numHidden, "numOutput" = numOutput)

  return(modelParams)
}

# Initialize the model
# Input : number of features
# number of hidden units
# number of units in output
# Returns: Weight and bias matrices and vectors
initializeModel <- function(numFeats, numHidden, numOutput) {
  set.seed(2)
  w <- rnorm(numHidden * numFeats) * 0.01
  W1 <- matrix(w, nrow = numHidden, ncol = numFeats) # Multiply by .01
  b1 <- matrix(rep(0, numHidden), nrow = numHidden, ncol = 1)

  w <- rnorm(numOutput * numHidden)
  W2 <- matrix(w, nrow = numOutput, ncol = numHidden)
  b2 <- matrix(rep(0, numOutput), nrow = numOutput, ncol = 1)

  # Create a list of the neural network parameters
  nnParameters <- list('W1' = W1, 'b1' = b1, 'W2' = W2, 'b2' = b2)

  return(nnParameters)
}

# Compute the forward propagation through the neural network
# Input : Features
# Weight and bias matrices and vectors
# Returns : The Activation of 2nd layer
# : Output and activation of layer 1 & 2
forwardPropagation <- function(X, nnParameters) {
  # Get the parameters
  W1 <- nnParameters$W1
  b1 <- nnParameters$b1
  W2 <- nnParameters$W2
  b2 <- nnParameters$b2

  z <- W1 %*% X

  # Broadcast the bias vector for each row. Use 'sweep' The value '1' for MARGIN
  # indicates sweep each row by this value( add a column vector to each row).
  # If we want to sweep by column use '2' for MARGIN. Here a row vector is added to
  # column (broadcasting!)
  Z1 <- sweep(z, 1, b1, '+')

  # Compute the output A1 with the tanh activation function. The tanh activation function
  # performs better than the sigmoid function
  A1 <- tanh(Z1)

  # Compute Z2 of the 2nd layer
  z <- W2 %*% A1

  # Broadcast the bias vector for each row. Use 'sweep'
  Z2 <- sweep(z, 1, b2, '+')

  # Compute the output A1 with the tanh activation function. The tanh activation function
  # performs better than the sigmoid function
  A2 <- sigmoid(Z2)

  cache <- list('Z1' = Z1, 'A1' = A1, 'Z2' = Z2, 'A2' = A2)

  return(list('A2' = A2, 'cache' = cache))
}

# Compute the cost
# Input : Activation of 2nd layer
# : Output from data
# Output: cost
computeCost <- function(A2, Y) {
  m <- length(Y)
  cost <- -1/m * sum(Y * log(A2) + (1 - Y) * log(1 - A2))
  # cost <- -1/m * sum(a + b)
  return(cost)
}

# Compute the backpropagation for 1 cycle
# Input : Neural Network parameters - weights and biases
# # Z and Activations of 2 layers
# # Input features
# # Output values Y
# Returns: Gradients
backPropagation <- function(nnParameters, cache, X, Y) {
  numtraining <- dim(X)[2]

  # Get parameters
  W1 <- nnParameters$W1
  W2 <- nnParameters$W2

  # Get the NN cache
  A1 <- cache$A1
  A2 <- cache$A2

  dZ2 <- A2 - Y
  dW2 <- 1/numtraining * dZ2 %*% t(A1)
  db2 <- 1/numtraining * rowSums(dZ2)

  dZ1 <- t(W2) %*% dZ2 * (1 - A1^2)
  dW1 <- 1/numtraining * dZ1 %*% t(X)
  db1 <- 1/numtraining * rowSums(dZ1)

  gradients <- list("dW1" = dW1, "db1" = db1, "dW2" = dW2, "db2" = db2)
  return(gradients)
}

# Gradient descent
# Perform Gradient Descent
# Input : Weights and biases
# : gradients
# : learning rate
# output : Updated weights after 1 iteration
gradientDescent <- function(nnParameters, gradients, learningRate) {
  W1 <- nnParameters$W1
  b1 <- nnParameters$b1
  W2 <- nnParameters$W2
  b2 <- nnParameters$b2

  dW1 <- gradients$dW1
  db1 <- gradients$db1
  dW2 <- gradients$dW2
  db2 <- gradients$db2

  W1 <- W1 - learningRate * dW1
  b1 <- b1 - learningRate * db1
  W2 <- W2 - learningRate * dW2
  b2 <- b2 - learningRate * db2

  updatedNNParameters <- list("W1" = W1, "b1" = b1, "W2" = W2, "b2" = b2)
  return(updatedNNParameters)
}

# Compute the Neural Network by minimizing the cost
# Input : Input data X,
# Output Y
# No of hidden units in hidden layer
# No of iterations
# Returns Updated weight and bias vectors of the neural network
computeNN <- function(X, Y, numHidden, learningRate, numIterations = 10000) {
  modelParams <- getModelShape(X, Y)
  numFeats <- modelParams$numFeats
  numOutput <- modelParams$numOutput

  costs <- NULL
  nnParameters <- initializeModel(numFeats, numHidden, numOutput)
  W1 <- nnParameters$W1
  b1 <- nnParameters$b1
  W2 <- nnParameters$W2
  b2 <- nnParameters$b2

  # Perform gradient descent
  for (i in 0:numIterations) {
    # Evaluate forward prop to compute activation at output layer
    # print("Here")
    fwdProp <- forwardPropagation(X, nnParameters)

    # Compute cost from Activation at output and Y
    cost <- computeCost(fwdProp$A2, Y)

    # Perform backprop to compute gradients
    gradients <- backPropagation(nnParameters, fwdProp$cache, X, Y)

    # Use gradients to update the weights for each iteration.
    nnParameters <- gradientDescent(nnParameters, gradients, learningRate)

    # Print the cost every 1000 iterations
    if (i %% 1000 == 0) {
      costs <- c(costs, cost)
      print(cost)
    }
  }

  nnVals <- list("nnParameter" = nnParameters, "costs" = costs)
  return(nnVals)
}

# Predict the output
predict <- function(parameters, X) {
  fwdProp <- forwardPropagation(X, parameters)
  predictions <- fwdProp$A2 > 0.5
  return(predictions)
}

# Plot a decision boundary
# This function uses the contour method
drawBoundary <- function(z, nn) {
  # Find the minimum and maximum of the 2 features
  xmin <- min(z[, 1])
  xmax <- max(z[, 1])
  ymin <- min(z[, 2])
  ymax <- max(z[, 2])

  a <- seq(xmin, xmax, length = 100)
  b <- seq(ymin, ymax, length = 100)

  grid <- expand.grid(x = a, y = b)
  grid1 <- t(grid)

  q <- predict(nn$nnParameter, grid1)

  # Works
  contour(a, b, z = matrix(q, nrow = 100), levels = 0.5)
}
```

