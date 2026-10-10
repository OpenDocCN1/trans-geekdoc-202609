
# Gradient Check Implementation

## 1.2a Gradient Check – Sigmoid Activation – Python

```python
for j in range(K):
    ix = range(N*j, N*(j+1))
    r = np.linspace(0.0, 1, N)  # radius
    t = np.linspace(j*4, (j+1)*4, N) + np.random.randn(N)*0.2  # theta
    X[ix] = np.c_[r*np.sin(t), r*np.cos(t)]
    y[ix] = j

# Plot the data
# plt.scatter(X[:, 0], X[:, 1], c=y, s=40, cmap=plt.cm.Spectral)

# Set layer dimensions
# 2 – number of input features
# 3 – 1 hidden layer with 3 activation units
# 3 – 3 classes with softmax activation unit at the output layer
layersDimensions = [2, 3, 3]

y1 = y.reshape(-1, 1).T
train_X = X.T
train_Y = y1

# Initialize model
parameters = initializeDeepModel(layersDimensions)

# Perform forward prop
AL, caches, dropoutMat = forwardPropagationDeep(train_X, parameters,
                                                keep_prob=1,
                                                hiddenActivationFunc="relu",
                                                outputActivationFunc="softmax")

# Compute cost
cost = computeCost(AL, train_Y, outputActivationFunc="softmax")
print("cost=", cost)

# Compute gradients from backprop
gradients = backwardPropagationDeep(AL, train_Y, caches, dropoutMat, lambd=0, keep_prob=1,
                                    hiddenActivationFunc="relu", outputActivationFunc="softmax")

# Note the transpose of the gradients for Softmax has to be taken
L = len(parameters)//2
print(L)

gradients['dW'+str(L)] = gradients['dW'+str(L)].T
gradients['db'+str(L)] = gradients['db'+str(L)].T

# Perform gradient check
gradient_check_n(parameters, gradients, train_X, train_Y, epsilon=1e-7, outputActivationFunc="softmax")
```

## Output

```text
## cost= 1.0986193170234435
## 2
## [92mYour backward propagation works perfectly fine! difference = 5.268804859613151e-07[0m
## 5.268804859613151e-07
```

## Gradients from backprop

```text
## {'dW1': array([[ 0.00053206,  0.00038987],
##        [ 0.00093941,  0.00038077],
##        [-0.00012177, -0.0004692 ]]),
##  'db1': array([[ 0.00072662],
##        [-0.00210198],
##        [ 0.00046741]]),
##  'dW2': array([[-7.83441270e-05, -9.70179498e-04, -1.08715815e-04],
##        [-7.70175008e-04,  9.54478237e-04,  2.27690198e-04],
##        [ 8.48519135e-04,  1.57012608e-05, -1.18974383e-04]]),
##  'db2': array([[-8.52190476e-06],
##        [-1.69954294e-05],
##        [ 2.55173342e-05]])}
```

## Gradapprox from gradient check

```text
## {'dW1': array([[ 0.00053206,  0.00038987],
##        [ 0.00093941,  0.00038077],
##        [-0.00012177, -0.0004692 ]]),
##  'db1': array([[ 0.00072662],
##        [-0.00210198],
##        [ 0.00046741]]),
##  'dW2': array([[-7.83439980e-05, -9.70180603e-04, -1.08716369e-04],
##        [-7.70173925e-04,  9.54478718e-04,  2.27690089e-04],
##        [ 8.48520143e-04,  1.57018842e-05, -1.18973720e-04]]),
##  'db2': array([[-8.52096171e-06],
##        [-1.69964043e-05],
##        [ 2.55162558e-05]])}
```

## 1.2a Gradient Check – Sigmoid Activation – R

```r
source("DLfunctions8.R")

z <- as.matrix(read.csv("circles.csv", header=FALSE))
x <- z[, 1:2]
y <- z[, 3]

X <- t(x)
Y <- t(y)

# Set layer dimensions
layersDimensions = c(2, 5, 1)

# Initialize model
parameters = initializeDeepModel(layersDimensions)

# Perform forward prop
retvals = forwardPropagationDeep(X, parameters, keep_prob=1,
                                 hiddenActivationFunc="relu",
                                 outputActivationFunc="sigmoid")

AL <- retvals[['AL']]
caches <- retvals[['caches']]
dropoutMat <- retvals[['dropoutMat']]

# Compute cost
cost <- computeCost(AL, Y, outputActivationFunc="sigmoid", numClasses=layersDimensions[length(layersDimensions)])
print(cost)

## [1] 0.6931447

# Perform backward propagation and get gradients
gradients = backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd=0, keep_prob=1,
                                    hiddenActivationFunc="relu",
                                    outputActivationFunc="sigmoid",
                                    numClasses=layersDimensions[length(layersDimensions)])

# Set values
epsilon = 1e-07
outputActivationFunc = "sigmoid"

# Convert parameter list to vector
parameters_values = list_to_vector(parameters)

# Convert gradient list to vector
grad = gradients_to_vector(parameters, gradients)

num_parameters = dim(parameters_values)[1]

# Initialize J_plus, J_minus and gradapprox
J_plus = matrix(rep(0, num_parameters), nrow=num_parameters, ncol=1)
J_minus = matrix(rep(0, num_parameters), nrow=num_parameters, ncol=1)
gradapprox = matrix(rep(0, num_parameters), nrow=num_parameters, ncol=1)

# Compute J_plus, J_minus and gradapprox
for(i in 1:num_parameters) {
    # Compute J_plus[i]
    thetaplus = parameters_values
    thetaplus[i][1] = thetaplus[i][1] + epsilon
    
    retvals = forwardPropagationDeep(X, vector_to_list(parameters, thetaplus), keep_prob=1,
                                     hiddenActivationFunc="relu", outputActivationFunc=outputActivationFunc)
    AL <- retvals[['AL']]
    J_plus[i] = computeCost(AL, Y, outputActivationFunc=outputActivationFunc)
    
    # Compute J_minus[i]
    thetaminus = parameters_values
    thetaminus[i][1] = thetaminus[i][1] - epsilon
    
    retvals = forwardPropagationDeep(X, vector_to_list(parameters, thetaminus), keep_prob=1,
                                     hiddenActivationFunc="relu", outputActivationFunc=outputActivationFunc)
    AL <- retvals[['AL']]
    J_minus[i] = computeCost(AL, Y, outputActivationFunc=outputActivationFunc)
    
    # Compute gradapprox[i]
    gradapprox[i] = (J_plus[i] - J_minus[i]) / (2 * epsilon)
}

# Compare gradapprox to backprop gradients by computing Euclidean difference
# Compute L2Norm
numerator = L2NormVec(grad - gradapprox)
denominator = L2NormVec(grad) + L2NormVec(gradapprox)
difference = numerator / denominator

# Output difference
if(difference > 1e-5) {
    cat("There is a mistake, the difference is too high", difference)
} else {
    cat("The implementations works perfectly", difference)
}

## The implementations works perfectly 1.279911e-06

# Technique to check gradients
print("Gradients from backprop")

## [1] "Gradients from backprop"

vector_to_list2(parameters, grad)

## $dW1
##       [,1]        [,2]
## [1,] -7.641588e-05 -3.427989e-07
## [2,] -9.049683e-06  6.906304e-05
## [3,]  3.401039e-06 -1.503914e-04
## [4,]  1.535226e-04 -1.686402e-04
## [5,] -6.029292e-05 -2.715648e-04
##
## $db1
##       [,1]
## [1,]  6.930318e-06
## [2,] -3.283117e-05
## [3,]  1.310647e-05
## [4,] -3.454308e-05
## [5,] -2.331729e-08
##
## $dW2
##       [,1]       [,2]       [,3]       [,4]       [,5]
## [1,] 0.0001612356 0.0001113475 0.0002435824 0.000362149 2.874116e-05
##
## $db2
##       [,1]
## [1,] -1.16364e-05

print("Grad approx from gradient check")

## [1] "Grad approx from gradient check"

vector_to_list2(parameters, gradapprox)

## $dW1
##       [,1]        [,2]
## [1,] -7.641554e-05 -3.430589e-07
## [2,] -9.049428e-06  6.906253e-05
## [3,]  3.401168e-06 -1.503919e-04
## [4,]  1.535228e-04 -1.686401e-04
## [5,] -6.029288e-05 -2.715650e-04
##
## $db1
##       [,1]
## [1,]  6.930012e-06
## [2,] -3.283096e-05
## [3,]  1.310618e-05
## [4,] -3.454237e-05
## [5,] -2.275957e-08
##
## $dW2
##       [,1]       [,2]       [,3]       [,4]       [,5]
## [1,] 0.0001612355 0.0001113476 0.0002435829 0.0003621486 2.87409e-05
##
## $db2
##       [,1]
## [1,] -1.16368e-05
```

## 1.2b Gradient Check – Softmax Activation – R

```r
source("DLfunctions8.R")

Z <- as.matrix(read.csv("spiral.csv", header=FALSE))

# Setup the data
X <- Z[, 1:2]
y <- Z[, 3]

X <- t(X)
Y <- t(y)

# Set layer dimensions
# 2 – number of input features
# 3 – 1 hidden layer with 3 activation units
# 3 – 3 classes with softmax activation unit at the output layer
layersDimensions = c(2, 3, 3)

# Initialize model
parameters = initializeDeepModel(layersDimensions)

# Perform forward propagation
retvals = forwardPropagationDeep(X, parameters, keep_prob=1,
                                 hiddenActivationFunc="relu",
                                 outputActivationFunc="softmax")

AL <- retvals[['AL']]
caches <- retvals[['caches']]
dropoutMat <- retvals[['dropoutMat']]

# Compute cost
cost <- computeCost(AL, Y, outputActivationFunc="softmax", numClasses=layersDimensions[length(layersDimensions)])
print(cost)

## [1] 1.098618

# Perform Backward propagation.
gradients = backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd=0, keep_prob=1,
                                    hiddenActivationFunc="relu",
                                    outputActivationFunc="softmax")
```
