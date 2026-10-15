# Joining_Tensors

PyTorch provides several methods to combine tensors, such as torch.cat() and torch.stack(). We will use torch.cat() to concatenate two tensors along a given dimension:

```
# Create two tensors

tensor1 = torch.tensor([1, 2, 3])

tensor2 = torch.tensor([4, 5, 6])

# Concatenate the tensors along dimension 0

concatenated_tensor = torch.cat((tensor1, tensor2))

print("\nConcatenated Tensor:")

print(concatenated_tensor)
```

Output:

Concatenated Tensor: