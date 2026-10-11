
print(`j.shape`)

```
(1, 8)
(9, 8)
(9, 8)
```

With this helper function, it is easy to generate a row-flattened tensor of data blocks from the original data tensor:

```
def im2row_indices(x, kH, kW, S=1, P=0):
    x_padded = np.pad(x, ((0, 0), (0, 0), (P, P), (P, P)), mode='constant')
    k, i, j = get_im2row_indices(x.shape, kH, kW, S, P)
    rows = x_padded[:, k, i, j]      # all blocks of data for each sample
    C = x.shape[1]
    rows = rows.reshape(-1, kH * kW * C) # all data blocks of the 1st sample, all data blocks of the 2nd sample
    return rows
```

Test this function:

```
X = np.arange(N*C*H*W).reshape(N, C, H, W)
X_row = im2row_indices(X, kH, kW, S, P)
print(X)
print(X_row)
```

```
[[[[ 0  1  2  3]
   [ 4  5  6  7 ]
   [ 8  9 10 11]
   [12 13 14 15]]

  [[16 17 18 19]
   [20 21 22 23]
   [24 25 26 27]
   [28 29 30 31]]]

 [[[32 33 34 35]
   [36 37 38 39]
   [40 41 42 43]
   [44 45 46 47]]

  [[48 49 50 51]
   [52 53 54 55]
   [56 57 58 59]
   [60 61 62 63]]]]

[[ 0  1  4  5 16 17 20 21]
 [ 1  2  5  6 17 18 21 22]
 [ 2  3  6  7 18 19 22 23]
 [ 4  5  8  9 20 21 24 25]
 [ 5  6  9 10 21 22 25 26]
 [ 6  7 10 11 22 23 26 27]
 [ 8  9 12 13 24 25 28 29]
 [ 9 10 13 14 25 26 29 30]
 [10 11 14 15 26 27 30 31]
 [32 33 36 37 48 49 52 53]
 [33 34 37 38 49 50 53 54]
 [34 35 38 39 50 51 54 55]
 [36 37 40 41 52 53 56 57]
 [37 38 41 42 53 54 57 58]
 [38 39 42 43 54 55 58 59]
 [40 41 44 45 56 57 60 61]
 [41 42 45 46 57 58 61 62]
 [42 43 46 47 58 59 62 63]]
```

Or conversely, convert the tensor of the data block flattened by row into the shape of the original data tensor.

```
def row2im_indices(rows, x_shape, kH, kW, S=1, P=0):
    N, C, H, W = x_shape
    H_pad, W_pad = H + 2 * P, W + 2 * P
    x_pad = np.zeros((N, C, H_pad, W_pad), dtype=rows.dtype)
    k, i, j = get_im2row_indices(x_shape, kH, kW, S, P)
    rows_reshaped = rows.reshape(N, -1, C * kH * kW)
    np.add.at(x_pad, (slice(None), k, i, j), rows_reshaped)
    if P == 0:
        return x_pad
    return x_pad[:, :, P:-P, P:-P]
```

Test whether this function is consistent with the previous function:

```
import numpy as np

H, W = 4, 4
kH, kW = 2, 2
oH, oW = 3, 3
N, C, S, P = 2, 2, 1, 0
# F = 4
nRow = oH * oW * N
K2C = C * kH * kW
dx_row = X_row.copy()  # np.arange(nRow*K2C).reshape(nRow, K2C)
print("dx_row.shape", dx_row.shape)
# print("dx_row", dx_row)
dx = row2im(dx_row, oH, oW, kH, kW, S)
print("dx.shape", dx.shape)
print("dx[0,0,:,:]", dx[0, 0, :, :])
# dx_row = dx_row.transpose()
dX = row2im_indices(dx_row, (N, C, H, W), kH, kW, S, P)
print("dX.shape", dX.shape)
print("dX[0,0,:,:]", dX[0, 0, :, :])
print(dX)
```

```
dx_row.shape (18, 8)
dx.shape (2, 2, 4, 4)
dx[0,0,:,:] [[ 0.  2.  4.  3.]
 [ 8. 20. 24. 14.]
 [16. 36. 40. 22.]
 [12. 26. 28. 15.]]

dX.shape (2, 2, 4, 4)
dX[0,0,:,:] [[ 0  2  4  3]
 [ 8 20 24 14 ]
 [16 36 40 22]
 [12 26 28 15]]

[[[[ 0  2  4  3]
   [ 8 20 24 14 ]
   [16 36 40 22]
   [12 26 28 15]]

  [[16 34 36 19]
   [40 84 88 46 ]
   [48 100 104 54]
   [28 58 60 31]]]

 [[[32 66 68 35]
   [72 148 152 78]
   [80 164 168 86]
   [44 90 92 47]]

  [[48 98 100 51]
   [104 212 216 110]
   [112 228 232 118]
   [60 122 124 63]]]]
```

With the helper function above that directly flattens multidimensional tensors into matrices (in the file `im2row.py`), you can write a convolution layer based on fast read convolution operations:

```
from Layers import *
from im2row import *

class Conv_fast:
    def __init__(self, in_channels, out_channels, kernel_size, stride=1, padding=0):
        super().__init__()
        self.C = in_channels
        self.F = out_channels
        self.kH = kernel_size
        self.kW = kernel_size
        self.S = stride
        self.P = padding
        # filters is a 3d array with dimensions (num_filters, self.K, self.K)
        # you can also use Xavier Initialization.
        # self.K = np.random.randn(self.F, self.C, self.kH, self.kW) #/(self.K*self.K)
        self.K = np.random.normal(0, 1, (self.F, self.C, self.kH, self.kW))
        self.b = np.zeros((1, self.F))  # ,1))
        self.params = [self.K, self.b]
        self.grads = [np.zeros_like(self.K), np.zeros_like(self.b)]
        self.X = None
        self.reset_parameters()

    def reset_parameters(self):
        kaiming_uniform(self.K, a=math.sqrt(5))
        if self.b is not None:
            # fan_in, _ = calculate_fan_in_and_fan_out(self.K)
            fan_in = self.C
            bound = 1 / math.sqrt(fan_in)
            self.b[:] = np.random.uniform(-bound, bound, (self.b.shape))

    def forward(self, X):
        # Convert to multi-channel
        self.X = X
        if len(X.shape) == 1:
            X = X.reshape(X.shape[0], 1, 1, 1)
        elif len(X.shape) == 2:
            X = X.reshape(X.shape[0], X.shape[1], 1, 1)
        self.N, self.H, self.W = X.shape[0], X.shape[2], X.shape[3]
        S, P, kH, kW = self.S, self.P, self.kH, self.kW
        self.oH = (self.H - kH + 2 * P) // S + 1
        self.oW = (self.W - kW + 2 * P) // S + 1
        X_shape = (self.N, self.C, self.H, self.W)
        self.X_row = im2row_indices(X, self.kH, self.kW, S=self.S, P=self.P)
        K_col = self.K.reshape(self.F, -1).transpose()
        Z_row = self.X_row @ K_col + self.b  # W_row @ self.X_row + self.b
        Z = Z_row.reshape(self.N, self.oH, self.oW, -1)
        Z = Z.transpose(0, 3, 1, 2)
        return Z

    def __call__(self, x):
        return self.forward(x)

    def backward(self, dZ):
        if len(dZ.shape) <= 2:
            dZ = dZ.reshape(dZ.shape[0], -1, self.oH, self.oW)
        K = self.K
        # flatten dZ into a matrix with the same shape as Z_row
        F = dZ.shape[1]  # Convert (N,F,oH,oW) to (N,oH,oW,F)
        assert F == self.F
        dZ_row = dZ.transpose(0, 2, 3, 1).reshape(-1, F)
        # Calculate the gradient of the loss function with respect to the convolution kernel parameters
        dK_col = np.dot(self.X_row.T, dZ_row)  # X_row.T @ dZ_row
        dK_col = dK_col.transpose(1, 0)  # Change the F channel axis from axis=1 to axis=0
        dK = dK_col.reshape(self.K.shape)
        db = np.sum(dZ, axis=(0, 2, 3))
        db = db.reshape(-1, F)
        # Calculate the gradient of the loss function with respect to the input of the convolution layer
        K_col = K.reshape(K.shape[0], -1).transpose()  # Flattening
        dX_row = np.dot(dZ_row, K_col.T)
        X_shape = (self.N, self.C, self.H, self.W)
        dX = row2im_indices(dX_row, X_shape, self.kH, self.kW, S=self.S, P=self.P)
        dX = dX.reshape(self.X.shape)
        self.grads[0] += dK
        self.grads[1] += db
        return dX

    # -------- add gradient of regular items -----
    def reg_grad(self, reg):
        self.grads[0] += 2 * reg * self.K

    def reg_loss(self, reg):
        return reg * np.sum(self.K**2)

    def reg_loss_grad(self, reg):
        self.grads[0] += 2 * reg * self.K
        return reg * np.sum(self.K**2)
```

#### Gradient Test

Similarly, the gradient test can be used to check whether the code is correct for this convolutional layer:

```
import util

np.random.seed(1)
N, C, H, W = 4, 3, 5, 5
F, kH, kW = 6, 3, 3
oH, oW = 3, 3
x = np.random.randn(N, C, H, W)
y = np.random.randn(N, F, oH, oW)
conv = Conv_fast(C, F, kH, 1, 0)
f = conv.forward(x)
loss, do = util.mse_loss_grad(f, y)
dx = conv.backward(do)

def loss_f():
    f = conv.forward(x)
    loss, do = util.mse_loss_grad(f, y)
    return loss

dW_num = util.numerical_gradient(loss_f, conv.params[0], 1e-6)
diff_error = lambda x, y: np.max(np.abs(x - y) / (np.maximum(1e-8, np.abs(x) + np.abs(y))))
print(diff_error(conv.grads[0], dW_num))
# print("dW", conv.grads[0][:2])
# print("dW_num", dW_num[:2])
```
