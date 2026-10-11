
# Objective Function

The objective is to minimize the sum of squared errors between the predicted values `f(xi)` and the actual values `yi`. The objective function for linear regression is the mean squared error (MSE):

![](image_rsrc9TN.jpg)

# Optimization

To find the parameters `θ0` and `θ1` that minimize the MSE, we can differentiate `L(θ)` with respect to `θ0` and `θ1`, set the derivatives to zero, and solve for `θ0` and `θ1`.

![](image_rsrc9TP.jpg)

Solving these equations gives the optimal values for `θ0` and `θ1`, which define the best-fitting linear function.

# Example

Suppose we have a dataset of housing prices where the size of the house (in square feet) is the input variable (`x`) and the price of the house is the output variable (`y`). We want to predict house prices based on their size.

![](image_rsrc9TR.jpg)

Using linear regression, we can find the best-fitting line that represents the relationship between house size and price. The line would have the form `f(x) = θ0 + θ1 x`, where `θ0` is the intercept and `θ1` is the slope of the line. The optimal values of `θ0` and `θ1` can be calculated using the least squares method, and the resulting line can be used to predict the price of a house given its size.

Linear regression is a simple yet powerful technique for approximating functions and is widely used in various applications, such as predicting sales based on advertising spend, forecasting stock prices, and analyzing trends in data.

# Linear Classification Problems

Linear classification is a fundamental problem in machine learning where the goal is to classify data points into two or more classes based on their features. In linear classification, the decision boundary separating the classes is a linear function of the input features. Here's an explanation of linear classification problems with suitable examples:

## Problem Statement

Given a set of data points, each associated with a class label, and a set of features describing each data point, the goal is to learn a linear function that can separate the data points into their respective classes.

## Model

The linear classification model assumes that the decision boundary separating the classes is a hyperplane defined by the equation:

![](image_rsrc9TS.jpg)

where `w0, w1, …, wn` are the coefficients (weights) of the hyperplane, `x1, …, xn` are the features of a data point, and `n` is the number of features.

## Classification Rule

To classify a new data point with features `x1, …, xn`, we evaluate the linear function `w0 + w1 x1 + … + wn xn` and assign the data point to the class corresponding to the sign of the result (e.g., if the result is positive, assign the data point to class 1; if negative, assign it to class 0).

## Examples

1. **Binary Classification**: One of the simplest examples of linear classification is the binary classification problem, where there are two classes (e.g., positive and negative). For example, classifying emails as spam or not spam based on features such as the presence of certain keywords, email length, and sender information.

2. **Linear Support Vector Machine (SVM)**: SVM is a popular linear classification algorithm that aims to find the hyperplane that maximally separates the classes while minimizing the classification error. SVM is widely used for tasks such as text classification, image recognition, and bioinformatics.

3. **Logistic Regression**: Despite its name, logistic regression is a linear classification algorithm used for binary classification. It models the probability of a data point belonging to a certain class using a logistic function and assigns the data point to the class with the highest probability. Logistic regression is commonly used in medical diagnosis, marketing, and credit risk analysis.

4. **Multi-class Classification**: Linear classification can also be extended to multi-class classification problems, where there are more than two classes. One approach is to use multiple binary classifiers (one for each class) and combine their outputs using techniques like one-vs.-all or one-vs.-one. For example, classifying images of digits into one of the ten digits (0-9) based on pixel intensities.

Linear classification is a powerful and widely used technique in machine learning due to its simplicity and interpretability. However, it assumes that the classes can be separated by a linear boundary, which may not always be the case in practice.

# Chapter No.: 4

## 4.1 Basics of NumPy Arrays

[NumPy](https://www.geeksforgeeks.org/python-numpy/) stands for Numerical Python. It is a Python library used for working with an array. In Python, we use the list for the purpose of the array but it’s slow to process. NumPy array is a powerful N-dimensional array object and its use in linear algebra, Fourier transform, and random number capabilities. It provides an array object much faster than traditional Python lists.

### Types of Array

1. One Dimensional Array
2. Multi-Dimensional Array

### One Dimensional Array

A one-dimensional array is a type of linear array.

![](image_rsrc9TT.jpg)

**One Dimensional Array**

**Example:**

```python
# importing numpy module
import numpy as np
# creating list
list_1 = [1, 2, 3, 4]
# creating numpy array
sample_array = np.array(list_1)
print("List in python : ", list_1)
print("Numpy Array in python :", sample_array)
```

**Output:**

```text
List in python :  [1, 2, 3, 4]
Numpy Array in python : [1 2 3 4]
```

**Check data type for list and array:**

```python
print(type(list_1))
print(type(sample_array))
```

**Output:**

```text
<class 'list'>
<class 'numpy.ndarray'>
```

### Multi-Dimensional Array

Data in multidimensional arrays are stored in tabular form.

![](image_rsrc9TU.jpg)

**Two Dimensional Array**

**Example:**

```python
# importing numpy module
import numpy as np
# creating list
list_1 = [1, 2, 3, 4]
list_2 = [5, 6, 7, 8]
list_3 = [9, 10, 11, 12]
# creating numpy array
sample_array = np.array([list_1, list_2, list_3])
print("Numpy multi dimensional array in python\n", sample_array)
```

**Output:**

```text
Numpy multi dimensional array in python
[[ 1  2  3  4]
 [ 5  6  7  8]
 [ 9 10 11 12]]
```

> **Note:** Use `[ ]` operators inside `numpy.array()` for multi-dimensional arrays.

### Anatomy of an Array

1. **Axis**: The Axis of an array describes the order of the indexing into the array.
   - Axis 0 = one dimensional
   - Axis 1 = Two dimensional
   - Axis 2 = Three dimensional

2. **Shape**: The number of elements along with each axis. It is from a tuple.

**Example:**

```python
# importing numpy module
import numpy as np
# creating list
list_1 = [1, 2, 3, 4]
list_2 = [5, 6, 7, 8]
list_3 = [9, 10, 11, 12]
# creating numpy array
sample_array = np.array([list_1, list_2, list_3])
print("Numpy array :")
print(sample_array)
# print shape of the array
print("Shape of the array :", sample_array.shape)
```

**Output:**

```text
Numpy array:
[[ 1  2  3  4]
 [ 5  6  7  8]
 [ 9 10 11 12]]
Shape of the array: (3, 4)
```

**Example:**

```python
import numpy as np
sample_array = np.array([[0, 4, 2], [3, 4, 5], [23, 4, 5], [2, 34, 5], [5, 6, 7]])
print("shape of the array :", sample_array.shape)
```

**Output:**

```text
shape of the array: (5, 3)
```

3. **Rank**: The rank of an array is simply the number of axes (or dimensions) it has.
   - The one-dimensional array has rank 1.
     ![](image_rsrc9TT.jpg)
     **Rank 1**
   - The two-dimensional array has rank 2.
     ![](image_rsrc9TU.jpg)
     **Rank 2**

4. **Data type objects (dtype)**: Data type objects (dtype) is an instance of `numpy.dtype` class. It describes how the bytes in the fixed-size block of memory corresponding to an array item should be interpreted.

**Example:**

```python
# Import module
import numpy as np
# Creating the array
sample_array_1 = np.array([[0, 4, 2]])
sample_array_2 = np.array([0.2, 0.4, 2.4])
# display data type
print("Data type of the array 1 :", sample_array_1.dtype)
print("Data type of array 2 :", sample_array_2.dtype)
```

**Output:**

```text
Data type of the array 1: int32
Data type of array 2: float64
```

### Some Different Ways of Creating NumPy Array
