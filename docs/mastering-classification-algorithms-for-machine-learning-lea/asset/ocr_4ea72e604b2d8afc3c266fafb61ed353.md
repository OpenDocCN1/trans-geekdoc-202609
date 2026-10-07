# Singular Value Decomposition 305

Now we start the process of compressing the image using the SVD method.

First, we break the image matrix into three matrices - one for each color channel.

# Break the image into three different arrays based on colors

```
image_red = image[:, :, 0]
image_green = image[:, :, 1]
image_blue = image[:, :, 2]
```

Then we perform SVD for each matrix. Let k = 1000.

```
U_r, D_r, VT_r = np.linalg.svd(image_red, full_matrices = True)
U_g, D_g, VT_g = np.linalg.svd(image_green, full_matrices = True)
U_b, D_b, VT_b = np.linalg.svd(image_blue, full_matrices = True)
```

# Check for the bytes to be stored

```
bytesToBeStored = sum([matrix.nbytes for matrix in [U_r, D_r, VT_r, U_g, D_g, VT_g, U_b, D_b, VT_b]])
```

```
print("The matrices that we store have total size (in bytes):",
bytesToBeStored, 'bytes')
```

The matrices that we store have a total size (in bytes): 609710976 bytes

```
k = 1000
```

# Selecting k columns from U and k rows from VT matrix

```
U_r_k = U_r[:, :k]
VT_r_k = VT_r[:k, :]
U_g_k = U_g[:, :k]
VT_g_k = VT_g[:k, :]
U_b_k = U_b[:, :k]
VT_b_k = VT_b[:k, :]
```

```
D_r_k = D_r[:k]
```