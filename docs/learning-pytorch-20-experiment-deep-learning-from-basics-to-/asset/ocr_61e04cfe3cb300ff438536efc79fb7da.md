# Squeezing a Tensor

The squeeze() function removes the dimensions or axes that have a length of one from the tensor. This operation is useful to transform a 2D tensor with one dimension of length 1 into a 1D tensor, or to remove unnecessary dimensions when you have a batch size of 1.

```
# Create a tensor of size (1,3)

tensor = torch.zeros((1, 3))

print("Original Tensor:")

print(tensor)

print("Shape:", tensor.shape)

# Squeeze the tensor

squeezed_tensor = tensor.squeeze()
```