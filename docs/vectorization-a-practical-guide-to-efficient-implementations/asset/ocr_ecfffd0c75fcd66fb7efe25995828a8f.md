![](bbox=[0.136, 0.11, 0.88, 0.225])

Figure 5.4 Boolean tensor masking and compressing.

a rectangular matrix of size (N, N-1). We can do this using the following procedure in PyTorch (see also Figure 5.4):

```
```python
import torch
X = torch.arange(25).reshape(5, 5) + 1
mask = torch.ones_like(X, dtype=bool)
mask.fill_diagonal_(False)
X_masked = torch.masked_select(X, mask).reshape(5, 4)
```
```

The equivalent operation can be implemented in Tensorflow but not using NumPy's `np.compress` since the `mask` is required to be 1D and operates along a certain dimension of the input tensor X.

# 5.1.6 Case Study: Top-k Masking

Suppose we have a batch of arrays (e.g. a 2D matrix). For each array, we would like to retain only the top three values, while setting all the other entries to be zeros (see Figure 5.5a). We can do this by creating a binary mask and applying the binary mask to the original matrix. The binary mask should have 1s at indices where the value of the original matrix is among the top three values, and 0s otherwise (see Figure 5.5b).

The code snippet below implements the top-k masking operation using NumPy.

```
```python
import numpy as np
def top_k_masking(y, top_k, masked_value=0):
    """Mask the input and retain only top_k values."""
    # Get top k indices
    index = np.argsort(y) [..., -top_k:][..., ::-1]
    # Initialize the zeros mask
    mask = np.zeros_like(y)
    # scatter the indices (in-place)
    np.put_along_axis(mask, index, 1, axis=-1)
    # Adjust values such that the masked elements
```
```