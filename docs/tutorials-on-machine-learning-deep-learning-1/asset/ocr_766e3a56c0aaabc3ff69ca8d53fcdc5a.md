Some real life examples converting tensors to numpy array:

# Example: Shared storage

PyTorch tensor residing on CPU shares the same storage as numpy array na`

```
import torch
a = torch.ones((1,2))
print(a)
a = a.numpy()
na[0][0]=10
print(na)
print(a)
```

Output:

```
tensor([[1., 1.]]])
[[10., 1.]]
tensor([[10., 1.]])
```

# Example: Eliminate effect of shared storage, copy numpy array first

To avoid the effect of shared storage we use copy() the numpy array na to a new numpy array. Numpy copy() method creates the new separate storage.

```
import torch
a = torch.ones((1,2))
print(a)
a = a.numpy()
ac = na.copy()
ac[0][0]=10
print(nac)
print(na)
print(a)
```

Output:

```
tensor([[1., 1.]])
[[10., 1.]]
tensor([[1., 1.]])
```

Now, the nac numpy array will be altered with the line nac[0][0]=10, na and a will remain as is.

# Example: CPU tensor with requires_grad=True

```
import torch
a = torch.ones((1,2)), requires_grad=True
print(a)
a = a.detach().numpy()
a[0][0]=10
print(na)
print(a)
```

Output:

```
tensor([[1., 1.]]), requires_grad=True)
[[10., 1.]]
tensor([[10., 1.]]), requires_grad=True)
```

Here we call:

```
na = a.numpy()
```