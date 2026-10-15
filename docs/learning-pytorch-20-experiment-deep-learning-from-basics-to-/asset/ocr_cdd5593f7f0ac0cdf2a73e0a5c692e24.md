# Permuting a Tensor

The permute() function rearranges the original dimensions of the tensor according to the input specified. It's often used to change the order of the dimensions or axes.

```
# Create a tensor of size (2, 3, 4)

tensor = torch.zeros((2, 3, 4))

print("\nOriginal Tensor Shape:", tensor.shape)

# Permute the dimensions of the tensor

permuted_tensor = tensor.permute(2, 0, 1)

print("Permuted Tensor Shape:",
permuted_tensor.shape)
```

Output: