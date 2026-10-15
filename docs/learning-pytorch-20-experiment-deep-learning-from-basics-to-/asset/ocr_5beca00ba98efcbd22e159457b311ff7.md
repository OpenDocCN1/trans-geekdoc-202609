# Changing Shape of Tensor

In PyTorch, reshape() is used to change the shape of a tensor without changing its data. This operation is commonly used when you want to rearrange the dimensions of your data to match the input expectations of a model.

```
# Import PyTorch

import torch

# Create a tensor

tensor = torch.arange(1, 9)

print("Original Tensor:")

print(tensor)

# Reshape the tensor
```