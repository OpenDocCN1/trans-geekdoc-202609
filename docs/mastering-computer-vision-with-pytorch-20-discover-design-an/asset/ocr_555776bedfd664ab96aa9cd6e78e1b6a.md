# Transpose

Flips a matrix over its diagonal.

```
# PyTorch
matrix = torch.tensor([[1, 2, 3], [4, 5, 6]])
transposed = torch.t(matrix)
print(transposed) # Outputs: tensor([[1, 4], [2, 5], [3, 6]])
```

Matrix operations can be visualized as transforming a grid of numbers. The transpose, for example, can be imagined as flipping a book’s page along its center binding.

Matrix operations are at the core of linear transformations in neural networks. Operations like matrix multiplication become increasingly important in layers like fully connected or dense layers in neural nets.

# Reshaping Operations

One of PyTorch’s strengths is the flexibility in manipulating tensor shapes, crucial for neural network layers that expect inputs of specific dimensions.

# View and Reshape

Both `view` and `reshape` methods allow you to change the shape of a tensor without altering its data. However, there is a subtle difference between them in terms of memory usage:

**view**: This method returns a reshaped tensor that shares the same memory as the original tensor, which makes it more memory-efficient. It requires the tensor to be contiguous in memory, meaning the elements are stored in an unbroken sequence. If the tensor isn’t contiguous, you may need to call `.contiguous()` before using `view`.

**reshape**: This method can return either a `view` or a copy of the original tensor. If possible, it will return a `view` for efficiency.