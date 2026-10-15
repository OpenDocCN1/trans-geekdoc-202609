# Tensor Manipulation

Tensor manipulation in PyTorch typically involves operations like reshaping, slicing, and joining tensors. We will delve into each of these topics.

# Reshaping Tensors

Reshaping tensors is a common operation, which allows us to restructure our data to have different numbers of dimensions or different sizes for each dimension.

We will create a tensor and then reshape it:

```
# Import PyTorch
import torch

# Create a tensor
tensor = torch.arange(9)
```