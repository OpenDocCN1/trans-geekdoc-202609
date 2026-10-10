
# Hidden Activation Function – tanh

# Output Activation Function – softmax

# Learning Rate – 0.005

# Optimizer="adam"

# Beta1 = 0.7

# Beta2 = 0.9

# Epsilon = 1e-8

# Mini_batch_size = 512

![Image 366](index-308_1.jpg)

```python
retvalsSGD = L_Layer_DeepModel_SGD(X1, Y1, layersDimensions,
    hiddenActivationFunc='tanh',
    outputActivationFunc="softmax",
    learningRate=0.005,
    optimizer="adam",
    beta1=0.7,
    beta2=0.9,
    epsilon=10^-8,
    mini_batch_size=512,
    num_epochs=5000,
    print_cost=True)
```

# Plot the cost vs number of epochs

```r
iterations <- seq(0, 5000, 1000)
costs = retvalsSGD$costs
df = data.frame(iterations, costs)
ggplot(df, aes(x=iterations, y=costs)) + geom_point() + geom_line(color="blue") +
    ggtitle("Costs vs number of epochs") + xlab("No of epochs") + ylab("Cost")
```

## 5.1c. Stochastic Gradient Descent with Adam – Octave

```matlab
source("DL7functions.m")
load('./mnist/mnist.txt.gz');

# Create a random permutation from 1024
permutation = randperm(1024);
disp(length(permutation));

# Use this 1024 as the batch
X = trainX(permutation, :);
Y = trainY(permutation, :);

# Set layer dimensions
# 784 – number of input features (28 x28)
# 15, 9 – 2 hidden layers with 15,9 hidden units respectively
# 10 – 10 output classes with softmax activation unit at the output layer
layersDimensions = [784, 15, 9, 10];

# Note the high value for epsilon.
# Otherwise GD with Adam does not seem to converge

# Execute a L-layer Deep Learning network using SGD with Adam optimization
# hidden Activation function – relu
# output activation function – softmax
# learning rate – 0.01
# optimizer="adam"
# beta1 = 0.9
# beta2 = 0.9
# epsilon = 100
# mini_batch_size = 512

[weights biases costs] = L_Layer_DeepModel_SGD(X', Y', layersDimensions,
    hiddenActivationFunc='relu',
    outputActivationFunc="softmax",
    learningRate=0.1,
    lrDecay=false,
    decayRate=1,
    lambd=0,
    keep_prob=1,
    optimizer="adam",
    beta=0.9,
    beta1=0.9,
    beta2=0.9,
    epsilon=100,
    mini_batch_size=512,
    num_epochs=5000);

# Plot cost vs number of epochs
plotCostVsEpochs(5000, costs)
```

![Image 367](index-311_1.jpg)

## 6. Conclusion

In this chapter I discuss and implement several Stochastic Gradient Descent optimization methods. The implementation of these methods enhance my already existing generic L-Layer Deep Learning Network implementation in vectorized Python, R and Octave.

![Image 368](index-313_1.jpg)
![Image 369](index-313_2.jpg)
![Image 370](index-313_3.jpg)
![Image 371](index-313_4.jpg)
![Image 372](index-313_5.jpg)
![Image 373](index-313_6.jpg)
![Image 374](index-313_7.jpg)

## 8. Gradient Check in Deep Learning

> *You don't understand anything until you learn it more than one way.* — Marvin Minsky
>
> *No computer has ever been designed that is ever aware of what it's doing; but most of the time, we aren't either.* — Marvin Minsky
>
> *A wealth of information creates a poverty of attention.* — Herbert Simon

In this final chapter, I discuss and implement a key functionality needed while building Deep Learning networks viz. 'Gradient Checking'. Gradient Checking is an important method to check the correctness of your implementation, specifically the forward propagation and the backward propagation cycles of an implementation. In addition, I also discuss some tips for tuning hyperparameters of a Deep Learning network based on my experience.

This chapter implements a critical function for ensuring the correctness of a L-Layer Deep Learning network implementation using Gradient Checking.

Gradient Checking is based on the following approach. One iteration of Gradient Descent computes and updates the parameters by doing .

To minimize the cost we will need to minimize .

Let be a function that computes the derivative . Gradient Checking allows us to numerically evaluate the implementation of the function and verify its correctness.

We know the derivative of a function is given by

**Note**: The above derivative is based on the 2-sided derivative. The 1-sided derivative is given by

Gradient Checking is based on the 2-sided derivative because the error is of the order as opposed for the 1-sided derivative.

Hence Gradient Check uses the 2-sided derivative as follows.

In Gradient Check the following is done:

**A) Run one normal cycle of your implementation by doing the following:**

a) Compute the output activation by running 1 cycle of forward propagation
b) Compute the cost using the output activation
c) Compute the gradients using backpropagation (`grad`)

**B) Perform gradient check steps as below:**

a) Set . Flatten all 'weights' and 'bias' matrices and vectors to a column vector.
b) Initialize by nudging up by adding ()
c) Perform forward propagation with
d) Compute cost with i.e.
e) Initialize by nudging down by subtracting
f) Perform forward propagation with
g) Compute cost with i.e.
h) Compute or 'gradapprox' as using the 2-sided derivative.
i) Compute L2norm or the Euclidean distance between 'grad' and 'gradapprox'.

If the difference is of the order of or the implementation is correct. In the Deep Learning

![Image 398](index-315_1.jpg)
![Image 399](index-315_2.jpg)

[Specialization](https://www.coursera.org/specializations/deep-learning) Prof Andrew Ng mentions that if the difference is of the order of then the implementation is correct. A difference of is also ok. Anything more than that is a cause of worry and you should look at your code more closely. To see more details click [Gradient checking and advanced optimization](http://ufldl.stanford.edu/wiki/index.php/Gradient_checking_and_advanced_optimization).

The implementations of the functions invoked in this chapter are in Appendix 8 – Gradient Check.

You can clone/download the code from Github at [DeepLearningFromFirstPrinciples](https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap8-DLGradientCheck).

After spending a better part of 3 days, I now realize how critical Gradient Check is for ensuring the correctness of your implementation. Initially I was getting very high difference and did not know how to understand the results or debug my implementation. After many hours of staring at the results, I was able to finally arrive at a way to localize issues in the implementation. In fact, I did catch a small bug in my Python code, which did not exist in the R and Octave implementations. I will demonstrate this below.

### 1.1a Gradient Check – Sigmoid Activation – Python

```python
import numpy as np
import matplotlib

exec(open("DLfunctions8.py").read())
exec(open("testcases.py").read())

# Load the circles data set
train_X, train_Y, test_X, test_Y = load_dataset()

# Set layer dimensions
# 2 – number of input features
# 4 – 1 hidden layer with 4 activation units
# 1 – 1 sigmoid activation unit at the output layer
layersDimensions = [2, 4, 1]

# Initialize parameters
parameters = initializeDeepModel(layersDimensions)
```
