To illustrate,

```
```
import numpy as np
import torch
x = np.arange(10)
buckets = [0, 3, 6, 9]

# Left-inclusive [1, 1, 1, 2, 2, 2, 3, 3, 3, 4]
indices_np_false = np.digitize(x, buckets, right=False)
indices_torch_true = torch.bucketize(
    torch.tensor(x), torch.tensor(buckets), right=True
)
assert np.allclose(indices_np_false, indices_torch_true)

# Left-exclusive [0, 1, 1, 1, 2, 2, 2, 3, 3, 3]
indices_np_true = np.digitize(x, buckets, right=True)
indices_torch_false = torch.bucketize(
    torch.tensor(x), torch.tensor(buckets), right=False
)
assert np.allclose(indices_np_true, indices_torch_false)
```
```

An alternative operation is `searchsorted` implemented by all three libraries. The following illustrates that these operations are equivalent:

```
```
import numpy as np
import tensorflow as tf
import torch

x = np.arange(10)
buckets = np.array([0, 3, 6, 9])
x_t = torch.tensor(x)
buckets_t = torch.tensor(buckets)

# Left inclusive [1, 1, 1, 2, 2, 2, 3, 3, 3, 4]
res = [
    # using digitize/bucketize
    np.digitize(x, buckets, right=False),
    torch.bucketize(x_t, buckets_t, right=True),
    # using searchsorted
    np.searchsorted(buckets, x, side="right"),
    torch.searchsorted(buckets_t, x_t, side="right"),
    tf.searchsorted(buckets, x, side="right")
]

# Pair-wise comparison
assert all((np.allclose(res[ii], res[ii+1]) for ii in range(len(res)-1]))

# Left exclusive [0, 1, 1, 1, 2, 2, 2, 3, 3, 3]
res = [
```
```