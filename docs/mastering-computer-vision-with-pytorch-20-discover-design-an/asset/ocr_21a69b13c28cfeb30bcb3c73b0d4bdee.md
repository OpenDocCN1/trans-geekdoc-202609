PyTorch will raise an error. For instance, (3, 2) and (3, 3) cannot be broadcast together.

Broadcasting simplifies arithmetic operations across tensors, especially in deep learning, where aligning inputs and outputs across layers is essential. Understanding these rules will make tensor operations smoother and help avoid shape mismatch errors.

# # Arithmetic Operations

These are foundational mathematical operations that you can perform element-wise on tensors.

# ## Addition

PyTorch supports the addition of two tensors of the same shape.

```
```python
# PyTorch
a = torch.tensor([1, 2, 3])
b = torch.tensor([4, 5, 6])
result = torch.add(a, b)
print(result) # Outputs: tensor([5, 7, 9])
```
```

# ## Subtraction

Similar to addition, subtraction is performed element-wise.

```
```python
# PyTorch
a = torch.tensor([1, 2, 3])
b = torch.tensor([4, 5, 6])
result = torch.sub(a, b)
print(result) # Outputs: tensor([-3, -3, -3])
```
```

# ## Multiplication

Element-wise multiplication, not matrix multiplication.

```
```python
# PyTorch
```
```