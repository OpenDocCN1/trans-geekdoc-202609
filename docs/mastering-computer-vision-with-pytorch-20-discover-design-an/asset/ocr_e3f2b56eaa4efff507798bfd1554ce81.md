Here's a simple example:

```
# Compute Gradient
x = torch.tensor([2.0, 3.0], requires_grad=True)
y = x * 2
z = y.mean()
z.backward() # Compute gradients
print(x.grad) # Outputs: tensor([2., 2.])
```

# Accumulating Gradients

Subsequent backward operations will accumulate gradients in the .grad attribute, rather than overwriting them. This accumulation is crucial for certain types of models and operations.

```
# Accumulating Gradients
y = x * 2
y.backward(torch.tensor([1.0, 1.0])) # Using a vector for
gradient scaling
print(x.grad) # Outputs: tensor([2., 2.])

# Doing another operation
y = x * 3
y.backward(torch.tensor([1.0, 1.0]))
print(x.grad) # Outputs: tensor([5., 5.]) because gradients
accumulate
```

# Non-Scalar Backward Operations

The .backward() operation expects a scalar, that is, a tensor with a single value. If it’s not a scalar, you need to specify the `gradient` argument, which is a tensor of the same shape, typically representing the gradient of a scalar function with respect to the non-scalar tensor.

```
# Non-Scalar Backward Operations
y = x * 2
# This would raise an error since y is not a scalar:
# y.backward()
```