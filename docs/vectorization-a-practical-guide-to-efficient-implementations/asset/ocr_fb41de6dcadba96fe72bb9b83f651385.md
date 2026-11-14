```
    [5, 7, 6, 4],
    [7, 3, 1, 2],
    ])
y_np = np.pad(X, [(1, 2), (1, 2)], mode="symmetric")
y_tf = tf.pad(X, [(1, 2), (1, 2)], mode="SYMMETRIC")
# no 'symmetric' mode in the torch.nn.functional.pad
# array([[[7, 7, 1, 4, 4, 4],
#         [7, 7, 1, 4, 4, 4],
#         [5, 5, 7, 6, 4, 6],
#         [7, 7, 3, 1, 2, 2, 1],
#         [7, 7, 3, 1, 2, 2, 1],
#         [5, 5, 7, 6, 4, 4, 6]]>)
```

Both NumPy and PyTorch implement edge or replicate mode, respectively. In this mode, values at the borders along each dimension are repeated. PyTorch's replicate mode has similar limitations as its reflect mode. See Figure 5.10 and the following code snippet for illustrations.

![](bbox=[0.136, 0.463, 0.856, 0.646])

Figure 5.9 Example illustration of symmetric padding. Dashed lines indicate the axes of symmetry.

![](bbox=[0.136, 0.713, 0.856, 0.888])

Figure 5.10 Example illustration of edge or replicate padding.