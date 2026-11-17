```
print(sum_tensors, product_tensors)
```

# Matrix Operations

Dives into linear algebra operations.

```
# Matrix operations
import torch
x = torch.tensor([[1, 2], [3, 4]])
y = torch.tensor([[5, 6], [7, 8]])
matmul_result = torch.matmul(x, y)
print(matmul_result)
```

# Reshaping Tensors

The tensors can be manipulated in several ways to change/reshape them.

# View and Reshape

Both methods allow you to change the shape of a tensor.

```
# Reshape tensors
import torch
x = torch.arange(10)
reshaped_tensor = x.view(2, 5)
print(reshaped_tensor)
reshaped_tensor_alt = x.reshape(5, 2)
print(reshaped_tensor_alt)
```

# Squeeze and Unsqueeze

Manipulates the dimensions of tensors.

```
# Squeeze & Unsqueeze tensors
import torch
tensor = torch.tensor([[1, 2, 3]])
squeezed_tensor = tensor.squeeze()
print(squeezed_tensor.shape)
```