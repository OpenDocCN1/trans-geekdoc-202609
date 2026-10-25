
![](img/194138d45b566d0634bfa2025ddf48f7_20_0.png)

**Figure 1.1:** Select “Add Anaconda3 to my PATH environment variable” during installation.

![](img/194138d45b566d0634bfa2025ddf48f7_20_1.png)

**Figure 1.2:** Computing environment by Jupyter Notebook.

![](img/194138d45b566d0634bfa2025ddf48f7_21_0.png)

**Figure 1.3:** Go to new → Python 3 to create a new programming script.

```python
import numpy as np
```

**Figure 1.4:** Import numpy library as np.

are created based on NumPy library. The NumPy module can be imported as “np” (different keywords can be chosen), and after importing, it can be used to call any array by typing “np.”

### 1.4.1 IMPORTING NUMPY AND BASIC COMMANDS

Let us use some basic functionalities of NumPy. First, open Jupyter Notebook (Anaconda3) from the search menu and create a new “Python 3” file (Fig. 1.3).

Type the following command to import the NumPy library as “np” and press “Shift+Enter” key to execute the line (Fig. 1.4).

Now let’s say we have a list of data, A = [1, 2, 3, 4, 5, 6, 7, 8, 9], and we would like to convert it to a 3 by 3 matrix. We may assign it to another array variable B. Note that in Fig. 1.5, the output “type” of A is a list, but the output “type” of B is a numpy.ndarray.

Now, we can use the “reshape” command to make a 3 by 3 matrix from B, but it will not change the original dimension of B, as shown in Fig. 1.6. If we want to change the original dimension, we will need to assign it to another variable, or B itself.

In Fig. 1.7, array B is assigned again using the reshape command. Here, the original data shape of B also changed to 3 by 3.

```python
In [2]: A = [1,2,3,4,5,6,7,8,9]

In [3]: type(A)
Out[3]: list

In [4]: B = np.array(A)

In [5]: type(B)
Out[5]: numpy.ndarray
```

**Figure 1.5:** Using numpy for converting python list to array type.

```python
In [6]: B.reshape(3,3)
Out[6]: array([[1, 2, 3],
              [4, 5, 6],
              [7, 8, 9]])

In [7]: print(B)
[1 2 3 4 5 6 7 8 9]
```

**Figure 1.6:** Reshaping array B without changing its data.

```python
In [8]: B = B.reshape(3,3)

In [9]: print(B)
[[1 2 3]
 [4 5 6]
 [7 8 9]]
```

**Figure 1.7:** Use reshape to change the original array dimension.

### 1.4.2 CHANGING ARRAY ELEMENTS

Changing element values of an array can be useful when we deal with a multi-dimensional large dataset. But here, we are providing an example on the small array, B (Fig. 1.7). Let’s say we want to change all the elements of row two to zeros.

Note that a Python list, as well as NumPy array, always starts from 0, i.e., in the 3 by 3 matrix B, we have rows from 0 to 2 (0,1,2 → 3 rows), and columns from 0 to 2 (0,1,2 → 3 columns). So when we try to access row 2, we will use B[1, :], as shown in Fig. 1.8. Here, ":" denotes that we want to reassign all the values (row 1 and column all).

Now, let’s try to update only one element located at row 3 and column 3, from 9 to 999. To access this location in NumPy, we will use [2, 2], as shown in Fig. 1.9.

```python
In [10]: B[1, :] = 0

In [11]: print(B)

[[1 2 3]
 [0 0 0]
 [7 8 9]]
```

**Figure 1.8:** Reassigning row values inside of an array.

```python
In [12]: B[2,2] = 999

In [13]: B

Out[13]: array([[ 1,  2,  3],
                [ 0,  0,  0],
                [ 7,  8, 999]])
```

**Figure 1.9:** Updating only one element of an array located at [2,2].

```python
In [14]: C = np.zeros(10000).reshape(100,100)

In [15]: C

Out[15]: array([[0., 0., 0., ..., 0., 0., 0.],
                [0., 0., 0., ..., 0., 0., 0.],
                [0., 0., 0., ..., 0., 0., 0.],
                ...,
                [0., 0., 0., ..., 0., 0., 0.],
                [0., 0., 0., ..., 0., 0., 0.],
                [0., 0., 0., ..., 0., 0., 0.]])
```

**Figure 1.10:** Creating a 100 by 100 array of zeros using NumPy.

Note that we can also use “B” in the command line instead of “print(B)”, and press “Shift+Enter” from the keyboard to see the array output.

### 1.4.3 CREATING ARRAY WITH SPECIFIC VALUES

We can also create arrays with any specific values. Let’s say we want to create a large array of 100 by 100 elements consists of 0s, and another one with 1s. The functions we could use here are “zeros” and “ones,” respectively (Figs. 1.10 and 1.11).

If a NumPy array has more than 1000 elements, it drops the middle rows and columns from the output display, as shown in Fig. 1.10. For checking the shape of an array, the “.shape” function can be used (Fig. 1.11).

We may also use “ones” or “zeros” and the “reshape” function together in one line. Figure 1.12 shows how to use “ones” and “reshape” functions in one line to create a 100 by 100 array.

```python
In [16]: C.shape

Out[16]: (100, 100)
```

**Figure 1.11:** Using “.shape” function to check an array shape.

```python
In [17]: D = np.ones(10000).reshape(100,100)

In [18]: D

Out[18]: array([[1., 1., 1., ..., 1., 1., 1.],
       [1., 1., 1., ..., 1., 1., 1.],
       [1., 1., 1., ..., 1., 1., 1.],
       ...,
       [1., 1., 1., ..., 1., 1., 1.],
       [1., 1., 1., ..., 1., 1., 1.],
       [1., 1., 1., ..., 1., 1., 1.]])
```

**Figure 1.12:** Using “ones” and “reshape” functions in one line to create a 100 by 100 array.

```python
In [19]: E = np.full((3,10),55)

In [20]: E

Out[20]: array([[55, 55, 55, 55, 55, 55, 55, 55, 55, 55],
       [55, 55, 55, 55, 55, 55, 55, 55, 55, 55],
       [55, 55, 55, 55, 55, 55, 55, 55, 55, 55]])
```

**Figure 1.13:** Using “full” function to create a 3 by 10 array where all elements are 55.

For creating an array filled with a different number (e.g., 55), we may use the “full” function. The following commands in Fig. 1.13 are creating a 3 by 10 array where all elements are 55.

### 1.4.4 BROADCASTING IN NUMPY

If we have arrays with different shapes that don’t allow mathematical operations, then changing the arrays based on the sizes is known as broadcasting. This operation is convenient, but sometimes it may give misleading output. Therefore we have to track the array shapes frequently while doing matrix operations in our programming.

NumPy always tries to perform the broadcasting if the shapes of arrays are different. If we use a scalar or single value, it will be broadcasted as a same shaped array. For example, if we add 5 to E (3 by 10 array in Fig. 1.13), 5 will be broadcasted, and will be added to all the elements of E. This broadcasting operation is shown in Fig. 1.14.

```python
In [21]: E+5
Out[21]: array([[60, 60, 60, 60, 60, 60, 60, 60, 60, 60],
              [60, 60, 60, 60, 60, 60, 60, 60, 60, 60],
              [60, 60, 60, 60, 60, 60, 60, 60, 60, 60]])
```

**Figure 1.14:** Scalar value 5 is added to E (3 by 10 array). Here, 5 is broadcasted and added to all the elements of E.

```python
In [22]: F = np.full((3,1),2)

In [23]: F

Out[23]: array([[2],
              [2],
              [2]])

In [24]: E*F

Out[24]: array([[110, 110, 110, 110, 110, 110, 110, 110, 110, 110],
              [110, 110, 110, 110, 110, 110, 110, 110, 110, 110],
              [110, 110, 110, 110, 110, 110, 110, 110, 110, 110]])
```

**Figure 1.15:** NumPy broadcasting operation during multiplication of two different array sizes.

```python
In [25]: np.dot(E,F)

ValueError                               Traceback (most recent call last)
<ipython-input-25-cbafb301adce> in <module>
----> 1 np.dot(E,F)

<__array_function__ internals> in dot(*args, **kwargs)

ValueError: shapes (3,10) and (3,1) not aligned: 10 (dim 1) != 3 (dim 0)
```

**Figure 1.16:** The NumPy dot multiplication will give an error since the array sizes of E and F are different.

Now let's say we have another array of “2” (Fig. 1.15) whose size is 3 by 1. If we multiply E and F, only the column of F will be broadcasted horizontally to get the multiplication done without any error.

Here, if we want to do the dot multiplication (using np.dot function), we will get an error because the sizes of these two matrices are not aligned (Fig. 1.16).

To fix this error, we have to make sure that the sizes of the matrices are such that actual matrix multiplication is allowed. Therefore, the column size of the first matrix should be equal to
