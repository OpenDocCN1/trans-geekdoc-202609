# 2.2.1 Tips on Specifying the dtypes During Tensor Initialization

Most tensor initializers listed in the previous section should accept an argument dtype where the user can specify the dtypes of the tensors after construction. Using the zeros initializer as an example:

+   For NumPy, x = np.zeros(5, dtype=np.float32) will initialize an array of np.float32 zeros.

+   For TensorFlow, x = tf.zeros(5, dtype=tf.float32) will initialize an array of tf.float32 zeros.

+   For PyTorch, x = torch.zeros(5, dtype=torch.float32) will initialize an array of torch.float32 zeros.

+   Both Tensorflow and PyTorch dtypes are compatible with native Python dtypes. So it is also possible to specify the dtypes using native Python dtypes, although care needs to be taken to make sure desired precision is used. For example, x = tf.zeros(5, dtype=float) is equivalent to x = tf.zeros(5, dtype=tf.float32), which is equivalent to x = tf.zeros(5, dtype=np.float32) (yes, Tensorflow dtypes is also compatible with NumPy's dtypes in many cases), even though native Python's float represents 64-bit floats. However, in PyTorch, x = torch.zeros(5, dtype=float) is equivalent to x = torch.zeros(5, dtype=torch.float64) (using np.float64 will, however, throw an error).

# 2.2.2 Tips on Casting

Casting means to convert one data type to another data type.

+   To cast between data types in NumPy, use x<numpy.ndarray>.astype(np.<dtype>). For example, x = np.array([1, 2, 3]).astype(np.float32) gives array([1., 2., 3.], dtype=float32)

+   To cast between data types in TensorFlow, use tf.cast(<tf.Tensor>x, tf.<dtype>)

+   To cast between data types in PyTorch, use x<torch.Tensor>.type(torch.<dtype>)

# 2.3 Mathematical Operations

Various scientific computing libraries (NumPy, MATLAB, Mathematica, etc.) are built specifically for the purpose of doing mathematical operations. Table 2.3 shows a list of typical mathematical operations that can be used on each element of the tensor in NumPy, Tensorflow, and PyTorch. Note that this table is not meant to be exhaustive of the library.