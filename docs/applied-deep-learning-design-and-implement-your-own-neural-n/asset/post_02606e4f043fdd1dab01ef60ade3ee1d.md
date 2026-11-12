
## Multiple choice questions

- 1. **Backpropagation refers to:**
  - a. The transmission of error back towards the network for adjusting the inputs
  - b. Another name specified for the curvy function of the perceptron
  - c. The transmission of error back through the network to allow weights to be adjusted so that the network can learn
  - d. None of the mentioned

- 2. **Artificial neural network promises the following:**
  - a. Explanation of the result
  - b. ANN can ensure the node failure
  - c. Inherent parallelism
  - d. Noise handling

- 3. **While in the backward pass, the purpose is to calculate which of the following for every input with respect to the final value of the output?**
  - a. Mean
  - b. Gradient
  - c. Sum
  - d. Differentiation

- 4. **A perceptron sums up all the weighted input values which it receives, and if it surpasses a certain value, it outputs a 1; otherwise, it just outputs a 0.**
  - a. False
  - b. True
  - c. Can't say
  - d. Sometimes

- 5. **Application of the Neural Network is:**
  - a. Data validation
  - b. Risk management
  - c. Sales forecasting
  - d. All of the mentioned

- 6. **In Gradient Descent, new weight can be calculated as:**
  - a. new_wt = old_wt - ∇w
  - b. new_wt = old_wt + ∇w
  - c. new_wt = old_wt * ∇w
  - d. new_wt = old_wt / ∇w

## Hands-on session

### 1. Plot a linear function in Python.

```python
def linear(x):
    return x

plot(x)

def linear(x):
    a = []
    for item in x:
        a.append(item)
    return a
```

![](img/7e519fee1b702b91799cdf1664598392_212_0.png)

Figure 3.47: Plot of a linear function in Python

### 2. Plot a sigmoid function in Python.

```python
def linear(x):
    return 1 / (1 + np.exp(-x))
plot(x)
```

```python
import matplotlib.pyplot as plt
import numpy as np
import math
def sigmoid(x):
    a = []
    for item in x:
        a.append(1/(1+math.exp(-item)))
    return a
```

![](img/7e519fee1b702b91799cdf1664598392_213_0.png)

Figure 3.48: Plot of a sigmoid function in Python

### 3. Plot a ReLU function in Python.

```python
def linear(z):
    return z (z > 0)
plot(z)
def relu(x):
    a = []
    for item in x:
        a.append(max(0, item))
    return a
```

![](img/7e519fee1b702b91799cdf1664598392_213_1.png)

Figure 3.49: Plot of a ReLU function in Python

### 4. Plot a Leaky ReLU in Python.

```python
def dReLU(x):
    return 1. * (x > 0)

plot(x)
```

```python
def leaky_relu(x):
    a = []
    for item in x:
        a.append(max(0.1*item, item))
    return a
```

![](img/7e519fee1b702b91799cdf1664598392_214_0.png)

Figure 3.50: Plot of a leaky ReLU function in Python

### 5. Plot a tanh function in Python.

```python
def tanh(z):
    return (2/(1 + np.exp(-2*z))-1)
plot(z)
```

```python
def tanh(x):
    a = []
    for item in x:
        a.append((2/(1+np.exp(-2*item)))-1)
    return a
```

![](img/7e519fee1b702b91799cdf1664598392_215_0.png)

```python
x = np.arange(-10., 10., 0.2)
x = np.arange(-10., 10., 0.2)
sig = tanh(x)
plt.plot(x,sig)
plt.show()
```

### 6. Python code for perceptron learning.

```python
import numpy as np
class Perceptron(object):
    def __init__(self, no_of_inputs, threshold=50, learning_rate=0.02):
        self.threshold = threshold
        self.learning_rate = learning_rate
        self.weights = np.zeros(no_of_inputs + 1)

    def predict(self, inputs):
        summation = np.dot(inputs, self.weights[1:]) + self.weights[0]
        if summation > 0:
            activation = 1
        else:
            activation = 0
        return activation

    def train(self, training_inputs, labels):
        for _ in range(self.threshold):
            for inputs, label in zip(training_inputs, labels):
                prediction = self.predict(inputs)
                self.weights[1:] += self.learning_rate * (label - prediction) * inputs
                self.weights[0] += self.learning_rate * (label - prediction)
```

### 7. Feed-forward network code in Python.

```python
import numpy as np
import matplotlib.pyplot as plt

Nclass = 500

X1 = np.random.randn(Nclass, 2) + np.array([0, -2])
X2 = np.random.randn(Nclass, 2) + np.array([2, 2])
X3 = np.random.randn(Nclass, 2) + np.array([-2, 2])
X = np.vstack([X1, X2, X3])

Y = np.array([0]*Nclass + [1]*Nclass + [2]*Nclass)

# let's see what it looks like
plt.scatter(X[:,0], X[:,1], c=Y, s=100, alpha=0.5)
plt.show()

# randomly initialize weights
D = 2 # dimensionality of input
M = 3 # hidden layer size
K = 3 # number of classes
W1 = np.random.randn(D, M)
b1 = np.random.randn(M)
W2 = np.random.randn(M, K)
b2 = np.random.randn(K)
```

```python
def sigmoid(a):
    return 1 / (1 + np.exp(-a))
```

```python
def forward(X, W1, b1, W2, b2):
    Z = sigmoid(X.dot(W1) + b1) # sigmoid
    # Z = np.tanh(X.dot(W1) + b1) # tanh
    # Z = np.maximum(X.dot(W1) + b1, 0) # relu
    A = Z.dot(W2) + b2
    expA = np.exp(A)
    Y = expA / expA.sum(axis=1, keepdims=True)
    return Y
```

```python
# determine the classification rate
# num correct / num total
def classification_rate(Y, P):
    n_correct = 0
    n_total = 0
    for i in range(len(Y)):
        n_total += 1
        if Y[i] == P[i]:
            n_correct += 1
    return float(n_correct) / n_total
```

```python
P_Y_given_X = forward(X, W1, b1, W2, b2)
P = np.argmax(P_Y_given_X, axis=1)
```

```python
# verify we chose the correct axis
assert(len(P) == len(Y))
```

```python
print("Classification rate for randomly chosen weights:", classification_rate(Y, P))
```

### Output

![](img/7e519fee1b702b91799cdf1664598392_218_0.png)

### 8. Gradient descent code for linear regression in Python.

```python
import numpy as np
def gradient_descent (x,y):
    m_curr = b_curr = 0
    iterations = 2
    learning_rate = 0.1
    n=len(x)
    for i in range(iterations):
        y_pred = m_curr*x + b_curr
        print("y_pred = ",y_pred)
        f= sum([val**2 for val in (y-y_pred)])
        print("f=", f)
        g= sum((y-y_pred)**2)
        print("g=", g)
        cost = (1/n)*sum((y-y_pred)**2)
        cost1 = (1/n)*sum([val**2 for val in (y-y_pred)])
        e=sum(x*(y-y_pred))
        print("e=", e)
        print("total=",sum(x*(y-y_pred)))
        md = -(2/n)*sum(x*(y-y_pred))
        bd = -(2/n)*sum(y-y_pred)
        m_curr = m_curr - learning_rate * md
        b_curr = b_curr - learning_rate * bd
        print("m_curr = , b_curr=, iteration =, md =, bd =, cost=, cost1= ", m_curr, b_curr, i, md, bd, cost, cost1)
x=np.array([1,2,3])
y=np.array([6,7,8])
```

```python
gradient_descent (x,y)
Output:
y_pred = [0 0 0]
f= 149
g= 149
e= 44
total= 44
m_curr = , b_curr=, iteration =, md =, bd =, cost=, cost1=
2.9333333333333336 1.4000000000000001 0 -29.333333333333332 -14.0
49.666666666666664 49.666666666666664
y_pred = [ 4.33333333 7.26666667 10.2 ]
f= 7.688888888888892
g= 7.688888888888892
e= -5.466666666666672
total= -5.466666666666666
m_curr = , b_curr=, iteration =, md =, bd =, cost=, cost1=
2.568888888888889 1.3466666666666667 1 3.644444444444448
0.5333333333333335 2.5629629629629638 2.5629629629629638
```

For 200th iteration, the output is:

```python
y_pred = [5.98311724 6.99637697 8.00963671]
f= 0.00039102027379503434
g= 0.00039102027379503434
e= -0.004781325193253139
total= -0.004781325193253139
m_curr = , b_curr=, iteration =, md =, bd =, cost=, cost1=
1.0129409835969365 4.970582102510175 199 0.0031875501288354258
-0.007246050675462357 0.00013034009126501145 0.00013034009126501145
```

We can see that the loss function reduces for the corresponding values of y_pred (Predicted Value).

## Join our book's Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

https://discord.bpbonline.com

![](img/7e519fee1b702b91799cdf1664598392_219_0.png)

## CHAPTER 4

### Convolutional Neural Networks

CNN is the heart of deep learning. This chapter discusses the concepts of convolutional neural networks (CNN), architectures, components, and parameters used in various applications. The difference between fully connected layers and CNN layers is also discussed in this chapter. The datasets such as MNIST, ImageNet, and CIFAR-10 consist of various types of images of different sizes, which are used in the study of convolutional neural networks. The main objective of CNN is to perform image classification by training different filters based on the input dataset and backpropagation. The difference between machine learning and deep learning is that in deep learning, the filters are automatically trained, and objects are classified, but in machine learning, filters remain fixed.

The basic concepts of image processing, such as the size of filters, type of filters, correlation, convolution, padding, and stride, are also discussed in this chapter, which are helpful for the readers to understand CNN. They can design their own CNN models for image classification for different applications.

Furthermore, in this chapter, the one-dimensional, two-dimensional, and three-dimensional convolutions are discussed with proper examples. Moreover, the entire CNN architecture and various components, such as convolution, ReLu, Max pooling, fully connected layers, and Softmax, are discussed in detail. In the later section, after a discussion of all the layers of convolutional neural networks, CNN is discussed
