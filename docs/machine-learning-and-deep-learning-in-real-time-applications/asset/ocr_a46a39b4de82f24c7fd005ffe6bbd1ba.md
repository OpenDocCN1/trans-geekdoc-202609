Deep Learning With PyTorch

```
(0, 0, 0, 0),
(0, 0, 0, 0))))
```

# torch.ones(dimension)

This creates a tensor populated with ones of a given dimension.

Example:

```
>>> torch.ones(2, 3)
tensor(((1., 1., 1.),
(1., 1., 1.)))
```

# torch.rand(dimension)

This creates a tensor populated with random digits of given dimension.

Example:

```
>>> torch.rand(2, 3)
tensor(((0.3273, 0.1834, 0.5345),
(0.2946, 0.4208, 0.7635)))
```

The default data type of tensors is torch.float32, which is generally used in deep learning to store information without loss. To change the default data type, an extra parameter is passed as dtype=<data_type>

Example:

```
>>> torch.rand(2,3, dtype=torch.float64)
tensor(((0.3187, 0.7623, 0.3013),
(0.1027, 0.4982, 0.1452)), dtype=torch.float64)
```

# <tensor>.size()

This is used to get the dimension of a declared tensor.

Example:

```
>>> x = torch.rand(2, 3)
>>> x.size()
torch.Size([2, 3))
```

# Integration with NumPy

Conversion between NumPy and PyTorch tensors is shown below: