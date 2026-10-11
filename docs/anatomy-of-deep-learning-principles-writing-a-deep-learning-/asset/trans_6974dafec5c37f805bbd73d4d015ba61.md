
# 执行池化操作

```python
Y_h, Y_w = (X.shape[0] - pool_h + 2 * P_h) // S_h + 1, (X.shape[1] - pool_w + 2 * P_w) // S_w + 1

Y = np.zeros((Y_h, Y_w), dtype=X.dtype)

for i in range(Y.shape[0]):
    hs = i * S_h
    for j in range(Y.shape[1]):
        ws = j * S_w
        if mode == 'max':  # 最大池化
            Y[i, j] = X[hs: hs + pool_h, ws: ws + pool_w].max()
        elif mode == 'avg':
            Y[i, j] = X[hs: hs + pool_h, ws: ws + pool_w].mean()

return Y
```

对于图 6-30 所示的二维矩阵，使用跨度为 3、窗口为 3×3 进行最大值池化和平均池化的结果如下：

```python
X = np.array([[2, 3, 0, 7, 9, 5], [6, 0, 4, 7, 2, 3], [8, 1, 0, 3, 2, 6],
              [7, 6, 1, 5, 2, 8], [9, 5, 1, 8, 3, 7], [2, 4, 1, 8, 6, 5]])

pool2d(X, (3, 3), (3, 3), (0, 0), mode='max')
```

```
array([[8, 9],
       [9, 8]])
```

执行平均池化：

```python
pool2d(X, (3, 3), (3, 3), (0, 0), mode='avg')
```

```
array([[2, 4],
       [4, 5]])
```

同理，对于多通道输入，只需在原池化操作的外层增加多通道遍历循环（`for c in range(Y.shape[0])`）：

```python
def pool(X, pool, stride=(1, 1), padding=(0, 0), mode='max'):
    pool_h, pool_w = pool
    S_h, S_w = stride
    P_h, P_w = padding

    if P_h or P_w:
        X_padded = np.pad(X, [(0, 0), (P_h, P_h), (P_w, P_w)], mode='constant')
    else:
        X_padded = X

    Y_h, Y_w = (X.shape[1] - pool_h + 2 * P_h) // S_h + 1, (X.shape[1] - pool_w + 2 * P_w) // S_w + 1
    Y = np.zeros((X.shape[0], Y_h, Y_w), dtype=X.dtype)

    print(X.shape)
    print(Y.shape)

    for c in range(Y.shape[0]):
        for i in range(Y.shape[1]):
            hs = i * S_h
            for j in range(Y.shape[2]):
                ws = j * S_w
                if mode == 'max':
                    Y[c, i, j] = X[c, hs: hs + pool_h, ws: ws + pool_w].max()
                elif mode == 'avg':
                    Y[c, i, j] = X[c, hs: hs + pool_h, ws: ws + pool_w].mean()

    return Y
```

测试上述多通道输入池化操作函数 `pool()`：

```python
X3 = np.array([[[0, 1, 2], [3, 4, 5], [6, 7, 8]],
               [[11, 2, 3], [4, 1, 16], [71, 8, 9]]])

pool(X3, (2, 2), (1, 1), (0, 0), mode='max')
```

```
(2, 3, 3)
(2, 2, 2)
array([[[ 4,  5],
        [ 7,  8]],

       [[11, 16],
        [71, 16]]])
```

使用 `pool()` 函数和 5×5 窗口以跨度 `(2, 2)` 对图像进行池化，生成的图像尺寸仅为原图的一半。

```python
img = np.moveaxis(lenna_img, -1, 0)  # np.rollaxis(lenna_img, 2, 0)
pooled_img = pool(img, [5, 5], (2, 2))
pooled_img = np.moveaxis(pooled_img, 0, -1)  # 将通道轴从 0 移动到最后一轴 -1
plt.imshow(pooled_img, cmap=plt.cm.gray)

print("Original image size:", img.shape)
print("Result image size:", pooled_img.shape)
```
