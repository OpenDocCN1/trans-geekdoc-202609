
Listing 2.11 displays the contents of np2array2.py that illustrates how to compute exponents of the elements in a NumPy array.

# LISTING 2.11: np2array2.py

```python
import numpy as np

# -1 = "the last element in ..." (row or col)

arr1 = np.array([[1,2,3], (4,5,6), (7,8,9), (10,11,12]])
print('arr1:', arr1)
print('arr1[-1,]:', arr1[-1,:])
print('arr1[:-1]:', arr1[:-1,:])
print('arr1[-1:-1]:', arr1[-1:-1])
```

Listing 2.11 contains a NumPy array called by four print statements, each of which displays a different subrange of values in arr1. The output from launching Listing 2.11 is:

```
'arr1': array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9],
       [10, 11, 12]])
'arr1[-1,]:', array([10, 11, 12])
'arr1[:-1]:', array([[3, 6, 9]])
'arr1[-1:-1]:', array([[12]]))
```

## OTHER USEFUL NUMPY METHODS

In addition to the NumPy methods that you saw in the code samples prior to this section, the following (often intuitively-named) NumPy methods are also very useful.

- The method np.zeros() initializes an array with 0 values.
- The method np.ones() initializes an array with 1 values.
- The method np.empty() initializes an array with 0 values.
- The method np.arange() provides a range of numbers:
- The method np.shape() displays the shape of an object:
- The method np.reshape() is very useful!
- The method np.linspace() is useful in regression.
- The method np.mean() computes the mean of a set of numbers:
- The method np.std() computes the standard deviation of a set of numbers:

Although the np.zeros() and np.empty() both initialize a 2D array with 0, np.zeros() requires less execution time. You could also use np.full(size, 0), but this method is the slowest of all three methods.

The reshape() method and the linspace() method are very useful for changing the dimensions of an array and generating a list of numeric values, respectively. The reshape() method often appears in TensorFlow code, and the linspace() method is useful for generating a set of numbers in linear regression (discussed in Chapter 4). The mean() and std() methods are useful for calculating the mean and the standard deviation of a set of numbers. For example, you can use these two methods in order to resize the values in a Gaussian distribution so that their mean is 0 and the standard deviation is 1. This process is called standardizing a Gaussian distribution.

## ARRAYS AND VECTOR OPERATIONS

Listing 2.12 displays the contents of array-vector.py that illustrates how to perform vector operations on the elements in a NumPy array.

# LISTING 2.12: array-vector.py

```python
import numpy as np

a = np.array([[1,2], [3, 4]])
b = np.array([[5,6], [7,8]])

print('a: ', a)
print('b: ', b)
print('a + b: ', a+b)
print('a - b: ', a-b)
print('a * b: ', a*b)
print('a / b: ', a/b)
print('b / a: ', b/a)
print('a.dot(b):', a.dot(b))
```

Listing 2.12 contains two NumPy arrays called a and b followed by eight print statements, each of which displays the result of "applying" a different arithmetic operation to the NumPy arrays a and b. The output from launching Listing 2.12 is here:

```
'a : , array([[1, 2], [3, 4]])
'b : , array([[5, 6], [7, 8]])
'a + b: , array([[6, 8], [10, 12]])
'a - b: , array([[-4, -4], [-4, -4]])
'a * b: , array([[5, 12], [21, 32]])
'a / b: , array([[0, 0], [0, 0]])
'b / a: , array([[5, 3], [2, 2]])
'a.dot(b):', array([[19, 22], [43, 50]])
```

## NUMPY AND DOT PRODUCTS (1)

Listing 2.13 displays the contents of dotproduct1.py that illustrates how to perform the dot product on the elements in a NumPy array.

# LISTING 2.13: dotproduct1.py

```python
import numpy as np

a = np.array([1,2])
b = np.array([2,3])

dot2 = 0
for e,f in zip(a,b):
    dot2 += e*f

print('a:', a)
print('b:', b)
print('a*b:', 'a*b')
print('dot1:', a.dot(b))
print('dot2:', dot2)
```

Listing 2.13 contains two NumPy arrays called by a simple loop that computes the dot product of a and b. The next section contains five print statements that display the contents of a and b, their inner product that is calculated in three different ways. The output from running Listing 2.13 is here:

```
('a:', 'array([1, 2])')
('b:', 'array([2, 3])')
('a*b:', 'array([2, 6])')
('dot1:', 8)
('dot2:', 8)
```

## NUMPY AND DOT PRODUCTS (2)

NumPy arrays support a "dot" method for calculating the inner product of an array of numbers, which uses the same formula you use for calculating the inner product of a pair of vectors. Listing 2.14 displays the contents of dotproduct2.py that illustrates how to calculate the dot product of two NumPy arrays.

# LISTING 2.14: dotproduct2.py

```python
import numpy as np

a = np.array([1,2])
b = np.array([2,3])

print('a:', a)
print('b:', b)
print('a*b:', 'a*b')
print('dot1:', a.dot(b))
print('dot2:', dot2)
```

Listing 2.14 contains two NumPy arrays called a and b followed by five print statements that display the contents of a and b, their inner product that is calculated in three different ways. The output from running Listing 2.14 is here:

```
('a:', 'array([1, 2])')
('b:', 'array([2, 3])')
('a*b:', 'array([2, 6])')
('dot1:', 8)
('dot2:', 8)
```
