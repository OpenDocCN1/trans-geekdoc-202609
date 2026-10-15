
```python
tensor = tensor.to(torch.int32)

print("\nAfter Changing Data Type to int32:")

print(tensor)

print("Data Type: ", tensor.dtype)

# Changing tensor data type to boolean

tensor = tensor.to(torch.bool)

print("\nAfter Changing Data Type to boolean:")

print(tensor)

print("Data Type: ", tensor.dtype)
```

The output will be:

```
tensor([[1., 1.],
        [1., 1.],
        [1., 1.]])
Data Type: torch.float32

After Changing Data Type to float64:
tensor([[1., 1.],
        [1., 1.],
        [1., 1.]], dtype=torch.float64)
Data Type: torch.float64

After Changing Data Type to int32:
tensor([[1, 1],
        [1, 1],
        [1, 1]], dtype=torch.int32)
Data Type: torch.int32

After Changing Data Type to boolean:
tensor([[True, True],
        [True, True],
        [True, True]])
Data Type: torch.bool
```

It's also worth mentioning that PyTorch provides a function to create a tensor of a specific type, for example: `torch.zeros(3, 2, dtype=torch.int32)`. It's also crucial to ensure tensors used in calculations are of the same type, as PyTorch does not perform implicit type conversion.

Understanding and properly managing tensor data types is an essential aspect of developing robust and efficient deep learning models in PyTorch.

## Standard Arithmetic Operations

We will see how to perform basic arithmetic operations on tensors. We will cover addition, subtraction, multiplication, and division operations.

Firstly, we will create two tensors of the same shape:

```python
# Import PyTorch
import torch

# Create two tensors
tensor1 = torch.tensor([1, 2, 3, 4], dtype=torch.float32)
tensor2 = torch.tensor([5, 6, 7, 8], dtype=torch.float32)
print("Tensor 1:", tensor1)
print("Tensor 2:", tensor2)
```

Output:

```
Tensor 1: tensor([1., 2., 3., 4.])
Tensor 2: tensor([5., 6., 7., 8.])
```

### Addition

```python
# Addition
result = tensor1 + tensor2
print("Addition Result: ", result)
```

Output:

```
Addition Result: tensor([ 6.,  8., 10., 12.])
```

### Subtraction

```python
# Subtraction
result = tensor1 - tensor2
print("Subtraction Result: ", result)
```

Output:

```
Subtraction Result: tensor([-4., -4., -4., -4.])
```

### Multiplication

```python
# Multiplication (Element-wise)
result = tensor1 * tensor2
print("Multiplication Result: ", result)
```

Output:

```
Multiplication Result: tensor([ 5., 12., 21., 32.])
```

### Division

```python
# Division
result = tensor1 / tensor2
print("Division Result: ", result)
```

Output:

```
Division Result: tensor([0.2000, 0.3333, 0.4286, 0.5000])
```

Please be informed that the operations are element-wise, meaning they are applied on corresponding elements of the two tensors.

These standard operations are fundamental for manipulating tensors and implementing various mathematical models, especially in the fields of machine learning and deep learning. Next, we'll get into more complex operations and explore how these basic operations can be combined to implement more complex computations.

## Tensor Manipulation

Tensor manipulation in PyTorch typically involves operations like reshaping, slicing, and joining tensors. We will delve into each of these topics.

### Reshaping Tensors

Reshaping tensors is a common operation, which allows us to restructure our data to have different numbers of dimensions or different sizes for each dimension.

We will create a tensor and then reshape it:

```python
# Import PyTorch
import torch

# Create a tensor
tensor = torch.arange(9)

print("Original Tensor:")

print(tensor)

# Reshape the tensor

reshaped_tensor = tensor.view(3, 3)

print("\nReshaped Tensor:")

print(reshaped_tensor)
```

Output:

```
Original Tensor:
tensor([0, 1, 2, 3, 4, 5, 6, 7, 8])

Reshaped Tensor:
tensor([[0, 1, 2],
        [3, 4, 5],
        [6, 7, 8]])
```

### Joining Tensors

PyTorch provides several methods to combine tensors, such as `torch.cat()` and `torch.stack()`. We will use `torch.cat()` to concatenate two tensors along a given dimension:

```python
# Create two tensors
tensor1 = torch.tensor([1, 2, 3])
tensor2 = torch.tensor([4, 5, 6])

# Concatenate the tensors along dimension 0
concatenated_tensor = torch.cat((tensor1, tensor2))

print("\nConcatenated Tensor:")
print(concatenated_tensor)
```

Output:

```
Concatenated Tensor:
tensor([1, 2, 3, 4, 5, 6])
```

These operations are foundational for tensor manipulation. Mastery of these concepts will enable you to effectively work with tensors and prepare your data for deep learning models.

## Matrix Multiplication

In PyTorch, you can perform matrix multiplication using the `torch.matmul()` function or the `@` operator. Both of these methods check the dimensionality of the tensors and apply the appropriate multiplication operation (element-wise multiplication for 1D tensors, matrix multiplication for 2D tensors, batched matrix multiplication for 3D tensors).

We will create two matrices and perform a matrix multiplication operation.

```python
# Import PyTorch
import torch

# Create two 2D tensors (matrices)
matrix1 = torch.tensor([[1, 2], [3, 4]])
matrix2 = torch.tensor([[5, 6], [7, 8]])

print("Matrix 1:")
print(matrix1)

print("\nMatrix 2:")
print(matrix2)

# Matrix multiplication using torch.matmul()
result = torch.matmul(matrix1, matrix2)

print("\nMatrix Multiplication Result using torch.matmul():")
print(result)

# Matrix multiplication using @ operator
result = matrix1 @ matrix2

print("\nMatrix Multiplication Result using @ operator:")
print(result)
```

Output:

```
Matrix 1:
tensor([[1, 2],
        [3, 4]])

Matrix 2:
tensor([[5, 6],
        [7, 8]])

Matrix Multiplication Result using torch.matmul():
tensor([[19, 22],
        [43, 50]])

Matrix Multiplication Result using @ operator:
tensor([[19, 22],
        [43, 50]])
```

The result of the multiplication operation is calculated by the dot product of rows from the first matrix and columns from the second matrix. This operation is fundamental in linear algebra and is frequently used in deep learning, for instance, when propagating inputs through the layers of a neural network.

When multiplying matrices, it is important to keep in mind that the number of rows in the second matrix must be equal to the number of columns in the first matrix.

## Manage Tensor Shape Errors

In PyTorch, dealing with tensor shape errors often requires understanding the nature of the operation you're performing and the dimensionality of your tensors. Below are a few common cases where you might encounter shape errors:

If you're doing matrix multiplication, the number of columns in the first matrix must equal the number of rows in the second matrix. If this condition is not satisfied, you'll encounter a size mismatch error.

For example:

```python
matrix1 = torch.rand(2, 3)
matrix2 = torch.rand(2, 3)
result = torch.matmul(matrix1, matrix2)  # This will raise a size mismatch error
```

In the above example, reshaping or transposing `matrix2` will resolve the issue:

```python
matrix2 = matrix2.t()  # Transpose the matrix
result = torch.matmul(matrix1, matrix2)  # This will not raise an error
```

### Element-wise Operations

If you're doing element-wise operations (like addition, subtraction, etc.), the tensors involved should have the same shape. PyTorch does support broadcasting (a concept borrowed from NumPy), which allows for binary operations on tensors of different sizes, but there are rules to this as well.

For example:

```python
tensor1 = torch.rand(2, 3)
tensor2 = torch.rand(2, 2)
result = tensor1 + tensor2  # This will raise a size mismatch error
```

In the above case, ensuring both tensors have the same shape will fix the error.

### Reshaping Tensors

If you're reshaping a tensor, the total number of elements before and after the reshape operation should remain the same. If this isn't the case, you'll encounter an error.

For example:

```python
tensor = torch.rand(2, 3)
reshaped_tensor = tensor.view(2, 4)  # This will raise an error
```

In the above case, ensuring the new shape is compatible with the number of elements in the tensor will solve the problem.
