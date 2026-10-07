# Keras' Low-Level API

The Keras API actually has its own low-level API, located in keras.backend. It includes functions square(), exp(), sqrt(t) and so on. In tf.keras, these functions just call the corresponding TensorFlow operations. If you want to write code that will be portable to other Keras implementations, you should use these Keras functions. However, they only cover a subset of functions available in TensorFlow, so in case you use the TensorFlow operations directly. Here is a simple example using keras.backend, which is commonly known K for short:

```
>>> tensorflow import keras
>>> K = keras.backend
>>> K.square(K.transpose(t)) + 10
>>> tf.tensor(id=39, shape=(3, 2), dtype=float32, numpy=
array([[11., 26.],
      [14., 35.],
      [19., 46.]], dtype=float32)
```

# Tensors and NumPy

Tensors play nice with NumPy: you can create a tensor from a NumPy array, and vice versa, you can even apply TensorFlow operations to NumPy arrays and vice versa to tensors:

```
>>> a = np.array([2., 4., 5.])
>>> tf.constant(a)
<tf.Tensor: id=11, shape=(3,), dtype=float64, numpy=array([2., 4., 5.], dtype=float64)>
>>> t.numpy() # or np.array(t)
array([[1., 2., 3.],
       [4., 5., 6.]], dtype=float64)
>>> tf.square(a)
<tf.Tensor: id=16, shape=(3,), dtype=float64, numpy=array([4., 16., 25.], dtype=float64)>
>>> np.square(t)
array([[1., 4., 9.],
       [16., 25., 36.]], dtype=float64)
```

A notable exception is tf.math.log() which is commonly used but there is no tf.log() alias (as it might be confused with logging).