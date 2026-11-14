# (a) X[1:3, 1:4, :2]

![](bbox=[0.13, 0.14, 0.81, 0.34])

# (b) X[1:3, 1:4, ::2]

![](bbox=[0.13, 0.44, 0.81, 0.64])

Figure 3.6 Examples of 3D tensor slicing in NumPy, Tensorflow, or PyTorch tensors. (a) Slicing a subset of the tensor elements along the row, column, and depth dimensions: X[1:3, 1:4, :2]; (b) slicing first and third layers of the tensor along the depth dimension, and for each layer (2D matrix), select a subset of elements: X[1:3, 1:4, ::2].

In addition to the syntaxes listed in Table 3.1, there are two additional convenient slicing operators, None (equivalently, np.newaxis in NumPy and tf.newaxis in Tensorflow) and ... (or equivalently Ellipsis, a Python's builtin constant), that can be used only with NumPy, Tensorflow, and PyTorch tensor slicing, but not with Python list. Slicing a dimension with None or np.newaxis adds an extra singleton dimension at the axis of slicing.