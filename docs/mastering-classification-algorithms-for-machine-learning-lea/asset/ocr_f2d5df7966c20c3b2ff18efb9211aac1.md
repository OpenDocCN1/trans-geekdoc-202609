# Singular Value Decomposition

Let us check the space required to store the image:

originalBytes = image.nbytes

print("Space needed to store this image is", originalBytes/1024/1024,
'MB')

Space needed to store this image is 93.0234375 MB

Now, we start the process of compressing the image using the SVD method.

# SVD decomposition

U, D, VT = np.linalg.svd(image, full_matrices = True)

# Check for the bytes to be stored

bytesToBeStored = sum([matrix.nbytes for matrix in [U, D, VT]])

print("The matrix that we store has a total size (in bytes):",
bytesToBeStored)

The matrix that we store has a total size (in bytes): 203269992

We will keep only the first k values in matrix D and set the remaining to 0. Let us
put k = 1000 is much smaller than either of the image's dimensions, which are
4032 and 3024.

```
k = 1000
```

# Selecting k columns from U matrix and k rows from VT matrix

```
U_k = U[:, 0:k]
```

```
VT_k = VT[0:k, :]
```

```
D_k = D[0:k]
```

```
compressedBytes = sum([matrix.nbytes for matrix in [U_k, D_k, VT_k]])
```

```
print("Compressed matrix that we store now has a total size:",
compressedBytes/1024/1024, 'MB')
```

Compressed matrix that we store now has a total size: 53.84063720703125 MB

Let us see how much compression we have achieved.

```
ratio = compressedBytes / originalBytes * 100
```