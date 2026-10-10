
# 随机梯度下降实现

## 1.1a. 随机梯度下降 (Vanilla) – Python

```python
X = pixels.reshape(pixels.shape[0], -1)
X1 = X.T
Y1 = y.T

# Create a list of 1024 random numbers.
permutation = list(np.random.permutation(2**10))

# Subset 1024 training samples from the data
X2 = X1[:, permutation]
Y2 = Y1[:, permutation].reshape((1, 2**10))
```

![Image 328](index-266_1.jpg)

```python
# Set the layer dimensions
# 784 – number of input features (28 x28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions = [784, 15, 9, 10]

# Execute the L-Layer Deep Network to perform SGD with regular gradient descent
# hidden Activation function – relu
# output activation function – softmax
# learning rate – 0.01
# optimizer="gd" # gradient descent
# mini_batch_size = 512

parameters = L_Layer_DeepModel_SGD(X2, Y2, layersDimensions,
                                   hiddenActivationFunc='relu',
                                   outputActivationFunc="softmax",
                                   learningRate=0.01,
                                   optimizer="gd",
                                   mini_batch_size=512,
                                   num_epochs=1000,
                                   print_cost=True,
                                   figure="fig1.png")
```

## 1.1b. 随机梯度下降 (Vanilla) – R

```r
source("mnist.R")
source("DLfunctions7.R")

# Load and read MNIST data
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
# 784 – number of input features (28 x28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions <- c(784, 15, 9, 10)

# Execute the L-Layer Deep Network to perform SGD with regular gradient descent
# hidden Activation function – tanh
# output activation function – softmax
# learning rate – 0.05
# optimizer="gd" # gradient descent
# mini_batch_size = 512

retvalsSGD <- L_Layer_DeepModel_SGD(X1, Y1, layersDimensions,
                                    hiddenActivationFunc='tanh',
                                    outputActivationFunc="softmax",
                                    learningRate=0.05,
                                    optimizer="gd",
                                    mini_batch_size=512,
                                    num_epochs=5000,
                                    print_cost=TRUE)

# Plot the cost vs number of epochs
iterations <- seq(0, 5000, 1000)
costs <- retvalsSGD$costs
df <- data.frame(iterations, costs)
ggplot(df, aes(x=iterations, y=costs)) + geom_point() + geom_line(color="blue") +
  ggtitle("Costs vs no of epochs") + xlab("No of epochss") + ylab("Cost")
```

![Image 329](index-268_1.jpg)

## 1.1c. 随机梯度下降 (Vanilla) – Octave

```matlab
source("DL7functions.m")

# Load and read MNIST
load('./mnist/mnist.txt.gz');

# Create a random permutation from 1024
permutation = randperm(1024);
disp(length(permutation));

# Use this 1024 as the mini-batch
X = trainX(permutation, :);
Y = trainY(permutation, :);

# Set layer dimensions
# 784 – number of input features (28 x28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions = [784, 15, 9, 10];

# Execute the L-Layer Deep Network to perform SGD with regular gradient descent
# hidden Activation function – relu
# output activation function – softmax
# learning rate – 0.005
# optimizer="gd" # gradient descent
# mini_batch_size = 512

[weights, biases, costs] = L_Layer_DeepModel_SGD(X', Y', layersDimensions,
                                                 hiddenActivationFunc='relu',
                                                 outputActivationFunc="softmax",
                                                 learningRate=0.005,
                                                 lrDecay=true,
                                                 decayRate=1,
                                                 lambd=0,
                                                 keep_prob=1,
                                                 optimizer="gd",
                                                 beta=0.9,
                                                 beta1=0.9,
                                                 beta2=0.999,
                                                 epsilon=10^-8,
                                                 mini_batch_size=512,
                                                 num_epochs=5000);

# Plot cost vs number epochs
plotCostVsEpochs(5000, costs);
```

![Image 330](index-271_1.jpg)
![Image 331](index-272_1.jpg)
![Image 332](index-272_2.jpg)
![Image 333](index-272_3.jpg)

## 2.1. 带学习率衰减的随机梯度下降

在随机梯度下降中，每个 epoch 使用略微不同的样本，当使用固定学习率时，梯度下降算法会在峡谷中振荡并在极小值附近游荡。在“学习率衰减”技术中，学习率随着 epoch 数量的增加而缓慢减小，变得越来越小，以便梯度下降能朝极小值迈出更小的步伐。

学习率衰减有几种技术：

a) 指数衰减：
b) 1/t 衰减：
c)

在我的实现中，我使用了“指数衰减”。Python 的代码片段如下：

```python
if lrDecay == True:
    # decay the learning rate exponentially
    learningRate = np.power(decayRate, (num_epochs/1000)) * learningRate
```

## 2.1a. 带学习率衰减的随机梯度下降 – Python

```python
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
import sklearn.linear_model
import pandas as pd
import sklearn
import sklearn.datasets

exec(open("DLfunctions7.py").read())
exec(open("load_mnist.py").read())

# Read the MNIST data
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

# Subset 1024 from the data
X2 = X1[:, permutation]
Y2 = Y1[:, permutation].reshape((1, 2**10))
```

![Image 334](index-274_1.jpg)

```python
# Set layer dimensions
# 784 – number of input features (28 x28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions = [784, 15, 9, 10]

# Execute the L-layer Deep Learning network using SGD with learning rate decay
# hidden Activation function – relu
# output activation function – softmax
# learning rate – 0.01
# lrDecay=True
# decayRate=0.9999
# optimizer="gd" # gradient descent
# mini_batch_size = 512

parameters = L_Layer_DeepModel_SGD(X2, Y2, layersDimensions,
                                   hiddenActivationFunc='relu',
                                   outputActivationFunc="softmax",
                                   learningRate=0.01,
                                   lrDecay=True,
                                   decayRate=0.9999,
                                   optimizer="gd",
                                   mini_batch_size=512,
                                   num_epochs=1000,
                                   print_cost=True,
                                   figure="fig2.png")
```

## 2.1b. 带学习率衰减的随机梯度下降 – R

```r
source("mnist.R")
source("DLfunctions7.R")

# Read and load MNIST
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
# 784 – number of input features (28 x28)
# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions <- c(784, 15, 9, 10)

# Execute the L-layer Deep Learning network using SGD with learning rate decay
# hidden Activation function – tanh
# output activation function – softmax
# learning rate – 0.05
# lrDecay=TRUE
# decayRate=0.9999
# optimizer="gd" # gradient descent
# mini_batch_size = 512

retvalsSGD <- L_Layer_DeepModel_SGD(X1, Y1, layersDimensions,
                                    hiddenActivationFunc='tanh',
                                    outputActivationFunc="softmax",
                                    learningRate=0.05,
                                    lrDecay=TRUE,
                                    decayRate=0.9999,
                                    optimizer="gd",
                                    mini_batch_size=512,
                                    num_epochs=5000,
                                    print_cost=TRUE)

# Plot the cost vs number of epochs
iterations <- seq(0, 5000, 1000)
costs <- retvalsSGD$costs
df <- data.frame(iterations, costs)
ggplot(df, aes(x=iterations, y=costs)) + geom_point() + geom_line(color="blue") +
  ggtitle("Costs vs number of epochs") + xlab("No of epochs") + ylab("Cost")
```
