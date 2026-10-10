
# Initialize costs vector as NULL

```r
costs <- NULL
```

# Parameters initialization.

```r
parameters = initializeDeepModel(layersDimensions)
```

# Loop (gradient descent)

```r
for( i in 0:numIterations){

  # Forward propagation: [LINEAR -> RELU]*(L-1) -> LINEAR -> SIGMOID/SOFTMAX.
  retvals = forwardPropagationDeep(X, parameters, hiddenActivationFunc, outputActivationFunc=outputActivationFunc)
  AL <- retvals[['AL']]
  caches <- retvals[['caches']]

  # Compute cost.
  cost <- computeCost(AL, Y, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions[3])

  # Backward propagation.
  gradients = backwardPropagationDeep(AL, Y, caches, hiddenActivationFunc, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions[3])

  # Update parameters.
  parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)

  if(i %% 1000 == 0){
    costs = c(costs, cost)
    print(cost)
  }
}

retvals <- list("parameters"=parameters, "costs"=costs)
return(retvals)
```

# Execute a L layer Deep learning model with Stochastic Gradient descent

**Input:**
- `X` - Input features
- `Y` - output
- `layersDimensions` - Dimension of layers
- `hiddenActivationFunc` - Activation function at hidden layer relu/tanh/sigmoid
- `outputActivationFunc` - Activation function at hidden layer sigmoid/softmax
- `learning rate`
- `mini_batch_size`
- `num of epochs`

**Output:** Updated weights after each iteration

```r
L_Layer_DeepModel_SGD <- function(X, Y, layersDimensions,
                                  hiddenActivationFunc='relu',
                                  outputActivationFunc= 'sigmoid',
                                  learningRate = .3,
                                  mini_batch_size = 64,
                                  num_epochs = 2500,
                                  print_cost=FALSE){

  set.seed(1)
  # Initialize costs vector as NULL
  costs <- NULL

  # Parameters initialization.
  parameters = initializeDeepModel(layersDimensions)

  seed = 10

  # Loop for number of epochs
  for( i in 0:num_epochs){
    seed = seed + 1
    minibatches = random_mini_batches(X, Y, mini_batch_size, seed)

    for(batch in 1:length(minibatches)){
      mini_batch_X = minibatches[[batch]][['mini_batch_X']]
      mini_batch_Y = minibatches[[batch]][['mini_batch_Y']]

      # Forward propagation:
      retvals = forwardPropagationDeep(mini_batch_X, parameters, hiddenActivationFunc, outputActivationFunc=outputActivationFunc)
      AL <- retvals[['AL']]
      caches <- retvals[['caches']]

      # Compute cost.
      cost <- computeCost(AL, mini_batch_Y, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions[length(layersDimensions)])

      # Backward propagation.
      gradients = backwardPropagationDeep(AL, mini_batch_Y, caches, hiddenActivationFunc, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions[length(layersDimensions)])

      # Update parameters.
      parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)
    }

    if(i %% 100 == 0){
      costs = c(costs, cost)
      print(cost)
    }
  }

  retvals <- list("parameters"=parameters, "costs"=costs)
  return(retvals)
}
```

# Predict the output for given input

**Input:**
- `parameters`
- `X`
- `hiddenActivationFunc`

**Output:** predictions

```r
predict <- function(parameters, X, hiddenActivationFunc='relu'){
  fwdProp <- forwardPropagationDeep(X, parameters, hiddenActivationFunc)
  predictions <- fwdProp$AL > 0.5
  return (predictions)
}
```

# Predict the output

```r
predictProba <- function(parameters, X, hiddenActivationFunc, outputActivationFunc){
  retvals = forwardPropagationDeep(X, parameters, hiddenActivationFunc, outputActivationFunc="softmax")
  if(outputActivationFunc =="sigmoid")
    predictions <- retvals$AL > 0.5
  else if (outputActivationFunc =="softmax")
    predictions <- apply(retvals$AL, 1, which.max) - 1
  return (predictions)
}
```

# Plot a decision boundary

**Note:** This function uses `ggplot2`.

```r
plotDecisionBoundary <- function(z, retvals, hiddenActivationFunc, lr){
  # Find the minimum and maximum for the data
  xmin <- min(z[,1])
  xmax <- max(z[,1])
  ymin <- min(z[,2])
  ymax <- max(z[,2])

  # Create a grid of values
  a = seq(xmin, xmax, length=100)
  b = seq(ymin, ymax, length=100)
  grid <- expand.grid(x=a, y=b)
  colnames(grid) <- c('x1', 'x2')
  grid1 <- t(grid)

  # Predict the output for this grid
  q <- predict(retvals$parameters, grid1, hiddenActivationFunc)
  q1 <- t(data.frame(q))
  q2 <- as.numeric(q1)
  grid2 <- cbind(grid, q2)
  colnames(grid2) <- c('x1', 'x2', 'q2')

  z1 <- data.frame(z)
  names(z1) <- c("x1", "x2", "y")
  atitle = paste("Decision boundary for learning rate:", lr)

  # Plot the contour of the boundary
  ggplot(z1) +
    geom_point(data = z1, aes(x = x1, y = x2, color = y)) +
    stat_contour(data = grid2, aes(x = x1, y = x2, z = q2, color=q2), alpha = 0.9) +
    ggtitle(atitle)
}
```

# Predict the probability scores for given data set

**Input:**
- `parameters`
- `X`

**Output:** probability of output

```r
computeScores <- function(parameters, X, hiddenActivationFunc='relu'){
  fwdProp <- forwardPropagationDeep(X, parameters, hiddenActivationFunc)
  scores <- fwdProp$AL
  return (scores)
}
```

# Create random mini batches

**Input:**
- `X` - Input features
- `Y` - output
- `miniBatchSize`
- `seed`

**Output:** `mini_batches`

```r
random_mini_batches <- function(X, Y, miniBatchSize = 64, seed = 0){
  set.seed(seed)

  # Get number of training samples
  m = dim(X)[2]

  # Initialize mini batches
  mini_batches = list()

  # Create a list of random numbers < m
  permutation = c(sample(m))

  # Randomly shuffle the training data
  shuffled_X = X[, permutation]
  shuffled_Y = Y[1, permutation]

  # Compute number of mini batches
  numCompleteMinibatches = floor(m / miniBatchSize)

  batch = 0
  for(k in 0:(numCompleteMinibatches-1)){
    batch = batch + 1

    # Set the lower and upper bound of the mini batches
    lower = (k * miniBatchSize) + 1
    upper = ((k + 1) * miniBatchSize)

    mini_batch_X = shuffled_X[, lower:upper]
    mini_batch_Y = shuffled_Y[lower:upper]

    # Add it to the list of mini batches
    mini_batch = list("mini_batch_X"=mini_batch_X, "mini_batch_Y"=mini_batch_Y)
    mini_batches[[batch]] = mini_batch
  }

  # If the batch size does not divide evenly with mini batch size
  if(m %% miniBatchSize != 0){
    p = floor(m / miniBatchSize) * miniBatchSize

    # Set the start and end of last batch
    q = p + m %% miniBatchSize

    mini_batch_X = shuffled_X[, (p+1):q]
    mini_batch_Y = shuffled_Y[(p+1):q]

    mini_batch = list("mini_batch_X"=mini_batch_X, "mini_batch_Y"=mini_batch_Y)
    mini_batches[[batch]] = mini_batch
  }

  # Return the list of mini batches
  return(mini_batches)
}
```

# 5.3 Octave

```matlab
############################################################################################################
#
# File: DLfunctions5.m
# Developer: Tinniam V Ganesh
# Date : 23 Mar 2018
#
##########################################################################################################

1;

# Define sigmoid function
function [A, cache] = sigmoid(Z)
  A = 1 ./ (1 + exp(-Z));
  cache = Z;
end

# Define Relu function
function [A, cache] = relu(Z)
  A = max(0, Z);
  cache = Z;
end

# Define Tanh function
function [A, cache] = tanhAct(Z)
  A = tanh(Z);
  cache = Z;
end

# Define Softmax function
function [A, cache] = softmax(Z)
  # get unnormalized probabilities
  exp_scores = exp(Z');

  # normalize them for each example
  A = exp_scores ./ sum(exp_scores, 2);
  cache = Z;
end

# Define Stable Softmax function
function [A, cache] = stableSoftmax(Z)
  # Normalize by max value in each row
  shiftZ = Z' - max(Z', [], 2);
  exp_scores = exp(shiftZ);

  # normalize them for each example
  A = exp_scores ./ sum(exp_scores, 2);
  # disp("sm")
  # disp(A);
  cache = Z;
end

# Define Relu Derivative
function [dZ] = reluDerivative(dA, cache)
  Z = cache;
  dZ = dA;

  # Get elements that are greater than 0
  a = (Z > 0);

  # Select only those elements where Z > 0
  dZ = dZ .* a;
end

# Define Sigmoid Derivative
function [dZ] = sigmoidDerivative(dA, cache)
  Z = cache;
  s = 1 ./ (1 + exp(-Z));
  dZ = dA .* s .* (1 - s);
end

# Define Tanh Derivative
function [dZ] = tanhDerivative(dA, cache)
  Z = cache;
  a = tanh(Z);
end
```
