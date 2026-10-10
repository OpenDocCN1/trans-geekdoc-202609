
# Outputs

`gradients["dA" + str(l + 1)]`, `gradients["dW" + str(l + 1)]`, `gradients["db" + str(l + 1)]`

```r
current_cache = caches[[l]]$cache

if (lambd == 0) {
  cat("l=", l)
  # Get the dropout matrix
  D <- dropoutMat[[paste("D", l, sep="")]]
  # Multiply gradient with dropout matrix
  gradients[[paste('dA', l+1, sep="")]] = gradients[[paste('dA', l+1, sep="")]] * D
  # Divide by keep_prob to keep expected value same
  gradients[[paste('dA', l+1, sep="")]] = gradients[[paste('dA', l+1, sep="")]] / keep_prob
  retvals = layerActivationBackward(gradients[[paste('dA', l+1, sep="")]], current_cache, Y,
                                    activationFunc = hiddenActivationFunc)
} else {
  retvals = layerActivationBackwardWithReg(gradients[[paste('dA', l+1, sep="")]], current_cache, Y, lambd,
                                           activationFunc = hiddenActivationFunc)
}

gradients[[paste("dA", l, sep="")]] <- retvals[['dA_prev']]
gradients[[paste("dW", l, sep="")]] <- retvals[['dW']]
gradients[[paste("db", l, sep="")]] <- retvals[['db']]
}

return(gradients)
}
```

# Perform Gradient Descent

**Input**: Weights and biases, gradients, learning rate, `outputActivationFunc` - Activation function at hidden layer sigmoid/softmax

**Output**: Updated weights after 1 iteration

```r
gradientDescent <- function(parameters, gradients, learningRate, outputActivationFunc="sigmoid") {
  L = length(parameters)/2 # number of layers in the neural network
  # Update rule for each parameter. Use a for loop.
  for(l in 1:(L-1)) {
    parameters[[paste("W", l, sep="")]] = parameters[[paste("W", l, sep="")]] - learningRate * gradients[[paste("dW", l, sep="")]]
    parameters[[paste("b", l, sep="")]] = parameters[[paste("b", l, sep="")]] - learningRate * gradients[[paste("db", l, sep="")]]
  }
  if(outputActivationFunc == "sigmoid") {
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * gradients[[paste("dW", L, sep="")]]
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * gradients[[paste("db", L, sep="")]]
  } else if (outputActivationFunc == "softmax") {
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * t(gradients[[paste("dW", L, sep="")]])
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * t(gradients[[paste("db", L, sep="")]])
  }
  return(parameters)
}
```

# Perform Gradient Descent with Momentum

**Input**: Weights and biases, `beta`, gradients, learning rate, `outputActivationFunc` - Activation function at hidden layer sigmoid/softmax

**Output**: Updated weights after 1 iteration

```r
gradientDescentWithMomentum <- function(parameters, gradients, v, beta, learningRate, outputActivationFunc="sigmoid") {
  L = length(parameters)/2 # number of layers in the neural network
  # Update rule for each parameter. Use a for loop.
  for(l in 1:(L-1)) {
    # Compute velocities
    # v[['dWk']] = beta * v[['dWk']] + (1-beta) * dWk
    v[[paste("dW", l, sep="")]] = beta * v[[paste("dW", l, sep="")]] + (1-beta) * gradients[[paste('dW', l, sep="")]]
    v[[paste("db", l, sep="")]] = beta * v[[paste("db", l, sep="")]] + (1-beta) * gradients[[paste('db', l, sep="")]]
    parameters[[paste("W", l, sep="")]] = parameters[[paste("W", l, sep="")]] - learningRate * v[[paste("dW", l, sep="")]]
    parameters[[paste("b", l, sep="")]] = parameters[[paste("b", l, sep="")]] - learningRate * v[[paste("db", l, sep="")]]
  }
  # Compute for the Lth layer
  if(outputActivationFunc == "sigmoid") {
    v[[paste("dW", L, sep="")]] = beta * v[[paste("dW", L, sep="")]] + (1-beta) * gradients[[paste('dW', L, sep="")]]
    v[[paste("db", L, sep="")]] = beta * v[[paste("db", L, sep="")]] + (1-beta) * gradients[[paste('db', L, sep="")]]
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * v[[paste("dW", l, sep="")]]
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * v[[paste("db", l, sep="")]]
  } else if (outputActivationFunc == "softmax") {
    v[[paste("dW", L, sep="")]] = beta * v[[paste("dW", L, sep="")]] + (1-beta) * t(gradients[[paste('dW', L, sep="")]])
    v[[paste("db", L, sep="")]] = beta * v[[paste("db", L, sep="")]] + (1-beta) * t(gradients[[paste('db', L, sep="")]])
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * t(gradients[[paste("dW", L, sep="")]])
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * t(gradients[[paste("db", L, sep="")]])
  }
  return(parameters)
}
```

# Perform Gradient Descent with RMSProp

**Input**: `parameters`, `gradients`, `s`, `beta1`, `epsilon`, learning rate, `outputActivationFunc` - Activation function at hidden layer sigmoid/softmax

**Output**: Updated weights after 1 iteration

```r
gradientDescentWithRMSProp <- function(parameters, gradients, s, beta1, epsilon, learningRate, outputActivationFunc="sigmoid") {
  L = length(parameters)/2 # number of layers in the neural network
  # Update rule for each parameter. Use a for loop.
  for(l in 1:(L-1)) {
    # Compute RMSProp
    # s[['dWk']] = beta1 * s[['dWk']] + (1-beta1) * dWk**2 / sqrt(s[['dWk']])
    # Element wise multiply of gradients
    s[[paste("dW", l, sep="")]] = beta1 * s[[paste("dW", l, sep="")]] + (1-beta1) * gradients[[paste('dW', l, sep="")]] * gradients[[paste('dW', l, sep="")]]
    s[[paste("db", l, sep="")]] = beta1 * s[[paste("db", l, sep="")]] + (1-beta1) * gradients[[paste('db', l, sep="")]] * gradients[[paste('db', l, sep="")]]
    parameters[[paste("W", l, sep="")]] = parameters[[paste("W", l, sep="")]] - learningRate * gradients[[paste('dW', l, sep="")]] / sqrt(s[[paste("dW", l, sep="")]] + epsilon)
    parameters[[paste("b", l, sep="")]] = parameters[[paste("b", l, sep="")]] - learningRate * gradients[[paste('db', l, sep="")]] / sqrt(s[[paste("db", l, sep="")]] + epsilon)
  }
  # Compute for the Lth layer
  if(outputActivationFunc == "sigmoid") {
    s[[paste("dW", L, sep="")]] = beta1 * s[[paste("dW", L, sep="")]] + (1-beta1) * gradients[[paste('dW', L, sep="")]] * gradients[[paste('dW', L, sep="")]]
    s[[paste("db", L, sep="")]] = beta1 * s[[paste("db", L, sep="")]] + (1-beta1) * gradients[[paste('db', L, sep="")]] * gradients[[paste('db', L, sep="")]]
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * gradients[[paste('dW', l, sep="")]] / sqrt(s[[paste("dW", L, sep="")]] + epsilon)
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * gradients[[paste('db', l, sep="")]] / sqrt(s[[paste("db", L, sep="")]] + epsilon)
  } else if (outputActivationFunc == "softmax") {
    s[[paste("dW", L, sep="")]] = beta1 * s[[paste("dW", L, sep="")]] + (1-beta1) * t(gradients[[paste('dW', L, sep="")]]) * t(gradients[[paste('dW', L, sep="")]])
    s[[paste("db", L, sep="")]] = beta1 * s[[paste("db", L, sep="")]] + (1-beta1) * t(gradients[[paste('db', L, sep="")]]) * t(gradients[[paste('db', L, sep="")]])
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * t(gradients[[paste("dW", L, sep="")]]) / sqrt(s[[paste("dW", L, sep="")]] + epsilon)
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * t(gradients[[paste("db", L, sep="")]]) / sqrt(s[[paste("db", L, sep="")]] + epsilon)
  }
  return(parameters)
}
```

# Perform Gradient Descent with Adam

**Input**: `parameters`, `gradients`, `v`, `s`, `t`, `beta1`, `beta2`, `epsilon`, learning rate, `outputActivationFunc` - Activation function at hidden layer sigmoid/softmax

**Output**: Updated weights after 1 iteration

```r
gradientDescentWithAdam <- function(parameters, gradients, v, s, t, beta1=0.9, beta2=0.999, epsilon=10^-8,
```
