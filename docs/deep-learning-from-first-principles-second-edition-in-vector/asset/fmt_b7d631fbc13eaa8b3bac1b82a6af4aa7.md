
# File: DLfunctions41.m

# Developer: Tinniam V Ganesh

# Date : 26 Feb 2018

---

## Define Relu function

```matlab
function [A,cache] = relu(Z)
A = max(0,Z);
cache=Z;
end
```

## Define Softmax function

```matlab
function [A,cache] = softmax(Z)
# get unnormalized probabilities
exp_scores = exp(Z');
# normalize them for each example
A = exp_scores ./ sum(exp_scores,2);
cache=Z;
end
```

## Define Relu Derivative

```matlab
function [dZ] = reluDerivative(dA,cache)
Z = cache;
dZ = dA;
# Get elements that are greater than 0
a = (Z > 0);
# Select only those elements where Z > 0
dZ = dZ .* a;
end
```

## Define Softmax Derivative

```matlab
function [dZ] = softmaxDerivative(dA,cache,Y)
Z = cache;
# get unnormalized probabilities
exp_scores = exp(Z');
# normalize them for each example
probs = exp_scores ./ sum(exp_scores,2);
# dZ = pi- yi
a=sum(Y==0);
b=sum(Y==1);
c=sum(Y==2);
m= repmat([1 0 0],a,1);
n= repmat([0 1 0],b,1);
o= repmat([0 0 1],c,1);
yi=[m;n;o];
dZ=probs-yi;
end
```

## Initialize the model

**Input**: number of features, number of hidden units, number of units in output

**Returns**: Weight and bias matrices and vectors

```matlab
function [W1 b1 W2 b2] = initializeModel(numFeats,numHidden,numOutput)
rand ("seed", 3);
W1=rand(numHidden,numFeats)*0.01; # Multiply by .01
b1=zeros(numHidden,1);
W2=rand(numOutput,numHidden)*0.01;
b2=zeros(numOutput,1);
end
```

## Compute the activation at a layer 'l' for forward prop in a Deep Network

**Input**:
- `A_prev` - Activation of previous layer
- `W,b` - Weight and bias matrices and vectors
- `activationFunc` - Activation function - sigmoid, tanh, relu etc

**Returns**: `A`, `forward_cache`, `activation_cache`

**Equations**:
- `Z = W * X + b`
- `A = sigmoid(Z)`, `A= Relu(Z)`, `A= tanh(Z)`

```matlab
function [A forward_cache activation_cache] = layerActivationForward(A_prev, W, b, activationFunc)
# Compute Z
Z = W * A_prev +b;
# Create a cell array
forward_cache = {A_prev W b};
# Compute the activation for sigmoid
if (strcmp(activationFunc,"sigmoid"))
[A activation_cache] = sigmoid(Z);
elseif (strcmp(activationFunc, "relu")) # Compute the activation for Relu
[A activation_cache] = relu(Z);
elseif(strcmp(activationFunc,'tanh')) # Compute the activation for tanh
[A activation_cache] = tanhAct(Z);
elseif(strcmp(activationFunc,'softmax')) # Compute the activation for softmax
[A activation_cache] = softmax(Z);
endif
end
```

## Compute the backpropoagation for 1 cycle

**Input**:
- Neural Network parameters - `dA`
- `cache` - `forward_cache` & `activation_cache`
- Input features
- Output values `Y`

**Returns**: `dA_prev`, `dW`, `db`

**Equations**:
- `dL/dWi= dL/dZi*Al-1`
- `dl/dbl = dL/dZl`
- `dL/dZ_prev=dL/dZl*W`

```matlab
function [dA_prev dW db] = layerActivationBackward(dA, forward_cache, activation_cache, Y, activationFunc)
if (strcmp(activationFunc,"relu"))
dZ = reluDerivative(dA, activation_cache);
elseif (strcmp(activationFunc,"sigmoid"))
dZ = sigmoidDerivative(dA, activation_cache);
elseif(strcmp(activationFunc, "tanh"))
dZ = tanhDerivative(dA, activation_cache);
elseif(strcmp(activationFunc, "softmax"))
dZ = softmaxDerivative(dA, activation_cache,Y);
endif

A_prev = forward_cache{1};
numTraining = size(A_prev)(2);

# If activation is softmax
if(strcmp(activationFunc, "softmax"))
W =forward_cache{2};
b = forward_cache{3};
dW = 1/numTraining * A_prev * dZ;
db = 1/numTraining * sum(dZ,1);
dA_prev = dZ*W;
else
W =forward_cache{2};
b = forward_cache{3};
dW = 1/numTraining * dZ * A_prev';
db = 1/numTraining * sum(dZ,2);
dA_prev = W'*dZ;
endif
end
```

## Plot cost vs iterations

```matlab
function plotCostVsIterations(iterations,costs)
plot(iterations,costs);
title ("Cost vs no of iterations for different learning rates");
xlabel("No of iterations");
ylabel("Cost");
print -dpng "figo2.png"
end;
```

## Plot softmax decision boundary

```matlab
function plotDecisionBoundary( X,Y,W1,b1,W2,b2)
% Make classification predictions over a grid of values
x1plot = linspace(min(X(:,1)), max(X(:,1)), 400)';
x2plot = linspace(min(X(:,2)), max(X(:,2)), 400)';
[X1, X2] = meshgrid(x1plot, x2plot);
vals = zeros(size(X1));
for i = 1:size(X1, 2)
gridPoints = [X1(:, i), X2(:, i)];
[A1,cache1 activation_cache1]= layerActivationForward(gridPoints',W1,b1,activationFunc ='relu');
[A2,cache2 activation_cache2] = layerActivationForward(A1,W2,b2,activationFunc='softmax');
[l m] = max(A2, [], 2);
vals(:, i)= m;
endfor
scatter(X(:,1),X(:,2),8,c=Y,"filled");
% Plot the boundary
hold on
contour(X1, X2, vals,"linewidth",4);
print -dpng "fig-o1.png"
end
```

---

# Appendix 5 - MNIST classification with Softmax

## 5.1 Python

```python
# -*- coding: utf-8 -*-
"""
############################################################################################################
#
# File: DLfunctions41.py
# Developer: Tinniam V Ganesh
# Date : 23 Mar 2018
#
##########################################################################################################
@author: Ganesh
"""
import numpy as np
import matplotlib.pyplot as plt
import matplotlib
import matplotlib.pyplot as plt
from matplotlib import cm
import math

# Conmpute the sigmoid of a vector
def sigmoid(Z):
    A=1/(1+np.exp(-Z))
    cache=Z
    return A,cache

# Conmpute the Relu of a vector
def relu(Z):
    A = np.maximum(0,Z)
    cache=Z
    return A,cache

# Conmpute the tanh of a vector
def tanh(Z):
    A = np.tanh(Z)
    cache=Z
    return A,cache

# Conmpute the softmax of a vector
def softmax(Z):
    # get unnormalized probabilities
    exp_scores = np.exp(Z.T)
    # normalize them for each example
    A = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    cache=Z
    return A,cache

# Conmpute the Stable Softmax of a vector
def stableSoftmax(Z):
    #Compute the softmax of vector x in a numerically stable way.
    shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)
    exp_scores = np.exp(shiftZ)
    # normalize them for each example
    A = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    cache=Z
    return A,cache

# Compute the derivative of Relu
def reluDerivative(dA, cache):
    Z = cache
    dZ = np.array(dA, copy=True) # just converting dz to a correct object.
    # When z <= 0, you should set dz to 0 as well.
    dZ[Z <= 0] = 0
    return dZ

# Compute the derivative of Sigmoid
def sigmoidDerivative(dA, cache):
    Z = cache
    s = 1/(1+np.exp(-Z))
    dZ = dA * s * (1-s)
    return dZ

# Compute the derivative of tanh
def tanhDerivative(dA, cache):
    Z = cache
    a = np.tanh(Z)
    dZ = dA * (1 - np.power(a, 2))
    return dZ

# Compute the derivative of Softmax
def softmaxDerivative(dA, cache,y,numTraining):
    # Note : dA not used. dL/dZ = dL/dA * dA/dZ = pi-yi
    Z = cache
    # Compute softmax
    exp_scores = np.exp(Z.T)
    # normalize them for each example
    probs = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    # compute the gradient on scores
    dZ = probs
    # dZ = pi- yi
    dZ[range(int(numTraining)),y[:,0]] -= 1
    return(dZ)

# Compute the derivative of Stable Softmax
def stableSoftmaxDerivative(dA, cache,y,numTraining):
    # Note : dA not used. dL/dZ = dL/dA * dA/dZ = pi-yi
    Z = cache
    # Compute stable softmax
    shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)
    exp_scores = np.exp(shiftZ)
    # normalize them for each example
    probs = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    #print(probs)
    # compute the gradient on scores
    dZ = probs
    # dZ = pi- yi
    dZ[range(int(numTraining)),y[:,0]] -= 1
    return(dZ)

# Initialize the model
# Input : number of features
# number of hidden units
# number of units in output
# Returns: nnParameters dict
def initializeModel(numFeats,numHidden,numOutput):
    np.random.seed(1)
    W1=np.random.randn(numHidden,numFeats)*0.01 # Multiply by .01
    b1=np.zeros((numHidden,1))
    W2=np.random.randn(numOutput,numHidden)*0.01
    b2=np.zeros((numOutput,1))
```
