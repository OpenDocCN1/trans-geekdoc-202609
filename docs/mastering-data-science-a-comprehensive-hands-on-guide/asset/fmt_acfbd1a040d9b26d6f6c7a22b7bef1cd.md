
## 5.4.2 Array Attributes

NumPy arrays provide several useful attributes to understand and interact with their properties. Here are the key attributes and what they represent:

### .shape

Describes the dimensions of the array, represented as a tuple. It specifies the number of elements along each dimension (e.g., rows and columns for a 2D array).

Example:
```
import numpy as np

array = np.array([[1, 2, 3], [4, 5, 6]])

print(array.shape)  # Output: (2, 3) -> 2 rows, 3 columns
```

### .size

Returns the total number of elements in the array. This is the product of all dimensions in the array.

Example:
```
array = np.array([[1, 2, 3], [4, 5, 6]])

print(array.size)  # Output: 6
```

### .ndim

Indicates the number of dimensions (axes) of the array.

Example:
```
array_1d = np.array([1, 2, 3])
array_2d = np.array([[1, 2], [3, 4]])

print(array_1d.ndim)  # Output: 1 (1D array)
print(array_2d.ndim)  # Output: 2 (2D array)
```

### .dtype

Provides the data type of the elements in the array (e.g., int, float, etc.).

Example:
```
array = np.array([1.5, 2.3, 3.7])

print(array.dtype)  # Output: float64
```

## 5.4.3 Reshaping and Flattening Arrays

Reshaping and flattening are two important techniques in NumPy that allow you to manipulate the structure of arrays. These operations are useful when preparing data for analysis or machine learning models.

### Reshaping Arrays (`reshape()`)

The `reshape()` method changes the shape of an array without altering its data. You can specify the new shape as a tuple, ensuring that the total number of elements remains constant.

Syntax: `array.reshape(new_shape)`

Examples:
```
import numpy as np

# Original array
array = np.array([1, 2, 3, 4, 5, 6])

# Reshape into a 2x3 array
reshaped_array = array.reshape(2, 3)

print(reshaped_array)
# Output:
# [[1 2 3]
#  [4 5 6]]

# Reshape into a 3x2 array
reshaped_array = array.reshape(3, 2)

print(reshaped_array)
# Output:
# [[1 2]
#  [3 4]
#  [5 6]]
```

Key Point:

The new shape must have the same total number of elements as the original array. Use `-1` to let NumPy infer one dimension automatically:
```
reshaped_array = array.reshape(3, -1)  # NumPy determines the number of columns
print(reshaped_array)
```

### Flattening Arrays (`ravel()`)

The `ravel()` method flattens a multi-dimensional array into a one-dimensional array. It returns a flattened view, meaning changes to the result may affect the original array.

Syntax: `array.ravel()`

Example:
```
# 2D array
array = np.array([[1, 2, 3], [4, 5, 6]])

# Flatten the array
flattened_array = array.ravel()

print(flattened_array)
# Output: [1 2 3 4 5 6]
```

Key Point: `ravel()` is faster than `flatten()` for large arrays as it tries to avoid copying data.

Summary

- `reshape()`: Used to modify the shape of an array (e.g., converting a 1D array to 2D).
- `ravel()`: Used to flatten a multi-dimensional array into a 1D array.

These operations are essential in data preprocessing, particularly when adapting data to the required input format for machine learning models or numerical computations.

## 5.5 Indexing and Slicing

Indexing and slicing are fundamental operations in NumPy that enable efficient data access, manipulation, and filtering within arrays.

### Accessing Array Elements

Indexing in 1D Arrays: Access elements using their position, starting from 0. For example, `array[2]` retrieves the third element of a 1D array.

Indexing in 2D Arrays: Use two indices to access elements, where the first index specifies the row, and the second specifies the column. For example, `array[1, 2]` accesses the element in the second row and third column.

Indexing in Multi-Dimensional Arrays: Extend the concept by providing indices for each dimension. For example, `array[0, 1, 2]` accesses a specific element in a 3D array.

### Slicing Arrays

Extracting Subarrays Using Slicing: Slicing extracts a subset of elements using the format `start:end:step`. For instance, `array[1:4]` selects elements from index 1 to 3 (end is exclusive).

Step Slicing: Specify a step to skip elements. For example, `array[0:6:2]` retrieves every second element between indices 0 and 5.

Reverse Slicing: Use negative indices or a negative step to reverse arrays. For instance, `array[::-1]` reverses the entire array.

### Boolean Indexing

Creating Masks for Filtering Arrays: Apply a condition to the array to create a Boolean mask. For example, `array > 5` creates a mask indicating which elements are greater than 5.

Using Conditions to Select Elements: Apply the mask to the array to retrieve specific elements. For instance, `array[array > 5]` filters out all elements greater than 5.

### Fancy Indexing

Indexing with Integer Arrays: Use lists or arrays of integers to access multiple elements simultaneously. For example, `array[[0, 2, 4]]` retrieves the elements at indices 0, 2, and 4.

Multi-Dimensional Fancy Indexing: Combine arrays of row and column indices to select specific elements. For instance, `array[[0, 1], [2, 3]]` retrieves elements at positions (0, 2) and (1, 3).

Indexing and slicing techniques make NumPy arrays versatile and powerful, enabling efficient data selection and manipulation for diverse applications in data science.

## 5.6 Array Operations

### Arithmetic Operations

NumPy supports element-wise arithmetic operations, making it easy to perform addition, subtraction, multiplication, and division directly on arrays. For example:
```
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(a + b)  # [5, 7, 9]
print(a * b)  # [4, 10, 18]
```

Broadcasting allows operations between arrays of different shapes by automatically expanding their dimensions to match. For instance, adding a 1D array to a 2D array applies the operation across rows or columns based on their alignment.

### Aggregation Functions

NumPy provides a variety of functions for summarizing data:

- `np.sum()`: Calculates the total sum of array elements.
- `np.mean()`: Computes the average.
- `np.median()`: Finds the middle value in sorted data.
- `np.std()` and `np.var()`: Calculate the standard deviation and variance, respectively.
- `np.min()` and `np.max()`: Retrieve the minimum and maximum values in an array.

Example:
```
data = np.array([1, 2, 3, 4, 5])

print(np.sum(data))      # 15
print(np.mean(data))     # 3.0
print(np.min(data))      # 1
print(np.max(data))      # 5
```

### Matrix Operations

NumPy is well-suited for matrix computations:

Dot Product: Calculated using `np.dot()` or the `@` operator.
```
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

print(np.dot(A, B))  # Dot product
print(A @ B)         # Alternative syntax
```

Transpose: Use `.T` to transpose a matrix.
```
print(A.T)  # [[1, 3], [2, 4]]
```

Determinants and Inverses: Utilize the `np.linalg` module for advanced operations.
```
print(np.linalg.det(A))  # Determinant of A
print(np.linalg.inv(A))  # Inverse of A
```

### Element-wise Comparisons

NumPy provides comparison functions to perform element-wise evaluations, resulting in boolean arrays:

- `np.equal()`: Checks equality.
- `np.greater()`: Compares if elements are greater.
- `np.less()`: Checks if elements are smaller.

Example:
```
a = np.array([1, 2, 3])
b = np.array([3, 2, 1])

print(np.equal(a, b))   # [False, True, False]
print(np.greater(a, b)) # [False, False, True]
print(np.less(a, b))    # [True, False, False]
```

These operations are fundamental to manipulating and analyzing data with NumPy, making it a cornerstone library in data science.

## 5.7 Advanced Array Manipulation

### Stacking and Splitting Arrays

Horizontal Stacking (`np.hstack()`): Combines arrays side-by-side.
```
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(np.hstack((a, b)))  # [1, 2, 3, 4, 5, 6]
```
