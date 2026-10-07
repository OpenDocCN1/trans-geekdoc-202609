Last but not least, TensorFlow has a dedicated team of passionate and helpful developers, and a large community contributing to improving it. To ask technical questions, you should use http://stackoverflow.com/ and tag your question with tensorflow and python. You can find figure bugs and feature requests through GitHub. For general discussions, join the Google group.

Okay, it's time to start coding!

# Using TensorFlow like NumPy

TensorFlow's API revolves around tensors, hence the name Tensor-Flow. A tensor is usually a multidimensional array (exactly like a NumPy ndarray), but it can also hold a scalar (a single value, such as 42). These tensors will be important when we create custom functions, custom metrics, custom layers and more, so let's see how to create and manipulate them.

# Tensors and Operations

You can easily create a tensor, using tf.constant(). For example, here is a tensor representing a matrix with two rows and three columns of floats:

```
>>> tf.constant([[1., 2., 3.], [4., 5., 6]]) # matrix
<tf.Tensor: id=0, shape=(2, 3), dtype=float32, numpy=array([[1., 2., 3.], [4., 5., 6.]], dtype=float32)>
>>> tf.constant(42) # scalar
<tf.Tensor: id=1, shape=(), dtype=int32, numpy=42)
```

Just like an ndarray, a tf.tensor has a shape and a data type (dtype):

```
>>> t = tf.constant([[1., 2., 3.], [4., 5., 6]])
>>> t.shape
TensorShape([2, 3])
>>> t.dtype
float32
```

Indexing works much like in NumPy:

```
>>> t[:, :2]
<tf.Tensor: id=5, shape=(2, 2), dtype=float32, numpy=array([[1., 2.], [4., 5.]], dtype=float32)>
>>> t[..., 1, tf.newaxis]
<tf.Tensor: id=15, shape=(2, 1), dtype=float32, numpy=array([[2.], [5]]], dtype=float32)
```

Most importantly, all sorts of tensor operations are available:

```
>>> t + 10
<tf.Tensor: id=18, shape=(2, 3), dtype=float32, numpy=array([[11., 12., 13.], [14., 15., 16.]], dtype=float32)>
```