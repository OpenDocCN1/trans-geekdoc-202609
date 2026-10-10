
# Gradient Check Implementation

## Code Snippets

```matlab
outputActivationFunc="softmax",numClasses=layersDimensions[length(layersDimensions)])
```

Need to take transpose of the last layer for Softmax

```matlab
L=length(parameters)/2
gradients[[paste('dW',L,sep="")]]=t(gradients[[paste('dW',L,sep="")]])
gradients[[paste('db',L,sep="")]]=t(gradients[[paste('db',L,sep="")]])
```

Perform gradient check

```matlab
gradient_check_n(parameters, gradients, X, Y,
epsilon = 1e-7,outputActivationFunc="softmax")
```

## Results

The implementations works perfectly `3.903011e-07`
[1] "Gradients from backprop"

### $dW1

| | [,1] | [,2] |
|---|---|---|
| [1,] | 0.0007962367 | -0.0001907606 |
| [2,] | 0.0004444254 | 0.0010354412 |
| [3,] | 0.0003078611 | 0.0007591255 |

### $db1

| | [,1] |
|---|---|
| [1,] | -0.0017305136 |
| [2,] | 0.0005393734 |
| [3,] | 0.0012484550 |

### $dW2

| | [,1] | [,2] | [,3] |
|---|---|---|---|
| [1,] | -3.515627e-04 | 7.487283e-04 | -3.971656e-04 |
| [2,] | -6.381521e-05 | -1.257328e-06 | 6.507254e-05 |
| [3,] | -1.719479e-04 | -4.857264e-04 | 6.576743e-04 |

### $db2

| | [,1] |
|---|---|
| [1,] | -5.536383e-06 |
| [2,] | -1.824656e-05 |
| [3,] | 2.378295e-05 |

[1] "Grad approx from gradient check"

### $dW1

| | [,1] | [,2] |
|---|---|---|
| [1,] | 0.0007962364 | -0.0001907607 |
| [2,] | 0.0004444256 | 0.0010354406 |
| [3,] | 0.0003078615 | 0.0007591250 |

### $db1

| | [,1] |
|---|---|
| [1,] | -0.0017305135 |
| [2,] | 0.0005393741 |
| [3,] | 0.0012484547 |

### $dW2

| | [,1] | [,2] | [,3] |
|---|---|---|---|
| [1,] | -3.515632e-04 | 7.487277e-04 | -3.971656e-04 |
| [2,] | -6.381451e-05 | -1.257883e-06 | 6.507239e-05 |
| [3,] | -1.719469e-04 | -4.857270e-04 | 6.576739e-04 |

### $db2

| | [,1] |
|---|---|
| [1,] | -5.536682e-06 |
| [2,] | -1.824652e-05 |
| [3,] | 2.378209e-05 |

---

# 1.3a Gradient Check – Sigmoid

## Activation – Octave

```matlab
source("DL8functions.m")
```

Read circles data

```matlab
data=csvread("circles.csv");
X=data(:,1:2);
Y=data(:,3);
```

Set layer dimensions

```matlab
# 2 – number of input features
# 5 – 1 hidden layer with 5 activation units
# 1 – 1 sigmoid activation unit at the output layer
layersDimensions = [2 5 1];
```

Initialize model

```matlab
[weights biases] = initializeDeepModel(layersDimensions);
```

Perform forward prop

```matlab
[AL forward_caches activation_caches droputMat] =
forwardPropagationDeep(X', weights, biases,keep_prob=1,
hiddenActivationFunc="relu", outputActivationFunc="sigmoid");
```

Compute cost

```matlab
cost = computeCost(AL,
Y',outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));
disp(cost);
```

Compute gradients from cost

```matlab
[gradsDA gradsDW gradsDB] = backwardPropagationDeep(AL, Y',
activation_caches,forward_caches, droputMat, lambd=0, keep_prob=1, hiddenActivationFunc="relu",
outputActivationFunc="sigmoid",
numClasses=layersDimensions(size(layersDimensions)
(2)));
```

Set values

```matlab
epsilon = 1e-07;
outputActivationFunc="sigmoid";
```

Convert paramters cell array to vector

```matlab
parameters_values = cellArray_to_vector(weights, biases);
```

Convert gradient cell array to vector

```matlab
grad = gradients_to_vector(gradsDW,gradsDB);
num_parameters = size(parameters_values)(1);
```

Initialize `J_plus`, `J_minus` and `gradapprox`

```matlab
J_plus = zeros(num_parameters, 1);
J_minus = zeros(num_parameters, 1);
gradapprox = zeros(num_parameters, 1);
```

Compute `gradapprox`

```matlab
for i = 1:num_parameters
# Compute J_plus[i].
thetaplus = parameters_values;
thetaplus(i,1) = thetaplus(i,1) + epsilon;
[weights1 biases1] =vector_to_cellArray(weights, biases,thetaplus);
[AL forward_caches activation_caches droputMat] =
forwardPropagationDeep(X', weights1, biases1,
keep_prob=1,
hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc);
J_plus(i) = computeCost(AL, Y',
outputActivationFunc=outputActivationFunc);

# Compute J_minus[i].
thetaminus = parameters_values;
thetaminus(i,1) = thetaminus(i,1) - epsilon ;
[weights1 biases1] = vector_to_cellArray(weights, biases,thetaminus);
[AL forward_caches activation_caches droputMat] =
forwardPropagationDeep(X',weights1, biases1, keep_prob=1,
hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc);
J_minus(i) = computeCost(AL, Y',
outputActivationFunc=outputActivationFunc);

# Compute gradapprox[i]
gradapprox(i) = (J_plus(i) - J_minus(i))/(2*epsilon);
endfor
```

Compute L2Norm or the Euclidean distance between gradients and gradapprox

```matlab
numerator = L2NormVec(grad-gradapprox);
denominator = L2NormVec(grad) +
L2NormVec(gradapprox);
difference = numerator/denominator;
disp(difference);
```

Check difference

```matlab
if difference > 1e-04
printf("There is a mistake in the implementation ");
disp(difference);
else
printf("The implementation works perfectly");
disp(difference);
endif
```

Technique to compare the weights and biases and localize issue

Convert `grad` to cell Array

```matlab
[weights1 biases1] = vector_to_cellArray(weights, biases,grad);
printf("Gradients from back propagation");
disp(weights1);
disp(biases1);
```

Convert `gradapprox` to cell array

```matlab
[weights2 biases2] = vector_to_cellArray(weights, biases,gradapprox);
printf("Gradients from gradient check");
```

Display

```matlab
disp(weights2);
disp(biases2);
```

### Output

```
0.69315
1.4893e-005
The implementation works perfectly 1.4893e-005
```

#### Gradients from back propagation

```
{
[1,1] =
5.0349e-005 2.1323e-005
8.8632e-007 1.8231e-006
9.3784e-005 1.0057e-004
1.0875e-004 -1.9529e-007
5.4502e-005 3.2721e-005
[1,2] =
1.0567e-005 6.0615e-005 4.6004e-005 1.3977e-004 1.0405e-004
}
{
[1,1] =
-1.8716e-005
1.1309e-009
4.7686e-005
1.2051e-005
-1.4612e-005
[1,2] = 9.5808e-006
}
```

#### Gradients from gradient check

```
{
[1,1] =
5.0348e-005 2.1320e-005
8.8485e-007 1.8219e-006
9.3784e-005 1.0057e-004
1.0875e-004 -1.9762e-007
5.4502e-005 3.2723e-005
[1,2] =
1.0565e-005 6.0614e-005 4.6007e-005 1.3977e-004 1.0405e-004
}
{
[1,1] =
-1.8713e-005
1.1102e-009
4.7687e-005
1.2048e-005
-1.4609e-005
[1,2] = 9.5790e-006
}
```

---

# 1.3b Gradient Check – Softmax

## Activation – Octave

```matlab
source("DL8functions.m")
```

```matlab
data=csvread("spiral.csv");
```

Setup the data

```matlab
X=data(:,1:2);
Y=data(:,3);
```

Set the layer dimensions

```matlab
# 2 – number of input features
# 3 – 1 hidden layer with 3 activation units
# 3 – 3 classes with softmax activation unit at the output layer
layersDimensions = [2 3 3];
```

```matlab
[weights biases] = initializeDeepModel(layersDimensions);
```

Run forward prop

```matlab
[AL forward_caches activation_caches droputMat] =
forwardPropagationDeep(X', weights, biases,keep_prob=1,
hiddenActivationFunc="relu", outputActivationFunc="softmax");
```

Compute cost

```matlab
cost = computeCost(AL,
Y',outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));
disp(cost);
```

Perform backward prop

```matlab
[gradsDA gradsDW gradsDB] = backwardPropagationDeep(AL, Y',
activation_caches,forward_caches, droputMat, lambd=0, keep_prob=1, hiddenActivationFunc="relu",
outputActivationFunc="softmax",
numClasses=layersDimensions(size(layersDimensions)
(2)));
```

Take transpose of last layer for Softmax

```matlab
L=size(weights)(2);
gradsDW{L}= gradsDW{L}';
gradsDB{L}= gradsDB{L}';
```

Perform gradient check

```matlab
difference= gradient_check_n(weights, biases, gradsDW,gradsDB, X, Y, epsilon
= 1e-7,
outputActivationFunc="softmax",numClasses=layersDimensions(size(layersDimensions) (2)));
```

### Output

```
1.0986
The implementation works perfectly! 2.0021e-005
```

#### Gradients from back propagation

```
{
[1,1] =
-7.1590e-005 4.1375e-005
-1.9494e-004 -5.2014e-005
-1.4554e-004 5.1699e-005
[1,2] =
3.3129e-004 1.9806e-004 -1.5662e-005
-4.9692e-004 -3.7756e-004 -8.2318e-005
1.6562e-004 1.7950e-004 9.7980e-005
}
{
[1,1] =
-3.0856e-005
-3.3321e-004
-3.8197e-004
[1,2] =
1.2046e-006
2.9259e-007
-1.4972e-006
}
```

#### Gradients from gradient check

```
{
[1,1] =
-7.1586e-005 4.1377e-005
-1.9494e-004 -5.2013e-005
-1.4554e-004 5.1695e-005
3.3129e-004 1.9806e-004 -1.5664e-005
-4.9692e-004 -3.7756e-004 -8.2316e-005
1.6562e-004 1.7950e-004 9.7979e-005
}
{
[1,1] =
```
