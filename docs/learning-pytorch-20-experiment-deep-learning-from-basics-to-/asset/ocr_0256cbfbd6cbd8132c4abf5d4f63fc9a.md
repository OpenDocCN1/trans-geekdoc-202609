# Un-squeezing a Tensor

unsqueeze() is the inverse operation to squeeze(). It adds a dimension with a length of one at the specified position in the tensor. This is commonly used to increase the dimensionality of your data to match the input requirements of a model.

```
# Unsqueeze the tensor

unsqueezed_tensor =
squeezed_tensor.unsqueeze(dim=0)

print("\nUnsqueezed Tensor:")

print(unsqueezed_tensor)

print("Shape:", unsqueezed_tensor.shape)
```

Output:

Unsqueezed Tensor: