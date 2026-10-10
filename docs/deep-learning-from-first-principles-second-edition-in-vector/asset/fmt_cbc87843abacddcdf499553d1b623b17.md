
# Define the random minibatches

We increment the seed to reshuffle differently the dataset after each epoch.

```python
seed = seed + 1
minibatches = random_mini_batches(X1, Y1, mini_batch_size, seed)
batch = 0
```

# Loop through each mini batch

```python
for minibatch in minibatches:
    # print("batch=", batch)
    batch = batch + 1

    # Select a minibatch
    (minibatch_X, minibatch_Y) = minibatch

    # Perform forward propagation
    AL, caches, dropoutMat = forwardPropagationDeep(
        minibatch_X,
        parameters,
        keep_prob,
        hiddenActivationFunc="relu",
        outputActivationFunc=outputActivationFunc
    )

    # Compute cost
    # Regularization parameter is 0
    if lambd == 0:
        # Compute cost
        cost = computeCost(
            parameters,
            AL,
            minibatch_Y,
            outputActivationFunc=outputActivationFunc
        )
    else:  # Include L2 regularization
        # Compute cost
        cost = computeCostWithReg(
            parameters,
            AL,
            minibatch_Y,
            lambd,
            outputActivationFunc=outputActivationFunc
        )

    # Backward propagation.
    gradients = backwardPropagationDeep(
        AL,
        minibatch_Y,
        caches,
        dropoutMat,
        lambd,
        keep_prob,
        hiddenActivationFunc="relu",
        outputActivationFunc=outputActivationFunc
    )

    if optimizer == "gd":
        # Update parameters normal gradient descent
        parameters = gradientDescent(
            parameters,
            gradients,
            learningRate=learningRate,
            outputActivationFunc=outputActivationFunc
        )
    elif optimizer == "momentum":
        # Update parameters for gradient descent with momentum
        parameters, v = gradientDescentWithMomentum(
            parameters,
            gradients,
            v,
            beta,
            learningRate=learningRate,
            outputActivationFunc=outputActivationFunc
        )
    elif optimizer == "rmsprop":
        # Update parameters for gradient descent with RMSProp
        parameters, s = gradientDescentWithRMSProp(
            parameters,
            gradients,
            s,
            beta1,
            epsilon,
            learningRate=learningRate,
            outputActivationFunc=outputActivationFunc
        )
    elif optimizer == "adam":
        t = t + 1  # Adam counter
        parameters, v, s = gradientDescentWithAdam(
            parameters,
            gradients,
            v,
            s,
            t,
            beta1,
            beta2,
            epsilon,
            learningRate=learningRate,
            outputActivationFunc=outputActivationFunc
        )

    # Print the cost every 1000 epoch
    if print_cost and i % 100 == 0:
        print("Cost after epoch %i: %f" % (i, cost))

    if print_cost and i % 100 == 0:
        costs.append(cost)

    if lrDecay == True:
        learningRate = np.power(decayRate, (num_epochs / 1000)) * learningRate
```

# Plot the cost

```python
plt.plot(np.squeeze(costs))
plt.ylabel('Cost')
plt.xlabel('No of epochs(x100)')
plt.title("Learning rate =" + str(learningRate))
plt.savefig(figure, bbox_inches='tight')
# plt.show()
plt.clf()
plt.close()
```

# Create random mini batches

**Input:**
- `X` - Input features
- `Y` - Output
- `miniBatchSize`
- `seed`

**Output:** `mini_batches`

```python
def random_mini_batches(X, Y, miniBatchSize=64, seed=0):
    np.random.seed(seed)

    # Get number of training samples
    m = X.shape[1]

    # Initialize mini batches
    mini_batches = []

    # Create a list of random numbers < m
    permutation = list(np.random.permutation(m))

    # Randomly shuffle the training data
    shuffled_X = X[:, permutation]
    shuffled_Y = Y[:, permutation].reshape((1, m))

    # Compute number of mini batches
    numCompleteMinibatches = math.floor(m / miniBatchSize)

    # For the number of mini batches
    for k in range(0, numCompleteMinibatches):
        # Set the start and end of each mini batch
        mini_batch_X = shuffled_X[:, k * miniBatchSize: (k + 1) * miniBatchSize]
        mini_batch_Y = shuffled_Y[:, k * miniBatchSize: (k + 1) * miniBatchSize]
        mini_batch = (mini_batch_X, mini_batch_Y)
        mini_batches.append(mini_batch)

    # If m % miniBatchSize != 0: The batch does not evenly divide by the mini batch
    if m % miniBatchSize != 0:
        l = math.floor(m / miniBatchSize) * miniBatchSize

        # Set the start and end of last mini batch
        m = l + m % miniBatchSize
        mini_batch_X = shuffled_X[:, l:m]
        mini_batch_Y = shuffled_Y[:, l:m]
        mini_batch = (mini_batch_X, mini_batch_Y)
        mini_batches.append(mini_batch)

    return mini_batches
```

# Plot a decision boundary

**Input:**
- Input Model
- `X`
- `Y`
- `sz` - Num of hidden units
- `lr` - Learning rate
- Fig to be saved as

**Returns:** Null

```python
def plot_decision_boundary(model, X, y, lr, figure1="figb.png"):
    print("plot")

    # Set min and max values and give it some padding
    x_min, x_max = X[0, :].min() - 1, X[0, :].max() + 1
    y_min, y_max = X[1, :].min() - 1, X[1, :].max() + 1

    colors = ['black', 'gold']
    cmap = matplotlib.colors.ListedColormap(colors)
    h = 0.01

    # Generate a grid of points with distance h between them
    xx, yy = np.meshgrid(
        np.arange(x_min, x_max, h),
        np.arange(y_min, y_max, h)
    )

    # Predict the function value for the whole grid
    Z = model(np.c_[xx.ravel(), yy.ravel()])
    Z = Z.reshape(xx.shape)

    # Plot the contour and training examples
    plt.contourf(xx, yy, Z, cmap="coolwarm")
    plt.ylabel('x2')
    plt.xlabel('x1')

    x = X.T
    y = y.T.reshape(300,)
    plt.scatter(x[:, 0], x[:, 1], c=y, s=20)
    print(X.shape)

    plt.title("Decision Boundary for learning rate:" + lr)
    plt.savefig(figure1, bbox_inches='tight')
    # plt.show()
```

# Predict output

```python
def predict(
    parameters,
    X,
    keep_prob=1,
    hiddenActivationFunc="relu",
    outputActivationFunc="sigmoid"
):
    A2, cache, dropoutMat = forwardPropagationDeep(
        X,
        parameters,
        keep_prob=1,
        hiddenActivationFunc="relu",
        outputActivationFunc=outputActivationFunc
    )
    predictions = (A2 > 0.5)
    return predictions
```

# Predict probability

```python
def predict_proba(parameters, X, outputActivationFunc="sigmoid"):
    A2, cache = forwardPropagationDeep(X, parameters)

    if outputActivationFunc == "sigmoid":
        proba = A2
    elif outputActivationFunc == "softmax":
        proba = np.argmax(A2, axis=0).reshape(-1, 1)

    print("A2=", A2.shape)
    return proba
```

# Plot a decision boundary (Alternative Implementation)

**Input:**
- Input Model
- `X`
- `Y`
- `sz` - Num of hidden units
- `lr` - Learning rate
- Fig to be saved as

**Returns:** Null

```python
def plot_decision_boundary1(X, y, W1, b1, W2, b2, figure2="figc.png"):
    # plot_decision_boundary(lambda x: predict(parameters, x.T), x1, y1.T, str(0.3), "fig2.png")

    h = 0.02
    x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
    y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1

    xx, yy = np.meshgrid(
        np.arange(x_min, x_max, h),
        np.arange(y_min, y_max, h)
    )

    Z = np.dot(
        np.maximum(
            0,
            np.dot(np.c_[xx.ravel(), yy.ravel()], W1.T) + b1.T
        ),
        W2.T
    ) + b2.T

    Z = np.argmax(Z, axis=1)
    Z = Z.reshape(xx.shape)

    fig = plt.figure()
    plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral, alpha=0.8)
    print(X.shape)

    y1 = y.reshape(300,)
    plt.scatter(X[:, 0], X[:, 1], c=y1, s=40, cmap=plt.cm.Spectral)
    plt.xlim(xx.min(), xx.max())
    plt.ylim(yy.min(), yy.max())
    plt.savefig(figure2, bbox_inches='tight')
```

# Load the circles dataset

```python
def load_dataset():
    np.random.seed(1)
    train_X, train_Y = sklearn.datasets.make_circles(n_samples=300, noise=.05)
    np.random.seed(2)
    test_X, test_Y = sklearn.datasets.make_circles(n_samples=100, noise=.05)

    # Visualize the data
    print(train_X.shape)
    print(train_Y.shape)
    # plt.scatter(train_X[:, 0], train_X[:, 1], c=train_Y, s=40, cmap=plt.cm.Spectral);

    train_X = train_X.T
    train_Y = train_Y.reshape((1, train_Y.shape[0]))
    test_X = test_X.T
    test_Y = test_Y.reshape((1, test_Y.shape[0]))

    return train_X, train_Y, test_X, test_Y
```

---

# Note: Using `dictionary_to_vector` followed by `vector_to_dictionary` => original dictionary

# Convert a weight, biases dictionary to a vector

**Input:** parameter dictionary
**Returns:** vector

```python
def dictionary_to_vector(parameters):
    """
    Roll all our parameters dictionary into a single vector satisfying our specific required shape.
    """
    keys = []
    count = 0

    for key in parameters:
        # flatten parameter
        new_vector = np.reshape(parameters[key], (-1, 1))
        keys = keys + [key] * new_vector.shape[0]

        if count == 0:
            theta = new_vector
        else:
            theta = np.concatenate((theta, new_vector), axis=0)

        count = count + 1

    return theta, keys
```

# Convert a gradient dictionary to a vector

**Input:**
- `parameters`
- `gradients` (gradient dictionary)

**Returns:** gradient vector

```python
def gradients_to_vector(parameters, gradients):
```
